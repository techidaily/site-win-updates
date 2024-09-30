---
title: "Repackaging Strategies: Revitalizing Your ClickOnce Software"
date: 2024-09-28T01:00:44.030Z
updated: 2024-09-30T09:48:37.218Z
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

Usually, you want an application to save some settings or running information in files. For per-user applications, most vendors consider placing those setting files near the executable.

The problem comes if you try to convert the application to per-machine. Why? Because users in an infrastructure will probably not have the necessary rights to write in a per-machine location.

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)Some might say that you can always give [additional permissions](https://tools.techidaily.com/advancedinstaller/products/) when you build your package, but that is a security point that needs a deeper discussion.   
For now, let’s consider that additional permissions are not allowed on per-machine installations. Check out the [MSI Permissions Guide: Three Ways to Add Rights With your Installer](https://tools.techidaily.com/advancedinstaller/products/)  

<!-- affiliate ads begin -->
<a href="https://ephamedtechinc.pxf.io/c/5597632/2145009/26400" target="_top" id="2145009">
  <img src="//a.impactradius-go.com/display-ad/26400-2145009" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://ephamedtechinc.pxf.io/i/5597632/2145009/26400" style="position:absolute;visibility:hidden;" border="0" />
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

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2094476/7443" target="_top" id="2094476">
  <img src="//a.impactradius-go.com/display-ad/7443-2094476" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2094476/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

When it comes to MSI’s, if the MSI is not present in the original install location and files need to be copied, then the self-healing process fails. That is one of the reasons we are not leaving the files as they were captured (in %appdata) and we are moving them in a per-machine location (C:\\Program FIles\\My App) and then copying them using a [Custom Action](https://tools.techidaily.com/advancedinstaller/products/).

One other aspect we need to consider is the shortcut. In our example, the shortcut is placed under each user Start Menu folder, located in:

C:\Users\YOUR USER\AppData\Roaming\Microsoft\Windows\Start Menu

Copy

To make it easier, we will place the shortcut on a per-user machine, but the [target of the shortcut](https://tools.techidaily.com/advancedinstaller/products/) will point to %appdata%, meaning it will open the executable from each user location.

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2151854/7443" target="_top" id="2151854">
  <img src="//a.impactradius-go.com/display-ad/7443-2151854" border="0" alt="https://techidaily.com" width="600" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2151854/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

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

6\. Now, the package is installing on a per-machine location and we have an Active Setup which will trigger the Custom Action that is introduced to copy the files to a per-user location once a user logs in. 

7\. The final step is to adjust the shortcut to point to the correct executable location. This is a two step process. 

7.1 First, navigate to the [Properties page](https://tools.techidaily.com/advancedinstaller/products/) and create a new property that looks something like this:

![ClickOnce Property](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/clickonce-property.png "ClickOnce Property")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2151892/7443" target="_top" id="2151892">
  <img src="//a.impactradius-go.com/display-ad/7443-2151892" border="0" alt="https://techidaily.com" width="600" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2151892/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

7.2 Once we have the property created, navigate to the [Shortcuts Page](https://tools.techidaily.com/advancedinstaller/products/) and create a new “External File” shortcut. The most important part here is to define the **Shortcut Targetdir** to point to:

[SHORPATH]\Sample.exe

Copy

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)SHORPATH is the property we previously created, replace it with the property name you have created in your project.

8\. At the end, the shortcut should look something like this:

![ClickOnce Shortcut](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/clickonceshortcut.png "ClickOnce Shortcut")  

As you can see, the shortcut is placed on a per-machine location, but the target of the shortcut will point at the end to %appdata%\\Sample.exe:

![Shortcut Properties](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/shortcut-properties.png "Shortcut Properties")

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2123739/7443" target="_top" id="2123739">
  <img src="//a.impactradius-go.com/display-ad/7443-2123739" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2123739/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

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
<li><a href="https://instagram-video-files.techidaily.com/new-2024-approved-the-essence-of-timelessness-instagrams-slow-motion-guide/"><u>[New] 2024 Approved The Essence of Timelessness Instagram's Slow-Motion Guide</u></a></li>
<li><a href="https://article-helps.techidaily.com/new-in-2024-professional-moving-less-imagery-tips/"><u>[New] In 2024, Professional Moving-Less Imagery Tips</u></a></li>
<li><a href="https://instagram-videos.techidaily.com/new-streamline-your-content-with-these-4-instagram-looping-hacks/"><u>[New] Streamline Your Content with These 4 Instagram Looping Hacks</u></a></li>
<li><a href="https://facebook-record-videos.techidaily.com/updated-the-ultimate-guide-to-effective-youtube-banners-for-2024/"><u>[Updated] The Ultimate Guide to Effective YouTube Banners for 2024</u></a></li>
<li><a href="https://win-updates.techidaily.com/1726028522591-skype/"><u>完全なオーディオレコードを作成せずにSkypeの会話をキャプチャするテクニック</u></a></li>
<li><a href="https://android-pokemon-go.techidaily.com/how-to-use-ispoofer-on-oppo-reno-10-proplus-5g-drfone-by-drfone-virtual-android/"><u>How to use iSpoofer on Oppo Reno 10 Pro+ 5G? | Dr.fone</u></a></li>
<li><a href="https://desktop-recording.techidaily.com/in-2024-capture-screens-free-cross-platform-for-windowsmac-users/"><u>In 2024, Capture Screens, Free! - Cross-Platform for Windows/Mac Users</u></a></li>
<li><a href="https://android-location-track.techidaily.com/in-2024-top-5-tracking-apps-to-track-oppo-k11x-without-them-knowing-drfone-by-drfone-virtual-android/"><u>In 2024, Top 5 Tracking Apps to Track Oppo K11x without Them Knowing | Dr.fone</u></a></li>
<li><a href="https://extra-support.techidaily.com/ios-android-unite-how-to-download-and-make-your-own-whatsapp-tones-for-2024/"><u>IOS, Android Unite How to Download and Make Your Own WhatsApp Tones for 2024</u></a></li>
<li><a href="https://win-updates.techidaily.com/no-more-plugins-embedding-rtsp-video-feeds-on-web-pages-using-vlcs-html5-transcoder/"><u>No More Plugins: Embedding RTSP Video Feeds on Web Pages Using VLC's HTML5 Transcoder</u></a></li>
<li><a href="https://win-updates.techidaily.com/pros-and-cons-free-and-professional-editions-of-zune-video-converter-analysis/"><u>Pros and Cons: Free and Professional Editions of Zune Video Converter Analysis</u></a></li>
<li><a href="https://win-updates.techidaily.com/simple-steps-converting-mov-files-to-wma-format-using-windows/"><u>Simple Steps: Converting Mov Files to Wma Format Using Windows</u></a></li>
<li><a href="https://win-updates.techidaily.com/the-ultimate-guide-top-5-elite-4k-video-transcoding-software/"><u>The Ultimate Guide: Top 5 Elite 4K Video Transcoding Software</u></a></li>
<li><a href="https://win-updates.techidaily.com/ultimate-guide-transforming-video-and-audio-files-into-various-formats/"><u>Ultimate Guide: Transforming Video and Audio Files Into Various Formats</u></a></li>
<li><a href="https://win-updates.techidaily.com/1726027350128-vimeo-firefox/"><u>ダウンロード: Vimeo 映像を Firefox でどうやって保存するか</u></a></li>
</ul></div>

