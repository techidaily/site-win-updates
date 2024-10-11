---
title: Steps for Creating and Removing Custom Action Handlers in DLLs or OCX Files
date: 2024-10-03T20:51:52.803Z
updated: 2024-10-10T21:14:51.165Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: This Article Describes Steps for Creating and Removing Custom Action Handlers in DLLs or OCX Files
thumbnail: https://thmb.techidaily.com/971161d0d4b1da3c5be518691bc7a9fd7e29d3fe831ffe5683f3df2b7e432663.jpg
---

## Steps for Creating and Removing Custom Action Handlers in DLLs or OCX Files

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## DLL/OCX register/unregister

Object Linking and Embedding (OLE) is a proprietary Microsoft technology that allows developers to embed and link to other objects. With OLE Control Extension (OCX), you can develop and use custom user interface elements. You can also achieve OLE controls via Dynamic-Link Library(.dll) files.

However, to make sure the data transfer between applications work , these OLE controls must be registered on the system. How can we do that? That's what we will show you in this article.

### What is the Regsvr32 tool?

Regsvr32 is a command-line utility that allows registering and unregistering OLE controls such as DLLs and ActiveX controls in the Windows Registry. Regsvr32 can be found in:

* For 64-bit version: %systemroot%\\System32\\regsvr32.exe
* For 32-bit version: %systemroot%\\SysWoW64\\regsvr32.exe

The syntax of the Regsvr32 is actually quite simple:

Regsvr32 \[/u\] \[/n\] \[/i\[:cmdline\]\] <dllname>

/u - Unregister control

/i - Call DllInstall passing it an optional \[cmdline\]; when it is used with /u, it calls dll uninstall

/n - do not call DllRegisterServer; this option must be used with /i

/s – Silent

/e - Suppress only the GUI success message but shows the GUI error message

![Note](https://cdn.advancedinstaller.com/svg/common/IconMessageNote.svg)Regsvr32 must always be used from an elevated command prompt.

<!-- affiliate ads begin -->
<a href="https://bluettius.sjv.io/c/5597632/2139111/17108" target="_top" id="2139111">
  <img src="//a.impactradius-go.com/display-ad/17108-2139111" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://bluettius.sjv.io/i/5597632/2139111/17108" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

For example, to register a DLL/OCX, you can use:

Regsvr32.exe PATHTODLL\name.DLL

Copy

To unregister a DLL/OCX, you can use:

Regsvr32.exe /U PATHTODLL\name.DLL

Copy

![Regsvr32 command-line utility](https://cdn.advancedinstaller.com/img/register-unregister-dll-ocx-files/regsvr32.png "Regsvr32 command-line utility")  

### How to Register DLL/OCX with VBscript?

Now that we know about the Regsvr32 utility, we can build the following scenario. Let's assume that we have a DLL in our project which will be installed in %systemroot%\\DLL. So, we can create the following registration script:

Option Explicit
On Error Resume Next
Dim strCmd,WshShell,strInstalldir
Set WshShell = CreateObject("WScript.Shell")
strSysRoot = WshShell.ExpandEnvironmentStrings("%SYSTEMROOT%")
strInstalldir = strSysRoot & "\DLL"
strCmd = "regsvr32.exe " & chr(34) & strInstalldir & "\libifcoremd.dll" & chr(34)& “ /s”
WshShell.Run strCmd

Copy

The script performs the following actions:

* Option Explicit: This statement enforces variable declaration in the script, ensuring that all variables are explicitly declared before they are used.
* On Error Resume Next: This statement allows the script to continue running even if an error occurs, bypassing the error and continuing with the next line of code.
* Dim strCmd, WshShell, strInstalldir: Declares three variables: strCmd to hold the command to be executed, WshShell to access the Windows Script Host Shell object, and strInstalldir to store the path to the DLL file.
* Set WshShell = CreateObject("WScript.Shell"): Creates an instance of the Windows Script Host Shell object, which allows the script to run shell commands and interact with the Windows environment.
* strSysRoot = WshShell.ExpandEnvironmentStrings("%SYSTEMROOT%"): Retrieves the value of the %SYSTEMROOT% environment variable using the ExpandEnvironmentStrings method of the WshShell object. The %SYSTEMROOT% variable represents the path to the Windows installation directory.
* strInstalldir = strSysRoot & "\\DLL": Constructs the path to the DLL file by appending the "\\DLL" folder to the strSysRoot variable. This assumes that the DLL file is located in the "DLL" folder within the Windows installation directory.
* strCmd = "regsvr32.exe " & chr(34) & strInstalldir & "\\libifcoremd.dll" & chr(34) & " /s": Constructs the command to be executed. It uses the regsvr32.exe utility to register a DLL file (libifcoremd.dll). The path to the DLL file is obtained by combining strInstalldir with the relative path \\libifcoremd.dll. The chr(34) is used to insert double quotes into the command string, and /s is a parameter to silently register the DLL without displaying any user interface.
* WshShell.Run strCmd: Executes the command stored in the strCmd variable using the Run method of the WshShell object. This runs the command in a separate process.

To unregister the DLL, we can use the following script:

Option Explicit
On Error Resume Next
Dim strCmd,WshShell,strInstalldir
Set WshShell = CreateObject("WScript.Shell")
strSysRoot = WshShell.ExpandEnvironmentStrings("%SYSTEMROOT%")
strInstalldir = strSysRoot & "\DLL"
strCmd = "regsvr32.exe /U " & chr(34) & strInstalldir & "\libifcoremd.dll" & chr(34)& “ /s”
WshShell.Run strCmd

Copy

* Now that the scripts are created, we need to open Advanced Installer and navigate to the Custom Actions page.
* There, search for the **Launch attached file** predefined custom action and add it into the sequence.
* Select your previously created registration script and configure the custom action as follows:

![register the DLL](https://cdn.advancedinstaller.com/img/register-unregister-dll-ocx-files/DLLRegisterVB.png "register the DLL")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2087253/19272" target="_top" id="2087253">
  <img src="//a.impactradius-go.com/display-ad/19272-2087253" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2087253/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

We also want to unregister the DLL during uninstallation, so let's create another custom action the same way as we did previously. Except this time, select the unregister script and configure the Custom Action as seen below:

![unregister the DLL during uninstallation](https://cdn.advancedinstaller.com/img/register-unregister-dll-ocx-files/DLLUnregisterVB.png "unregister the DLL during uninstallation")  

And that is it, all you need to do is **Build the MSI and install it.** The DLL will be registered.

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2068426/7443" target="_top" id="2068426">
  <img src="//a.impactradius-go.com/display-ad/7443-2068426" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2068426/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### How to Register DLL/OCX with PowerShell?

Using the same logic as above, we can construct the following script to register a DLL with PowerShell:

$Arguments = "C:\Windows\DLL\libifcoremd.dll", "/s"
Start-Process -FilePath 'regsvr32.exe' -Args $Arguments -Wait -NoNewWindow -PassThru

Copy

The script performs the following actions:

* $Arguments: Declares a variable to hold the arguments for the regsvr32.exe command and assigns the arguments to be passed to the regsvr32.exe command. The first argument is the path to the DLL file (C:\\Windows\\DLL\\libifcoremd.dll), and the second argument (/s) is a parameter to silently register the DLL without displaying any user interface.
* Start-Process -FilePath 'regsvr32.exe' -Args $Arguments -Wait -NoNewWindow -PassThru: Executes the regsvr32.exe command using the Start-Process cmdlet. The -FilePath parameter specifies the path to the executable (regsvr32.exe). The -Args parameter specifies the arguments to be passed to the executable, which are stored in the $Arguments variable. The -Wait parameter ensures that the script waits for the command to complete before continuing. The -NoNewWindow parameter prevents the command from opening a new window. The -PassThru parameter returns an object representing the newly created process, allowing for further interaction if needed.

To unregister the DLL, we can use the following script:

$Arguments = “/u”,"C:\Windows\DLL\libifcoremd.dll", "/s"
Start-Process -FilePath 'regsvr32.exe' -Args $Arguments -Wait -NoNewWindow -PassThru

Copy

* When the scripts are created, we navigate to the Custom Actions page.
* Search for the **Run PowerShell script file** predefined Custom Action and add it in the sequence.
* Once we select the registration PowerShell script, we can proceed to configure the Custom Actions as follows:

![DLL Register PowerShell script](https://cdn.advancedinstaller.com/img/register-unregister-dll-ocx-files/DLLRegisterPS.png "DLL Register PowerShell script")  

For the unregister action, we follow the same steps as above and configure the Custom Actions:

![DLL Unregister PowerShell script](https://cdn.advancedinstaller.com/img/register-unregister-dll-ocx-files/DLLUnregisterPS.png "DLL Unregister PowerShell script")  

And you're done, now you can Build the MSI and install it. The DLL will be registered.

<!-- affiliate ads begin -->
<a href="https://imp.i357552.net/c/5597632/1001453/11832" target="_top" id="1001453">
  <img src="//a.impactradius-go.com/display-ad/11832-1001453" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://imp.i357552.net/i/5597632/1001453/11832" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### How to Register DLL/OCX with Advanced Installer?

Advanced Installer makes it much easier to handle OLE control registration by providing a [Registration Tab GUI](https://tools.techidaily.com/advancedinstaller/products/). 

Accessing the GUI is quite easy with these steps:

1. First navigate to the [Files and Folders](https://tools.techidaily.com/advancedinstaller/products/) page
2. Add the DLL/OCX files.
3. Once the files are added, right-click on the DLL/OCX and select **Properties.**
4. Then, navigate to the Registration Tab.

![Register DLL/OCX with Advanced Installer](https://cdn.advancedinstaller.com/img/register-unregister-dll-ocx-files/DLLRegisterAI.png "Register DLL/OCX with Advanced Installer")  

As you may notice, there are three methods for registering files, two for native libraries and one for .NET assemblies.

\- Self-register native library

This file is marked for self-registration, however, the self-registration method for registering components has many drawbacks (like not being able to roll back the changes if something fails later in the install) and it is against Microsoft guidelines.

\- Extract registration info from the native library

All the necessary registry entries and keys are installed separately. You can see them in the [Registry](https://tools.techidaily.com/advancedinstaller/products/)and [COM](https://tools.techidaily.com/advancedinstaller/products/)pages. **This is the preferred way to register a file.**

\- Register .NET assembly for COM interoperability

It creates the required registry entries so that your assembly is operable through COM. You can see those registry entries in the Registry page.

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
<li><a href="https://fox-hovers.techidaily.com/new-chucklecraft-pixel-perfect-humor/"><u>[New] ChuckleCraft Pixel-Perfect Humor</u></a></li>
<li><a href="https://facebook-videos.techidaily.com/new-methods-for-a-no-ads-experience-on-social-platforms-for-2024/"><u>[New] Methods for a No-Ads Experience on Social Platforms for 2024</u></a></li>
<li><a href="https://win-updates.techidaily.com/custom-action-enabled-process-detection-and-termination-techniques/"><u>Custom Action-Enabled Process Detection & Termination Techniques</u></a></li>
<li><a href="https://mondly-stories.techidaily.com/get-fluent-in-swedish-script-and-sounds-speedily/"><u>Get Fluent in Swedish Script & Sounds Speedily</u></a></li>
<li><a href="https://screen-mirror.techidaily.com/how-nubia-z50-ultra-mirror-screen-to-pc-drfone-by-drfone-android/"><u>How Nubia Z50 Ultra Mirror Screen to PC? | Dr.fone</u></a></li>
<li><a href="https://win-updates.techidaily.com/how-protected-are-your-files-on-windows-10-expert-advice-from-malwarefox/"><u>How Protected Are Your Files on Windows 10? Expert Advice From MalwareFox</u></a></li>
<li><a href="https://win-solutions.techidaily.com/master-the-solution-a-detailed-guide-to-prevent-fifa-21-game-crashes-on-pc/"><u>Master the Solution: A Detailed Guide to Prevent FIFA 21 Game Crashes on PC</u></a></li>
<li><a href="https://win-updates.techidaily.com/simple-steps-to-unlock-your-iphone-6-a-beginners-manual/"><u>Simple Steps to Unlock Your iPhone 6: A Beginner's Manual</u></a></li>
<li><a href="https://win-updates.techidaily.com/step-by-step-guide-transferring-your-redmi-smartphone-data-to-your-computer/"><u>Step-by-Step Guide: Transferring Your Redmi Smartphone Data to Your Computer</u></a></li>
<li><a href="https://win-updates.techidaily.com/ultimate-guide-to-capturing-screenshots-on-your-alcatel-one-touch-device/"><u>Ultimate Guide to Capturing Screenshots on Your Alcatel One Touch Device</u></a></li>
<li><a href="https://audio-editing.techidaily.com/updated-in-2024-comparing-titans-in-digital-audio-workstations-is-magix-samplitude-at-the-pinnacle/"><u>Updated In 2024, Comparing Titans in Digital Audio Workstations Is MAGIX Samplitude at the Pinnacle?</u></a></li>
</ul></div>

