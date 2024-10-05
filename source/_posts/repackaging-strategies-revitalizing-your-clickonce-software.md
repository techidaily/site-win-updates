---
title: "Repackaging Strategies: Revitalizing Your ClickOnce Software"
date: 2024-09-29T18:16:03.020Z
updated: 2024-10-05T19:59:08.513Z
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

<!-- affiliate ads begin -->
<a href="https://imp.i357552.net/c/5597632/1030380/11832" target="_top" id="1030380">
  <img src="//a.impactradius-go.com/display-ad/11832-1030380" border="0" alt="https://techidaily.com" width="720" height="90"/>
</a>
<img height="0" width="0" src="https://imp.i357552.net/i/5597632/1030380/11832" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

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

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1885943/19272" target="_top" id="1885943">
  <img src="//a.impactradius-go.com/display-ad/19272-1885943" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1885943/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

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

<!-- affiliate ads begin -->
<span id="1484963">
					<video width="864" height="864" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1484963.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/16446-1484963">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1484963.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:540px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Flaganoo.pxf.io%2Fc%2F5597632%2F1484963%2F16446'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1484963/16446" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

4\. The next step is to implement a simple Active Setup into the MSI. In Advanced Installer,navigate to the [Product Details page](https://tools.techidaily.com/advancedinstaller/products/) and click on the Active Setup tab. 

5\. There, click on **New** and only change the **Stub Path** from /fou to /fus and click **OK**.

![ClickOnce Active Setup](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/clickonce-active-setup.png "ClickOnce Active Setup")  

6\. Now, the package is installing on a per-machine location and we have an Active Setup which will trigger the Custom Action that is introduced to copy the files to a per-user location once a user logs in. 

7\. The final step is to adjust the shortcut to point to the correct executable location. This is a two step process. 

7.1 First, navigate to the [Properties page](https://tools.techidaily.com/advancedinstaller/products/) and create a new property that looks something like this:

![ClickOnce Property](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/clickonce-property.png "ClickOnce Property")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1934288/19272" target="_top" id="1934288">
  <img src="//a.impactradius-go.com/display-ad/19272-1934288" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1934288/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

7.2 Once we have the property created, navigate to the [Shortcuts Page](https://tools.techidaily.com/advancedinstaller/products/) and create a new “External File” shortcut. The most important part here is to define the **Shortcut Targetdir** to point to:

[SHORPATH]\Sample.exe

Copy

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)SHORPATH is the property we previously created, replace it with the property name you have created in your project.

8\. At the end, the shortcut should look something like this:

![ClickOnce Shortcut](https://cdn.advancedinstaller.com/img/repackage-clickonce-application/clickonceshortcut.png "ClickOnce Shortcut")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2043638/7443" target="_top" id="2043638">
  <img src="//a.impactradius-go.com/display-ad/7443-2043638" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2043638/7443" style="position:absolute;visibility:hidden;" border="0" />
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
<li><a href="https://some-techniques.techidaily.com/new-fostering-friendship-through-conversations-with-viewers/"><u>[New] Fostering Friendship Through Conversations With Viewers</u></a></li>
<li><a href="https://fox-links.techidaily.com/updated-2024-approved-the-therapeutic-effects-of-asmr-for-everyone/"><u>[Updated] 2024 Approved The Therapeutic Effects of ASMR for Everyone</u></a></li>
<li><a href="https://fox-hovers.techidaily.com/updated-high-altitude-heroes-aerospaces-persistent-innovations-top-10/"><u>[Updated] High Altitude Heroes Aerospace's Persistent Innovations (Top 10)</u></a></li>
<li><a href="https://extra-hints.techidaily.com/2024-approved-5-top-tier-gaming-displays-in-4k-quality/"><u>2024 Approved 5 Top-Tier Gaming Displays in 4K Quality</u></a></li>
<li><a href="https://remote-screen-capture.techidaily.com/2024-approved-capturewin-the-hassle-free-screen-recorder/"><u>2024 Approved CaptureWin The Hassle-Free Screen Recorder</u></a></li>
<li><a href="https://howto.techidaily.com/7-solutions-to-fix-chrome-crashes-or-wont-open-on-realme-11x-5g-drfone-by-drfone-fix-android-problems-fix-android-problems/"><u>7 Solutions to Fix Chrome Crashes or Wont Open on Realme 11X 5G | Dr.fone</u></a></li>
<li><a href="https://win-updates.techidaily.com/best-strategies-mastering-the-art-of-writing-in-pdf-documents/"><u>Best Strategies: Mastering the Art of Writing in PDF Documents</u></a></li>
<li><a href="https://techidaily.com/how-to-transfer-whatsapp-from-apple-iphone-14-to-android-drfone-by-drfone-transfer-whatsapp-from-ios-transfer-whatsapp-from-ios/"><u>How To Transfer WhatsApp From Apple iPhone 14 to Android? | Dr.fone</u></a></li>
<li><a href="https://some-techniques.techidaily.com/in-2024-expedite-your-experience-quick-iphone-time-lapse/"><u>In 2024, Expedite Your Experience Quick iPhone Time-Lapse</u></a></li>
<li><a href="https://win-updates.techidaily.com/mastering-the-removal-of-superfluous-android-programs-on-your-personal-computer-top-strategies-and-techniques/"><u>Mastering the Removal of Superfluous Android Programs on Your Personal Computer: Top Strategies and Techniques</u></a></li>
<li><a href="https://screen-video-capture.techidaily.com/quick-and-easy-way-to-record-iphone-screens-for-2024/"><u>Quick & Easy Way to Record iPhone Screens for 2024</u></a></li>
<li><a href="https://win-updates.techidaily.com/ransomware-explained-insights-and-prevention-tips-from-malwarefox/"><u>Ransomware Explained: Insights and Prevention Tips From MalwareFox</u></a></li>
<li><a href="https://win-updates.techidaily.com/restore-missing-voicemail-audio-files-on-your-ios-device/"><u>Restore Missing Voicemail Audio Files on Your iOS Device</u></a></li>
<li><a href="https://win-updates.techidaily.com/step-by-step-guide-removing-the-white-canvas-in-microsoft-paint/"><u>Step-by-Step Guide: Removing the White Canvas in Microsoft Paint</u></a></li>
<li><a href="https://win-updates.techidaily.com/top-5-online-image-shrinkers-of-2022-choosing-the-best-one/"><u>Top 5 Online Image Shrinkers of 2022 - Choosing the Best One</u></a></li>
<li><a href="https://win-updates.techidaily.com/understanding-cloud-based-antivirus-advantages-over-classic-security-solutions/"><u>Understanding Cloud-Based Antivirus: Advantages Over Classic Security Solutions</u></a></li>
</ul></div>

