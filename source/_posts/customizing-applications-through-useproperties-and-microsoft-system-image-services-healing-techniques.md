---
title: Customizing Applications Through UseProperties & Microsoft System Image Services Healing Techniques
date: 2024-09-28T04:29:36.036Z
updated: 2024-09-29T17:52:50.543Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: This Article Describes Customizing Applications Through UseProperties & Microsoft System Image Services Healing Techniques
thumbnail: https://thmb.techidaily.com/cfe1e4fd673ca5fb5a36d3dc03d18f188db6311040ef6f07e920236b71a10c10.jpg
---

## Customizing Applications Through UseProperties & Microsoft System Image Services Healing Techniques

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Application Customization

### Significance of Advertised Shortcuts

An advertised shortcut is a pointer to a file or folder that is installed by an MSI package. When running an advertised shortcut, Windows Installer first checks that all the components of the respective feature are installed before running the file. If any of the components are missing, Windows Installer repairs the installation by installing the missing components. This ensures that the application remains consistent and that all of its features are available when required.

The best is to keep in mind the following about advertised shortcuts:

* When running an advertised shortcut, Windows Installer first checks that all the components **of the respective feature** are installed (before running the file).
* The target of the shortcut must be present in the package.

What is to take is that if your application contains multiple features, but the shortcut is available only on one feature, then during the self-healing process only that feature will be checked if all the components are properly installed on the machine. 

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)For more information regarding shortcuts, check out our first [MSI Packaging Essentials ebook](https://tools.techidaily.com/advancedinstaller/products/).

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2105870/7443" target="_top" id="2105870">
  <img src="//a.impactradius-go.com/display-ad/7443-2105870" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2105870/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### What is Self-Healing

The MSI (Microsoft Installer) self-healing mechanism is a powerful feature that ensures the integrity and availability of installed applications. It is intended to detect and repair any missing or corrupted files, registry entries, or other components of an application, preserving the application's functionality and preventing potential problems.

When an MSI-based application is installed, Windows Installer creates a comprehensive installation database known as the installation package or MSI package. This package contains all of the resources and information needed to install and maintain the application. Files, registry entries, shortcuts, components, and other configuration settings are all included. This small MSI it’s also known as the “cached MSI” and can be found in the %systemroot%\\installer folder. 

![Important](https://cdn.advancedinstaller.com/svg/common/IconMessageInfo.svg)It is very important to mention that manual interventions for the Installer folder should never be done. For more details about the Installer folder check out [this article](https://tools.techidaily.com/advancedinstaller/products/).

Specific events, such as the launch of an application, the opening of a document associated with the application, or the invocation of a Windows Installer action such as repair or modify, initiate the self-healing process. When any of these events occurs, Windows Installer validates the application's integrity by comparing the recorded installation information to the current state of the system.

When the self-healing mechanism detects that a file, registry entry, or other component associated with the application is missing or damaged, it begins the repair process automatically. Locating the original installation source (usually the installation media or a network location) and restoring the missing or corrupted components is the first step in this process.

Windows Installer follows a predefined sequence of steps during the repair process:

* Verification:The digital signature of the installation package is checked by Windows Installer to ensure that it is authentic and has not been tampered with.
* Component Detection: By comparing the recorded installation information with the current system state, Windows Installer determines which components are missing or damaged.
* Source Resolution: The installation source is attempted to be located by Windows Installer by referring to the original installation media or other specified locations.
* File and Registry Restoration: Windows Installer uses the installation package's source files to replace missing or damaged files, registry entries, and other components.
* Reconfiguration: Windows Installer reconfigures the repaired components, restoring any necessary settings or dependencies.

When the repair process is finished, the application is returned to its original state, with all of the necessary files, registry entries, and settings in place. This ensures that the application works as expected and that any missing or damaged components are completely restored.

It is important to note that the self-healing mechanism in MSI is dependent on the original installation source being available. If the installation source is not available, the repair process may fail, requiring manual intervention to restore the application.

MSI's self-healing mechanism offers numerous advantages:

* Maintenance: It makes application maintenance easier by automatically repairing any issues that may arise as a result of file corruption, accidental deletion, or system changes.
* Data Integrity: It contributes to data integrity protection by ensuring that applications have access to the necessary files and resources. This prevents application crashes, data loss, and other problems caused by missing or corrupted components.
* User Experience:It improves the user experience by restoring application functionality without the need for manual intervention or reinstallation.

However, to ensure that the self-healing mechanism works properly, the installation package must be properly configured and tested. This entails precisely specifying the dependencies, files, and registry entries that are required for the application to function.

In summary, MSI's self-healing mechanism is a critical feature that automatically detects and repairs missing or corrupted application components. It ensures smooth operation and helps prevent potential issues caused by component-related problems by maintaining the integrity and availability of applications.

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2135412/19272" target="_top" id="2135412">
  <img src="//a.impactradius-go.com/display-ad/19272-2135412" border="0" alt="https://techidaily.com" width="250" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2135412/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Properties

Properties are used in MSI packaging to define and customize various aspects of the installation process, such as installation location, product key, and installation options. MSI properties are classified as public or private based on whether or not end users can access them.

Public properties are those that users can access and modify during the installation process. These properties are usually defined in the MSI database's Property table and are used to store values like the installation directory, product name, and version number. When launching an installation, public properties are frequently specified on the command line, or they can be set using a [transform file (.mst)](https://www.advancedinstaller.com/application-packaging-training/msi-advanced/ebook/create-mst-files.html "transform file (.mst)").

Private properties, on the other hand, are used internally by the installer and should not be changed by end users. These properties are typically used to control the installer's behavior and are hidden from users during the installation process. Private properties, which are typically defined in the MSI database's CustomAction table, are used to control the execution of custom actions, install sequences, or logging behavior.

It is critical to understand that MSI properties are typically stored as string values rather than integers or Boolean values when they are defined. Values are thus stored as text strings and must be converted to the appropriate data type as needed. A property that stores a version number, for example, could be defined as a string value but would need to be converted to a numerical value before performing arithmetic or comparison operations.

MSI comes with a plethora of built-in properties for defining various aspects of the installation process, including directory properties. The following are some of the most frequently used properties in MSI:

* ALLUSERS: Specifies whether the installation is for all [users of the machine](https://tools.techidaily.com/advancedinstaller/products/) (1) or only the current user (2).
* INSTALLDIR: Specifies the default installation directory for the application.
* INSTALLLEVEL: Specifies the installation level, which controls which features are installed during the installation process.
* REBOOT: Specifies whether a reboot is required after installation (force, suppress, or prompt).
* TARGETDIR: Specifies the target installation directory for the application.
* USERNAME: Specifies the name of the user performing the installation.
* USERPROFILE: Specifies the user profile directory for the current user.

MSI also supports the creation of custom properties that can be used to define other aspects of the installation process in addition to these built-in properties. For example, you could define a custom property to specify a product's license key or a custom installation path.

When working with directory properties, it is critical to understand that MSI organizes files and resources using a hierarchical directory structure. The INSTALLDIR directory is at the top of the directory structure and is where the application is installed by default. Other directory properties, such as TARGETDIR and APPDATA, are used to specify specific directories within a larger directory structure.

It is important to understand these base concepts as we will dive deeper into this topic [later down the road](https://tools.techidaily.com/advancedinstaller/products/).

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)For more details about Properties, check out our first [MSI Packaging Essentials ebook](https://tools.techidaily.com/advancedinstaller/products/).

<!-- affiliate ads begin -->
<span id="1155462">
					<video width="1024" height="576" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1155462.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/14559-1155462">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1155462.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:640px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fpropmoneyinc.pxf.io%2Fc%2F5597632%2F1155462%2F14559'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1155462/14559" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Custom vlc settings

Now that we've captured and repackaged VLC Media Player as an MSI, we need to figure out how to detect and implement any custom settings that may be required for this application.

In this example, we will look at the number one rule when it comes to repackaging applications in an enterprise environment: always disable automatic updates.

There are multiple ways in which we can detect where the settings of the application are stored, such as:

* Using Advanced Repackager with Session Monitoring
* Using Process Monitor
* Using other 3rd party tools such as Systracer

We have already covered in our first book how you can [detect the settings of VLC Media Player with Systracer](https://tools.techidaily.com/advancedinstaller/products/), this basically acts exactly like Advanced Repackager and captures two states of the system and displays the difference between them.

We already looked at how to use Process Monitor to detect if an EXE contains an embedded MSI; we can do the same to detect where VLC Media Player writes its settings, but some additional settings must be performed in the filter section:

* Launch Process Monitor: Open Process Monitor from the Start menu or the shortcut on your desktop.
* Configure filters: Before monitoring the installation process, it's helpful to set up filters to narrow down the captured events and focus on the relevant activities. Click on the "Filter" menu, and then select "Filter..." to open the Filter dialog box.
* Under “Display entries matching these conditions” select “Process Name”, “is”, “vlc.exe”, then “include”. Click on Add

![process monitor detect vlc settings](https://cdn.advancedinstaller.com/img/application-customization/process-monitor-detect-vlc-settings.png "process monitor detect vlc settings")  

* Click OK and start the capture process
* Open VLC Media Player and go to Tools > Preferences and implement the desired configurations. Close the preferences and close VLC Media Player

After we have completed all of these steps, we can see at the bottom of the Process Monitor capture that VLC Media Player created and modified the file vlcrc, which can be found in %appdata%vlc.

![process monitor detect vlc settings info](https://cdn.advancedinstaller.com/img/application-customization/process-monitor-detect-vlc-settings-info.png "process monitor detect vlc settings info")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1959778/19272" target="_top" id="1959778">
  <img src="//a.impactradius-go.com/display-ad/19272-1959778" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1959778/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

If you want to use Advanced Repackager, follow the same steps as when we started the VLC Media Player repackaging process, but instead of selecting an executable, check the Session Monitoring checkbox. At the end, Advanced Repackager will identify the modified vlcrc.

### Custom settings implementation in the package

Now that we know which file needs to be added into the package, we can simplify our repackaged project [that we did earlier](https://tools.techidaily.com/advancedinstaller/products/), navigate to the [Files and Folders page](https://tools.techidaily.com/advancedinstaller/products/) and under the Application Data folder, create a new directory called vlc and add the vlcrc file. You can also include the vlc-qt-interface.ini and ml.xspf, and the project should look something like this:

![vlc media player settings ai](https://cdn.advancedinstaller.com/img/application-customization/vlc-media-player-settings-ai.png "vlc media player settings ai")  

When it comes to installers, however, working with user files or the registry is more difficult. When an application is deployed in an infrastructure using any infrastructure management tools, the NT System\\Administrator account is used. This is the most privileged account available.

One of the golden rules when it comes to installation testing as an IT Professional is to always test your applications using the PSExec utility. We have a more in-detail look over this topic in our first book and you can check it [here](https://tools.techidaily.com/advancedinstaller/products/), but if we would leave the installer as it is right now, the settings won’t reach the logged on user or any user that is using that particular computer, because the settings will only be populated within the NT System\\Administrator account files.

This is where [advertised shortcuts](https://tools.techidaily.com/advancedinstaller/products/) come into play. When working with Windows Installer, one important concept to understand is the concept of [advertised shortcuts](https://tools.techidaily.com/advancedinstaller/products/). Advertised shortcuts are a feature provided by Windows Installer that allows for the dynamic installation and repair of applications. In this article, we will explore the concept of advertised shortcuts, how they work, and best practices for utilizing them effectively.

Advertised shortcuts serve two main purposes: advertisement and resiliency. Let's take a closer look at each of these points.

When an advertised shortcut is launched, Windows Installer validates that all the components included in the same feature as the shortcut feature are installed on the device. This is accomplished by determining whether their keypaths, which represent the critical resources for each component, are present. If a component is missing, Windows Installer launches the installation package and reinstalls all required resources from the.msi file. This ensures that the application has been completely installed before being launched.

To create an advertised shortcut, the resource it points to in the Component table must be designated as a KeyPath. A KeyPath is a resource that represents the feature's core component. Once a resource has been designated as a KeyPath, it cannot be moved to another component, and no other resource can be designated as a KeyPath for that component. This ensures that the advertised shortcut works properly and, if necessary, initiates the installation process.

Another advantage of advertised shortcuts is their resiliency. When the user clicks on the advertised shortcut, Windows Installer automatically triggers a repair of the application if any of the keypaths associated with the components are missing or corrupted. This ensures that the application will continue to function even if critical resources are compromised.

To take full advantage of both advertisement and self-healing, it is important to adhere to certain best practices:

* Set all features' states to Advertise: It is recommended that all features be set to Advertise. While having only one feature is preferable, if multiple features are required, make sure that all of them are set to Advertise. This ensures that the required resources are correctly installed when the application is launched.
* Advertise all shortcuts: All shortcuts should be advertised in order to enable the dynamic installation and repair process. This is accomplished by checking the "Advertised shortcut" checkbox in the Shortcut Properties view during the shortcut's creation.
* Assign a keypath to all components: Each application component should have its own keypath. The keypath represents the component's critical resource and assists Windows Installer in validating the installation and initiating repairs if necessary. To ensure proper functionality, it is recommended that you follow Microsoft's general rules for organizing resources into components.

By following these guidelines, you can harness the power of advertised shortcuts to provide your users with a dynamic and resilient installation experience. Advertised shortcuts make application deployment and maintenance easier by ensuring that all necessary resources are installed correctly and that repairs are triggered when necessary.

Because all the files used by the shortcuts are included in the MSI package, we can navigate to the [Shortcuts Page](https://tools.techidaily.com/advancedinstaller/products/) and for each shortcut available in the package we must enable the Advertised Shortcut checkbox.

![ai shorcut advertised shortcut](https://cdn.advancedinstaller.com/img/application-customization/ai-shorcut-advertised-shortcut.png "ai shorcut advertised shortcut")  

When the package is installed and a user opens a shortcut, the MSI will perform a self-healing action and copy the previously placed files to the currently logged in user profile.

However, while this solution may work, it does not represent industry best practice, and we must consider some other issues that may arise if we place user data in this manner.

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
<li><a href="https://instagram-clips.techidaily.com/new-in-2024-rewind-and-play-instagrams-backwards-videos-unveiled/"><u>[New] In 2024, Rewind and Play Instagram's Backwards Videos Unveiled</u></a></li>
<li><a href="https://win-updates.techidaily.com/1726030172013-aviutl/"><u>音声編集ガイド：AviUtlでの切り取り・レベリング技術を学ぶ</u></a></li>
<li><a href="https://solve-popular.techidaily.com/enhance-user-experience-with-our-cookiebot-integration-solutions/"><u>Enhance User Experience with Our Cookiebot Integration Solutions</u></a></li>
<li><a href="https://instagram-video-recordings.techidaily.com/fixing-audio-input-device-recognition-issues-in-windows-7810/"><u>Fixing Audio Input Device Recognition Issues in Windows 7/8/10</u></a></li>
<li><a href="https://techidaily.com/how-to-transfer-data-from-apple-iphone-15-plus-to-other-iphone-drfone-by-drfone-transfer-data-from-ios-transfer-data-from-ios/"><u>How To Transfer Data From Apple iPhone 15 Plus To Other iPhone? | Dr.fone</u></a></li>
<li><a href="https://ios-unlock.techidaily.com/in-2024-how-to-unlock-iphone-12-mini-without-passcode-4-easy-methods-by-drfone-ios/"><u>In 2024, How To Unlock iPhone 12 mini Without Passcode? 4 Easy Methods</u></a></li>
<li><a href="https://blog-min.techidaily.com/mastering-the-art-of-converting-isos-to-dvd-format-on-windows-operating-systems-win-1187/"><u>Mastering the Art of Converting ISOs to DVD Format on Windows Operating Systems (Win 11/8/7)</u></a></li>
<li><a href="https://hardware-updates.techidaily.com/navigating-the-world-of-computing-toms-hardware-expertise/"><u>Navigating the World of Computing: Tom's Hardware Expertise</u></a></li>
<li><a href="https://win-updates.techidaily.com/no-more-plugins-embedding-rtsp-video-feeds-on-web-pages-using-vlcs-html5-transcoder/"><u>No More Plugins: Embedding RTSP Video Feeds on Web Pages Using VLC's HTML5 Transcoder</u></a></li>
<li><a href="https://win-updates.techidaily.com/1726029980771-ogg/"><u>Oggファイル改竢・マージ・カット・レベル変更のための劣化しない編集手法</u></a></li>
<li><a href="https://buynow-info.techidaily.com/step-by-step-mastery-utilizing-the-secret-features-of-preview-on-macos-devices/"><u>Step-by-Step Mastery: Utilizing the Secret Features of Preview on macOS Devices</u></a></li>
<li><a href="https://win-updates.techidaily.com/syncing-mobile-photographs-with-your-desktop-tips-for-android-users-on-windows-computers-zdnet/"><u>Syncing Mobile Photographs with Your Desktop: Tips for Android Users on Windows Computers | ZDNet</u></a></li>
<li><a href="https://win-updates.techidaily.com/the-future-of-winamp-beyond-open-source-exploring-its-strategic-shift-explained-by-zdnet/"><u>The Future of Winamp Beyond Open-Source: Exploring Its Strategic Shift Explained by ZDNet</u></a></li>
<li><a href="https://location-social.techidaily.com/top-7-skype-hacker-to-hack-any-skype-account-on-your-xiaomi-redmi-note-12-5g-drfone-by-drfone-virtual-android/"><u>Top 7 Skype Hacker to Hack Any Skype Account On your Xiaomi Redmi Note 12 5G | Dr.fone</u></a></li>
<li><a href="https://win-updates.techidaily.com/why-and-how-to-access-windows-11-using-your-microsoft-365-business-account-expert-tips-from-zdnet/"><u>Why and How to Access Windows 11 Using Your Microsoft 365 Business Account | Expert Tips From ZDNET</u></a></li>
<li><a href="https://win-updates.techidaily.com/44oa44km44oz44ot44o844oj44oy44or44or44o844ks5l244gj44gf44ot44oh44kq44oa44km44oz44ot44o844oj44gr5asx5pwx44gz44kl5ac05zci44gu6kej5rg6562w/"><u>ダウンロードヘルパーを使ったビデオダウンロードに失敗する場合の解決策</u></a></li>
</ul></div>

