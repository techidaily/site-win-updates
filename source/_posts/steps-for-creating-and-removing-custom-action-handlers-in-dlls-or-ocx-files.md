---
title: Steps for Creating and Removing Custom Action Handlers in DLLs or OCX Files
date: 2024-09-26T17:19:14.538Z
updated: 2024-09-30T00:14:03.450Z
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

For example, to register a DLL/OCX, you can use:

Regsvr32.exe PATHTODLL\name.DLL

Copy

To unregister a DLL/OCX, you can use:

Regsvr32.exe /U PATHTODLL\name.DLL

Copy

![Regsvr32 command-line utility](https://cdn.advancedinstaller.com/img/register-unregister-dll-ocx-files/regsvr32.png "Regsvr32 command-line utility")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2080312/19272" target="_top" id="2080312">
  <img src="//a.impactradius-go.com/display-ad/19272-2080312" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2080312/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2144276/7443" target="_top" id="2144276">
  <img src="//a.impactradius-go.com/display-ad/7443-2144276" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2144276/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

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

We also want to unregister the DLL during uninstallation, so let's create another custom action the same way as we did previously. Except this time, select the unregister script and configure the Custom Action as seen below:

![unregister the DLL during uninstallation](https://cdn.advancedinstaller.com/img/register-unregister-dll-ocx-files/DLLUnregisterVB.png "unregister the DLL during uninstallation")  

And that is it, all you need to do is **Build the MSI and install it.** The DLL will be registered.

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

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2135349/19272" target="_top" id="2135349">
  <img src="//a.impactradius-go.com/display-ad/19272-2135349" border="0" alt="https://techidaily.com" width="120" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2135349/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

For the unregister action, we follow the same steps as above and configure the Custom Actions:

![DLL Unregister PowerShell script](https://cdn.advancedinstaller.com/img/register-unregister-dll-ocx-files/DLLUnregisterPS.png "DLL Unregister PowerShell script")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2135359/19272" target="_top" id="2135359">
  <img src="//a.impactradius-go.com/display-ad/19272-2135359" border="0" alt="https://techidaily.com" width="392" height="72"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2135359/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

And you're done, now you can Build the MSI and install it. The DLL will be registered.

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
<li><a href="https://fox-helps.techidaily.com/new-2024-approved-turning-onoff-picture-in-picture-for-maciosipad/"><u>[New] 2024 Approved Turning On/Off Picture-in-Picture for Mac/iOS/iPad</u></a></li>
<li><a href="https://facebook-videos.techidaily.com/updated-keeping-your-browsing-free-of-pop-up-videos-for-2024/"><u>[Updated] Keeping Your Browsing Free of Pop-Up Videos for 2024</u></a></li>
<li><a href="https://fox-hovers.techidaily.com/2024-approved-melodies-of-the-night-king-recommended-sites-for-tts-downloads/"><u>2024 Approved Melodies of the Night King Recommended Sites for TTS Downloads</u></a></li>
<li><a href="https://win-updates.techidaily.com/iuwlleeuuplusodhplusocpoodsplusocvplusodvoodroodvooctplusodpplusodsplusockueqhuinoplusobmeocizog44k544og44o844k644gn44kv44oq44ki44gq5yan55sf5pa55rovig/"><u>動画デインターレーションを理解する: スムーズでクリアな再生方法</u></a></li>
<li><a href="https://win11-tips.techidaily.com/easing-overuse-signal-fixing-chatgpt-on-windowed-systems/"><u>Easing Overuse Signal: Fixing ChatGPT on Windowed Systems</u></a></li>
<li><a href="https://win-updates.techidaily.com/efficient-techniques-for-reducing-file-size-m4a-audio-compression-on-pcs-and-mac/"><u>Efficient Techniques for Reducing File Size: M4A Audio Compression on PCs & MAC</u></a></li>
<li><a href="https://win-updates.techidaily.com/effortless-conversion-techniques-for-turning-dem-demos-into-watchable-mp4-formats/"><u>Effortless Conversion Techniques for Turning DEM Demos Into Watchable MP4 Formats</u></a></li>
<li><a href="https://win-updates.techidaily.com/elite-power-user-secrets-unveil-top-11-undiscovered-gesture-shortcuts-on-your-trackpad/"><u>Elite Power User Secrets: Unveil Top 11 Undiscovered Gesture Shortcuts on Your Trackpad</u></a></li>
<li><a href="https://screen-sharing-recording.techidaily.com/file-sharing-solutions-beyond-sharex/"><u>File Sharing Solutions Beyond ShareX</u></a></li>
<li><a href="https://facebook-videos.techidaily.com/in-2024-boosting-daily-use-tips-to-stay-active-on-facebook/"><u>In 2024, Boosting Daily Use Tips to Stay Active on Facebook</u></a></li>
<li><a href="https://technical-tips.techidaily.com/inside-look-at-samsung-unpacked-2025-all-upcoming-devices-rumors-and-breakthrough-tech-news-covered/"><u>Inside Look at Samsung Unpacked 2025 - All Upcoming Devices, Rumors, and Breakthrough Tech News Covered</u></a></li>
<li><a href="https://win-updates.techidaily.com/mastering-dns-configuration-a-step-by-step-guide-for-changing-ip-addresses-in-windows-os/"><u>Mastering DNS Configuration: A Step-by-Step Guide for Changing IP Addresses in Windows OS</u></a></li>
<li><a href="https://fox-direct.techidaily.com/pazera-free-audio-extractor-review-2024/"><u>Pazera Free Audio Extractor Review 2024</u></a></li>
<li><a href="https://win-updates.techidaily.com/restore-your-tunes-troubleshooting-and-fixing-no-sound-problems-in-windows-media-player-for-windows-1110-users/"><u>Restore Your Tunes: Troubleshooting and Fixing No Sound Problems in Windows Media Player for WIndows 11/10 Users</u></a></li>
<li><a href="https://win-updates.techidaily.com/top-flac-file-reader-apps-for-windows-10-users/"><u>Top FLAC File Reader Apps for Windows 10 Users</u></a></li>
<li><a href="https://win-answers.techidaily.com/troubleshooting-steps-fixing-hyper-scape-pc-game-crashes/"><u>Troubleshooting Steps: Fixing Hyper Scape PC Game Crashes</u></a></li>
<li><a href="https://win-updates.techidaily.com/wavmp43/"><u>WAVからMP4へ変換するための3つの最新方法とアプリケーションをご紹介</u></a></li>
</ul></div>

