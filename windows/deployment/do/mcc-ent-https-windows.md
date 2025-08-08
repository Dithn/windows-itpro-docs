---
title: Configure HTTPS Support for Windows
description: Details on how to configure HTTPS support Microsoft Connected Cache for Enterprise and Education cache nodes on Windows.
ms.service: windows-client
ms.subservice: itpro-updates
ms.topic: how-to
manager: naengler
ms.author: adityamiddha
author: adityamiddha
appliesto: 
- ✅ <a href=https://learn.microsoft.com/windows/release-health/supported-versions-windows-client target=_blank>Windows 11</a>
- ✅ Supported Linux distributions
- ✅ <a href=https://learn.microsoft.com/windows/deployment/do/waas-microsoft-connected-cache target=_blank>Microsoft Connected Cache for Enterprise</a> 
ms.date: 07/23/2025
---

# Enable HTTPS support for Microsoft Connected Cache on Windows

This article provides step-by-step instructions for enabling HTTPS support on Microsoft Connected Cache for Enterprise nodes running on Windows with WSL (Windows Subsystem for Linux).

## Prerequisites

Before enabling HTTPS functionality, ensure your cache node has been migrated to support HTTPS.

1. In Azure portal, under **Cache Node Management**, find the cache node you wish to enable HTTPS on.
2. Verify that the node has been migrated by checking that "Yes" appears in the **Migrated** column.
3. If not migrated, select the cache node, navigate to the **Deployment** tab, and follow the instructions to redeploy Connected Cache.

## Generate a Certificate Signing Request (CSR)

1. Open PowerShell as Administrator and navigate to the PowerShell scripts folder.

   Run the following command to locate the scripts folder:

   ```powershell
   cd (deliveryoptimization-cli mcc-get-scripts-path)
   ```

2. Configure the parameters for `generateCsr.ps1` and run the script.

   ### Parameters for generateCsr.ps1

    **Basic Syntax**

    ```powershell
    .\generateCsr.ps1 [Required Parameters] [Subject Parameters] [SAN Parameters]
    ```

    **Required Parameters**

    | Parameter | Type | Description |
    |-----------|------|-------------|
    | `-RunTimeAccountName` | String | Username from your PowerShell credential object |
    | `-LocalAccountCredential` | PSCredential | Complete PowerShell credential object |
    | `-algo` | String | Certificate algorithm: `RSA`, `EC`, `ED25519`, or `ED448` |
    | `-keySizeOrCurve` | String | For RSA: key size (`2048`, `3072`, `4096`). For EC: curve name (`prime256v1`, `secp384r1`) |
    | `-csrName` | String | Name for the generated CSR file |

    > [!NOTE]
    > If using gMSA (Group Managed Service Account), use `-mccRunTimeAccount $User` instead of the `RunTimeAccountName` and `LocalAccountCredential` parameters.

    **Subject Parameters**

    | Parameter | Required | Description | Example |
    |-----------|----------|-------------|---------|
    | `-subjectCommonName` | Yes | Common name for the certificate | `"localhost"`, `"example.com"` |
    | `-subjectCountry` | No | Two-letter country code | `"US"`, `"CA"`, `"GB"` |
    | `-subjectState` | No | State or province | `"WA"`, `"TX"`, `"Ontario"` |
    | `-subjectOrg` | No | Organization name | `"MyCompany"`, `"ACME Corp"` |

    **Subject Alternative Names (choose at least one)**

    | Parameter | Description | Example |
    |-----------|-------------|---------|
    | `-sanDns` | DNS names (comma-separated) | `"localhost,example.com,api.example.com"` |
    | `-sanIp` | IP addresses (comma-separated) | `"127.0.0.1,192.168.1.100"` |
    | `-sanUri` | URIs (comma-separated) | `"https://example.com,http://localhost"` |
    | `-sanEmail` | Email addresses (comma-separated) | `"admin@example.com,user@domain.com"` |
    | `-sanRid` | Registered IDs (comma-separated) | |
    | `-sanDirName` | Directory names (comma-separated) | |
    | `-sanOtherName` | Other names (comma-separated) | |

   ### Subject Alternative Name (SAN) considerations

    When configuring SAN options, consider how your clients are configured to reach MCC. The certificate on the Connected Cache node must match the exact hostname or IP address used by the client.

    - If clients are configured to connect via IP address, your certificate must include that IP in the SAN.
    - If clients use a DNS name, the SAN must include that DNS name.

   ### Examples

    **Full Certificate with Multiple Components**

      ```powershell
        .\generateCsr.ps1 `
          -RunTimeAccountName $myLocalAccountCredential.Username `
          -LocalAccountCredential $myLocalAccountCredential `
          -algo RSA `
          -keySize 2048 `
          -csrName "myservercsr" `
          -subjectCountry "US" `
          -subjectState "WA" `
          -subjectOrg "MyOrg" `
          -subjectCommonName "localhost" `
          -sanDns "localhost,example.com" `
          -sanIp "127.0.0.1,192.168.1.100"
      ```

    **Minimal Certificate with Common Name Only**

      ```powershell
        .\generateCsr.ps1 `
          -RunTimeAccountName $myLocalAccountCredential.Username `
          -LocalAccountCredential $myLocalAccountCredential `
          -algo EC `
          -keySize prime256v1 `
          -csrName "webapp" `
          -subjectCommonName "webapp.company.com" `
          -sanDns "webapp.company.com,api.company.com"
      ```

    **RSA Certificate with Email SAN**

      ```powershell
        .\generateCsr.ps1 `
          -RunTimeAccountName $myLocalAccountCredential.Username `
          -LocalAccountCredential $myLocalAccountCredential `
          -algo RSA `
          -keySize 3072 `
          -csrName "emailcert" `
          -subjectCommonName "John Doe" `
          -subjectOrg "ACME Corporation" `
          -sanEmail "john.doe@acme.com,admin@acme.com"
      ```

3. Validate that the CSR generation process completed successfully.

   If you encounter errors, locate the timestamped `generateCSR.log` file in the folder specified in the script output. Look for the output line that starts with "You can find logs here: ..."

4. Locate the generated CSR file in your Certificates folder and transfer it if necessary.

   The CSR file location is specified in the script output, starting with "CSR file created at: ..."

## Sign the CSR

1. Select a public or enterprise Certificate Authority (CA) to sign the CSR.

   > [!IMPORTANT]
   > The CA signature must match a root certificate in the client's trusted root store.

   Most customers utilize their enterprise PKI infrastructure for this process. If you need to use a public CA, consider these resources:
   - [DigiCert Certificate Utility](https://www.digicert.com/kb/util/import-code-signing-certificate-digicert-utility.htm)
   - [Let's Encrypt CSR Process](https://community.letsencrypt.org/t/how-to-obtain-a-ssl-certificate-from-lets-encrypt-with-a-csr/15942)

2. Submit your CSR to your chosen CA and save the signed certificate.

   The certificate must meet these requirements:
   - **File type**: .crt
   - **Format**: X.509

   If your CA doesn't support .crt files:
   1. Request a Base64-encoded .cer or .pem file
   2. Convert to .crt by renaming the file extension or using OpenSSL

3. Move your signed certificate to the **Certificates folder** on your cache node (the same folder where you found your generated CSR).

## Import signed TLS certificate

1. Open PowerShell as Administrator and navigate to the PowerShell scripts folder.

2. Configure the parameters for `importCert.ps1` and run the script.

   ### Parameters for importCert.ps1

    **Basic Syntax**

    ```powershell
    .\importCert.ps1 [Required Parameters]
    ```

    **Required Parameters**

    | Parameter | Type | Description |
    |-----------|------|-------------|
    | `-certName` | String | Complete filename of your signed TLS certificate (with or without .crt extension) |
    | `-RunTimeAccountName` | String | Username from your PowerShell credential object |
    | `-LocalAccountCredential` | PSCredential | Complete PowerShell credential object |

    > [!NOTE]
    > If using gMSA, use `-mccRunTimeAccount $User` instead of the `RunTimeAccountName` and `LocalAccountCredential` parameters.

    **Example**

    ```powershell
    .\importCert.ps1 `
      -RunTimeAccountName $myLocalAccountCredential.Username `
      -LocalAccountCredential $myLocalAccountCredential `
      -certName "myTlsCert.crt"
    ```

3. Validate that the import process completed successfully.

   If you encounter errors, locate the timestamped `importCert.log` file in the folder specified in the script output. Look for the output line that starts with "You can find logs here: ..."

### Test HTTPS content retrieval

1. Configure port forwarding and open port 443 on your firewall.

   **Port Forwarding**

   ```powershell
   $ipFilePath = Join-Path ([System.Environment]::GetEnvironmentVariable("MCC_INSTALLATION_FOLDER", "Machine")) "wslIp.txt"
   $ipAddress = (Get-Content $ipFilePath | Select-Object -First 1).Trim()
   netsh interface portproxy add v4tov4 listenport=443 listenaddress=0.0.0.0 connectport=443 connectaddress=$ipAddress
   ```

   **Firewall Rules**

   ```powershell
   [void](New-NetFirewallRule -DisplayName "WSL2 Port Bridge (HTTPS)" -Direction Inbound -Action Allow -Protocol TCP -LocalPort "443")
   [void](New-NetFirewallRule -DisplayName "WSL2 Port Bridge (HTTPS)" -Direction Outbound -Action Allow -Protocol TCP -LocalPort "443")
   ```

2. Test HTTP and HTTPS content downloads.

   > [!NOTE]
   > Based on the subject/SAN parameters you configured, determine how you want to connect to the test server. The certificate must match the exact hostname or IP address used by the client.

   Run the following curl commands to test both protocols:

   **HTTPS Test**

   ```powershell
   curl.exe -v -o NUL "https://[insert-connection-option]/ee344de8-d177-4720-86c1-a076581766f9/070a8fd4-79a7-42c8-b7c8-9883253bb01a/c7b1b825-88b2-4e66-9b15-ff5fe0374bc6.appxbundle.bin" --include -H "host:swda01-mscdn.manage.microsoft.com"
   ```

   **HTTP Test**

   ```powershell
   curl.exe -v -o NUL "http://[insert-connection-option]/ee344de8-d177-4720-86c1-a076581766f9/070a8fd4-79a7-42c8-b7c8-9883253bb01a/c7b1b825-88b2-4e66-9b15-ff5fe0374bc6.appxbundle.bin" --include -H "host:swda01-mscdn.manage.microsoft.com"
   ```

    **Troubleshooting**

    If you encounter issues during testing downloads:

    - Use `-v -k -o NUL` with curl to check if your certificate can be validated
    - Use `-v --ssl-no-revoke -o NUL` with curl to check if your signing CA has an inaccessible revocation check

## Disable HTTPS support

If you need to revert your Connected Cache to HTTP-only communication, follow these steps. This process won't delete anything in the Certificates folder, including CSR files, certificates, and logs.

1. Open PowerShell as Administrator and navigate to the PowerShell scripts folder.

2. Configure the parameters for `disableTls.ps1` and run the script.

   ### Parameters for disableTls.ps1

    **Basic Syntax**

    ```powershell
    .\disableTls.ps1 [Required Parameters]
    ```

    **Required Parameters**

    | Parameter | Type | Description |
    |-----------|------|-------------|
    | `-RunTimeAccountName` | String | Username from your PowerShell credential object |
    | `-LocalAccountCredential` | PSCredential | Complete PowerShell credential object |

    > [!NOTE]
    > If using gMSA, use `-mccRunTimeAccount $User` instead of the `RunTimeAccountName` and `LocalAccountCredential` parameters used for local user accounts.

    **Example**

    ```powershell
    .\disableTls.ps1 `
      -RunTimeAccountName $myLocalAccountCredential.Username `
      -LocalAccountCredential $myLocalAccountCredential `
    ```

3. Validate that the disable process completed successfully.

4. Test HTTP and HTTPS content downloads to confirm the configuration.

   After disabling HTTPS, HTTP requests should work while HTTPS requests should fail:

   ```powershell
   curl.exe -v -o NUL "https://[insert-connection-option]/ee344de8-d177-4720-86c1-a076581766f9/070a8fd4-79a7-42c8-b7c8-9883253bb01a/c7b1b825-88b2-4e66-9b15-ff5fe0374bc6.appxbundle.bin" --include -H "host:swda01-mscdn.manage.microsoft.com"
   
   curl.exe -v -o NUL "http://[insert-connection-option]/ee344de8-d177-4720-86c1-a076581766f9/070a8fd4-79a7-42c8-b7c8-9883253bb01a/c7b1b825-88b2-4e66-9b15-ff5fe0374bc6.appxbundle.bin" --include -H "host:swda01-mscdn.manage.microsoft.com"
   ```

## Next steps

- [HTTPS support overview](mcc-ent-https-overview.md)
- [Troubleshooting Connected Cache](mcc-ent-troubleshooting.md)


