---
title: "Mastering Conditionals: A Guide to Implementing In MSI Package Deployments"
date: 2024-10-03T18:50:12.311Z
updated: 2024-10-05T17:24:43.230Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: "This Article Describes Mastering Conditionals: A Guide to Implementing In MSI Package Deployments"
thumbnail: https://thmb.techidaily.com/b65c1700fc3be6103fe73469bcdff9ebd5593034f3622d27aea03408c9719ceb.jpg
---

## Mastering Conditionals: A Guide to Implementing In MSI Package Deployments

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Working with Conditional Statements

Conditional statements give you greater control and flexibility when creating MSI packages. This allows you to build robust setups that can be tailored to suit various system configurations, making it easier for users to install as required.

Conditional statements in MSI packaging give you the control to decide when an action should be taken. This means that certain files or applications will only get installed if a certain set of conditions are met. As an example, you can specify that a file should only be installed if another file is already present on the system.

To use conditional statements in MSI packaging, you'll need to specify the condition in the appropriate section of the MSI package. For example, to conditionally install a file based on the presence of a specific registry key, you would add the following code to the component where the file is located:

<Component Id="MyComponent" Directory="INSTALLDIR"> <File Id="MyFile" Source="MyFile.txt"> <Condition><![CDATA[REGISTRY_VALUE_EXISTS("HKEY_LOCAL_MACHINE\Software\MyApp", "MyKey")]]></Condition> </File> </Component>

Copy

In this example, the file "MyFile.txt" will only be installed if the registry key "HKEY\_LOCAL\_MACHINE\\Software\\MyApp\\MyKey" exists on the system.

[Custom actions](https://tools.techidaily.com/advancedinstaller/products/) are yet another way to use conditional statements. Custom actions are scripts or programs that are executed during the installation process and can be used to perform tasks that the standard MSI package does not support.

For example, you can use a custom action to check for the presence of a specific file on the system, and use that information to conditionally install a file. To do this, you would create a custom action that checks for the presence of the file, and set a property that can be used as a condition in the appropriate section of the MSI package.

The last type of conditional statements that you could use with MSI are called [launch conditions](https://tools.techidaily.com/advancedinstaller/products/). Prior to initiating the installation process, launch conditions must be satisfied. This can include verifying that certain system requirements are met, for example, determining if specific hardware or software components are present. or the presence of certain registry keys. In other words, launch conditions are a type of conditional statement that are used to control the behavior of the installation process based on the system configuration. By using launch conditions, you can ensure that the installation package is installed only on systems that meet the specified requirements, reducing the potential for errors and improving the overall reliability of the installation process.

### Component Conditions

Advanced Installer makes it much easier to work with conditions while building MSI components. You can easily set conditions on files, registry keys and other elements to control their setup process. This streamlined interface really simplifies the entire MSI component creation process based on system configuration.

To add a condition to an MSI component in Advanced Installer, simply select the component and add the appropriate condition under **Component Properties**. There are numerous conditions to choose from, including system properties, registry keys, file and folder presence, and custom conditions.

![component conditions](https://cdn.advancedinstaller.com/img/conditional-statements-and-custom-actions/component-conditions.png "component conditions")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2087394/7443" target="_top" id="2087394">
  <img src="//a.impactradius-go.com/display-ad/7443-2087394" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2087394/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

To perform the same actions as explained earlier where the file is only installed if a certain registry key exists, we must do some steps:

1\. Search for the registry key and store this result into a property. We are going to use the default RESULT\_PROPERTY

To do this, navigate to the Search page and click on New Search. A wizard will appear that will guide you through the process.

![search new search wizzard](https://cdn.advancedinstaller.com/img/conditional-statements-and-custom-actions/search-new-search-wizzard.png "search new search wizzard")  

Next, select to Search for a registry value. As mentioned we will leave the search results in the RESULT\_PROPERTY.

![search new search wizzard registry key](https://cdn.advancedinstaller.com/img/conditional-statements-and-custom-actions/search-new-search-wizzard-registry-key.png "search new search wizzard registry key")  

Next, define the registry key value that we are searching for.

![search new search wizzard registry key input](https://cdn.advancedinstaller.com/img/conditional-statements-and-custom-actions/search-new-search-wizzard-registry-key-input.png "search new search wizzard registry key input")  

Select to retrieve the value and finish the wizard. After the wizard is completed check if your registry key is in the 64-bit portion of the registry and check the appropriate checkbox. You can also do a Test Search just to confirm that everything is in order.

![search new search wizzard registry key test](https://cdn.advancedinstaller.com/img/conditional-statements-and-custom-actions/search-new-search-wizzard-registry-key-test.png "search new search wizzard registry key test")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1915865/19272" target="_top" id="1915865">
  <img src="//a.impactradius-go.com/display-ad/19272-1915865" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1915865/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

2\. Use the above created Property to define the condition on the component where the file is located.

A property has two states:

* It has a value and therefore it exists
* It has no value and therefore it does not exist

Because we don’t care about what value the property outputs and we are only interested if it exists or not, defining the condition on the component where the file is located is quite simple. All we have to do is navigate to the Organization page and we set the condition for our HelloWorld.exe component to RESULT\_PROPERTY.

![component condition set property](https://cdn.advancedinstaller.com/img/conditional-statements-and-custom-actions/component-condition-set-property.png "component condition set property")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2080333/19272" target="_top" id="2080333">
  <img src="//a.impactradius-go.com/display-ad/19272-2080333" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2080333/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

During the install phase, the MSI will first perform the search function to see if the registry key exists and populate the property, afterwards it will parse through all the components which are marked to install. Once it reaches our component with the HelloWorld.exe file, it will first check if the condition is met, meaning if the property is present or not. If the property is present, it means the condition has been passed and the component is then installed on the machine.

### Launch Conditions

In Advanced Installer, configuring a launch condition is a straightforward process. You can create a launch condition to check for the presence of specific system requirements, such as the availability of a specific version of the .NET Framework, or the presence of specific registry keys or files on the system.

To configure a launch condition in Advanced Installer, you can simply navigate to the [Launch Conditions page](https://tools.techidaily.com/advancedinstaller/products/) and create a new launch condition. Advanced Installer offers by default multiple pre-configured types of launch conditions and we can separate them into:

* System
* Software

### System Launch Conditions

When it comes to system launch conditions, you can easily define on which Operating System your package will be supported, what minimum version of Windows Installer is needed, but also more in-depth checks such as minimum physical memory that the user needs to run the software, minimum screen resolution, minimum color quality and so on. For more details check [out this page](https://tools.techidaily.com/advancedinstaller/products/).

![system launch conditions ai](https://cdn.advancedinstaller.com/img/conditional-statements-and-custom-actions/system-launch-conditions-ai.png "system launch conditions ai")  

<!-- affiliate ads begin -->
<a href="https://wigfever.sjv.io/c/5597632/2005183/22899" target="_top" id="2005183">
  <img src="//a.impactradius-go.com/display-ad/22899-2005183" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://wigfever.sjv.io/i/5597632/2005183/22899" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Software Launch Conditions

Coming back to our scenario where you would need a certain version of .NET Framework installed on the machine, if we navigate to the[Software launch conditions tab](https://tools.techidaily.com/advancedinstaller/products/) we can see that Advanced Installer offers many predefined checks for some of the most popular software products out there such as:

* .NET Core
* .NET Framework
* Internet Explorer
* Internet Information Services (IIS)
* Adobe Reader
* Java Runtime Environment (JRE)
* Java Development Kit (JDK)
* DirectX
* Office applications
* XNA Framework
* SQL Server Express
* SQL Server Compact
* SQL Server ODBC Driver
* ActiveSync / WMDC
* VSTO Runtimes
* Office 2003 PIA
* Office 2007 PIA
* Office 2010 PIA
* Office Shared Interop Assembly
* Sharepoint Foundation
* PowerShell
* Windows PowerShell

In our case, all we need to do is check .NET Framework and select the desired version, for the scope of this example we went with .NET Framework version 4.7.2.

![software launch condition net framework](https://cdn.advancedinstaller.com/img/conditional-statements-and-custom-actions/software-launch-condition-net-framework.png "software launch condition net framework")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2135361/19272" target="_top" id="2135361">
  <img src="//a.impactradius-go.com/display-ad/19272-2135361" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2135361/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Custom Launch Conditions

In Advanced Installer, you can define [custom launch conditions](https://tools.techidaily.com/advancedinstaller/products/) by using installer properties or environment variables. These properties can be predefined or set by searches and custom actions.

To create a new launch condition, simply click on the "New" button, the "New" list context menu item, or press the Insert key while the list control is focused. The Edit Launch Condition Dialog will pop up, allowing you to specify a launch condition.

![custom launch condition adobe reader](https://cdn.advancedinstaller.com/img/conditional-statements-and-custom-actions/custom-launch-condition-adobe-reader.png "custom launch condition adobe reader")  

To modify a launch condition, use the "Edit" button, the "Edit" list context menu item, or press the Space key while an element from the list control is selected. The Edit Launch Condition Dialog will pop up, allowing you to edit the launch condition.

If you no longer need a launch condition, you can remove it using the "Remove" button, the "Remove" list context menu item, or by pressing the Delete key while an element from the list control is selected.

Defining custom launch conditions in Advanced Installer is a best practice that can help to ensure the reliability and efficiency of the installation process. By specifying the conditions that must be met before installation, you can reduce the potential for errors and ensure that the installation package is installed only on systems that meet the required specifications.

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1997675/19272" target="_top" id="1997675">
  <img src="//a.impactradius-go.com/display-ad/19272-1997675" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1997675/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Custom Actions as Conditional Statements

One of the key benefits of custom actions is their ability to act as conditional statements, enabling you to create complex installation packages that can adapt to different system configurations.

Custom actions can be used to perform a wide range of tasks during the installation process, including creating registry keys and values, copying files, and executing scripts or other programs. By using custom actions as conditional statements, you can control the behavior of the installation process based on the system configuration.

For example, you can use a custom action to check for the presence of a specific file or registry key on the system, and use that information to conditionally install or execute other custom actions. You can also use custom actions to perform tasks that are specific to a particular system configuration, such as installing a driver or configuring a network adapter.

This can be done using a wide range of syntax and scripting languages, including VBScript, JavaScript, C++ and [even C#](https://www.alexandrumarin.com/create-c-csharp-dll-for-msi-custom-actions/ "even C#").

Depending on the approach you want to take with Custom Actions you can either:

* Write the custom action to initialize a variable as we did above and then check during the custom launch condition if the variable is initialized or not
* Write the custom action to produce an error if the check is not passed. When the custom action is inserted in the Sequence with Advanced Installer make sure that the “Fail installation if custom action returns an error” is checked. The installer is awaiting a return code either with 0 (success) either with 3010 (reboot)

Let's take the second scenario and consider that we want to create a script that checks if a certain registry key exists. If that registry key is missing we will give back the return code 100 which will be interpreted as a failure.

Const HKEY_LOCAL_MACHINE = &H80000002
Dim RegKey
Dim objWshShell
Set objWshShell = CreateObject("WScript.shell")
strComputer = "."
Set objRegistry = GetObject("winmgmts:\\" & strComputer & "\root\default:StdRegProv")
RegKey= "ProgramFilesDir"
strKeyPath = "SOFTWARE\Microsoft\Windows\CurrentVersion"
objRegistry.GetStringValue HKEY_LOCAL_MACHINE,strKeyPath,RegKey,strValue
'check if the value exists
If IsNull(strValue) Then
    wscript.quit (100)
End If

Copy

As you can see above, we are checking with VBScript if the ProgramFilesDir which is located in HKLM\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion has any value. If the value is null then we will return the error code 100\. 

Now that we have the script created, all we need to do is navigate to the Custom Action page and set it up like so:

![custom action launch condition vbscript](https://cdn.advancedinstaller.com/img/conditional-statements-and-custom-actions/custom-action-launch-condition-vbscript.png "custom action launch condition vbscript")  

If you remember our discussion in the [MSI Packaging Fundamentals ebook](https://tools.techidaily.com/advancedinstaller/products/), immediate execution custom actions can be executed before the [InstallInitialize Action](https://learn.microsoft.com/en-us/windows/win32/msi/installinitialize-action "InstallInitialize Action"), and this is exactly what we need because we need to run this script as soon as possible to confirm that the system has the requested parameters. 

As you can see in the Install Execution Stage, the custom action is set at the top to be the first CA that is executed, and when it comes to Execution Stage Conditions we are only setting it to run during the Install phase.

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
<li><a href="https://screen-activity-recording.techidaily.com/new-2024-approved-advanced-tips-for-recording-google-voice-dialogues/"><u>[New] 2024 Approved Advanced Tips for Recording Google Voice Dialogues</u></a></li>
<li><a href="https://some-approaches.techidaily.com/new-transformative-meme-making-discovering-the-best-8-tools/"><u>[New] Transformative Meme-Making Discovering the Best 8 Tools</u></a></li>
<li><a href="https://activate-lock.techidaily.com/3-easy-methods-to-unlock-icloud-locked-apple-iphone-14-pro-maxipadipod-by-drfone-ios/"><u>3 Easy Methods to Unlock iCloud Locked Apple iPhone 14 Pro Max/iPad/iPod</u></a></li>
<li><a href="https://android-location-track.techidaily.com/3-ways-to-track-poco-m6-pro-4g-without-them-knowing-drfone-by-drfone-virtual-android/"><u>3 Ways to Track Poco M6 Pro 4G without Them Knowing | Dr.fone</u></a></li>
<li><a href="https://win-updates.techidaily.com/best-techniques-for-professional-audio-capture-on-a-windows-10-pc/"><u>Best Techniques for Professional Audio Capture on a Windows 10 PC</u></a></li>
<li><a href="https://win11.techidaily.com/bringing-the-missing-search-back-into-win11s-task-manager/"><u>Bringing the Missing Search Back Into Win11's Task Manager</u></a></li>
<li><a href="https://win-updates.techidaily.com/complete-step-by-step-guide-to-screen-record-functionality-on-ios-11-devices/"><u>Complete Step-by-Step Guide to Screen Record Functionality on iOS 11 Devices</u></a></li>
<li><a href="https://location-social.techidaily.com/does-find-my-friends-work-on-zte-blade-a73-5g-drfone-by-drfone-virtual-android/"><u>Does find my friends work on ZTE Blade A73 5G | Dr.fone</u></a></li>
<li><a href="https://win-updates.techidaily.com/effective-methods-for-packaging-applications-using-a-repacker/"><u>Effective Methods for Packaging Applications Using a Repacker</u></a></li>
<li><a href="https://win-updates.techidaily.com/effective-techniques-to-fully-eliminate-adchoices-pop-ups-permanently/"><u>Effective Techniques to Fully Eliminate AdChoices Pop-Ups Permanently</u></a></li>
<li><a href="https://hardware-updates.techidaily.com/ensure-seamless-printing-with-the-newest-epson-wf-n3620-drivers-compatible-with-all-windows-versions-windows-1187/"><u>Ensure Seamless Printing with the Newest Epson WF-N3620 Drivers - Compatible With All Windows Versions (Windows 11/8/7)</u></a></li>
<li><a href="https://win-updates.techidaily.com/evaluating-the-security-of-microsofts-latest-os-a-comprehensive-guide-to-windows-11-safety/"><u>Evaluating the Security of Microsoft's Latest OS: A Comprehensive Guide to Windows 11 Safety</u></a></li>
<li><a href="https://some-knowledge.techidaily.com/flight-paths-revealed-full-review-of-dji-phantom-4-for-2024/"><u>Flight Paths Revealed Full Review of DJI Phantom 4 for 2024</u></a></li>
<li><a href="https://win-updates.techidaily.com/identifying-fraudulent-android-applications-expert-tips-from-malwarefox/"><u>Identifying Fraudulent Android Applications: Expert Tips From MalwareFox</u></a></li>
<li><a href="https://games-able.techidaily.com/nvidias-magic-formula-how-g-sync-improves-graphics/"><u>Nvidia's Magic Formula: How G-Sync Improves Graphics</u></a></li>
<li><a href="https://win-updates.techidaily.com/protect-your-chrome-from-malicious-notification-attacks-essential-tips/"><u>Protect Your Chrome From Malicious Notification Attacks: Essential Tips</u></a></li>
<li><a href="https://win-updates.techidaily.com/revive-your-missing-office-documents-expert-strategies-for-restoring-deleted-file-versions/"><u>Revive Your Missing Office Documents: Expert Strategies for Restoring Deleted File Versions</u></a></li>
</ul></div>

