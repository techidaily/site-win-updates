---
title: "MSI Upgrades Versus MSP: Navigating Through Microsoft's System Package Options"
date: 2024-09-27T05:42:03.605Z
updated: 2024-09-30T08:07:26.725Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: "This Article Describes MSI Upgrades Versus MSP: Navigating Through Microsoft's System Package Options"
thumbnail: https://thmb.techidaily.com/84120ce1dd040ef96ca974489513e09e6fd38ddc4b035ddddd4021d7d15c6c74.jpg
---

## MSI Upgrades Versus MSP: Navigating Through Microsoft's System Package Options

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Introduction to MSI Upgrades

### What is an MSI Upgrade?

An MSI upgrade refers to the process of installing a new version of a software product that replaces an existing installation. It involves updating the installed product with a higher version while preserving user data and settings. MSI upgrades provide a comprehensive update mechanism that allows users to transition seamlessly from one version to another.

When an MSI upgrade process is started, the following actions are considered:

* Versioning: A version number is assigned to each version of a software product. A major version, a minor version, a build number, and a revision number are all part of the version number. Upgrades usually necessitate increasing the major or minor version number.
* Upgrade Table: The MSI database's Upgrade table contains information that defines how the upgrade process should be carried out. It contains upgrade codes, product codes, and version ranges that are used to determine compatibility between old and new versions.
* Detection: The installer checks for the presence of a previously installed version during the upgrade process by comparing product codes and version numbers. If a compatible version is found, the installer will begin the upgrade process.
* Upgrade Options:Depending on the upgrade scenario, the installer provides the user with options such as "Upgrade," "Repair," or "Uninstall." The user can choose to upgrade the current installation or take other actions based on their needs.
* Files and Settings: The installer replaces old files with new ones, updates registry entries, and modifies configuration settings to reflect the changes introduced in the new version during the upgrade. To ensure a smooth transition, user-specific data and settings are typically preserved.

When doing MSI upgrades, it is important that you follow some of the best practices which were developed during the years:

* Versioning: To avoid confusion and ensure proper compatibility checks during the upgrade process, use a consistent versioning scheme. When significant changes are introduced, the major or minor version number is incremented.
* Testing: Test the upgrade process thoroughly to ensure compatibility, data integrity, and a smooth transition from the old to the new version. To identify and address any issues, perform functional testing, compatibility testing, and user acceptance testing (UAT).
* Compatibility Checks: To ensure a smooth upgrade process, conduct thorough compatibility checks between different versions of the software. Check to see if the new version is compatible with your existing data, settings, and dependencies.
* Documentation:To guide users through the upgrade process, provide clear and comprehensive documentation, including release notes and upgrade instructions. To manage user expectations, communicate any changes, new features, or known issues.
* Rollback Plan: Prepare a rollback strategy in case the upgrade process fails. This entails making a backup of the existing installation or having a mechanism in place to revert to a previous version if necessary.
* User Communication: Communicate effectively with users to inform them of the availability of upgrades, benefits, and any actions they must take. To keep users informed about the upgrade process, use notifications, emails, or in-app messages.
* Customization: Provide options for customizing the upgrade process to meet the needs of different users. During the upgrade process, allow users to select installation options, configure settings, or provide feedback.
* Compatibility with Previous Versions: When designing upgrades, keep backward compatibility in mind. Check that the new version can interact with previous versions of the software and that data compatibility issues are handled.
* Automation and Deployment: To speed up the upgrade process, use automation tools or software deployment systems, especially in enterprise environments. This helps to ensure consistency, reduces manual effort, and allows for centralized upgrade management.

### Patch vs upgrade

Windows Installer (MSI) provides two primary mechanisms for managing software updates and new releases: patches and upgrades. Both are used to modify an existing installation, but they have different characteristics and are used in different scenarios.An MSI patch (MSP) is primarily used to fix specific issues or bugs in an existing installation without affecting the installed product significantly. It typically targets a specific version or range of versions and addresses specific software problems. Patches are intended to be small and focused, addressing specific issues without introducing new features or functionality.

Patching is a differential process that updates only the modified files or components. A patch package usually includes the binary differences between the old and new versions of the files, allowing for quick updates. Only the affected files are replaced during patch installation, reducing installation time and impact on system resources.

MSI patches are version-specific and typically target a specific software base version. They are intended to update a specific set of versions, addressing only the issues or changes identified between those versions. Patches frequently have strict version dependencies and may necessitate additional prerequisites to ensure compatibility.

They are also typically installed silently, with no user interaction required. They operate in the background, frequently during system maintenance or automated update processes. Patches are intended to be non-intrusive and seamless, providing fixes while not interfering with the user's workflow.

MSI upgrades, on the other hand, entail installing a new version of the software that includes enhancements, new features, or significant changes to the product. It is a full update that replaces the current installation with a newer version. Upgrades frequently necessitate careful planning and testing to ensure a smooth transition from the old to the new version.

Upgrades entail completely replacing the installed product. The previous version is uninstalled, and the new version is installed separately. Uninstalling previous versions, copying new files, modifying registry entries, and updating the installation database are all possible steps in this process. Upgrades necessitate a more involved installation process than patches.

MSI upgrades affect the entire installed base, allowing users to transition from one major version to the next. They typically support upgrades from multiple previous versions to the most recent release. To ensure a smooth transition, upgrades frequently include mechanisms to handle data migration, configuration updates, and compatibility checks.

Upgrades also give you more control and flexibility over your user experience. They can be installed interactively, allowing users to select installation options, configure settings, or provide feedback while the upgrade is taking place. User notifications, such as release notes or upgrade prompts, may also be included in upgrades to inform users about new features or changes.

Patches, on the other hand, are typically easier to test and deploy than upgrades because they address specific issues within a limited scope. Testing efforts can be concentrated on the affected areas, reducing overall testing effort. Patch deployment can be done automatically with software distribution tools or manually with patch management systems.

MSI upgrades do necessitate extensive testing to ensure compatibility, data integrity, and a smooth transition from the old to the new version. They entail a more thorough testing procedure, which includes functional testing, compatibility testing, and user acceptance testing (UAT). Additional considerations for upgrades may include data migration, backward compatibility, or upgrade rollback options.

Be aware of the various restrictions that come with patches when working with them. Not taking them into consideration may cause your main application to stop working or the patch installation to fail.

Now we'll go over the most common restrictions to be aware of when working with patches. By understanding these constraints, you can ensure that your patching process runs smoothly and without incident.

The following are the most common patch restrictions:

* Between the original and new MSI file versions, do not change the primary keys in the File table.
* Files should not be moved from one folder to another.
* Files should not be moved from one cabinet to another.
* Do not rearrange the files in a cabinet.
* Change the Component GUID for any Component at all.
* Change the name of the Component's key file only if you want to change the Component GUID.
* Do not change the existing feature and component hierarchy. A new Feature can be added, but removing a parent Feature requires the removal of all its child Features.
* Components should not be removed from a Feature.
* The names of the Target and Upgraded MSI packages must be the same.
* The Product Code for the Target and Upgraded MSI packages must be the same.

![Important](https://cdn.advancedinstaller.com/svg/common/IconMessageInfo.svg)You can find the full list of restrictions for patches on the [Microsoft website](https://learn.microsoft.com/en-us/windows/win32/msi/changing-the-product-code?redirectedfrom=MSDN "Microsoft website").

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2123730/7443" target="_top" id="2123730">
  <img src="//a.impactradius-go.com/display-ad/7443-2123730" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2123730/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Example patch for VLC

If you're new to patching, you might notice that creating an MSP is a difficult task. Unlike MSIs, which can be created with the click of a button, MSPs require additional steps and can appear more complicated. But don't be concerned! Here are the straightforward steps for creating an MSP in Advanced Installer:

1. Create the MSI for v1.0 of your app.
2. Create the MSI for v1.1 following the patch rules.
3. Create a patch project to compare the two MSI packages.

We already repackaged VLC Media player earlier, but let’s assume that a new version came along and only changed 1 file and 1 registry. 

![ai modified vlc for patch](https://cdn.advancedinstaller.com/img/msi-upgrades-and-patches/ai-modified-vlc-for-patch.png "ai modified vlc for patch")  

We will simply copy the resulted VLC Media Player MSI and change any desired file and registry and we will assume that this is the second MSI for VLC Media Player.

Once we have our 2 MSI files, let's get started with creating the patch file using Advanced Installer:

\- Launch Advanced Installer and navigate to the Updates tab.

![ai patch](https://cdn.advancedinstaller.com/img/msi-upgrades-and-patches/ai-patch.png "ai patch")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2144310/7443" target="_top" id="2144310">
  <img src="//a.impactradius-go.com/display-ad/7443-2144310" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2144310/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)If you haven't installed Advanced Installer yet, you can download a 30-day full-featured trial from our website.

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2016165/19272" target="_top" id="2016165">
  <img src="//a.impactradius-go.com/display-ad/19272-2016165" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2016165/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- Create a new Installer Patch project and fill in all the necessary information related to your patch identification in the Patch Details page and then in the Product Details.

![ai patch details](https://cdn.advancedinstaller.com/img/msi-upgrades-and-patches/ai-patch-details.png "ai patch details")  

\- Configure the Add/Remove (Control Panel) information. This sets up the display name in the Control Panel. There, you can also set the option to Allow patch removal.

![ai patch control panel](https://cdn.advancedinstaller.com/img/msi-upgrades-and-patches/ai-patch-control-panel.png "ai patch control panel")  

\- Optional: Digitally sign the patch. This step helps ensure the integrity and authenticity of the patch.

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)Note that signing the patch requires a valid digital certificate.

![ai patch digital sign](https://cdn.advancedinstaller.com/img/msi-upgrades-and-patches/ai-patch-digital-sign.png "ai patch digital sign")  

<!-- affiliate ads begin -->
<a href="https://ephamedtechinc.pxf.io/c/5597632/2137216/26400" target="_top" id="2137216">
  <img src="//a.impactradius-go.com/display-ad/26400-2137216" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://ephamedtechinc.pxf.io/i/5597632/2137216/26400" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- Proceed to the Images page and right-click on the Target Computer. Here you need to first point out the Upgraded MSI and then the Targeted one. The upgraded MSI is the version you want to update to, while the targeted MSI is the base version you want to patch.

![ai patch images](https://cdn.advancedinstaller.com/img/msi-upgrades-and-patches/ai-patch-images.png "ai patch images")  

<!-- affiliate ads begin -->
<a href="https://bluettius.sjv.io/c/5597632/2139116/17108" target="_top" id="2139116">
  <img src="//a.impactradius-go.com/display-ad/17108-2139116" border="0" alt="https://techidaily.com" width="250" height="90"/>
</a>
<img height="0" width="0" src="https://bluettius.sjv.io/i/5597632/2139116/17108" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

By pointing out these two MSI files, Advanced Installer will generate the necessary delta (difference) between them to create the patch.

\- Save and build the patch project.

Once you have completed all the necessary configurations, save the patch project. Then, build the project to generate the patch file (MSP).

![ai patch generated](https://cdn.advancedinstaller.com/img/msi-upgrades-and-patches/ai-patch-generated.png "ai patch generated")  

You can use the Windows Installer Patch command-line tool (Msiexec.exe) with the /p parameter to install an MSP (Microsoft Patch) file. The following is the general syntax for installing an MSP file:

msiexec /p PathToMSPFile /qb

Copy

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
<li><a href="https://facebook-record-videos.techidaily.com/new-4-effective-methods-for-slide-embedding-from-youtube-for-2024/"><u>[New] 4 Effective Methods for Slide Embedding From YouTube for 2024</u></a></li>
<li><a href="https://facebook-video-footage.techidaily.com/updated-2024-approved-enchanting-viewers-the-art-of-crafting-engaging-youtube-description-templates/"><u>[Updated] 2024 Approved Enchanting Viewers The Art of Crafting Engaging YouTube Description Templates</u></a></li>
<li><a href="https://fox-boxes.techidaily.com/updated-voice-vaults-best-speech-to-text-tools-without-online-dependency/"><u>[Updated] Voice Vaults Best Speech-to-Text Tools Without Online Dependency</u></a></li>
<li><a href="https://facebook-video-share.techidaily.com/updated-youtube-subscriber-boost-the-4-simplest-tricks-to-grow-your-channel-faster/"><u>[Updated] YouTube Subscriber Boost – The 4 Simplest Tricks to Grow Your Channel Faster</u></a></li>
<li><a href="https://win-updates.techidaily.com/1726030172013-aviutl/"><u>音声編集ガイド：AviUtlでの切り取り・レベリング技術を学ぶ</u></a></li>
<li><a href="https://fake-location.techidaily.com/apply-these-techniques-to-improve-how-to-detect-fake-gps-location-on-nubia-red-magic-8s-proplus-drfone-by-drfone-virtual-android/"><u>Apply These Techniques to Improve How to Detect Fake GPS Location On Nubia Red Magic 8S Pro+ | Dr.fone</u></a></li>
<li><a href="https://win-updates.techidaily.com/elite-power-user-secrets-unveil-top-11-undiscovered-gesture-shortcuts-on-your-trackpad/"><u>Elite Power User Secrets: Unveil Top 11 Undiscovered Gesture Shortcuts on Your Trackpad</u></a></li>
<li><a href="https://games-able.techidaily.com/expert-tips-for-effective-steam-product-returns/"><u>Expert Tips for Effective Steam Product Returns</u></a></li>
<li><a href="https://activate-lock.techidaily.com/in-2024-new-guide-how-to-check-icloud-activation-lock-status-from-your-apple-iphone-12-pro-max-by-drfone-ios/"><u>In 2024, New Guide How To Check iCloud Activation Lock Status From Your Apple iPhone 12 Pro Max</u></a></li>
<li><a href="https://win-updates.techidaily.com/mastering-dns-configuration-a-step-by-step-guide-for-changing-ip-addresses-in-windows-os/"><u>Mastering DNS Configuration: A Step-by-Step Guide for Changing IP Addresses in Windows OS</u></a></li>
<li><a href="https://win-updates.techidaily.com/1726029980771-ogg/"><u>Oggファイル改竢・マージ・カット・レベル変更のための劣化しない編集手法</u></a></li>
<li><a href="https://win-updates.techidaily.com/syncing-mobile-photographs-with-your-desktop-tips-for-android-users-on-windows-computers-zdnet/"><u>Syncing Mobile Photographs with Your Desktop: Tips for Android Users on Windows Computers | ZDNet</u></a></li>
<li><a href="https://win-updates.techidaily.com/the-future-of-winamp-beyond-open-source-exploring-its-strategic-shift-explained-by-zdnet/"><u>The Future of Winamp Beyond Open-Source: Exploring Its Strategic Shift Explained by ZDNet</u></a></li>
<li><a href="https://common-error.techidaily.com/1723205625785-total-war-rome-remastered-crash-issues-simple-solutions-uncovered/"><u>Total War: Rome Remastered Crash Issues - Simple Solutions Uncovered</u></a></li>
<li><a href="https://win-updates.techidaily.com/wavmp43/"><u>WAVからMP4へ変換するための3つの最新方法とアプリケーションをご紹介</u></a></li>
<li><a href="https://howto.techidaily.com/what-to-do-if-your-tecno-spark-20-proplus-auto-does-not-work-drfone-by-drfone-fix-android-problems-fix-android-problems/"><u>What To Do if Your Tecno Spark 20 Pro+ Auto Does Not Work | Dr.fone</u></a></li>
<li><a href="https://win-updates.techidaily.com/why-and-how-to-access-windows-11-using-your-microsoft-365-business-account-expert-tips-from-zdnet/"><u>Why and How to Access Windows 11 Using Your Microsoft 365 Business Account | Expert Tips From ZDNET</u></a></li>
<li><a href="https://android-pokemon-go.techidaily.com/will-pokemon-go-ban-the-account-if-you-use-pgsharp-on-infinix-gt-10-pro-drfone-by-drfone-virtual-android/"><u>Will Pokémon Go Ban the Account if You Use PGSharp On Infinix GT 10 Pro | Dr.fone</u></a></li>
<li><a href="https://win-updates.techidaily.com/44oa44km44oz44ot44o844oj44oy44or44or44o844ks5l244gj44gf44ot44oh44kq44oa44km44oz44ot44o844oj44gr5asx5pwx44gz44kl5ac05zci44gu6kej5rg6562w/"><u>ダウンロードヘルパーを使ったビデオダウンロードに失敗する場合の解決策</u></a></li>
</ul></div>

