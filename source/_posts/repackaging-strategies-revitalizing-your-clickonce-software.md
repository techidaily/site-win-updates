---
title: "Repackaging Strategies: Revitalizing Your ClickOnce Software"
date: 2024-10-03T21:41:27.083Z
updated: 2024-10-10T17:29:09.415Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: "This Article Describes Repackaging Strategies: Revitalizing Your ClickOnce Software"
thumbnail: https://thmb.techidaily.com/e95b10a90432b136a95f53788d2f6a34587f22e1538a737ba31a5504b6070516.jpg
---

## Repackaging Strategies: Revitalizing Your ClickOnce Software

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

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2135363/19272" target="_top" id="2135363">
  <img src="//a.impactradius-go.com/display-ad/19272-2135363" border="0" alt="https://techidaily.com" width="120" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2135363/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Usually, you want an application to save some settings or running information in files. For per-user applications, most vendors consider placing those setting files near the executable.

The problem comes if you try to convert the application to per-machine. Why? Because users in an infrastructure will probably not have the necessary rights to write in a per-machine location.

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)Some might say that you can always give [additional permissions](https://tools.techidaily.com/advancedinstaller/products/) when you build your package, but that is a security point that needs a deeper discussion.   
For now, let’s consider that additional permissions are not allowed on per-machine installations. Check out the [MSI Permissions Guide: Three Ways to Add Rights With your Installer](https://tools.techidaily.com/advancedinstaller/products/)  

<!-- affiliate ads begin -->
<a href="https://unicoeye.pxf.io/c/5597632/2148772/18498" target="_top" id="2148772">
  <img src="//a.impactradius-go.com/display-ad/18498-2148772" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://unicoeye.pxf.io/i/5597632/2148772/18498" style="position:absolute;visibility:hidden;" border="0" />
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

4\. The next step is to implement a simple Active Setup into the MSI. In Advanced Installer,navigate to the [Product Details page](https://tools.techidaily.com/advancedinstaller/products/) and click on the Active Setup tab. 

5\. There, click on **New** and only change the **Stub Path** from /fou to /fus and click **OK**.

![ClickOnce Active Setup](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/clickonce-active-setup.png "ClickOnce Active Setup")  

<!-- affiliate ads begin -->
<a href="https://ephamedtechinc.pxf.io/c/5597632/2130530/26400" target="_top" id="2130530">
  <img src="//a.impactradius-go.com/display-ad/26400-2130530" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://ephamedtechinc.pxf.io/i/5597632/2130530/26400" style="position:absolute;visibility:hidden;" border="0" />
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
<span id="1498635">
					<video width="320" height="320" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1498635.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/17326-1498635">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1498635.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:200px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fancheer.sjv.io%2Fc%2F5597632%2F1498635%2F17326'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1498635/17326" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

8\. At the end, the shortcut should look something like this:

![ClickOnce Shortcut](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/clickonceshortcut.png "ClickOnce Shortcut")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2037335/7443" target="_top" id="2037335">
  <img src="//a.impactradius-go.com/display-ad/7443-2037335" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2037335/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

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
<li><a href="https://extra-approaches.techidaily.com/updated-maintain-eye-contact-this-helps-establish-rapport-with-the-speaker-and-shows-your-engagement/"><u>[Updated] Maintain Eye Contact This Helps Establish Rapport with the Speaker and Shows Your Engagement</u></a></li>
<li><a href="https://buynow-info.techidaily.com/arias-novelty-in-audio-wearables/"><u>Aria's Novelty in Audio Wearables</u></a></li>
<li><a href="https://win-updates.techidaily.com/best-techniques-for-professional-audio-capture-on-a-windows-10-pc/"><u>Best Techniques for Professional Audio Capture on a Windows 10 PC</u></a></li>
<li><a href="https://win-updates.techidaily.com/complete-step-by-step-guide-to-screen-record-functionality-on-ios-11-devices/"><u>Complete Step-by-Step Guide to Screen Record Functionality on iOS 11 Devices</u></a></li>
<li><a href="https://tech-renaissance.techidaily.com/easy-fixes-for-when-rockalldlldll-is-mia-a-comprehensive-error-handling-tutorial/"><u>Easy Fixes for When Rockalldll.dll Is MIA: A Comprehensive Error Handling Tutorial</u></a></li>
<li><a href="https://phone-solutions.techidaily.com/easy-steps-to-recover-deleted-music-from-itel-p40-by-fonelab-android-recover-music/"><u>Easy steps to recover deleted music from Itel P40</u></a></li>
<li><a href="https://win-updates.techidaily.com/effective-methods-for-packaging-applications-using-a-repacker/"><u>Effective Methods for Packaging Applications Using a Repacker</u></a></li>
<li><a href="https://win-updates.techidaily.com/evaluating-the-security-of-microsofts-latest-os-a-comprehensive-guide-to-windows-11-safety/"><u>Evaluating the Security of Microsoft's Latest OS: A Comprehensive Guide to Windows 11 Safety</u></a></li>
<li><a href="https://technical-tips.techidaily.com/guide-on-dealing-with-microsoft-word-files-that-wont-load/"><u>Guide on Dealing with Microsoft Word Files That Won't Load</u></a></li>
<li><a href="https://win-blog.techidaily.com/how-to-repair-a-broken-link-in-terraria-5-effective-methods/"><u>How To Repair A Broken Link In Terraria - 5 Effective Methods</u></a></li>
<li><a href="https://win-updates.techidaily.com/how-to-transfer-your-free-iphone-tracks-to-pc-or-mac-without-costs/"><u>How to Transfer Your Free iPhone Tracks to PC or Mac Without Costs</u></a></li>
<li><a href="https://win-updates.techidaily.com/identifying-fraudulent-android-applications-expert-tips-from-malwarefox/"><u>Identifying Fraudulent Android Applications: Expert Tips From MalwareFox</u></a></li>
<li><a href="https://win-updates.techidaily.com/protect-your-chrome-from-malicious-notification-attacks-essential-tips/"><u>Protect Your Chrome From Malicious Notification Attacks: Essential Tips</u></a></li>
<li><a href="https://win-updates.techidaily.com/revive-your-missing-office-documents-expert-strategies-for-restoring-deleted-file-versions/"><u>Revive Your Missing Office Documents: Expert Strategies for Restoring Deleted File Versions</u></a></li>
<li><a href="https://discover-bytes.techidaily.com/step-by-step-guide-converting-your-vimeo-videos-into-various-formats-like-mov-mp4-and-more/"><u>Step-by-Step Guide: Converting Your Vimeo Videos Into Various Formats Like MOV, MP4, and More</u></a></li>
<li><a href="https://extra-tips.techidaily.com/the-cutting-edge-of-cinematography-kinemasters-zoom-excellence/"><u>The Cutting Edge of Cinematography Kinemaster’s Zoom Excellence</u></a></li>
<li><a href="https://tech-revival.techidaily.com/transformation-gratuite-de-fichiers-jpg-en-bmp-directement-dans-votre-navigateur-solutions-de-movavi/"><u>Transformation Gratuite De Fichiers JPG en BMP Directement Dans Votre Navigateur - Solutions De Movavi</u></a></li>
</ul></div>

