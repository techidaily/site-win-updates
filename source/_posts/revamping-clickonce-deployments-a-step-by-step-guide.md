---
title: "Revamping ClickOnce Deployments: A Step-by-Step Guide"
date: 2024-09-28T09:02:19.449Z
updated: 2024-09-30T09:04:48.138Z
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
<a href="https://appsumo.8odi.net/c/5597632/2151883/7443" target="_top" id="2151883">
  <img src="//a.impactradius-go.com/display-ad/7443-2151883" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2151883/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

When it comes to MSI’s, if the MSI is not present in the original install location and files need to be copied, then the self-healing process fails. That is one of the reasons we are not leaving the files as they were captured (in %appdata) and we are moving them in a per-machine location (C:\\Program FIles\\My App) and then copying them using a [Custom Action](https://tools.techidaily.com/advancedinstaller/products/).

One other aspect we need to consider is the shortcut. In our example, the shortcut is placed under each user Start Menu folder, located in:

C:\Users\YOUR USER\AppData\Roaming\Microsoft\Windows\Start Menu

Copy

To make it easier, we will place the shortcut on a per-user machine, but the [target of the shortcut](https://tools.techidaily.com/advancedinstaller/products/) will point to %appdata%, meaning it will open the executable from each user location.

<!-- affiliate ads begin -->
<a href="https://laganoo.pxf.io/c/5597632/1657399/16446" target="_top" id="1657399">
  <img src="//a.impactradius-go.com/display-ad/16446-1657399" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://laganoo.pxf.io/i/5597632/1657399/16446" style="position:absolute;visibility:hidden;" border="0" />
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

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2068433/7443" target="_top" id="2068433">
  <img src="//a.impactradius-go.com/display-ad/7443-2068433" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2068433/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

6\. Now, the package is installing on a per-machine location and we have an Active Setup which will trigger the Custom Action that is introduced to copy the files to a per-user location once a user logs in. 

7\. The final step is to adjust the shortcut to point to the correct executable location. This is a two step process. 

7.1 First, navigate to the [Properties page](https://tools.techidaily.com/advancedinstaller/products/) and create a new property that looks something like this:

![ClickOnce Property](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/clickonce-property.png "ClickOnce Property")  

7.2 Once we have the property created, navigate to the [Shortcuts Page](https://tools.techidaily.com/advancedinstaller/products/) and create a new “External File” shortcut. The most important part here is to define the **Shortcut Targetdir** to point to:

[SHORPATH]\Sample.exe

Copy

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)SHORPATH is the property we previously created, replace it with the property name you have created in your project.

8\. At the end, the shortcut should look something like this:

![ClickOnce Shortcut](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/clickonceshortcut.png "ClickOnce Shortcut")  

<!-- affiliate ads begin -->
<a href="https://dhgate.sjv.io/c/5597632/1186802/12108" target="_top" id="1186802">
  <img src="//a.impactradius-go.com/display-ad/12108-1186802" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://dhgate.sjv.io/i/5597632/1186802/12108" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

As you can see, the shortcut is placed on a per-machine location, but the target of the shortcut will point at the end to %appdata%\\Sample.exe:

![Shortcut Properties](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/shortcut-properties.png "Shortcut Properties")

<!-- affiliate ads begin -->
<a href="https://ephamedtechinc.pxf.io/c/5597632/2136622/26400" target="_top" id="2136622">
  <img src="//a.impactradius-go.com/display-ad/26400-2136622" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://ephamedtechinc.pxf.io/i/5597632/2136622/26400" style="position:absolute;visibility:hidden;" border="0" />
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
<li><a href="https://instagram-videos.techidaily.com/new-2024-approved-decoding-and-manipulating-gender-presentation-online-a-step-by-step-approach/"><u>[New] 2024 Approved Decoding and Manipulating Gender Presentation Online A Step-by-Step Approach</u></a></li>
<li><a href="https://facebook-video-content.techidaily.com/updated-in-2024-how-to-watch-facebook-live/"><u>[Updated] In 2024, How to Watch Facebook Live?</u></a></li>
<li><a href="https://android-location-track.techidaily.com/3-ways-to-track-itel-s23plus-without-them-knowing-drfone-by-drfone-virtual-android/"><u>3 Ways to Track Itel S23+ without Them Knowing | Dr.fone</u></a></li>
<li><a href="https://win-updates.techidaily.com/1726030172013-aviutl/"><u>音声編集ガイド：AviUtlでの切り取り・レベリング技術を学ぶ</u></a></li>
<li><a href="https://tech-haven.techidaily.com/boosting-your-social-media-engagement-writing-top-notch-posts-with-chatgpt/"><u>Boosting Your Social Media Engagement: Writing Top-Notch Posts with ChatGPT</u></a></li>
<li><a href="https://screen-sharing-recording.techidaily.com/detailed-framework-elevating-your-mobile-screenshots-using-mobizen/"><u>Detailed Framework Elevating Your Mobile Screenshots Using Mobizen</u></a></li>
<li><a href="https://win-updates.techidaily.com/elite-power-user-secrets-unveil-top-11-undiscovered-gesture-shortcuts-on-your-trackpad/"><u>Elite Power User Secrets: Unveil Top 11 Undiscovered Gesture Shortcuts on Your Trackpad</u></a></li>
<li><a href="https://fox-hovers.techidaily.com/essential-mobile-photography-boosters-iphone-vs-android-for-2024/"><u>Essential Mobile Photography Boosters IPhone vs Android for 2024</u></a></li>
<li><a href="https://easy-unlock-android.techidaily.com/in-2024-bypassing-google-account-with-vnrom-bypass-for-realme-12-5g-by-drfone-android/"><u>In 2024, Bypassing Google Account With vnROM Bypass For Realme 12 5G</u></a></li>
<li><a href="https://phone-solutions.techidaily.com/is-fake-gps-location-spoofer-a-good-choice-on-vivo-y100a-drfone-by-drfone-virtual-android/"><u>Is Fake GPS Location Spoofer a Good Choice On Vivo Y100A? | Dr.fone</u></a></li>
<li><a href="https://win-updates.techidaily.com/mastering-dns-configuration-a-step-by-step-guide-for-changing-ip-addresses-in-windows-os/"><u>Mastering DNS Configuration: A Step-by-Step Guide for Changing IP Addresses in Windows OS</u></a></li>
<li><a href="https://some-tips.techidaily.com/movavi-opus/"><u>Movavi 오픈소스를 쉽고 무료로 OPUS 형식으로 변환: 비용과 시간을 모두 절침하는 전문가 기법</u></a></li>
<li><a href="https://win-updates.techidaily.com/no-more-plugins-embedding-rtsp-video-feeds-on-web-pages-using-vlcs-html5-transcoder/"><u>No More Plugins: Embedding RTSP Video Feeds on Web Pages Using VLC's HTML5 Transcoder</u></a></li>
<li><a href="https://win-updates.techidaily.com/1726029980771-ogg/"><u>Oggファイル改竢・マージ・カット・レベル変更のための劣化しない編集手法</u></a></li>
<li><a href="https://win-updates.techidaily.com/syncing-mobile-photographs-with-your-desktop-tips-for-android-users-on-windows-computers-zdnet/"><u>Syncing Mobile Photographs with Your Desktop: Tips for Android Users on Windows Computers | ZDNet</u></a></li>
<li><a href="https://win-updates.techidaily.com/the-future-of-winamp-beyond-open-source-exploring-its-strategic-shift-explained-by-zdnet/"><u>The Future of Winamp Beyond Open-Source: Exploring Its Strategic Shift Explained by ZDNet</u></a></li>
<li><a href="https://win-solutions.techidaily.com/unleash-the-power-of-your-pc-with-ultimate-guide-how-to-harness-infinite-riches-in-dragonia/"><u>Unleash the Power of Your PC with Ultimate Guide: How to Harness Infinite Riches in Dragonia</u></a></li>
<li><a href="https://win-updates.techidaily.com/why-and-how-to-access-windows-11-using-your-microsoft-365-business-account-expert-tips-from-zdnet/"><u>Why and How to Access Windows 11 Using Your Microsoft 365 Business Account | Expert Tips From ZDNET</u></a></li>
<li><a href="https://win-updates.techidaily.com/44oa44km44oz44ot44o844oj44oy44or44or44o844ks5l244gj44gf44ot44oh44kq44oa44km44oz44ot44o844oj44gr5asx5pwx44gz44kl5ac05zci44gu6kej5rg6562w/"><u>ダウンロードヘルパーを使ったビデオダウンロードに失敗する場合の解決策</u></a></li>
</ul></div>

