---
title: "Effective Application Repackaging Methods: Mastering MSI Vs. EXE File Formats"
date: 2024-10-06T02:35:35.055Z
updated: 2024-10-10T19:56:52.631Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: "This Article Describes Effective Application Repackaging Methods: Mastering MSI Vs. EXE File Formats"
thumbnail: https://thmb.techidaily.com/dfb31f4a374c12c54be4691af9a495853d8fa50fd8b2538ecaa291b275493185.jpg
---

## Effective Application Repackaging Methods: Mastering MSI Vs. EXE File Formats

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Way forward for your installer

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2043662/7443" target="_top" id="2043662">
  <img src="//a.impactradius-go.com/display-ad/7443-2043662" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2043662/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Strategies for Repackaging Applications: MSI and EXE Approaches

Depending on the situation, there are a number of actions you can take when it comes to repackaging an application:

* **MSI**: If the application comes as an MSI, the way forward to further customize and deploy the application would be to create transform files (MST)
* **EXE**: There are three possibilities on how to advance with an EXE installer. The most popular one is to repackage it via the snapshot method, but there are cases where the EXE installer actually contains an embedded MSI which is extracted and then installed, and the final case is where the application is so complex that it’s best to install it silently via a wrapper method

The MSI scenario is quite straightforward so we would go ahead and have a look over the EXE scenario.

The first step is to determine whether the EXE requires repackaging or if it contains an embedded MSI. There are several ways to determine whether an EXE installer contains an embedded MSI:

* Open Task Manager and check if the msiexec service appears in the list during the installation
* Check the [Uninstall registry](https://tools.techidaily.com/advancedinstaller/products/) and see what uninstall command has appeared or if the key name resembles an MSI Product Code
* Use [Process Monitor](https://learn.microsoft.com/en-us/sysinternals/downloads/procmon "Process Monitor")

<!-- affiliate ads begin -->
<a href="https://ephamedtechinc.pxf.io/c/5597632/2137208/26400" target="_top" id="2137208">
  <img src="//a.impactradius-go.com/display-ad/26400-2137208" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://ephamedtechinc.pxf.io/i/5597632/2137208/26400" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Using Process Monitor to Detect embedded MSI in EXE

Process Monitor has grown in popularity among IT professionals for not only detecting whether an MSI is embedded in another MSI, but also for detecting additional system changes performed by applications, debugging applications, and so on.

To detect if an EXE contains an embedded MSI with Process Monitor, follow these steps:

\- DownloadProcess Monitor: Visit the official website of Process Monitor (<https://learn.microsoft.com/en-us/sysinternals/downloads/procmon>) and download the latest version of the tool. 

\- Launch Process Monitor: Extract the archive and start Process Monitor

\- Configure filters: Before monitoring the installation process, it's helpful to set up filters to narrow down the captured events and focus on the relevant activities. Click on the "Filter" menu, and then select "Filter..." to open the Filter dialog box.

![process monitor filters window](https://cdn.advancedinstaller.com/img/repackaging-action-steps/process-monitor-filters-window.png "process monitor filters window")  

\- Configure filter rules: In the Filter dialog box, specify the conditions to filter the events. To detect if an EXE installer contains an embedded MSI, you can set up the following filters: In the "Display entries matching these conditions" select "Operation", “is”, “Process Create” and then “include’. Click on Add.

![process monitor operation is process create](https://cdn.advancedinstaller.com/img/repackaging-action-steps/process-monitor-operation-is-process-create.png "process monitor operation is process create")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2135370/19272" target="_top" id="2135370">
  <img src="//a.impactradius-go.com/display-ad/19272-2135370" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2135370/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- These filters will record events related to the EXE installer and any MSI files used during its execution.

\- Begin capturing events: After configuring the filters, select "Start" from the "Capture" menu, or press the Ctrl + E shortcut to begin capturing events.

\- Run the EXE installer: Launch the EXE installer you want to analyze. The Process Monitor will start capturing events in real-time.

\- Analyze captured events: When the installation is finished, or when you want to stop capturing events, go to the "Capture" menu and select "Stop," or press the Ctrl + E shortcut. In the main window of Process Monitor, a list of captured events will be displayed.

\- Filter and analyze events: To analyze the captured events, use the various columns and filter options in the Process Monitor window. Look for file system operations involving MSI files (with the extension ".msi") and registry operations involving MSI execution (ending with ".msiexec.exe"). These events indicate that an MSI is embedded within the EXE installer.

For example, if we install Tableau Reader and start the Process Monitor tool and follow the above steps, we will have the following operations captured:

![process monitor detect msi](https://cdn.advancedinstaller.com/img/repackaging-action-steps/process-monitor-detect-msi.png "process monitor detect msi")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2135394/19272" target="_top" id="2135394">
  <img src="//a.impactradius-go.com/display-ad/19272-2135394" border="0" alt="https://techidaily.com" width="120" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2135394/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

We're most interested in the Path and Detail columns. Looking at what TableauReader.exe does, it first extracts the installer data into a temporary directory in the %temp% directory, then installs the Visual C++ Redistributables 2013, followed by the Tableau Reader. However, if we look closely, we can see that the msiexec.exe service is called, indicating that the exe file is extracting the file in that %temp% location.

This is an example where you will need to create a transform file (MST) to further customize the Tableau Reader MSI installation, but also to use the [dependencies](https://tools.techidaily.com/advancedinstaller/products/) to declare that Visual C++ Redistributable 2013 is needed in order for the application to function properly.

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
<li><a href="https://fox-links.techidaily.com/new-mastering-the-art-of-selecting-premium-free-srt-translation-services/"><u>[New] Mastering the Art of Selecting Premium Free SRT Translation Services</u></a></li>
<li><a href="https://fox-blue.techidaily.com/updated-expert-guide-to-eliminating-red-eye-on-your-iphone-shots-for-free-for-2024/"><u>[Updated] Expert Guide to Eliminating Red Eye on Your iPhone Shots for Free for 2024</u></a></li>
<li><a href="https://howto.techidaily.com/9-solutions-to-fix-xiaomi-redmi-k70-system-crash-issue-drfone-by-drfone-fix-android-problems-fix-android-problems/"><u>9 Solutions to Fix Xiaomi Redmi K70 System Crash Issue | Dr.fone</u></a></li>
<li><a href="https://win-updates.techidaily.com/advanced-techniques-in-editing-registry-settings-using-advanced-installer/"><u>Advanced Techniques in Editing Registry Settings Using Advanced Installer</u></a></li>
<li><a href="https://techidaily.com/best-fixes-for-samsung-galaxy-s24-hard-reset-drfone-by-drfone-reset-android-reset-android/"><u>Best Fixes For Samsung Galaxy S24 Hard Reset | Dr.fone</u></a></li>
<li><a href="https://digital-screen-recording.techidaily.com/clear-video-logger-for-windows-10-systems-for-2024/"><u>Clear Video Logger for Windows 10 Systems for 2024</u></a></li>
<li><a href="https://win-updates.techidaily.com/effective-strategies-for-enabling-tamper-defense-in-windows-10-insights-from-malwarefox-experts/"><u>Effective Strategies for Enabling Tamper Defense in Windows 10 - Insights From MalwareFox Experts</u></a></li>
<li><a href="https://tech-recovery.techidaily.com/essential-fixes-for-the-not-found-error-in-msi-dll-file/"><u>Essential Fixes for the Not Found Error in MSI DLL File</u></a></li>
<li><a href="https://win-updates.techidaily.com/guard-your-system-with-malwarefox-a-powerful-defense-for-ransomware-threats/"><u>Guard Your System with MalwareFox - A Powerful Defense for Ransomware Threats</u></a></li>
<li><a href="https://ai-vdieo-software.techidaily.com/slow-down-time-10-exceptional-video-editing-software/"><u>Slow Down Time 10 Exceptional Video Editing Software</u></a></li>
<li><a href="https://win-updates.techidaily.com/the-ultimate-guide-choosing-the-top-4-best-android-emulators-for-samsungs/"><u>The Ultimate Guide: Choosing the Top 4 Best Android Emulators for Samsungs</u></a></li>
</ul></div>

