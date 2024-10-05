---
title: "MSI Upgrades Versus MSP: Navigating Through Microsoft's System Package Options"
date: 2024-09-29T18:50:08.224Z
updated: 2024-10-05T19:39:13.077Z
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

<!-- affiliate ads begin -->
<a href="https://review-au.sjv.io/c/5597632/2098700/14409" target="_top" id="2098700">
  <img src="//a.impactradius-go.com/display-ad/14409-2098700" border="0" alt="https://techidaily.com" width="160" height="90"/>
</a>
<img height="0" width="0" src="https://review-au.sjv.io/i/5597632/2098700/14409" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

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
<a href="https://aligracehair.sjv.io/c/5597632/1885928/19272" target="_top" id="1885928">
  <img src="//a.impactradius-go.com/display-ad/19272-1885928" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1885928/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)If you haven't installed Advanced Installer yet, you can download a 30-day full-featured trial from our website.

<!-- affiliate ads begin -->
<a href="https://25home.pxf.io/c/5597632/2148642/16836" target="_top" id="2148642">
  <img src="//a.impactradius-go.com/display-ad/16836-2148642" border="0" alt="https://techidaily.com" width="300" height="50"/>
</a>
<img height="0" width="0" src="https://25home.pxf.io/i/5597632/2148642/16836" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- Create a new Installer Patch project and fill in all the necessary information related to your patch identification in the Patch Details page and then in the Product Details.

![ai patch details](https://cdn.advancedinstaller.com/img/msi-upgrades-and-patches/ai-patch-details.png "ai patch details")  

<!-- affiliate ads begin -->
<a href="https://imp.i357552.net/c/5597632/947746/11832" target="_top" id="947746">
  <img src="//a.impactradius-go.com/display-ad/11832-947746" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://imp.i357552.net/i/5597632/947746/11832" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- Configure the Add/Remove (Control Panel) information. This sets up the display name in the Control Panel. There, you can also set the option to Allow patch removal.

![ai patch control panel](https://cdn.advancedinstaller.com/img/msi-upgrades-and-patches/ai-patch-control-panel.png "ai patch control panel")  

<!-- affiliate ads begin -->
<a href="https://arkmc.pxf.io/c/5597632/352557/5172" target="_top" id="352557">
  <img src="//a.impactradius-go.com/display-ad/5172-352557" border="0" alt="https://techidaily.com" width="720" height="90"/>
</a>
<img height="0" width="0" src="https://arkmc.pxf.io/i/5597632/352557/5172" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- Optional: Digitally sign the patch. This step helps ensure the integrity and authenticity of the patch.

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)Note that signing the patch requires a valid digital certificate.

![ai patch digital sign](https://cdn.advancedinstaller.com/img/msi-upgrades-and-patches/ai-patch-digital-sign.png "ai patch digital sign")  

\- Proceed to the Images page and right-click on the Target Computer. Here you need to first point out the Upgraded MSI and then the Targeted one. The upgraded MSI is the version you want to update to, while the targeted MSI is the base version you want to patch.

![ai patch images](https://cdn.advancedinstaller.com/img/msi-upgrades-and-patches/ai-patch-images.png "ai patch images")  

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
<li><a href="https://desktop-recording.techidaily.com/new-2024-approved-mastery-in-motion-steam-switch-controller-techniques/"><u>[New] 2024 Approved Mastery in Motion Steam Switch Controller Techniques</u></a></li>
<li><a href="https://digital-screen-recording.techidaily.com/new-2024-approved-premier-5-minute-longshot-recorder/"><u>[New] 2024 Approved Premier 5-Minute Longshot Recorder</u></a></li>
<li><a href="https://video-screen-grab.techidaily.com/updated-in-2024-ultimate-ios-compatible-ps2-software/"><u>[Updated] In 2024, Ultimate iOS Compatible PS2 Software</u></a></li>
<li><a href="https://win-updates.techidaily.com/1-top-5-no-cost-asf-to-mp4-format-converter-tools/"><u>1. Top 5 No-Cost ASF to MP4 Format Converter Tools</u></a></li>
<li><a href="https://blog-min.techidaily.com/6-ways-to-transfer-contacts-from-oneplus-ace-2-pro-to-iphone-drfone-by-drfone-transfer-from-android-transfer-from-android/"><u>6 Ways To Transfer Contacts From OnePlus Ace 2 Pro to iPhone | Dr.fone</u></a></li>
<li><a href="https://techidaily.com/different-methods-for-resetting-oneplus-12r-phones-with-screen-locked-and-not-drfone-by-drfone-reset-android-reset-android/"><u>Different Methods for Resetting OnePlus 12R Phones with Screen Locked and Not | Dr.fone</u></a></li>
<li><a href="https://youtube-clips.techidaily.com/follow-your-favorites-top-6-mobile-apps-for-downloading-youtube-beats/"><u>Follow Your Favorites Top 6 Mobile Apps for Downloading YouTube Beats</u></a></li>
<li><a href="https://win-updates.techidaily.com/how-does-a-browser-fingerprint-reveal-your-online-identity-and-what-steps-can-you-take-to-guard-it/"><u>How Does a Browser Fingerprint Reveal Your Online Identity & What Steps Can You Take to Guard It?</u></a></li>
<li><a href="https://win-updates.techidaily.com/how-to-change-your-youtube-video-collection-into-mp3-files/"><u>How to Change Your YouTube Video Collection Into MP3 Files</u></a></li>
<li><a href="https://win-updates.techidaily.com/step-by-step-guide-getting-rid-of-deceptive-windows-security-warnings/"><u>Step-by-Step Guide: Getting Rid of Deceptive Windows Security Warnings</u></a></li>
<li><a href="https://win-updates.techidaily.com/the-ultimate-list-of-leading-sd-card-restoration-apps-find-your-perfect-match/"><u>The Ultimate List of Leading SD Card Restoration Apps - Find Your Perfect Match!</u></a></li>
<li><a href="https://data-safeguard.techidaily.com/top-iphone-contact-restoration-apps-how-to-retrieve-your-lost-connections/"><u>Top iPhone Contact Restoration Apps: How to Retrieve Your Lost Connections</u></a></li>
<li><a href="https://win-updates.techidaily.com/urgent-warning-your-mac-compromised-signs-of-gmail-phishing-and-trojan-threats/"><u>Urgent Warning: Your Mac Compromised - Signs of Gmail Phishing & Trojan Threats</u></a></li>
</ul></div>

