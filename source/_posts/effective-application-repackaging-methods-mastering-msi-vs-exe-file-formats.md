---
title: "Effective Application Repackaging Methods: Mastering MSI Vs. EXE File Formats"
date: 2024-09-30T18:03:34.459Z
updated: 2024-10-05T19:58:56.963Z
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
<a href="https://appsumo.8odi.net/c/5597632/2087390/7443" target="_top" id="2087390">
  <img src="//a.impactradius-go.com/display-ad/7443-2087390" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2087390/7443" style="position:absolute;visibility:hidden;" border="0" />
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
<a href="https://laganoo.pxf.io/c/5597632/1528681/16446" target="_top" id="1528681">
  <img src="//a.impactradius-go.com/display-ad/16446-1528681" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://laganoo.pxf.io/i/5597632/1528681/16446" style="position:absolute;visibility:hidden;" border="0" />
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
<a href="https://united.elfm.net/c/5597632/2139558/4704" target="_top" id="2139558">
  <img src="//a.impactradius-go.com/display-ad/4704-2139558" border="0" alt="https://techidaily.com" width="160" height="90"/>
</a>
<img height="0" width="0" src="https://united.elfm.net/i/5597632/2139558/4704" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- These filters will record events related to the EXE installer and any MSI files used during its execution.

\- Begin capturing events: After configuring the filters, select "Start" from the "Capture" menu, or press the Ctrl + E shortcut to begin capturing events.

\- Run the EXE installer: Launch the EXE installer you want to analyze. The Process Monitor will start capturing events in real-time.

\- Analyze captured events: When the installation is finished, or when you want to stop capturing events, go to the "Capture" menu and select "Stop," or press the Ctrl + E shortcut. In the main window of Process Monitor, a list of captured events will be displayed.

\- Filter and analyze events: To analyze the captured events, use the various columns and filter options in the Process Monitor window. Look for file system operations involving MSI files (with the extension ".msi") and registry operations involving MSI execution (ending with ".msiexec.exe"). These events indicate that an MSI is embedded within the EXE installer.

For example, if we install Tableau Reader and start the Process Monitor tool and follow the above steps, we will have the following operations captured:

![process monitor detect msi](https://cdn.advancedinstaller.com/img/repackaging-action-steps/process-monitor-detect-msi.png "process monitor detect msi")  

<!-- affiliate ads begin -->
<a href="https://ephamedtechinc.pxf.io/c/5597632/2136627/26400" target="_top" id="2136627">
  <img src="//a.impactradius-go.com/display-ad/26400-2136627" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://ephamedtechinc.pxf.io/i/5597632/2136627/26400" style="position:absolute;visibility:hidden;" border="0" />
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
<li><a href="https://visual-screen-recording.techidaily.com/new-2024-approved-quick-methods-for-saving-google-voice-communication/"><u>[New] 2024 Approved Quick Methods for Saving Google Voice Communication</u></a></li>
<li><a href="https://youtube-webster.techidaily.com/njoy-premium-video-artwork-download-at-no-cost-today/"><u>[New] Enjoy Premium Video Artwork - Download at No Cost Today</u></a></li>
<li><a href="https://screen-video-capture.techidaily.com/new-step-by-step-full-ps4-game-recording-in-obs-studio/"><u>[New] Step-by-Step Full PS4 Game Recording in OBS Studio</u></a></li>
<li><a href="https://fox-glue.techidaily.com/updated-in-2024-elaborate-inspection-gopro-silver-hero4-unit-test/"><u>[Updated] In 2024, Elaborate Inspection GoPro Silver HERO4 Unit Test</u></a></li>
<li><a href="https://article-tips.techidaily.com/2024-approved-core-elements-in-virtual-narrative-design/"><u>2024 Approved Core Elements in Virtual Narrative Design</u></a></li>
<li><a href="https://win-updates.techidaily.com/how-can-malicious-software-evade-detection-by-security-suites-insights-from-malwarefox/"><u>How Can Malicious Software Evade Detection by Security Suites: Insights From MalwareFox</u></a></li>
<li><a href="https://win-updates.techidaily.com/leading-green-screen-application-tools-for-live-video-streaming-platforms/"><u>Leading Green Screen Application Tools for Live Video Streaming Platforms</u></a></li>
<li><a href="https://win-updates.techidaily.com/learn-cutting-edge-methods-for-msi-product-packaging-using-our-comprehensive-video-series/"><u>Learn Cutting-Edge Methods for MSI Product Packaging Using Our Comprehensive Video Series</u></a></li>
<li><a href="https://win-updates.techidaily.com/simplest-methods-for-removing-images-from-your-ipad/"><u>Simplest Methods for Removing Images From Your iPad</u></a></li>
<li><a href="https://tech-haven.techidaily.com/unleashing-power-integrating-chatgpt-and-wolfram-alpha-plugin-techniques/"><u>Unleashing Power: Integrating ChatGPT and Wolfram Alpha Plugin Techniques</u></a></li>
<li><a href="https://win-updates.techidaily.com/why-does-google-send-you-to-bing-understanding-and-resolving-unintended-redirection/"><u>Why Does Google Send You to Bing? Understanding & Resolving Unintended Redirection</u></a></li>
</ul></div>

