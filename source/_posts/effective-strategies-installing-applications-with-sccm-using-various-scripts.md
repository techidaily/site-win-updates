---
title: "Effective Strategies: Installing Applications with SCCM Using Various Scripts"
date: 2024-10-04T16:08:05.942Z
updated: 2024-10-05T20:00:04.736Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: "This Article Describes Effective Strategies: Installing Applications with SCCM Using Various Scripts"
thumbnail: https://thmb.techidaily.com/15954b5de302fb65bb19b216711303e6c7127c1ad83145148cdedf78055491f8.png
---

## Effective Strategies: Installing Applications with SCCM Using Various Scripts

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Deploy with SCCM

SCCM is an abbreviation for System Center Configuration Manager. It is a comprehensive systems management solution offered by Microsoft for managing large-scale software, operating system, and device deployments. SCCM enables IT administrators to automate software installations, manage updates and patches, deploy operating systems to new machines, and perform a variety of other administrative tasks across a network.

SCCM provides a centralized console through which administrators can efficiently manage and monitor software and hardware resource deployment and configuration. It includes inventory management, software distribution, patch management, remote control, and reporting capabilities. SCCM integrates with Active Directory to enable targeted deployments based on user and device information.

Administrators can use SCCM to create packages and programs that can be used to deploy software applications, perform system updates, and manage configurations across multiple devices such as desktops, laptops, servers, and mobile devices. It supports both on-premises and cloud-based deployments, giving organizations of all sizes flexibility.

SCCM is critical for streamlining IT operations, reducing manual efforts, ensuring compliance, and ensuring a standardized and secure computing environment. It enables organizations to manage their software and hardware assets more efficiently, improve security and compliance, and simplify the process of deploying and managing systems across the enterprise.

When it comes to SCCM, there are two methods for deploying packages. If the package is an MSI, the steps are much simpler, as shown below. Of course, if you want to use wrappers or EXE bundles, you can, but there are some extra steps to take.

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2043661/7443" target="_top" id="2043661">
  <img src="//a.impactradius-go.com/display-ad/7443-2043661" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2043661/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Deploy MSI via SCCM

To deploy an MSI via SCCM, go to Software Library -> Application Management -> Applications -> right click Create Application

![sccm create application](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application.png "sccm create application")  

Because the source is an MSI, choose Windows Installer and browse for source content

![sccm create application msi](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-msi.png "sccm create application msi")  

This warning is present with most MSI packages, so we can click YES:

![sccm create application msi warning](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-msi-warning.png "sccm create application msi warning")  

The next steps require only to acknowledge what is going to be created so click Next until the wizard is finished.

![sccm create application msi info](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-msi-info.png "sccm create application msi info")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2118325/7443" target="_top" id="2118325">
  <img src="//a.impactradius-go.com/display-ad/7443-2118325" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2118325/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

![sccm create application msi general info](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-msi--general-info.png "sccm create application msi general info")  

![sccm create application msi completion](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-msi-completion.png "sccm create application msi completion")  

An that is it, all that is left to be done is to distribute the package content on all available Distribution Points and deploy the packaged to the desired list of devices/users in the infrastructure.

### Deploy EXE/VBscript/PowerShell via SCCM

When it comes to other forms of installers, there are a few additional steps which need to be taken. First, go to Software Library -> Application Management -> Applications -> right click Create Application

![sccm create application](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application.png "sccm create application")  

<!-- affiliate ads begin -->
<span id="1630055">
					<video width="192" height="320" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1630055.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/18460-1630055">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1630055.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:120px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fcaperobbin.sjv.io%2Fc%2F5597632%2F1630055%2F18460'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1630055/18460" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

We will have to choose Manually specify the application information, which will give you the option to choose Script Installer later on this wizard.

![sccm create application script manual](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-manual.png "sccm create application script manual")  

Next, fill in all the information for the General Information tab. Keep in mind that “Name” is only an internal information in SCCM and not what the user sees in Software Center.

![sccm create application script general information](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-general-information.png "sccm create application script general information")  

Next, select English default and remove all other languages if not specifically mentioned otherwise. The Localized application name is the name shown is Software Center:

![sccm create application script selected language](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-selected-language.png "sccm create application script selected language")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2075462/7443" target="_top" id="2075462">
  <img src="//a.impactradius-go.com/display-ad/7443-2075462" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2075462/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

We will need to create a deployment type. A deployment type includes all of the information and instructions required for SCCM to successfully install and manage the application. Details such as the installation command, installation behavior, requirements, detection methods, and user experience settings are all included. SCCM supports a variety of deployment types to accommodate a variety of application scenarios and deployment needs.

![sccm create application script create deployment](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-create-deployment.png "sccm create application script create deployment")  

When we reach the specify settings dialog, we choose again Script Installer:

![sccm create application script select script installer](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-select-script-installer.png "sccm create application script select script installer")  

<!-- affiliate ads begin -->
<a href="https://bluetties.sjv.io/c/5597632/2141688/17094" target="_top" id="2141688">
  <img src="//a.impactradius-go.com/display-ad/17094-2141688" border="0" alt="https://techidaily.com" width="120" height="90"/>
</a>
<img height="0" width="0" src="https://bluetties.sjv.io/i/5597632/2141688/17094" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Next, we fill in the application deployment type name:

![sccm create application script deployment name](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-deployment-name.png "sccm create application script deployment name")  

Now is the part where we add the Content location from the master share and the install and uninstall lines.

![sccm create application script deployment content location](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-deployment-content-location.png "sccm create application script deployment content location")  

On the next tab, add the detection method. The detection method checks for the existence of an application using specific criteria or rules. When you deploy an application in SCCM, you define a detection method to ensure that the application is only installed on devices that require it, or to determine whether an upgrade or update is needed.

The detection method can be configured to use various criteria, such as:

* File or Folder Detection: SCCM can check the device for the presence of a specific file or folder. It can look for the presence of an executable file, a configuration file, or a specific folder structure associated with the application, for example.
* Registry Key Detection: SCCM can check the device for the presence or value of a specific registry key. This is frequently used to identify applications that generate specific registry entries during installation.
* Windows Installer Detection: SCCM can use the Windows Installer database (MSI) to see if a particular product code, package code, or product version is already installed on the device.
* Custom Script Detection: Custom scripts (VBScript, PowerShell, etc.) can be used to define detection logic in SCCM. Administrators can create scripts to perform complex checks based on their needs.

With the MSI deployment method, this is easy because SCCM uses the Windows Installer detection which checks for the presence of the product code, and these steps which we are doing here are skipped. In case your package contains an MSI it is recommended to use the Windows Installer Detection.

![sccm create application script detection method](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-detection-method.png "sccm create application script detection method")  

<!-- affiliate ads begin -->
<a href="https://ephamedtechinc.pxf.io/c/5597632/2137207/26400" target="_top" id="2137207">
  <img src="//a.impactradius-go.com/display-ad/26400-2137207" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://ephamedtechinc.pxf.io/i/5597632/2137207/26400" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

![sccm create application script detection method options](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-detection-method-options.png "sccm create application script detection method options")  

Next, we reach the user experience settings. The configuration options that determine how an application installation or update is presented and handled on end-user devices are referred to as user experience settings with applications. Administrators can use these settings to customize the behavior and appearance of application deployments in order to provide a consistent user experience. The following are some of the most common user experience settings available in SCCM:

* Install for User or System: This setting determines whether the application is installed per user or per system. Per-user installation installs the application for the currently logged-on user, whereas per-system installation installs it for all users on the device.
* Install Whether or Not a User is Logged On: Determines whether the application installation should continue even if no user is currently logged in.
* Allow Users to Interact with the Installation: Allows or disables user interaction with the installation process, such as displaying or suppressing installation prompts or dialogs.

The most used configuration options for these step are:

* Installation behavior: Install for system (runs under NT System/Administrator account)
* Logon requirement: Whether or not a user is logged in
* Installation program visibility: Normal
* Allow users to view and interact with the program installation: Checked

![sccm create application script user experience](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-user-experience.png "sccm create application script user experience")  

Click next and add installation requirements if needed and dependency application

![sccm create application script dependencies](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-dependencies.png "sccm create application script dependencies")  

In the final part, click Next until everything is done.

![sccm create application script confirm deployment](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-confirm-deployment.png "sccm create application script confirm deployment")  

<!-- affiliate ads begin -->
<a href="https://imp.i110150.net/c/5597632/798165/11305" target="_top" id="798165">
  <img src="//a.impactradius-go.com/display-ad/11305-798165" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://imp.i110150.net/i/5597632/798165/11305" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

![sccm create application script confirm deployment success](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-confirm-deployment-success.png "sccm create application script confirm deployment success")  

![sccm create application script confirm application creation](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-confirm-application-creation.png "sccm create application script confirm application creation")  

![sccm create application script confirm application creation success](https://cdn.advancedinstaller.com/img/sccm-package-deployment/sccm-create-application-script-confirm-application-creation-success.png "sccm create application script confirm application creation success")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2006919/19272" target="_top" id="2006919">
  <img src="//a.impactradius-go.com/display-ad/19272-2006919" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2006919/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

And that is it. As with MSI deployments, all that remains is to distribute the package content to all available Distribution Points and deploy the package to the desired list of infrastructure devices/users.

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
<li><a href="https://youtube-sure.techidaily.com/he-ultimate-guide-to-aspect-ratios-for-youtube-images/"><u>[New] The Ultimate Guide to Aspect Ratios for YouTube Images</u></a></li>
<li><a href="https://instagram-video-recordings.techidaily.com/2024-approved-instavideo-magic-crafting-a-plan-to-capture-your-audiences-attention/"><u>2024 Approved InstaVideo Magic Crafting a Plan to Capture Your Audience's Attention</u></a></li>
<li><a href="https://network-issues.techidaily.com/d3d-startup-error-successfully-overcome/"><u>D3D Startup Error, Successfully Overcome</u></a></li>
<li><a href="https://win-updates.techidaily.com/essential-techniques-for-preserving-contact-information-on-android-devices/"><u>Essential Techniques for Preserving Contact Information on Android Devices</u></a></li>
<li><a href="https://win-updates.techidaily.com/guide-utilizing-vbscript-and-powershell-for-efficient-driver-management-tasks/"><u>Guide: Utilizing VBScript and PowerShell for Efficient Driver Management Tasks</u></a></li>
<li><a href="https://win-amazing.techidaily.com/how-to-convert-amv-video-formats-for-free-using-movavis-easy-to-use-software/"><u>How to Convert AMV Video Formats for Free Using Movavi's Easy-to-Use Software</u></a></li>
<li><a href="https://unlock-android.techidaily.com/how-to-track-imei-number-of-xiaomi-mix-fold-3-through-google-earth-by-drfone-android/"><u>How To Track IMEI Number Of Xiaomi Mix Fold 3 Through Google Earth?</u></a></li>
<li><a href="https://review-topics.techidaily.com/how-to-use-face-id-make-purchases-on-iphone-8-plus-by-drfone-ios-unlock-ios-unlock/"><u>How to Use Face ID make purchases on iPhone 8 Plus ?</u></a></li>
<li><a href="https://extra-hints.techidaily.com/insightful-review-the-comprehensive-theta-s-experience/"><u>Insightful Review The Comprehensive Theta S Experience</u></a></li>
<li><a href="https://win-updates.techidaily.com/new-release-alert-explore-the-advanced-capabilities-of-apowermanager-version-30/"><u>New Release Alert: Explore the Advanced Capabilities of ApowerManager Version 3.0!</u></a></li>
<li><a href="https://techidaily.com/remove-the-lock-of-itel-by-drfone-android-unlock-android-unlock/"><u>Remove the lock of Itel</u></a></li>
<li><a href="https://win-updates.techidaily.com/securing-file-transfers-comprehensive-guide-to-defending-against-krack-vulnerability/"><u>Securing File Transfers: Comprehensive Guide to Defending Against KRACK Vulnerability</u></a></li>
<li><a href="https://win-updates.techidaily.com/step-by-step-guide-capturing-your-safari-sessions-on-iphone/"><u>Step-by-Step Guide: Capturing Your Safari Sessions on iPhone</u></a></li>
<li><a href="https://win-updates.techidaily.com/step-by-step-guide-disabling-find-my-iphone-feature-safely-without-a-passcode/"><u>Step-by-Step Guide: Disabling Find My iPhone Feature Safely without a Passcode</u></a></li>
<li><a href="https://win-updates.techidaily.com/top-5-essential-tactics-to-fortify-your-gmail-security-against-cyber-attacks/"><u>Top 5 Essential Tactics to Fortify Your Gmail Security Against Cyber Attacks</u></a></li>
<li><a href="https://vp-tips.techidaily.com/top-tier-drones-for-sale-today-for-2024/"><u>Top-Tier Drones for Sale Today for 2024</u></a></li>
<li><a href="https://win-updates.techidaily.com/unlocking-affordable-data-rescue-solutions-the-best-free-replacement-for-mackeeper-on-macs-and-pcs/"><u>Unlocking Affordable Data Rescue Solutions: The Best Free Replacement for Mackeeper on Macs and PCs</u></a></li>
</ul></div>

