---
title: Clean Up Directory Clutter via PowerShell Commands and Tailored Solutions
date: 2024-10-03T22:08:38.899Z
updated: 2024-10-10T17:52:28.389Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: This Article Describes Clean Up Directory Clutter via PowerShell Commands and Tailored Solutions
thumbnail: https://thmb.techidaily.com/5cbb31b0aa89284f511ea895d4dc406591717af976dec90561d5751a6efa2298.jpg
---

## Clean Up Directory Clutter via PowerShell Commands and Tailored Solutions

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Delete empty directory

Technically, during the uninstallation process, based on what directories are defined in the Directory table, the MSI usually handles the deletion of all directories and assures a clean machine. However, the rules of erasing directories are:

* The directory must be empty
* The directory must appear in the Directory table

Looking at the requirements, it might be the case that the application creates another directory that isn’t present in the Directory table, and when the MSI is uninstalled, the directories will remain behind.

As discussed in our first book, you have the RemoveFile table. To ensure that a directory is deleted during MSI uninstallation, you need to modify the RemoveFile table in the MSI. Here's how you can achieve this:

* Open the MSI file using a compatible MSI editing tool like Orca, Wise Package Studio, or Advanced Installer.
* Locate and open the RemoveFile table within the MSI editing tool. This table specifies files and directories to be removed during uninstallation.
* Identify the directory you want to delete during uninstallation.
* Add a new row to the RemoveFile table with the following information: **Component**: Enter the component identifier for the component that contains the directory, **FileName**: Specify the name of the directory (not the full path), **DirProperty**: Enter the directory property associated with the directory.
* Save the modified MSI file.

By adding an entry in the RemoveFile table, you instruct the Windows Installer to remove the specified directory during the uninstallation process. The Windows Installer engine will automatically remove the directory if it exists and is empty. If the directory is not empty, the uninstallation will fail unless you have custom actions or scripts in place to handle the removal of files within the directory.

<!-- affiliate ads begin -->
<span id="1983575">
					<video width="576" height="240" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1983575.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/22993-1983575">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1983575.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:360px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Fhomestyler.sjv.io%2Fc%2F5597632%2F1983575%2F22993'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1983575/22993" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Delete empty directories with Custom Actions

**Delete with VBScript**

When it comes to removing emty directories you can go in two ways with VBScript:

* Use the navite functions VBScript provides
* Use the [RD utility](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/rd "RD utility") inside the OS

When it comes to native VBScript functions, we can use the following script:

Dim objFSO, objFolder
Dim folderPath
folderPath = "C:\Path\to\folder"
Set objFSO = CreateObject("Scripting.FileSystemObject")
' Check if the folder exists
If objFSO.FolderExists(folderPath) Then
    Set objFolder = objFSO.GetFolder(folderPath)
    ' Check if the folder is empty
    If objFolder.Files.Count = 0 And objFolder.SubFolders.Count = 0 Then
        ' Delete the empty folder
        objFolder.Delete
        WScript.Echo "Folder deleted successfully."
    Else
        WScript.Echo "Folder is not empty."
    End If
Else
    WScript.Echo "Folder does not exist."
End If
Set objFolder = Nothing
Set objFSO = Nothing

Copy

Replace "C:Pathtofolder" with the actual path to the folder you want to inspect. This script checks the folder's existence, counts the files and subfolders within it, and deletes the folder if it is empty. Let's look at how the script works:

* The script begins by declaring variables: objFSO, objFolder, and folderPath.
* folderPath is set to the path of the folder you want to check for emptiness and delete if empty.
* CreateObject("Scripting.FileSystemObject") creates an instance of the FileSystemObject to work with file system objects.
* objFSO.FolderExists(folderPath) checks if the folder specified by folderPath exists.
* If the folder exists, objFolder is set to represent the folder using objFSO.GetFolder(folderPath).
* The script then checks if the folder is empty by verifying that both objFolder.Files.Count (number of files) and objFolder.SubFolders.Count (number of subfolders) are zero.
* If the folder is empty, objFolder.Delete is called to delete the folder.
* If the folder is not empty or if it doesn't exist, appropriate messages are echoed using WScript.Echo.
* Finally, the script releases the object references by setting objFolder and objFSO to Nothing.

If we want to use the RD utility together with VBScript, the following code can be used:

Dim objShell
Dim folderPath
folderPath = "C:\Path\to\folder"
Set objShell = CreateObject("WScript.Shell")
' Check if the folder exists
If objShell.FileSystemObject.FolderExists(folderPath) Then
    ' Execute the rd command to delete the folder
    objShell.Run "cmd /c rd /s /q """ & folderPath & """", 0, True
    WScript.Echo "Folder deleted successfully."
Else
    WScript.Echo "Folder does not exist."
End If
Set objShell = Nothing

Copy

Here's how the script works:

* The script begins by declaring variables: objShell and folderPath.
* folderPath is set to the path of the folder you want to delete.
* CreateObject("WScript.Shell") creates an instance of the WScript.Shell object, which allows us to execute shell commands.
* The script checks if the folder specified by folderPath exists using objShell.FileSystemObject.FolderExists.
* If the folder exists, objShell.Run is used to execute the rd command with the appropriate arguments (/s to delete all files and subdirectories, and /q to perform the deletion silently without prompts).
* The folder is enclosed in double quotes to handle any spaces or special characters in the folder path.
* The third argument of objShell.Run is set to True, which specifies that the script should wait for the command to complete before continuing.
* After the folder is deleted, a success message is echoed using WScript.Echo.
* If the folder does not exist, an appropriate message is echoed.
* Finally, the script releases the object reference by setting objShell to Nothing.

### Delete with PowerShell

For PowerShell, we can use the following script:

$folderPath = "C:\Path\to\folder"

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2130870/7443" target="_top" id="2130870">
  <img src="//a.impactradius-go.com/display-ad/7443-2130870" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2130870/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

## Check if the folder exists
if (Test-Path $folderPath) {
# Check if the folder is empty
    if ((Get-ChildItem $folderPath | Measure-Object).Count -eq 0) {
# Delete the folder
        Remove-Item $folderPath -Force -Recurse
        Write-Host "Folder deleted successfully."
    } else {
        Write-Host "Folder is not empty."

} else {
    Write-Host "Folder does not exist."

Copy

Replace "C:\\Path\\to\\folder" with the actual path of the folder you want to check. Here's how the script works:

* The script begins by setting the variable $folderPath to the path of the folder you want to delete.
* The script uses the Test-Path cmdlet to check if the folder specified by $folderPath exists.
* If the folder exists, the script uses the Get-ChildItem cmdlet to get all items (files and subfolders) within the folder.
* The Measure-Object cmdlet is used to count the number of items. If the count is equal to zero, it means the folder is empty.
* If the folder is empty, the script uses the Remove-Item cmdlet to delete the folder.
* The -Force parameter is used to force the deletion without prompting for confirmation.
* The -Recurse parameter is used to delete the folder and its contents recursively.
* After deleting the folder, the script writes a success message using Write-Host.
* If the folder is not empty, the script writes a message indicating that the folder is not empty.
* If the folder does not exist, the script writes a message indicating that the folder does not exist.

### Delete empty directories with Advanced Installer

Advanced Installer offers a much simpler method to remove folders generated by the application. If you navigate to the Files and Folders page and right-click on a desired folder, you will see the Uninstall Cleanup option:

![ai files folders uninstall cleanup](https://cdn.advancedinstaller.com/img/delete-empty-directory-with-custom-actions/ai-files-folders-uninstall-cleanup.png "ai files folders uninstall cleanup")  

The uninstall cleanup wizard launches, allowing you to specify which files and folders created by your application will be removed when you uninstall it. To launch this wizard, select the parent folder, the directory from which you want to delete files and folders, and then choose "Uninstall Cleanup..." from the context menu. Following the wizard's launch, simply follow the on-screen instructions to select the files you want to delete.

![ai uninstall cleanup step1](https://cdn.advancedinstaller.com/img/delete-empty-directory-with-custom-actions/ai-uninstall-cleanup-step1.png "ai uninstall cleanup step1")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/1062447/7443" target="_top" id="1062447">
  <img src="//a.impactradius-go.com/display-ad/7443-1062447" border="0" alt="https://techidaily.com" width="600" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/1062447/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

As you can see, you can delete the desired folder and all of its subfolders, or just the contents of the folder, including non-empty directories.

![ai uninstall cleanup step2](https://cdn.advancedinstaller.com/img/delete-empty-directory-with-custom-actions/ai-uninstall-cleanup-step2.png "ai uninstall cleanup step2")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2087253/19272" target="_top" id="2087253">
  <img src="//a.impactradius-go.com/display-ad/19272-2087253" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2087253/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

Furthermore, Advanced Installer allows you to ask the user if the specified folders should be deleted when the cleanup is performed, or you can perform the cleanup silently.

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
<li><a href="https://fox-boxes.techidaily.com/new-lifetime-of-memories-elevated-in-the-cloud-free-and-paid-storage-compared-for-2024/"><u>[New] Lifetime of Memories, Elevated in the Cloud Free & Paid Storage Compared for 2024</u></a></li>
<li><a href="https://win-updates.techidaily.com/1-ultimate-guide-top-4-proven-methods-for-easy-photo-stamp-elimination/"><u>1. Ultimate Guide: Top 4 Proven Methods for Easy Photo Stamp Elimination</u></a></li>
<li><a href="https://remote-screen-capture.techidaily.com/2024-approved-smooth-streams-from-obs-to-insta/"><u>2024 Approved Smooth Streams From OBS to Insta</u></a></li>
<li><a href="https://win-updates.techidaily.com/comprehensive-guide-mastering-the-art-of-recording-audio-chats/"><u>Comprehensive Guide: Mastering the Art of Recording Audio Chats</u></a></li>
<li><a href="https://unlock-android.techidaily.com/in-2024-unlock-your-zte-axon-40-lites-potential-the-top-20-lock-screen-apps-you-need-to-try-by-drfone-android/"><u>In 2024, Unlock Your ZTE Axon 40 Lites Potential The Top 20 Lock Screen Apps You Need to Try</u></a></li>
<li><a href="https://win-updates.techidaily.com/practical-strategies-for-streamlining-mp4-files-via-online-tools/"><u>Practical Strategies for Streamlining MP4 Files via Online Tools</u></a></li>
<li><a href="https://win-updates.techidaily.com/step-by-step-guide-activating-usb-debug-for-android-using-the-apowersoft-phone-manager-tool/"><u>Step-by-Step Guide: Activating USB Debug for Android Using the Apowersoft Phone Manager Tool</u></a></li>
<li><a href="https://win-updates.techidaily.com/step-by-step-strategy-for-detecting-deleting-and-defending-your-phone-from-android-ransomware-threats/"><u>Step-by-Step Strategy for Detecting, Deleting, and Defending Your Phone From Android Ransomware Threats</u></a></li>
<li><a href="https://facebook-video-footage.techidaily.com/transforming-spontaneitous-tunes-into-structured-youtube-playlists-for-2024/"><u>Transforming Spontaneitous Tunes Into Structured YouTube Playlists for 2024</u></a></li>
<li><a href="https://howto.techidaily.com/troubleshooting-guide-how-to-fix-an-unresponsive-itel-p40plus-screen-drfone-by-drfone-fix-android-problems-fix-android-problems/"><u>Troubleshooting Guide How to Fix an Unresponsive Itel P40+ Screen | Dr.fone</u></a></li>
<li><a href="https://win11.techidaily.com/upgrading-windows-11-the-top-10-best-replacements/"><u>Upgrading Windows 11: The Top 10 Best Replacements</u></a></li>
</ul></div>

