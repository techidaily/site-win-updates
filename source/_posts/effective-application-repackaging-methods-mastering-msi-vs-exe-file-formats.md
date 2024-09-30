---
title: "Effective Application Repackaging Methods: Mastering MSI Vs. EXE File Formats"
date: 2024-09-29T00:11:26.654Z
updated: 2024-09-30T07:22:37.352Z
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
<a href="https://aligracehair.sjv.io/c/5597632/1902324/19272" target="_top" id="1902324">
  <img src="//a.impactradius-go.com/display-ad/19272-1902324" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1902324/19272" style="position:absolute;visibility:hidden;" border="0" />
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

### Using Process Monitor to Detect embedded MSI in EXE

Process Monitor has grown in popularity among IT professionals for not only detecting whether an MSI is embedded in another MSI, but also for detecting additional system changes performed by applications, debugging applications, and so on.

To detect if an EXE contains an embedded MSI with Process Monitor, follow these steps:

\- DownloadProcess Monitor: Visit the official website of Process Monitor (<https://learn.microsoft.com/en-us/sysinternals/downloads/procmon>) and download the latest version of the tool. 

\- Launch Process Monitor: Extract the archive and start Process Monitor

\- Configure filters: Before monitoring the installation process, it's helpful to set up filters to narrow down the captured events and focus on the relevant activities. Click on the "Filter" menu, and then select "Filter..." to open the Filter dialog box.

![process monitor filters window](https://cdn.advancedinstaller.com/img/repackaging-action-steps/process-monitor-filters-window.png "process monitor filters window")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1925544/19272" target="_top" id="1925544">
  <img src="//a.impactradius-go.com/display-ad/19272-1925544" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1925544/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- Configure filter rules: In the Filter dialog box, specify the conditions to filter the events. To detect if an EXE installer contains an embedded MSI, you can set up the following filters: In the "Display entries matching these conditions" select "Operation", “is”, “Process Create” and then “include’. Click on Add.

![process monitor operation is process create](https://cdn.advancedinstaller.com/img/repackaging-action-steps/process-monitor-operation-is-process-create.png "process monitor operation is process create")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2006960/19272" target="_top" id="2006960">
  <img src="//a.impactradius-go.com/display-ad/19272-2006960" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2006960/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

\- These filters will record events related to the EXE installer and any MSI files used during its execution.

\- Begin capturing events: After configuring the filters, select "Start" from the "Capture" menu, or press the Ctrl + E shortcut to begin capturing events.

\- Run the EXE installer: Launch the EXE installer you want to analyze. The Process Monitor will start capturing events in real-time.

\- Analyze captured events: When the installation is finished, or when you want to stop capturing events, go to the "Capture" menu and select "Stop," or press the Ctrl + E shortcut. In the main window of Process Monitor, a list of captured events will be displayed.

\- Filter and analyze events: To analyze the captured events, use the various columns and filter options in the Process Monitor window. Look for file system operations involving MSI files (with the extension ".msi") and registry operations involving MSI execution (ending with ".msiexec.exe"). These events indicate that an MSI is embedded within the EXE installer.

For example, if we install Tableau Reader and start the Process Monitor tool and follow the above steps, we will have the following operations captured:

![process monitor detect msi](https://cdn.advancedinstaller.com/img/repackaging-action-steps/process-monitor-detect-msi.png "process monitor detect msi")  

<!-- affiliate ads begin -->
<a href="https://malaysia-healthcare-travel-council.pxf.io/c/5597632/1557747/17382" target="_top" id="1557747">
  <img src="//a.impactradius-go.com/display-ad/17382-1557747" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://malaysia-healthcare-travel-council.pxf.io/i/5597632/1557747/17382" style="position:absolute;visibility:hidden;" border="0" />
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
<li><a href="https://screen-mirroring-recording.techidaily.com/new-in-device-recorder-activation-huaweis-mate-1020-and-p-series-phones-p20-p10/"><u>[New] In-Device Recorder Activation Huawei's Mate 10/20 & P Series Phones (P20, P10)</u></a></li>
<li><a href="https://desktop-recording.techidaily.com/updated-2024-approved-efficient-techniques-for-capturing-macos-content/"><u>[Updated] 2024 Approved Efficient Techniques for Capturing macOS Content</u></a></li>
<li><a href="https://screen-sharing-recording.techidaily.com/updated-in-2024-seamless-transitions-made-simple-screen-record-with-aiseesoft/"><u>[Updated] In 2024, Seamless Transitions Made Simple Screen Record With Aiseesoft</u></a></li>
<li><a href="https://fox-hovers.techidaily.com/updated-realistic-or-risky-vrs-hidden-dangers-for-2024/"><u>[Updated] Realistic or Risky? VR's Hidden Dangers for 2024</u></a></li>
<li><a href="https://easy-unlock-android.techidaily.com/5-solutions-for-realme-10t-5g-unlock-without-password-by-drfone-android/"><u>5 Solutions For Realme 10T 5G Unlock Without Password</u></a></li>
<li><a href="https://tech-revival.techidaily.com/conquering-challenges-with-gpt-3-openai-style/"><u>Conquering Challenges with GPT-3, OpenAI Style</u></a></li>
<li><a href="https://phone-solutions.techidaily.com/does-moto-g-5g-2023-has-native-mov-support-by-aiseesoft-video-converter-play-mov-on-android/"><u>Does Moto G 5G (2023) has native MOV support?</u></a></li>
<li><a href="https://win-updates.techidaily.com/no-more-plugins-embedding-rtsp-video-feeds-on-web-pages-using-vlcs-html5-transcoder/"><u>No More Plugins: Embedding RTSP Video Feeds on Web Pages Using VLC's HTML5 Transcoder</u></a></li>
<li><a href="https://win-updates.techidaily.com/pros-and-cons-free-and-professional-editions-of-zune-video-converter-analysis/"><u>Pros and Cons: Free and Professional Editions of Zune Video Converter Analysis</u></a></li>
<li><a href="https://win-updates.techidaily.com/simple-steps-converting-mov-files-to-wma-format-using-windows/"><u>Simple Steps: Converting Mov Files to Wma Format Using Windows</u></a></li>
<li><a href="https://win-updates.techidaily.com/the-ultimate-guide-top-5-elite-4k-video-transcoding-software/"><u>The Ultimate Guide: Top 5 Elite 4K Video Transcoding Software</u></a></li>
<li><a href="https://win-updates.techidaily.com/ultimate-guide-transforming-video-and-audio-files-into-various-formats/"><u>Ultimate Guide: Transforming Video and Audio Files Into Various Formats</u></a></li>
<li><a href="https://win-updates.techidaily.com/1726027350128-vimeo-firefox/"><u>ダウンロード: Vimeo 映像を Firefox でどうやって保存するか</u></a></li>
</ul></div>

