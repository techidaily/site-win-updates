---
title: How to Automate Driver Installation and Removal with VBScript & PowerShell
date: 2024-09-30T18:55:49.807Z
updated: 2024-10-05T17:52:26.930Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: This Article Describes How to Automate Driver Installation and Removal with VBScript & PowerShell
thumbnail: https://thmb.techidaily.com/b9ef13db0d4015b8f432338d38cc3c79dffc2187f90b8af800f112790cda12e7.JPG
---

## How to Automate Driver Installation and Removal with VBScript & PowerShell

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Install/uninstall driver

Working with drivers is not something to be worried about. Although the MSI technology does not offer a native way via the database tables that you can use, the OS is offering multiple choices for you to achieve this goal.

Let’s have a look at how you can install drivers with MSI by taking different approaches.

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2094415/7443" target="_top" id="2094415">
  <img src="//a.impactradius-go.com/display-ad/7443-2094415" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2094415/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

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

<!-- affiliate ads begin -->
<span id="1983551">
					<video width="576" height="240" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1983551.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/22993-1983551">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1983551.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:360px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fhomestyler.sjv.io%2Fc%2F5597632%2F1983551%2F22993'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1983551/22993" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

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

Next, navigate to the Custom Actions Page and add the **Launch attached file** predefined custom action into the sequence, select the installation vbscript file that was previously created and configure the Custom Action as such:

![add the Launch attached file predefined custom action](https://cdn.advancedinstaller.com/img/install-uninstall-driver-using-custom-actions/dpinstvbscriptCAINST.png "add the Launch attached file predefined custom action")  

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

<!-- affiliate ads begin -->
<a href="https://unicoeye.pxf.io/c/5597632/2148771/18498" target="_top" id="2148771">
  <img src="//a.impactradius-go.com/display-ad/18498-2148771" border="0" alt="https://techidaily.com" width="350" height="90"/>
</a>
<img height="0" width="0" src="https://unicoeye.pxf.io/i/5597632/2148771/18498" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Installing drivers with Advanced Installer

Advanced Installer makes it much easier to handle driver operations by providing a simple and intuitive GUI for these actions.

Navigate to the Drivers page and click on **New Driver**. A window will open for you to select the .inf file which must be present in the package.

![select the .inf file](https://cdn.advancedinstaller.com/img/install-uninstall-driver-using-custom-actions/advinstdriverinst.png "select the .inf file")  

Advanced Installer parses the .INF file and detects what is needed and you have multiple settings to choose from:

![parses the .INF file](https://cdn.advancedinstaller.com/img/install-uninstall-driver-using-custom-actions/advinstdriverinstconfig.png "parses the .INF file")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1886069/19272" target="_top" id="1886069">
  <img src="//a.impactradius-go.com/display-ad/19272-1886069" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1886069/19272" style="position:absolute;visibility:hidden;" border="0" />
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
<li><a href="https://fox-direct.techidaily.com/new-2024-approved-converting-gifs-to-emoticon-stickers-on-telegram-and-friends-servers/"><u>[New] 2024 Approved Converting GIFs to Emoticon Stickers on Telegram & Friends Servers</u></a></li>
<li><a href="https://instagram-clips.techidaily.com/new-building-personalized-instagram-feed-outlines-for-2024/"><u>[New] Building Personalized Instagram Feed Outlines for 2024</u></a></li>
<li><a href="https://fox-access.techidaily.com/new-in-2024-exclusive-list-general-knowledge-quiz-channels-24/"><u>[New] In 2024, Exclusive List General Knowledge Quiz Channels '24</u></a></li>
<li><a href="https://some-guidance.techidaily.com/new-unlock-15-simple-vlog-inspirations-today/"><u>[New] Unlock 15 Simple Vlog Inspirations Today</u></a></li>
<li><a href="https://fox-hovers.techidaily.com/updated-ultimate-live-streaming-selection-guide-for-2024/"><u>[Updated] Ultimate Live Streaming Selection Guide for 2024</u></a></li>
<li><a href="https://youtube-zero.techidaily.com/st-youtube-keyword-tools-to-get-more-views/"><u>10 Best YouTube Keyword Tools to Get More Views</u></a></li>
<li><a href="https://buynow-reviews.techidaily.com/comprehensive-imo-messenger-app-evaluation/"><u>Comprehensive Imo Messenger App Evaluation</u></a></li>
<li><a href="https://win-updates.techidaily.com/has-dashlane-lost-its-edge-a-fresh-look-at-todays-leading-password-managers/"><u>Has Dashlane Lost Its Edge? A Fresh Look at Today's Leading Password Managers.</u></a></li>
<li><a href="https://win-solutions.techidaily.com/improper-installation/"><u>Improper Installation:</u></a></li>
<li><a href="https://facebook-video-content.techidaily.com/in-2024-evasion-of-ennui-comical-cells-and-chuckles-in-facebooks-boundaries/"><u>In 2024, Evasion of Ennui Comical Cells and Chuckles in Facebook's Boundaries</u></a></li>
<li><a href="https://win-updates.techidaily.com/1727401240850-master-the-switch-seamless-conversion-from-markdown-to-pdf-in-minutes-revised-tutorial/"><u>Master the Switch: Seamless Conversion From Markdown to PDF in Minutes (Revised Tutorial)</u></a></li>
<li><a href="https://win-updates.techidaily.com/recognizing-the-warning-indicators-how-to-determine-if-your-pc-is-infected-with-malware/"><u>Recognizing the Warning Indicators: How to Determine If Your PC Is Infected With Malware</u></a></li>
<li><a href="https://win-updates.techidaily.com/safeguard-internet-exploration-on-chrome-the-leading-antivirus-solutions-for-banks-and-shopping/"><u>Safeguard Internet Exploration on Chrome: The Leading Antivirus Solutions for Banks & Shopping</u></a></li>
<li><a href="https://win-updates.techidaily.com/solving-the-mystery-of-googles-sudden-diverts-to-bing-causes-and-solutions-explained/"><u>Solving the Mystery of Google's Sudden Diverts to Bing: Causes & Solutions Explained</u></a></li>
<li><a href="https://win-updates.techidaily.com/step-by-step-tutorial-getting-started-with-genshin-impact-on-pc-platforms/"><u>Step-by-Step Tutorial: Getting Started with Genshin Impact on PC Platforms</u></a></li>
<li><a href="https://win-updates.techidaily.com/top-strategies-for-effectively-removing-items-from-images/"><u>Top Strategies for Effectively Removing Items From Images</u></a></li>
</ul></div>

