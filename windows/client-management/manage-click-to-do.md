---
title: Manage Click to Do for Windows clients
description: Learn how to manage Click to Do for commercial environments and about Click to Do features.
ms.topic: how-to
ms.subservice: windows-copilot
ms.date: 04/24/2025
ms.author: mstewart
author: mestew
ms.collection:
  - windows-copilot
  - magic-ai-copilot
appliesto:
- ✅ <a href="https://www.microsoft.com/windows/business/devices/copilot-plus-pcs#copilot-plus-pcs" target="_blank">Copilot+ PCs</a>
---

# Manage Click to Do
<!--9687427, 9608247-->
>**Looking for consumer information?** See [Click to Do: do more with what's on your screen](https://support.microsoft.com/topic/6848b7d5-7fb0-4c43-b08a-443d6d3f5955).

Click to Do (preview) helps users to get things done faster by identifying text and images that are currently on their screen so they can perform actions on them. This article provides information about Click to Do and how to manage it in a commercial environment.

> [!NOTE]
> - Click to Do is behind [temporary enterprise feature control](/windows/whats-new/temporary-enterprise-feature-control) and will be enabled when the next annual feature update is installed. To enable Click to Do, use the **Enable features introduced via servicing that are off by default** policy setting. For more information, see [Enable features introduced via servicing that are off by default](/windows/deployment/update/waas-configure-wufb#enable-features-introduced-via-servicing-that-are-off-by-default). <!--10088089-->
> - In-market commercial devices are defined as devices with an Enterprise (ENT) or Education (EDU) SKU or any premium SKU device that is managed by an IT administrator (whether via Microsoft Endpoint Manager or other endpoint management solution), has a volume license key, or is joined to a domain. Commercial devices during Out of Box Experience (OOBE) are defined as those with ENT or EDU SKU or any premium SKU device that has a volume license key or is Microsoft Entra joined. 
> - Click to Do is optimized for select languages English, Chinese (simplified), French, German, Japanese, and Spanish. Content-based and storage limitations apply. For more information, see [https://aka.ms/copilotpluspcs](https://aka.ms/copilotpluspcs).


## What is Click to Do?

Click to Do (preview) analyzes what's on the screen and then allows users to choose the text or image they want to take action on. Users can open Click to Do by using **Windows key** + **Q** or with **Windows key** + **mouse click**. Other entry points for Click to Do include right swipe on touch enabled PCs, Snipping Tool, search results, and the Start menu.

The analysis of screenshots is always performed locally on the device. Analysis only begins after users actively engage with Click to Do and ends when they exit Click to Do. Click to Do only identifies text and images, not the content of those text or images. It doesn't analyze any content in, for example, minimized applications that aren't on the screen.  
 
Content is only shared if users choose to complete an action like **Search the web**. When Click to Do is active, the cursor is blue and white. The cursor also changes shape depending on the type of info beneath it. What users can do with the info changes based on what kind of content Click to Do detects. For instance, users can perform actions on text such as copy, summarize or rewrite it, or share it. For images, users can perform actions such as copy, save, or blurring the background using Microsoft Photos.

:::image type="content" source="images/9687427-text-actions-click-to-do.png" alt-text="Screenshot of the text actions in Click to Do" lightbox="images/9687427-text-actions-click-to-do.png":::


## System requirements

Click to Do has the following minimum requirements:

- A [Copilot+ PC](https://aka.ms/copilotpluspcs)
  - 40 TOPs NPU ([neural processing unit](https://support.microsoft.com/windows/all-about-neural-processing-units-npus-e77a5637-7705-4915-96c8-0c6a975f9db4))
  - 16 GB RAM
  - 8 logical processors
  - 256 GB storage capacity

To display the Click to Do entry point from Snipping Tool, Snipping Tool version 11.2411.20.0, or later is required. 

The more intelligent text actions are available only on Snapdragon-powered Copilot+ PCs today when your language is set to English with support for AMD and Intel-powered Copilot+ PCs coming soon. 


## Configure policy for Click to Do

When activated, Click to Do takes a screenshot of the user's screen and analyzes it to present actions. Click to Do ends when users exit it, and it can't take screenshots while closed. Screenshot analysis is always performed locally on the device. By default, Click to Do is enabled for users.

The policy setting below allows you to determine whether Click to Do is available for users on their device:

| &nbsp; | Setting  |
|---|---|
| **CSP** | ./Device/Vendor/MSFT/Policy/Config/WindowsAI/[DisableClickToDo](mdm/policy-csp-windowsai.md#disableclicktodo) </br></br> ./User/Vendor/MSFT/Policy/Config/WindowsAI/[DisableClickToDo](mdm/policy-csp-windowsai.md#disableclicktodo)|
| **Group policy** | Computer Configuration > Administrative Templates > Windows Components > Windows AI > **Disable Click to Do** </br></br>User Configuration > Administrative Templates > Windows Components > Windows AI > **Disable Click to Do**|

- When the policy is enabled, the Click to Do component and entry points won't be available to users.
- When the policy is disabled or not configured, users will have Click to Do available on their device.

> [!Important]
> - This policy doesn't affect Click to Do in Recall. For more information, see [Manage Recall](manage-recall.md).
> - If a user prefers to disable Click to Do on their device, they can turn it **Off** using the **Click to Do** setting under **Settings** > **Privacy & security** > **Click to Do**. <!--10088089-->

## Click to Do privacy considerations  

When you choose to send info from Click to Do to an app, like Paint, Click to Do will temporarily save this info in order to complete the transfer. Click to Do creates a temporary file in the following location: 

- `C:\Users\{username}\AppData\Local\Temp`

Temporary files may also be saved when you choose send feedback. These temporary files aren't saved long term. Click to Do doesn't keep any content from your screen after completing the requested action, but some [diagnostic data](/windows/privacy/configure-windows-diagnostic-data-in-your-organization) is gathered to keep Click to Do secure, up to date, and working.

Click to Do's more intelligent text actions, including **Summarize**, **Rewrite (Casual)**, **Rewrite (Formal)**, **Rewrite (Refine)**, and **Create a bulleted list** are powered by a state-of-the-art small language model called Phi Silica. Phi Silica leverages the NPU and the language model runs locally on Copilot+ PCs. Phi Silica ships inbox with Windows on Copilot+ PCs. 

When a user clicks on the Click to Do text actions, the selected text and the chosen action are sent to Phi Silica as part of a prompt. Phi Silica intelligently rewrites the selected text as per the user's request and streams back the response from the model. Phi Silica provides responses quickly and efficiently, using little power. For more information, see [Phi Silica, small but mighty on-device SLM](https://blogs.windows.com/windowsexperience/?p=179250). 

In keeping with Microsoft's commitment to data privacy and security, all saved images and processed data are kept on the device and processed locally. However, Click to Do allows you to choose if you want to get more information about your selected content online. When you choose one of the following Click to Do actions, the selected content is sent to the online provider from your local device to complete your request:

- **Search the web**: Sends the selected content to Bing using Microsoft Edge
- **Open website**: Opens the selected website in your default browser
-	**Visual search with Bing**: Sends the selected content to [Bing visual search](https://support.microsoft.com/topic/62771a0c-4daa-47e4-a9f7-e1bfa85f0d7c) using your default browser



## Microsoft's commitment to responsible AI and Privacy
 
Microsoft has been working to advance AI responsibly since 2017, when we first defined our AI principles and later operationalized our approach through our Responsible AI Standard. Privacy and security are core principles as we develop and deploy AI systems. We work to help our customers use our AI products responsibly, sharing our learnings, and building trust-based partnerships. For more about our responsible AI efforts, the principles that guide us, and the tools and capabilities we've created to assure that we develop AI technology responsibly, see [Responsible AI](https://www.microsoft.com/ai/responsible-ai).

To provide clarity on how each AI feature works, it's important for you to understand its capabilities and limitations. You should understand the choices available to you in an AI feature and the responsibility associated with those choices. 

Click to Do suggests actions that you can take, and you can choose the apps that will be the provider (if applicable) for those actions. Once you choose the action and provider for the action, the results from that action are the responsibility of the provider. For example, from Click to Do you can choose the action Remove background with Paint, which means you've chosen Paint as the provider for the action. Once you have selected the action from the Click to Do context menu, it launches the Paint app and the selected image is processed by Paint.


Click to Do uses optical character recognition (OCR) on your PC to detect text entities on screenshots. For more information about OCR, see [Transparency note and use cases for OCR](/legal/cognitive-services/computer-vision/ocr-transparency-note). 

Click to Do's intelligent text actions use a small language model called Phi Silica. For more information on Phi Silica, see [Get started with Phi Silica in the Windows App SDK](/windows/ai/apis/phi-silica#responsible-ai). For information about the Responsible AI principles guiding Phi Silica deployment and the safety measures in place when using generative language models, see [Responsible Generative AI Development on Windows](/windows/ai/rai). 


Click to Do's models have undergone fairness assessments, alongside comprehensive responsible AI, security and privacy assessments, to make sure the technology is effective and equitable while adhering to Microsoft's Responsible AI best practices.

## Related links

- [Policy CSP - WindowsAI](/windows/client-management/mdm/policy-csp-windowsai)
- [Responsible AI](https://www.microsoft.com/ai/responsible-ai)