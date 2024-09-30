---
title: "Step-by-Step Guide: Proper Management of End-User Details Using Windows Setup Software"
date: 2024-09-29T03:28:48.161Z
updated: 2024-09-29T19:09:48.250Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: "This Article Describes Step-by-Step Guide: Proper Management of End-User Details Using Windows Setup Software"
thumbnail: https://thmb.techidaily.com/17e5357e78d53548c97f4d85021e25770f5faa06fc039457c29951eca12e67ea.jpg
---

## Step-by-Step Guide: Proper Management of End-User Details Using Windows Setup Software

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Best practices for user data

Because of the way MSI packages are cached in the OS once they are installed, the above solution may not be the best suited to cover all cases when it comes to user data in the form of files.

If you've ever looked through your Windows system directory, you might have noticed a folder called "Installer" in the C:Windows directory. This folder, which is frequently overlooked, plays an important role in Windows Installer technology by storing cached copies of MSI files.

The cached MSI files in the C:\\Windows\\Installer folder serve several important purposes:

* Repair and Maintenance: When an installed application has problems or becomes corrupted, Windows Installer uses the cached MSI files to repair it. This ensures the application's proper operation by restoring missing or damaged files.
* Uninstallation: The cached MSI files are used to completely remove the application from the system during the uninstallation process. To reverse the installation and remove all associated components, Windows Installer accesses the original installation package stored in the Installer folder.
* Patching: When updating or patching an installed application, Windows Installer uses the cached MSI files to identify the installed version and apply the necessary changes. Patch files, which are used for incremental updates to installed applications, are also stored in the Installer folder.

However, an MSI is not fully cached into the C:\\Windows\\Installer directory; instead, the files are removed during the caching process to save hard drive space.

If we use the above solution and delete the MSI from where it was originally installed, this operation will fail and the user will not have the VLC Media Player preferences copied in his profile when he opens the shortcut and the self-healing mechanism starts.

![vc_runtimeMinimum_x64 is missing](https://cdn.advancedinstaller.com/img/best-practices-for-user-data/vc_runtimeMinimum_x64-is-missing.png "vc_runtimeMinimum_x64 is missing")  

If the user data files are not correctly implemented, the only way for the self-healing mechanism to work is to browse to the MSI, which means copying it again on the computer.

There are several approaches we can take in this situation, but the following two will usually suffice:

* Move the files to a per-machine location and copy them to the user profile using a custom action, keep the advertised shortcuts enabled, and add a dummy registry key to HKEY CURRENT USER.
* Move the files on a per-machine location and copy them in the user profile by using a custom action, turn off the advertised shortcuts, insert the Active Setup mechanism

Both methods rely on a per-machine location for the user files and a script that copies them. Let's look at each scenario and see how we can configure it.

### Scenario one - Advertised shortcuts

We already have the advertised shortcut option on all of the shortcuts, so we'll keep it that way. Let's start with the simple part of this implementation: add a random HKEY CURRENT USER registry key if it isn't already present in the package. In our case, VLC contains the following user registry keys:

![ai vlc hkcu](https://cdn.advancedinstaller.com/img/best-practices-for-user-data/ai-vlc-hkcu.png "ai vlc hkcu")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2123736/7443" target="_top" id="2123736">
  <img src="//a.impactradius-go.com/display-ad/7443-2123736" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2123736/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

We need user registry keys so that the self-healing mechanism detects their absence when a user launches the shortcuts and initiates the actions. When the self-healing mechanism kicks in, it also considers the custom actions in the sequence.

The user data files are then moved to a per-machine location. To do so, go to the Files and Folders page and create a new folder called UserData under the Application Folder, then drag the previously created vlc folder under the Application Data and drop it under the newly created UserData. At the end, it should look like this:

![ai vlc user data per machine](https://cdn.advancedinstaller.com/img/best-practices-for-user-data/ai-vlc-user-data-per-machine.png "ai vlc user data per machine")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2135363/19272" target="_top" id="2135363">
  <img src="//a.impactradius-go.com/display-ad/19272-2135363" border="0" alt="https://techidaily.com" width="120" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2135363/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

We can now be certain that the files that must be copied on each user profile are always present on a per-machine basis, and that the files will be available even if the MSI is deleted. The final step is to create a custom action that copies the files from the UserData folder to the %appdata% folder.

As usual, we can do this either with VBScript or PowerShell. The code for the VBScript:

Dim objFSO, objShell
Set objFSO = CreateObject("Scripting.FileSystemObject")
Set objShell = CreateObject("WScript.Shell")
Dim sourceFolder, destinationFolder, programFilesPath, appDataPath
programFilesPath = objShell.SpecialFolders("ProgramW6432")
appDataPath = objShell.SpecialFolders("APPDATA")
sourceFolder = programFilesPath & "\VideoLAN\VLC\UserData"
destinationFolder = appDataPath & "\VLC"
    ' Copy the folder and its contents
    objFSO.CopyFolder sourceFolder, destinationFolder, True
Set objFSO = Nothing

Copy

The following actions are carried out by the code snippet:

* Creates objects for the FileSystemObject and WScript.Shell to access file system operations and special folder locations.
* Retrieves the paths for the Program Files folder (ProgramW6432) and the AppData folder (APPDATA) using the SpecialFolders property of the WScript.Shell object.
* Constructs the source folder path by appending the desired subfolder path (in this case, "\\VideoLAN\\VLC\\UserData") to the Program Files path.
* Constructs the destination folder path by appending the desired subfolder path (in this case, "\\VLC") to the AppData path.
* Uses the CopyFolder method of the FileSystemObject to copy the entire contents of the source folder to the destination folder. The third parameter (True) indicates that the operation should overwrite existing files if necessary.
* Releases the resources by setting the FileSystemObject to Nothing.

Then, launch Advanced Installer and go to the Custom Actions Page. Look for the Launch attached file and select the VBScript's location. Then, as shown below, configure the custom action to execute:

![ai vlc user data per machine vbscript](https://cdn.advancedinstaller.com/img/best-practices-for-user-data/ai-vlc-user-data-per-machine-vbscript.png "ai vlc user data per machine vbscript")  

The code for the PowerShell script:

$programfiles = $env:ProgramW6432
$appdata = $env:APPDATA
$sourcePath = $programfiles + "\VideoLAN\VLC\UserData"
$destinationPath = $appdata + "\VLC"
## Copy the folder and its contents recursively
Copy-Item -Path $sourcePath -Destination $destinationPath -Recurse -Force

Copy

The following actions are carried out by the code snippet:

* Retrieves the values of the Program Files directory and the AppData directory using environment variables ($env:ProgramW6432 and $env:APPDATA).
* Constructs the source folder path by appending the desired subfolder path ("\\VideoLAN\\VLC\\UserData") to the Program Files directory.
* Constructs the destination folder path by appending the desired subfolder path ("\\VLC") to the AppData directory.
* Uses the Copy-Item cmdlet in PowerShell to recursively copy the contents of the source folder to the destination folder. The -Recurse parameter ensures that all files and subdirectories are copied, and the -Force parameter overrides any restrictions that would prevent the copying operation.
* The files and directories from the source path are copied to the destination path.

Then, launch Advanced Installer and go to the Custom Actions Page. Search for the Run PowerShell script file and select the PowerShell script's location. Then, as shown below, configure the custom action to execute:

![ai vlc user data per machine powershell](https://cdn.advancedinstaller.com/img/best-practices-for-user-data/ai-vlc-user-data-per-machine-powershell.png "ai vlc user data per machine powershell")  

### Scenario two - Active Setup

The only difference between scenarios 1 and 2 is that in the active setup case, we disable the advertised shortcuts and do not require any other HKCU registry keys. After you've disabled the advertised shortcuts, go to the Product Details page and look for the Active Setup tab.

![ai vlc user data per machine active setup page](https://cdn.advancedinstaller.com/img/best-practices-for-user-data/ai-vlc-user-data-per-machine-active-setup-page.png "ai vlc user data per machine active setup page")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2068439/7443" target="_top" id="2068439">
  <img src="//a.impactradius-go.com/display-ad/7443-2068439" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2068439/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

In here, click on New and you can leave everything as default in the new window that appears.

![ai vlc user data per machine active setup config](https://cdn.advancedinstaller.com/img/best-practices-for-user-data/ai-vlc-user-data-per-machine-active-setup-config.png "ai vlc user data per machine active setup config")  

<!-- affiliate ads begin -->
<span id="1304647">
					<video width="240" height="200" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1304647.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/15852-1304647">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1304647.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:150px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fthefitville.pxf.io%2Fc%2F5597632%2F1304647%2F15852'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1304647/15852" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

We have discussed more in-depth about the [Active Setup mechanism in our first book](https://tools.techidaily.com/advancedinstaller/products/), but if we check what the above settings mean we end up with the following:

* ID: The ID which will appear in the Active Setup registry. This can be basically anything because the Active Setup mechanism will check if on the current logged in user the registry for Active Setup which is present under HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Active Setup is also present under HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Active Setup
* Display Name: The purpose of the "DisplayName" value is to provide a meaningful name or description for the Active Setup component so that users can understand its purpose or functionality. It helps users identify the component when they view it in registry editors or other software that displays registry information.
* Stub Path: By setting the "StubPath" value, software developers can define the action or task that should be executed when the Active Setup component runs. It allows them to perform various installation or configuration operations during user logon, ensuring that specific tasks are completed for each user. In our case we are triggering a repair of the installed MSI with /fou.
* Locale: The purpose of the "Locale" value is to define the language or regional settings that should be used when executing the Active Setup component. It allows software developers to provide localized versions of their installation or configuration tasks, ensuring that the appropriate language or regional settings are applied for each user.
* Is Installed: Software developers can use the "IsInstalled" registry key to check the installation status of their Active Setup component. During the Active Setup process, the component can set or update the "IsInstalled" value based on the successful completion of its installation or configuration tasks. This allows subsequent logons by the user to skip the installation process if the component is already installed.

So the active setup is doing exactly what we need, and that is to trigger a repair of the MSI when the user logs in again.

And that is it, in both cases after the application is installed we have ensured that even after the deletion of the MSI the users will still be able to receive the user data files in their profile. The difference between the two scenarios are the following:

* If we are using the advertised shortcuts route, every time a HKCU registry is missing the self-healing will start again. Also, the self-healing will start immediately after the user starts any shortcuts, meaning that after the application gets installed the user will also have the configuration once he starts the application
* If we are using the active setup route, this will only be executed once. Another downside of this method is that the user must log off/log on again in order for the Active Setup mechanism to start running and find the differences

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
<li><a href="https://fox-cloud.techidaily.com/new-2024-approved-the-ultimate-collection-best-zero-price-photo-editing-software/"><u>[New] 2024 Approved The Ultimate Collection Best Zero-Price Photo Editing Software</u></a></li>
<li><a href="https://instagram-clips.techidaily.com/new-shining-up-photos-on-instagram-three-effective-ways-for-2024/"><u>[New] Shining Up Photos on Instagram Three Effective Ways for 2024</u></a></li>
<li><a href="https://youtube-zero.techidaily.com/he-rising-tide-of-infographics-for-social-insights-for-2024/"><u>[New] The Rising Tide of Infographics for Social Insights for 2024</u></a></li>
<li><a href="https://screen-capture.techidaily.com/updated-frame-by-frame-findings-insightful-recorder-analysis-for-2024/"><u>[Updated] Frame by Frame Findings Insightful Recorder Analysis for 2024</u></a></li>
<li><a href="https://fox-glue.techidaily.com/updated-pc-hdr-optimization-made-simple-for-2024/"><u>[Updated] PC HDR Optimization Made Simple for 2024</u></a></li>
<li><a href="https://win-updates.techidaily.com/iuwlleeuuplusodhplusocpoodsplusocvplusodvoodroodvooctplusodpplusodsplusockueqhuinoplusobmeocizog44k544og44o844k644gn44kv44oq44ki44gq5yan55sf5pa55rovig/"><u>動画デインターレーションを理解する: スムーズでクリアな再生方法</u></a></li>
<li><a href="https://win-updates.techidaily.com/compatibility-issues-with-quicktime-files-heres-how-to-resolve-them-thoroughly/"><u>Compatibility Issues with QuickTime Files? Here's How to Resolve Them Thoroughly</u></a></li>
<li><a href="https://win-updates.techidaily.com/efficient-techniques-for-reducing-file-size-m4a-audio-compression-on-pcs-and-mac/"><u>Efficient Techniques for Reducing File Size: M4A Audio Compression on PCs & MAC</u></a></li>
<li><a href="https://tech-haven.techidaily.com/effortless-book-migration-converting-and-sharing-reading-materials-from-windowsmac-os-to-ios-devices/"><u>Effortless Book Migration: Converting and Sharing Reading Materials From Windows/Mac OS to iOS Devices</u></a></li>
<li><a href="https://win-updates.techidaily.com/effortless-conversion-techniques-for-turning-dem-demos-into-watchable-mp4-formats/"><u>Effortless Conversion Techniques for Turning DEM Demos Into Watchable MP4 Formats</u></a></li>
<li><a href="https://technical-tips.techidaily.com/effortless-pdf-modification-techniques-discover-3-simple-strategies/"><u>Effortless PDF Modification Techniques: Discover 3 Simple Strategies</u></a></li>
<li><a href="https://win-updates.techidaily.com/restore-your-tunes-troubleshooting-and-fixing-no-sound-problems-in-windows-media-player-for-windows-1110-users/"><u>Restore Your Tunes: Troubleshooting and Fixing No Sound Problems in Windows Media Player for WIndows 11/10 Users</u></a></li>
</ul></div>

