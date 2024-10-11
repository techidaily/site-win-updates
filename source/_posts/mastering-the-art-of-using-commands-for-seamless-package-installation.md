---
title: Mastering the Art of Using Commands for Seamless Package Installation
date: 2024-10-06T02:08:56.607Z
updated: 2024-10-10T17:52:04.488Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: This Article Describes Mastering the Art of Using Commands for Seamless Package Installation
thumbnail: https://thmb.techidaily.com/46162ff1d50cb6f1b35f044048a0b2464ebecd738e59505ca40bf7c4a2c48673.png
---

## Mastering the Art of Using Commands for Seamless Package Installation

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Command lines

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2135367/19272" target="_top" id="2135367">
  <img src="//a.impactradius-go.com/display-ad/19272-2135367" border="0" alt="https://techidaily.com" width="180" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2135367/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### MSI Command Lines

MSI command lines are used to customize the installation and configuration of MSI (Microsoft Installer) packaged applications. The following are some of the most commonly used MSI command lines:

INSTALL: The INSTALL command starts the installation of an MSI package. It usually takes the form msiexec /i <path to MSI file>.

Msiexec /i VLC Media Player.msi

Copy

UNINSTALL: The UNINSTALL command is used to uninstall an MSI package that has been installed. It has the syntax msiexec /x <ProductCode>, where the ProductCode represents the installed package's unique identifier.

Msiexec /x {35A71788-FB15-4046-BFBA-58913DDE5D9C}

Copy

REINSTALL: The REINSTALL command is used to repair or reinstall an MSI package that has already been installed. It can be used to repair problems or to update the installation. msiexec /f <ProductCode> is the syntax.

Msiexec /fus {35A71788-FB15-4046-BFBA-58913DDE5D9C}

Copy

MODIFY: The MODIFY command is used to modify an MSI package's installed features or settings. Users can add or remove specific components. msiexec /i <path to MSI file> MODIFY=<feature name> is the syntax.

Msiexec /i VLC Media Player.msi MODIFY=MainFeature

Copy

TRANSFORM: To apply an MST (transform) file to an MSI package, use the TRANSFORM command. MST files are modifications and customizations to the original MSI. msiexec /i <path to MSI file> TRANSFORMS=<path to MST file> is the syntax.

Msiexec /i VLC Media Player.msi TRANSFORMS=VLC.MST

Copy

PROPERTY: The PROPERTY command is used to set or change the value of an MSI package's property. Properties are used to manage different aspects of the installation. msiexec /i <path to MSI file> <property name>=<value> is the syntax.

Msiexec /i VLC Media Player.msi ALLUSERS=1

Copy

/qn: The /qn switch is used for silent installation, which means that no user interface is displayed during the installation process. To perform silent installations, it can be added to any installation command line.

Msiexec /i VLC Media Player.msi /qn

Copy

/LV: During the installation process, the /LV switch is used to generate a verbose log file. It collects detailed installation information that can be used for troubleshooting. msiexec /i <path to MSI file> /L\*V <log file path> is the syntax.

Msiexec /i VLC Media Player.msi /L*V C:\temp\vlc.log

Copy

These are only a few examples of commonly used MSI command lines. Depending on the MSI package and its configuration, the command line options and parameters may differ. It is best to consult the documentation or vendor's instructions for the specific command lines needed for a given application.

For more information about MSI command lines check out our [in-depth user guide](https://tools.techidaily.com/advancedinstaller/products/).

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)When deploying applications with SCCM or Intune, you don’t need to specify the full path to the installation because when the user installs it from Software Center/Company Portal, the installation runs directly from the downloaded directory which contains the files.

<!-- affiliate ads begin -->
<a href="https://laganoo.pxf.io/c/5597632/1484950/16446" target="_top" id="1484950">
  <img src="//a.impactradius-go.com/display-ad/16446-1484950" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://laganoo.pxf.io/i/5597632/1484950/16446" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

<!-- affiliate ads begin -->
<span id="1982457">
					<video width="576" height="240" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1982457.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/22993-1982457">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1982457.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:360px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fhomestyler.sjv.io%2Fc%2F5597632%2F1982457%2F22993'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1982457/22993" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### PowerShell Command Lines

PowerShell scripts are executed using the PowerShell command-line environment, which is a powerful scripting and automation framework provided by Microsoft. 

The general command line is:

Powershell.exe -file Install.ps1

Copy

PowerShell, on the other hand, introduced the concept of execution policies. PowerShell's execution policy determines the level of security for running scripts. It is a security feature that aids in the prevention of malicious or unauthorized script execution. The execution policy can be configured to control whether and where scripts can be run.

PowerShell has different execution policy levels available:

* Restricted: This is the default execution policy. It does not allow the execution of any scripts. It only allows individual commands to be run from the command line.
* AllSigned: With this execution policy, scripts can only be run if they are signed by a trusted publisher. PowerShell will prompt for confirmation before running scripts that are not digitally signed.
* RemoteSigned: Scripts downloaded from the internet or other remote sources must be signed by a trusted publisher. Locally created scripts do not require a digital signature.
* Unrestricted: This execution policy allows the execution of any script, regardless of its source. PowerShell will still display a warning before running scripts downloaded from the internet.
* Bypass: This execution policy disables the execution policy. No restrictions are applied, and PowerShell will not prompt for confirmation.
* Undefined: This execution policy is used when no execution policy is set. It inherits the execution policy from the parent or user's machine.

In most enterprises, the setting for the execution policy is usually set to either AllSigned or RemoteSigned. In this case it is recommended to sign your PowerShell scripts before executing.

But in case you are unable to sign them, there is an alternative way to run the script:

PowerShell.exe -executionpolicy bypass -file Install.ps1

Copy

By doing this, you are bypassing the set execution policy Sand no restrictions are applied, thus allowing you to run your PowerShell script.

Lastly, one other major aspect we need to consider is in regards of parameters. In PowerShell, script parameters are used to pass values or arguments to a script during runtime. They allow scripts to be flexible and configurable by accepting input from the user or other sources. Script parameters are defined within the script's code and can be accessed and used within the script.

param(
    [Parameter(Mandatory=$true)]
    [string]$ApplicationName,
    [Parameter()]
    [int]$Execution
)

Copy

Looking at the above code, the parameter $ApplicationName is mandatory and must be provided in order for the script execution to continue, while the $Execution parameter is optional.

If we take a look at PSADT and how it’s executed when you want to run the uninstallation part, you can use the DeploymentType parameter which is not mandatory.

powershell.exe -executionpolicy bypass -file deployapplication.ps1 -DeploymentType Uninstall

Copy

The parameters are different with each and every script, but PSADT uses the DeploymentType parameter to know which part of the script you wish to execute. If you want to use the install part you can either remove the parameter or use the following:

powershell.exe -executionpolicy bypass -file deployapplication.ps1 -DeploymentType Install

Copy

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1918666/19272" target="_top" id="1918666">
  <img src="//a.impactradius-go.com/display-ad/19272-1918666" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1918666/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### VBScript Command Lines

When it comes to running VBScripts, you have two different script hosts available in the OS:

* Wscript
* Cscript

Wscript is a built-in Windows scripting host that allows you to run VBScript (Visual Basic Scripting Edition) and JScript (JavaScript) scripts on Windows. It interprets and executes these scripts, provides access to various system objects, and facilitates interactions with the Windows operating system.

Cscript is a Windows command-line scripting host that is used to run VBScript (Visual Basic Scripting Edition) and JScript (JavaScript) scripts. It is an alternative to the graphical scripting host, Wscript, and is typically used when scripts must be run from the command line or when a graphical user interface is not available or desired.

The primary distinction between Wscript and Cscript is how VBScript or JScript code is executed. Comparing the two we have the following:

Wscript:

* On Windows operating systems, Wscript (Windows Script Host) is the default scripting host for VBScript and JScript.
* Wscript is used by default when a script file is double-clicked or executed from the command prompt without explicitly specifying the scripting host.
* Wscript includes a graphical user interface (GUI) environment for displaying script dialogs and message boxes to the user.
* It is commonly used for interactive scripting as well as user-oriented script execution.

Cscript:

* On Windows operating systems, Cscript (Console Script Host) is a command-line scripting host for VBScript and JScript.
* Because it operates within the command prompt or batch files, it is intended for non-interactive scripting and batch processing.
* Cscript lacks a graphical user interface and displays all output in the command prompt window.
* It is commonly used for background script execution, automation tasks, and script execution in command-line environments.

To summarize, Wscript is used when running scripts with a graphical user interface, displaying message boxes, or interacting with users, whereas Cscript is used for command-line execution and non-interactive script processing. The choice between Wscript and Cscript is determined by the script's specific requirements and the desired execution environment.

In general, most VBScripts should be Wscript and Cscript compatible and can be run on either scripting host. However, in some cases, a VBScript may fail to run as expected when using Cscript. Among the most common reasons are:

* Graphical User Interface (GUI) interactions: Because Cscript operates in a command-line environment without a GUI, VBScripts that rely on graphical elements such as message boxes, dialog boxes, or user input prompts may not work properly. These scripts are more appropriate for Wscript.
* Wscript-specific methods: VBScripts that use Wscript-specific methods or properties, such as Wscript.Echo or Wscript.Sleep, may not work properly with Cscript. These methods are intended to be used in conjunction with the Wscript scripting host.
* External dependencies: When a VBScript is executed with Cscript, it may encounter errors or unexpected behavior if it relies on external dependencies that are not available or accessible in the command-line environment.
* Script-specific requirements: Certain VBScripts may have requirements or dependencies that are incompatible with Cscript. Scripts that use COM components or ActiveX controls, for example, may need additional configuration or permissions to run with Cscript.

In general the preferred execution method with VBScript is to use the wscript. However, let’s have a look at how to run scripts in both ways.

For wscript:

Wscript.exe Install.vbs

Copy

For cscript:

Cscript.exe Install.vbs

Copy

VBScript, like PowerShell, supports the use of parameters. Parameters are used in VBScript to pass values to a subroutine or function when it is called. Parameters enable you to modify the behavior of a subroutine or function based on the values supplied at runtime.

You can use the WScript.Arguments collection to access the values passed from the command line when adding parameters to a VBScript. Here's how you can change a VBScript to accept and use parameters:

' Get the number of parameters passed
numArgs = WScript.Arguments.Count
' Check if any parameters were passed
If numArgs > 0 Then
    ' Access the parameters using the WScript.Arguments collection
    ' Parameters are zero-based, so the first parameter is at index 0
    param1 = WScript.Arguments(0)
    ' Check if additional parameters were passed
    If numArgs > 1 Then
        param2 = WScript.Arguments(1)
    End If
Else
    ' Display a message if no parameters were passed
    WScript.Echo "No parameters were passed."
End If

Copy

To run a VBScript with parameters from the command line, you can run this command:

Wscript.exe MyScript.vbs param1 param2

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
<li><a href="https://youtube-tips.techidaily.com/ed-the-ultimate-checklist-for-protecting-your-digital-assets/"><u>[Updated] The Ultimate Checklist for Protecting Your Digital Assets</u></a></li>
<li><a href="https://fox-info.techidaily.com/2024-approved-find-your-dream-free-vfx-alternative-top-30-sites-explored-deeply/"><u>2024 Approved Find Your Dream Free VFX Alternative - Top 30 Sites Explored Deeply</u></a></li>
<li><a href="https://win-updates.techidaily.com/best-tools-for-windows-users-to-save-and-edit-system-sounds/"><u>Best Tools for Windows Users to Save and Edit System Sounds</u></a></li>
<li><a href="https://article-knowledge.techidaily.com/bring-life-to-graphics-adobe-blur-masterclass-for-2024/"><u>Bring Life to Graphics Adobe Blur Masterclass for 2024</u></a></li>
<li><a href="https://win-updates.techidaily.com/complete-guide-how-to-eliminate-and-prevent-pop-up-ads-in-firefox-top-4-methods/"><u>Complete Guide: How to Eliminate and Prevent Pop-Up Ads in Firefox - Top 4 Methods</u></a></li>
<li><a href="https://win-updates.techidaily.com/comprehensive-overview-understanding-the-avi-video-file-format/"><u>Comprehensive Overview: Understanding the AVI Video File Format</u></a></li>
<li><a href="https://games-able.techidaily.com/exclusive-list-of-best-pads-for-gamers/"><u>Exclusive List of Best Pads for Gamers</u></a></li>
<li><a href="https://win-updates.techidaily.com/identifying-and-removing-spyware-from-your-android-device-a-comprehensive-guide/"><u>Identifying and Removing Spyware From Your Android Device: A Comprehensive Guide</u></a></li>
<li><a href="https://win-updates.techidaily.com/master-the-art-of-video-editing-seamlessly-convert-avi-videos-into-space-saving-crisp-h264-format-using-our-advanced-encoder/"><u>Master the Art of Video Editing: Seamlessly Convert AVI Videos Into Space-Saving, Crisp H.264 Format Using Our Advanced Encoder</u></a></li>
<li><a href="https://program-issues.techidaily.com/mastering-end-of-cycle-error-prevention-proven-techniques-to-fix-last-epoch-crashes-in-modern-computers/"><u>Mastering End of Cycle Error Prevention - Proven Techniques to Fix Last Epoch Crashes in Modern Computers</u></a></li>
<li><a href="https://data-safeguard.techidaily.com/revolutionize-data-capture-using-advanced-cookiebot-tools/"><u>Revolutionize Data Capture Using Advanced Cookiebot Tools</u></a></li>
<li><a href="https://techno-recovery.techidaily.com/the-ultimate-guide-effective-techniques-for-wiping-down-screens-safely/"><u>The Ultimate Guide: Effective Techniques for Wiping Down Screens Safely</u></a></li>
</ul></div>

