---
title: "Guide: Utilizing VBScript and PowerShell for Efficient Driver Management Tasks"
date: 2024-10-07T02:25:06.484Z
updated: 2024-10-10T20:31:17.608Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: "This Article Describes Guide: Utilizing VBScript and PowerShell for Efficient Driver Management Tasks"
thumbnail: https://thmb.techidaily.com/3a153ca8f2151a31f0bfcdf6fa8070d85fd583f87560d1faafe457040c6fd984.jpg
---

## Guide: Utilizing VBScript and PowerShell for Efficient Driver Management Tasks

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Install/uninstall driver

Working with drivers is not something to be worried about. Although the MSI technology does not offer a native way via the database tables that you can use, the OS is offering multiple choices for you to achieve this goal.

Let’s have a look at how you can install drivers with MSI by taking different approaches.

### DPInst

Driver Package Installer (DPInst)is a component of [Driver Install Frameworks (DIFx)](http://msdn.microsoft.com/en-us/library/ff544838.aspx "Driver Install Frameworks (DIFx)") version 2.1\. DIFx simplifies and customizes the installation of driver packages for devices that you wish to install on the computer. This type of installation is commonly known as a software-first installation. DPInst also automatically updates the drivers for any installed devices that are supported by the newly installed driver packages.

DPInst searches for INF files for driver packages in the DPInst working directory which by default is the DPInst root directory, which is the directory that contains the DPInst executable (DPInst.exe).

You can also use the /path command-line switch to specify a custom DPInst working directory.

The log files for the DPInst utility can be found in the %SystemRoot%\\DPInst.log. However, DPInst does not come natively with the OS and must be added into the MSI package, preferably near the driver .inf files.

To install a driver with DPInst, the following command can be used:

DPInst_x64.exe /F /LM /S

Copy

For the full list of commands which DPInst supports, you can use the following:

DPInst_x64.exe /?

Copy

### PnPUtil

Unlike DPInst, [PnPUtil](https://learn.microsoft.com/en-us/windows-hardware/drivers/devtest/pnputil "PnPUtil")tool comes natively into the OS and lets an administrator perform actions on driver packages. lets an administrator perform actions on driver packages. With it you can add a driver package to the store, install a driver package on the computer and delete a driver package.

To install a driver with PnPUtil, the following command can be used:

PNPUtil.exe /add-driver PATH\DRIVERNAME.inf /install

Copy

For the full list of commands which PnPUtil supports, you can use the following:

PNPUtil.exe /?

Copy

Now that we know two methods which we can use to install the drivers, let’s see how we can use them in VBScript or PowerShell.

### Installing drivers with VBScript

Let’s take a look at both utility tools and create the necessary scripts to install a driver. Let’s assume that the driver **.inf** name is HP.inf. Also, let’s assume that we are going to place the DPInst.exe utility directly into the C:\\Windows\\DPInst folder and there we are going to place the .inf file as well.

The script to install the driver is:

Option Explicit
On Error Resume Next
Dim strCmd,WshShell,strInstalldir
Set WshShell = CreateObject("WScript.Shell")
strInstalldir = WshShell.ExpandEnvironmentStrings("%SYSTEMROOT%")
strCmd = chr(34) & strInstalldir & "\DPInst\DPInst_x64.exe" & chr(34) & " /F /LM /S"
WshShell.Run strCmd
Set WshShell = Nothing

Copy

This VBScript performs the following actions:

* Option Explicit: Enables explicit variable declaration, ensuring that all variables are declared before use.
* On Error Resume Next: Instructs the script to continue execution even if an error occurs.
* Dim strCmd, WshShell, strInstalldir: Declares variables to hold the command, Windows Script Host Shell object, and the installation directory.
* Set WshShell = CreateObject("WScript.Shell"): Creates an instance of the Windows Script Host Shell object.
* strInstalldir = WshShell.ExpandEnvironmentStrings("%SYSTEMROOT%"): Retrieves the path of the Windows installation directory using the %SYSTEMROOT% environment variable.
* strCmd = chr(34) & strInstalldir & "\\DPInst\\DPInst\_x64.exe" & chr(34) & " /F /LM /S": Constructs the command to be executed. It combines the installation directory path with the relative path to the "DPInst\_x64.exe" executable. The /F, /LM, and /S are command-line switches or parameters for the executable.
* WshShell.Run strCmd: Runs the command stored in strCmd using the Run method of the Windows Script Host Shell object. This executes the DPInst\_x64.exe installer with the specified command-line switches.
* Set WshShell = Nothing: Releases the reference to the Windows Script Host Shell object.

In summary, the script runs the DPInst\_x64.exe installer, located in the DPInst subfolder under the Windows installation directory, with the command-line switches /F, /LM, and /S. The purpose and functionality of the DPInst\_x64.exe installer may depend on the specific software or device driver being installed.

The script to uninstall the driver is:

Option Explicit
On Error Resume Next
Dim strCmd,WshShell,strInstalldir,strcmd1, strcmd2
Set WshShell = CreateObject("WScript.Shell")
strInstalldir = WshShell.ExpandEnvironmentStrings("%SYSTEROOT%")
strcmd= chr(34) & strInstalldir & "\DPInst\DPInst_x64.exe" & chr(34) & " /S /U " & chr(34) & strInstalldir & "\DPInst\HP.inf" & chr(34) &" /D"
WshShell.Run strCmd
Set WshShell = Nothing

Copy

This VBScript performs the following actions:

* Option Explicit: Enables explicit variable declaration, ensuring that all variables are declared before use.
* On Error Resume Next: Instructs the script to continue execution even if an error occurs.
* Dim strCmd, WshShell, strInstalldir, strCmd1, strCmd2: Declares variables to hold the commands, Windows Script Host Shell object, and the installation directory.
* Set WshShell = CreateObject("WScript.Shell"): Creates an instance of the Windows Script Host Shell object.
* strInstalldir = WshShell.ExpandEnvironmentStrings("%SYSTEROOT%"): Retrieves the path of the Windows installation directory using the %SYSTEROOT% environment variable.
* strCmd = chr(34) & strInstalldir & "\\DPInst\\DPInst\_x64.exe" & chr(34) & " /S /U " & chr(34) & strInstalldir & "\\DPInst\\HP.inf" & chr(34) &" /D": Constructs the command to be executed. It combines the installation directory path with the relative paths to the "DPInst\_x64.exe" executable and "HP.inf" file. The /S, /U, and /D are command-line switches or parameters for the executable.
* WshShell.Run strCmd: Runs the command stored in strCmd using the Run method of the Windows Script Host Shell object. This executes the DPInst\_x64.exe installer with the specified command-line switches and the "HP.inf" file for driver uninstallation.
* Set WshShell = Nothing: Releases the reference to the Windows Script Host Shell object.

Once we have the scripts done and the DPInst utility downloaded, open Advanced Installer and first navigate to the Files and Folders Page. In here, create a new directory under **Windows Volume\\Windows** called **DPInst** and add the DPInst utility with the HP.inf file near it.

![add the DPInst utility with the HP.inf](https://cdn.advancedinstaller.com/img/install-uninstall-driver-using-custom-actions/dpinstvbscript.png "add the DPInst utility with the HP.inf")  

<!-- affiliate ads begin -->
<span id="1328683">
					<video width="200" height="200" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1328683.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/15852-1328683">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1328683.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:125px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fthefitville.pxf.io%2Fc%2F5597632%2F1328683%2F15852'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1328683/15852" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Next, navigate to the Custom Actions Page and add the **Launch attached file** predefined custom action into the sequence, select the installation vbscript file that was previously created and configure the Custom Action as such:

![add the Launch attached file predefined custom action](https://cdn.advancedinstaller.com/img/install-uninstall-driver-using-custom-actions/dpinstvbscriptCAINST.png "add the Launch attached file predefined custom action")  

<!-- affiliate ads begin -->
<a href="https://bluettiit.sjv.io/c/5597632/2148127/17093" target="_top" id="2148127">
  <img src="//a.impactradius-go.com/display-ad/17093-2148127" border="0" alt="https://techidaily.com" width="120" height="90"/>
</a>
<img height="0" width="0" src="https://bluettiit.sjv.io/i/5597632/2148127/17093" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Repeat the same steps for the uninstall script and configure the custom action as follows:

![uninstall script and configure the custom action](https://cdn.advancedinstaller.com/img/install-uninstall-driver-using-custom-actions/dpinstvbscriptCAUNINST.png "uninstall script and configure the custom action")  

And that is it, build your package and install it and the driver will appear as installed.

If we don’t want to use the DPInst method and want to go with the PnPUtil one, the VBScript for installation should look like this:

Option Explicit
On Error Resume Next
Dim strCmd,WshShell,strInstalldir,strcmd1, strcmd2
Set WshShell = CreateObject("WScript.Shell")
strInstalldir = WshShell.ExpandEnvironmentStrings("%SYSTEROOT%")
strcmd= "pnputil.exe /add-driver " & chr(34) & strInstalldir & "\DPInst\HP.inf" & chr(34)
WshShell.Run strCmd
Set WshShell = Nothing

Copy

This VBScript performs the following actions:

* Option Explicit: Enables explicit variable declaration, ensuring that all variables are declared before use.
* On Error Resume Next: Instructs the script to continue execution even if an error occurs.
* Dim strCmd, WshShell, strInstalldir, strCmd1, strCmd2: Declares variables to hold the commands, Windows Script Host Shell object, and the installation directory.
* Set WshShell = CreateObject("WScript.Shell"): Creates an instance of the Windows Script Host Shell object.
* strInstalldir = WshShell.ExpandEnvironmentStrings("%SYSTEROOT%"): Retrieves the path of the Windows installation directory using the %SYSTEROOT% environment variable.
* strCmd = "pnputil.exe /add-driver " & chr(34) & strInstalldir & "\\DPInst\\HP.inf" & chr(34): Constructs the command to be executed. It combines the pnputil.exe utility command /add-driver with the path to the "HP.inf" file for driver installation. The chr(34) is used to enclose the path in double quotes.
* WshShell.Run strCmd: Runs the command stored in strCmd using the Run method of the Windows Script Host Shell object. This executes the pnputil.exe utility with the /add-driver command and the specified driver inf file for installation.
* Set WshShell = Nothing: Releases the reference to the Windows Script Host Shell object.

The script to remove the driver with PnPUtil is:

Option Explicit
On Error Resume Next
Dim strCmd,WshShell,strInstalldir,strcmd1, strcmd2
Set WshShell = CreateObject("WScript.Shell")
strInstalldir = WshShell.ExpandEnvironmentStrings("%SYSTEROOT%")
strcmd= "pnputil.exe /delete-driver " & chr(34) & strInstalldir & "\DPInst\HP.inf" & chr(34)
WshShell.Run strCmd
Set WshShell = Nothing

Copy

This VBScript performs the following actions:

* Option Explicit: Enables explicit variable declaration, ensuring that all variables are declared before use.
* On Error Resume Next: Instructs the script to continue execution even if an error occurs.
* Dim strCmd, WshShell, strInstalldir, strCmd1, strCmd2: Declares variables to hold the commands, Windows Script Host Shell object, and the installation directory.
* Set WshShell = CreateObject("WScript.Shell"): Creates an instance of the Windows Script Host Shell object.
* strInstalldir = WshShell.ExpandEnvironmentStrings("%SYSTEROOT%"): Retrieves the path of the Windows installation directory using the %SYSTEROOT% environment variable.
* strCmd = "pnputil.exe /delete-driver " & chr(34) & strInstalldir & "\\DPInst\\HP.inf" & chr(34): Constructs the command to be executed. It combines the pnputil.exe utility command /delete-driver with the path to the "HP.inf" file for driver deletion. The chr(34) is used to enclose the path in double quotes.
* WshShell.Run strCmd: Runs the command stored in strCmd using the Run method of the Windows Script Host Shell object. This executes the pnputil.exe utility with the /delete-driver command and the specified driver inf file for deletion.
* Set WshShell = Nothing: Releases the reference to the Windows Script Host Shell object.

Do the same steps as we did before to add the VBScript files in the custom actions, build the installer and the driver should get installed.

### Installing drivers with PowerShell

Let’s assume that the driver **.inf** name is HP.inf. Also, let’s assume that we are going to place the DPInst.exe utility directly into the C:\\Windows\\DPInst folder and there we are going to place the .inf file as well.

The script to install the file as we did with VBScript is:

$DPInstLoc = $env:SystemRoot + "\DPInst\DPInst_x64.exe"
$cmd = "$DPInstLoc /F /LM /S"
Invoke-Expression $cmd

Copy

The script performs the following actions:

* $DPInstLoc = $env:SystemRoot + "\\DPInst\\DPInst\_x64.exe": Sets the variable $DPInstLoc to the path of the DPInst\_x64.exe file located in the %SystemRoot%\\DPInst directory. The $env:SystemRoot environment variable represents the path to the Windows installation directory.
* $cmd = "$DPInstLoc /F /LM /S": Constructs a command string that includes the value of $DPInstLoc and additional command-line arguments. In this case, the command is DPInst\_x64.exe /F /LM /S. The /F switch specifies that existing driver packages should be deleted, /LM specifies that the driver should be installed for all users on the local machine, and /S enables silent installation without displaying any user interface.
* Invoke-Expression $cmd: Executes the command stored in the $cmd variable using the Invoke-Expression cmdlet. This cmdlet interprets and runs the command as if it were typed directly into the PowerShell console.

The script to uninstall the driver is:

$DPInstLoc = $env:SystemRoot + "\DPInst\DPInst_x64.exe"
$INFLocation = $env:SystemRoot + "\DPInst\HP.inf"
$cmd = "$DPInstLoc /S /U $INFLocation"
Invoke-Expression $cmd

Copy

The script performs the following actions:

* $DPInstLoc = $env:SystemRoot + "\\DPInst\\DPInst\_x64.exe": Sets the variable $DPInstLoc to the path of the DPInst\_x64.exe file located in the %SystemRoot%\\DPInst directory. The $env:SystemRoot environment variable represents the path to the Windows installation directory.
* $INFLocation = $env:SystemRoot + "\\DPInst\\HP.inf": Sets the variable $INFLocation to the path of the HP.inf file located in the %SystemRoot%\\DPInst directory.
* $cmd = "$DPInstLoc /S /U $INFLocation": Constructs a command string that includes the values of $DPInstLoc and $INFLocation as well as additional command-line arguments. In this case, the command is DPInst\_x64.exe /S /U HP.inf. The /S switch enables silent installation without displaying any user interface, and the /U switch specifies the INF file to be used for uninstallation.
* Invoke-Expression $cmd: Executes the command stored in the $cmd variable using the Invoke-Expression cmdlet. This cmdlet interprets and runs the command as if it were typed directly into the PowerShell console.

Once we have the scripts done and the DPInst utility downloaded, open Advanced Installer and first navigate to the Files and Folders Page. In here, create a new directory under **Windows Volume\\Windows** called **DPInst** and add the DPInst utility with the HP.inf file near it.

Next, navigate to the Custom Actions Page and add the **Run PowerShell script file** predefined custom action into the sequence, select **Attached Script** and select the file that was previously created and configure the Custom Action as such:

![add the Run PowerShell script file predefined custom action](https://cdn.advancedinstaller.com/img/install-uninstall-driver-using-custom-actions/dpinstPSInst.png "add the Run PowerShell script file predefined custom action")  

Repeat the same process for the uninstall script and configure the Custom Action as follows:

![configure the Custom Action](https://cdn.advancedinstaller.com/img/install-uninstall-driver-using-custom-actions/dpinstPSUninst.png "configure the Custom Action")  

Next, build the package and during installation/uninstallation the PowerShell scripts will run and install/uninstall the driver.

If we are going with the PnPUtil route, the script to install is quite simple:

$DriverPath = $env:windir + "\DPInst"
Get-ChildItem $DriverPath -Recurse -Filter "*inf" | ForEach-Object { PNPUtil.exe /add-driver $_.FullName /install }

Copy

The script performs the following actions:

* $DriverPath = $env:windir + "\\DPInst": Sets the variable $DriverPath to the path of the DPInst directory located in the Windows installation directory (%windir%). The $env:windir environment variable represents the path to the Windows directory.
* Get-ChildItem $DriverPath -Recurse -Filter "\*inf": Retrieves all the files with the ".inf" extension located in the $DriverPath directory and its subdirectories using the Get-ChildItem cmdlet. The -Recurse parameter ensures that files are searched recursively.
* ForEach-Object { PNPUtil.exe /add-driver $\_.FullName /install }: For each ".inf" file found in the previous step, it executes the PNPUtil.exe utility to add and install the driver specified by the $\_ variable (represents the current file object). The /add-driver switch is used to add the driver package, and the /install switch is used to install the driver.

The script to uninstall the driver with PnPUtil is:

$DriverPath = $env:windir + "\DPInst\HP.inf"
$Arguments = "pnputil /delete-driver $DriverPath"
Start-Process -FilePath PowerShell.exe -ArgumentList $Arguments -Wait

Copy

Thescript performs the following actions:

* $DriverPath = $env:windir + "\\DPInst\\HP.inf": Sets the variable $DriverPath to the path of the "HP.inf" file located in the DPInst directory within the Windows installation directory (%windir%). The $env:windir environment variable represents the path to the Windows directory.
* $Arguments = "pnputil /delete-driver $DriverPath": Sets the variable $Arguments to the command-line arguments that will be passed to the PowerShell process. In this case, it constructs a command to delete the driver specified by the $DriverPath variable using the pnputil utility.
* Start-Process -FilePath PowerShell.exe -ArgumentList $Arguments -Wait: Starts a new instance of the PowerShell process and passes the $Arguments as command-line arguments. The -Wait parameter ensures that the script waits for the PowerShell process to complete before continuing.

Once we have the scripts we need to do the same steps as we did with the DPInst method and then build and install the package.

### Installing drivers with Advanced Installer

Advanced Installer makes it much easier to handle driver operations by providing a simple and intuitive GUI for these actions.

Navigate to the Drivers page and click on **New Driver**. A window will open for you to select the .inf file which must be present in the package.

![select the .inf file](https://cdn.advancedinstaller.com/img/install-uninstall-driver-using-custom-actions/advinstdriverinst.png "select the .inf file")  

<!-- affiliate ads begin -->
<a href="https://laganoo.pxf.io/c/5597632/1657400/16446" target="_top" id="1657400">
  <img src="//a.impactradius-go.com/display-ad/16446-1657400" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://laganoo.pxf.io/i/5597632/1657400/16446" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Advanced Installer parses the .INF file and detects what is needed and you have multiple settings to choose from:

![parses the .INF file](https://cdn.advancedinstaller.com/img/install-uninstall-driver-using-custom-actions/advinstdriverinstconfig.png "parses the .INF file")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2135405/19272" target="_top" id="2135405">
  <img src="//a.impactradius-go.com/display-ad/19272-2135405" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2135405/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

And that is it, all you have to do is build the MSI and install the package. Simple right?

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
<li><a href="https://fox-hovers.techidaily.com/new-best-fusion-of-cost-effective-and-premium-video-collage-for-android-devices/"><u>[New] Best Fusion of Cost-Effective and Premium Video Collage for Android Devices</u></a></li>
<li><a href="https://youtube-blog.techidaily.com/he-future-of-content-creation-profitability-on-youtube-for-2024/"><u>[New] The Future of Content Creation Profitability on YouTube for 2024</u></a></li>
<li><a href="https://youtube-videos.techidaily.com/updated-building-a-successful-online-presence-wirecast-streaming-to-youtube/"><u>[Updated] Building a Successful Online Presence WireCast Streaming to Youtube</u></a></li>
<li><a href="https://win-updates.techidaily.com/essential-techniques-for-preserving-contact-information-on-android-devices/"><u>Essential Techniques for Preserving Contact Information on Android Devices</u></a></li>
<li><a href="https://howto.techidaily.com/how-to-fix-unresponsive-phone-touchscreen-of-zte-nubia-z60-ultra-drfone-by-drfone-fix-android-problems-fix-android-problems/"><u>How To Fix Unresponsive Phone Touchscreen Of ZTE Nubia Z60 Ultra | Dr.fone</u></a></li>
<li><a href="https://discover-alternatives.techidaily.com/leveraging-digital-intelligence-how-modern-businesses-are-evolving-with-abbyys-insights/"><u>Leveraging Digital Intelligence: How Modern Businesses Are Evolving with ABBYY's Insights</u></a></li>
<li><a href="https://extra-hints.techidaily.com/mastering-the-art-with-sony-fdr-x1000v-action-footage/"><u>Mastering the Art with Sony FDR-X1000V Action Footage</u></a></li>
<li><a href="https://sound-tweaking.techidaily.com/new-in-2024-the-ultimate-list-of-no-cost-audio-to-text-transformation-tools-for-multimedia-creators/"><u>New In 2024, The Ultimate List of No-Cost Audio-to-Text Transformation Tools for Multimedia Creators</u></a></li>
<li><a href="https://smart-video-editing.techidaily.com/new-mac-gopro-editing-101-from-import-to-export/"><u>New Mac GoPro Editing 101 From Import to Export</u></a></li>
<li><a href="https://win-updates.techidaily.com/new-release-alert-explore-the-advanced-capabilities-of-apowermanager-version-30/"><u>New Release Alert: Explore the Advanced Capabilities of ApowerManager Version 3.0!</u></a></li>
<li><a href="https://win-updates.techidaily.com/securing-file-transfers-comprehensive-guide-to-defending-against-krack-vulnerability/"><u>Securing File Transfers: Comprehensive Guide to Defending Against KRACK Vulnerability</u></a></li>
<li><a href="https://win-updates.techidaily.com/step-by-step-guide-capturing-your-safari-sessions-on-iphone/"><u>Step-by-Step Guide: Capturing Your Safari Sessions on iPhone</u></a></li>
<li><a href="https://win-updates.techidaily.com/step-by-step-guide-disabling-find-my-iphone-feature-safely-without-a-passcode/"><u>Step-by-Step Guide: Disabling Find My iPhone Feature Safely without a Passcode</u></a></li>
<li><a href="https://win-updates.techidaily.com/top-5-essential-tactics-to-fortify-your-gmail-security-against-cyber-attacks/"><u>Top 5 Essential Tactics to Fortify Your Gmail Security Against Cyber Attacks</u></a></li>
<li><a href="https://win-updates.techidaily.com/unlocking-affordable-data-rescue-solutions-the-best-free-replacement-for-mackeeper-on-macs-and-pcs/"><u>Unlocking Affordable Data Rescue Solutions: The Best Free Replacement for Mackeeper on Macs and PCs</u></a></li>
<li><a href="https://buynow-info.techidaily.com/unveiling-apple-macbook-pro-16-inch-m1-2021-the-ultimate-gadget-showdown/"><u>Unveiling Apple MacBook Pro 16-Inch (M1, 2021): The Ultimate Gadget Showdown</u></a></li>
</ul></div>

