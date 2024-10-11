---
title: "Revamping ClickOnce Deployments: A Step-by-Step Guide"
date: 2024-10-06T22:07:40.892Z
updated: 2024-10-10T21:28:42.051Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: "This Article Describes Revamping ClickOnce Deployments: A Step-by-Step Guide"
thumbnail: https://thmb.techidaily.com/122fad585a96b844750a62c04c4dce3455583d7dfd3b684b7339ff82c163bd28.jpg
---

## Revamping ClickOnce Deployments: A Step-by-Step Guide

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Click-Once Apps

ClickOnce is a Microsoft deployment technology that facilitates deploying Windows applications.

In one of our previous articles, we discussed [How to Replace the ClickOnce app with MSIX](https://tools.techidaily.com/advancedinstaller/products/). But, what if you want to ["repackage"](https://tools.techidaily.com/advancedinstaller/products/) a ClickOnce application? That's what we'll be covering in this article. 

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)If you want to learn more about repackaging, take a look at our [repackaging best practices](https://tools.techidaily.com/advancedinstaller/products/).

### What are the challenges of repackaging a ClickOnce application?

ClickOnce shares some similarities with MSIX – the main one being that they are **per-user applications**.

**Per-user applications** are kind of difficult to repackage. In general, IT Pros are used to building MSI and EXE packages to be [installed per-machine](https://tools.techidaily.com/advancedinstaller/products/). That means that most of the applications that we find on the market today require administrative rights to be installed. So, most vendors prefer the per-machine method of deploying applications.

This comes as no surprise, since the [per-machine approach](https://tools.techidaily.com/advancedinstaller/products/) makes it much easier to [manage your applications in the infrastructure](https://tools.techidaily.com/advancedinstaller/products/).

One mistake that we see happening very frequently is for IT Pros to convert ClickOnce applications (per-user) to per-machine applications without considering all the issues that could occur during the execution of that particular application.

![Important](https://cdn.advancedinstaller.com/svg/common/IconMessageInfo.svg)Never change the installation type of an application unless you fully understand how it works.

Usually, you want an application to save some settings or running information in files. For per-user applications, most vendors consider placing those setting files near the executable.

The problem comes if you try to convert the application to per-machine. Why? Because users in an infrastructure will probably not have the necessary rights to write in a per-machine location.

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)Some might say that you can always give [additional permissions](https://tools.techidaily.com/advancedinstaller/products/) when you build your package, but that is a security point that needs a deeper discussion.   
For now, let’s consider that additional permissions are not allowed on per-machine installations. Check out the [MSI Permissions Guide: Three Ways to Add Rights With your Installer](https://tools.techidaily.com/advancedinstaller/products/)  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2100537/7443" target="_top" id="2100537">
  <img src="//a.impactradius-go.com/display-ad/7443-2100537" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2100537/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### How to Repackage ClickOnce Applications?

As you will see, repackaging a ClickOnce application is not very different from capturing other types of installers.

1. Open [Advanced Repackager](https://tools.techidaily.com/advancedinstaller/products/) and go through the standard process of repackaging an application. A full tutorial can be found [here](https://tools.techidaily.com/advancedinstaller/products/).
2. Once you repackaged your application, your AIP(Advanced Installer Project) should contain all the files in a per-user location:

![ClickOnce Repackaging](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/clickonce-repackaging.png "ClickOnce Repackaging")  

### Best practices for Per-user applications

There are two main golden rules for per-user applications:

1. Make sure the **self-healing mechanism** is working properly at all times
2. Don’t change an **application installation behavior**

Following the second rule, while using **ClickOnce applications**, we must place files exactly where the original installer places them. In our case, all the files are copied directly into **%appdata%**.

But, how do you address this situation when you have a multiple-user setup on a single machine? 

When you deploy per-user applications within any infrastructure, it takes time before it reaches the user. It also uses up additional bandwidth for the actual installer to be downloaded into the user cache again. So, what do we do in this case?

We need to place all the files in a per-machine folder (e.g. C:\\Program Files\\My App) and copy them for each user when he/she logs into the machine with the Active Setup mechanism.

The challenge here is making sure we also follow golden rule number one: making sure that the self-healing mechanism works. 

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)If you want to read more about it, we already [touched on this subject in this article](https://tools.techidaily.com/advancedinstaller/products/).

When it comes to MSI’s, if the MSI is not present in the original install location and files need to be copied, then the self-healing process fails. That is one of the reasons we are not leaving the files as they were captured (in %appdata) and we are moving them in a per-machine location (C:\\Program FIles\\My App) and then copying them using a [Custom Action](https://tools.techidaily.com/advancedinstaller/products/).

One other aspect we need to consider is the shortcut. In our example, the shortcut is placed under each user Start Menu folder, located in:

C:\Users\YOUR USER\AppData\Roaming\Microsoft\Windows\Start Menu

Copy

To make it easier, we will place the shortcut on a per-user machine, but the [target of the shortcut](https://tools.techidaily.com/advancedinstaller/products/) will point to %appdata%, meaning it will open the executable from each user location.

### How to adjust the package?

Knowing what we know now, we can adjust the package.

1\. Let's first move all the files into the Application folder:

![ClickOnce Application Folder](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/clickonce-application-folder.png "ClickOnce Application Folder")  

<!-- affiliate ads begin -->
<span id="1265663">
					<video width="240" height="200" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1265663.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/4482-1265663">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1265663.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:150px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fmartinic.evyy.net%2Fc%2F5597632%2F1265663%2F4482'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1265663/4482" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

2\. Now that the files are placed on a per-machine location (C:\\Program Files (x86)\\Caphyon\\ClickOnce App Repackaged), it’s time to add the Custom Action that will copy the files during the [Active Setup](https://tools.techidaily.com/advancedinstaller/products/). To do this, navigate to the [Custom Actions Page](https://tools.techidaily.com/advancedinstaller/products/) and add a new “Launch attached file” action. For this, we are using this simple VBScript:

Option Explicit
Dim fso, objWShell, appData
Set fso = CreateObject("Scripting.FileSystemObject")
Set objWShell = WScript.CreateObject("WScript.Shell")
appData = objWShell.expandEnvironmentStrings("%APPDATA%")
fso.CopyFile "C:\Program Files (x86)\Caphyon\ClickOnce App Repackaged\*.*", appData + "\"

Copy

3\. Once you have selected the VBScript, configure the rest of the settings, as shown below:

![ClickOnce Custom Action](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/clickonce-custom-action.png "ClickOnce Custom Action")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1896560/19272" target="_top" id="1896560">
  <img src="//a.impactradius-go.com/display-ad/19272-1896560" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1896560/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

4\. The next step is to implement a simple Active Setup into the MSI. In Advanced Installer,navigate to the [Product Details page](https://tools.techidaily.com/advancedinstaller/products/) and click on the Active Setup tab. 

5\. There, click on **New** and only change the **Stub Path** from /fou to /fus and click **OK**.

![ClickOnce Active Setup](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/clickonce-active-setup.png "ClickOnce Active Setup")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2037345/7443" target="_top" id="2037345">
  <img src="//a.impactradius-go.com/display-ad/7443-2037345" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2037345/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

6\. Now, the package is installing on a per-machine location and we have an Active Setup which will trigger the Custom Action that is introduced to copy the files to a per-user location once a user logs in. 

7\. The final step is to adjust the shortcut to point to the correct executable location. This is a two step process. 

7.1 First, navigate to the [Properties page](https://tools.techidaily.com/advancedinstaller/products/) and create a new property that looks something like this:

![ClickOnce Property](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/clickonce-property.png "ClickOnce Property")  

7.2 Once we have the property created, navigate to the [Shortcuts Page](https://tools.techidaily.com/advancedinstaller/products/) and create a new “External File” shortcut. The most important part here is to define the **Shortcut Targetdir** to point to:

[SHORPATH]\Sample.exe

Copy

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)SHORPATH is the property we previously created, replace it with the property name you have created in your project.

<!-- affiliate ads begin -->
<span id="1993652">
					<video width="576" height="240" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1993652.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/22993-1993652">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1993652.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:360px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fhomestyler.sjv.io%2Fc%2F5597632%2F1993652%2F22993'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1993652/22993" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

8\. At the end, the shortcut should look something like this:

![ClickOnce Shortcut](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/clickonceshortcut.png "ClickOnce Shortcut")  

As you can see, the shortcut is placed on a per-machine location, but the target of the shortcut will point at the end to %appdata%\\Sample.exe:

![Shortcut Properties](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/shortcut-properties.png "Shortcut Properties")

<ins class="adsbygoogle"
     style="display:block"
     data-ad-format="autorelaxed"
     data-ad-client="ca-pub-7571918770474297"
     data-ad-slot="1223367746"></ins>

<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-7571918770474297"
     data-ad-slot="8358498916"
     data-ad-format="auto"
     data-full-width-responsive="true"></ins>

<span class="atpl-alsoreadstyle">Also read:</span>
<div><ul>
<li><a href="https://tiktok-video-recordings.techidaily.com/updated-in-2024-select-best-tiktok-video-apps-reviewed/"><u>[Updated] In 2024, Select Best TikTok Video Apps Reviewed</u></a></li>
<li><a href="https://some-tips.techidaily.com/updated-the-metaverse-unraveled-explore-these-6-vivid-models/"><u>[Updated] The Metaverse Unraveled Explore These 6 Vivid Models</u></a></li>
<li><a href="https://win-updates.techidaily.com/demystifying-the-mrbeast-prize-scheme-tips-for-staying-safe-from-potential-frauds/"><u>Demystifying the MrBeast Prize Scheme: Tips for Staying Safe From Potential Frauds</u></a></li>
<li><a href="https://twitter-videos.techidaily.com/in-2024-how-to-keep-the-momentum-ios-and-android-gif-savings/"><u>In 2024, How to Keep the Momentum IOS & Android GIF Savings</u></a></li>
<li><a href="https://activate-lock.techidaily.com/in-2024-how-to-successfully-bypass-icloud-activation-lock-from-apple-iphone-13-by-drfone-ios/"><u>In 2024, How to Successfully Bypass iCloud Activation Lock from Apple iPhone 13</u></a></li>
<li><a href="https://meme-emoji.techidaily.com/new-how-to-add-emojis-to-discord-for-2024/"><u>New How to Add Emojis To Discord for 2024</u></a></li>
<li><a href="https://win-updates.techidaily.com/tailored-vs-universal-choosing-between-user-or-machine-based-app-setup/"><u>Tailored Vs. Universal: Choosing Between User or Machine Based App Setup</u></a></li>
<li><a href="https://win-updates.techidaily.com/top-6-fantastic-tools-to-sharpen-your-images-in-2n2-free-and-premium-options-available/"><u>Top 6 Fantastic Tools to Sharpen Your Images in 2N2 - Free and Premium Options Available</u></a></li>
<li><a href="https://win-updates.techidaily.com/top-8-secure-password-management-tools-compatible-with-windows-10/"><u>Top 8 Secure Password Management Tools Compatible with Windows 10</u></a></li>
<li><a href="https://win-updates.techidaily.com/transferring-iphone-visuals-onto-desktop-techniques-and-tools-for-easy-display-syncing/"><u>Transferring iPhone Visuals Onto Desktop: Techniques and Tools for Easy Display Syncing</u></a></li>
<li><a href="https://win-howtos.techidaily.com/troubleshooting-fixing-computer-unable-to-power-off-in-windows-10-solution/"><u>Troubleshooting: Fixing Computer Unable to Power Off in Windows 10 - SOLUTION</u></a></li>
</ul></div>

