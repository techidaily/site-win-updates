---
title: Overcoming Group Policy Constraints on Windows Defender – Your Ultimate 4-Step Solution
date: 2024-09-28T19:37:50.422Z
updated: 2024-10-05T19:14:36.019Z
tags:
  - product
  - antivirus
  - utilities
categories:
  - malwarefox
thumbnail: https://thmb.techidaily.com/3f45b4986206d046cd956542a295fe465671e73b81f9c11e8f6862999203849a.jpg
---

## Overcoming Group Policy Constraints on Windows Defender – Your Ultimate 4-Step Solution

With the growing cyber threats, a good security solution is the need of the hour. Windows users have the luxury of a robust security program, **Windows Defender**, which is now known as **Microsoft Defender**. It comes in-built into the latest Windows 10 devices. 

![TotalAv Logo](https://www.malwarefox.com/wp-content/uploads/2024/02/totalav-svg.webp "totalav-svg")

**Stay malware-free with reliable antivirus**

Don't compromise your Data and Privacy. TotalAV is a top-notch antivirus program that handles various viruses, trojans, and other malware that may target your devices. It will safeguard your devices and enhance your system performance.

**4.9**/5

⭐ **Editor's Choice**

✔️ Excellent Malware Detection  
✔️ Multiple set of Features  
✔️ 30 Day Money-Back

[](https://tools.techidaily.com/malwarefox/products/) Get TotalAV > 

Taking lessons from the backlashes it receives after its initial release, Microsoft made some necessary security changes. Today, Microsoft Defender is one of the [top antivirus solutions](https://tools.techidaily.com/malwarefox/products/) in the cybersecurity field and used by millions of users.

However, this extensive security program can malfunction and stop working because of a few errors caused intentionally to stop it; one of those errors is “**Windows Defender blocked by Group Policy**.” 

In this guide, we would list out the possible fixes for this error.

[Is Windows Defender Enough?](https://tools.techidaily.com/malwarefox/products/)

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Why “Windows Defender blocked by Group Policy” Error Occurs?

There could be a number of reasons for this error to happen. Here are the most common ones.

* Another [third-party antivirus](https://tools.techidaily.com/malwarefox/products/) or antimalware is clashing with the Windows Defender program.
* Cybercriminals might have used infiltrate Group Policy using [malware](https://tools.techidaily.com/malwarefox/products/) to disable the security of the Windows system.
* Some unauthorized changes in the Group Policies can also lead to the error. The changes can be made by mistake or intentionally too.

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1885999/19272" target="_top" id="1885999">
  <img src="//a.impactradius-go.com/display-ad/19272-1885999" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1885999/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

## How to fix “Windows Defender is Turned off by Group Policy”?

### **Using Group Policy Editor**

**_Note_**_: The Group Policy Editor is not available on the Windows 10 Home version_

1. Search for the **Group Policy Editor** in the windows search bar and launch it.![Open Group Policy Editor](https://www.malwarefox.com/wp-content/uploads/2020/06/Group-Policy-Editor.png)
2. In the editor, navigate to: **Computer Configuration** \-> **Administrative Templates** \-> **Windows Components** \-> **Microsoft Defender Antivirus**.
3. Locate “**Turn off Microsoft Defender Antivirus**” and double click on it to open it.![Turn Off Microsoft Defender Antivirus](https://www.malwarefox.com/wp-content/uploads/2020/10/Turn-Off-Microsoft-Defender-Antivirus.png)
4. In order to enable the Microsoft Defender, click on the **Disabled** bullet.![Enable-MS-Defender](https://www.malwarefox.com/wp-content/uploads/2020/10/Enable-MS-Defender.png)

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2123733/7443" target="_top" id="2123733">
  <img src="//a.impactradius-go.com/display-ad/7443-2123733" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2123733/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

5. Click **Apply** and **OK** to finish the configuration.

6. Restart the system to enable the settings.

---

### **Using Registry Editor**

1. Search for “**Registry Editor**” in the windows search box and launch it.![launch registry editor](https://www.malwarefox.com/wp-content/uploads/2020/10/launch-registry-editor.png)
2. Navigate to or copy & paste this path to reach the Windows Defender folder: **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Policies\\Microsoft\\Windows Defender**

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2144287/7443" target="_top" id="2144287">
  <img src="//a.impactradius-go.com/display-ad/7443-2144287" border="0" alt="https://techidaily.com" width="600" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2144287/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

3. Right-click on the **DisableRealTimeMonitoring** key and Delete it.![Delete DisableRealtimeMonitoring key](https://www.malwarefox.com/wp-content/uploads/2020/10/Delete-DisableRealtimeMonitoring-key.png)
4. Exit from the Registry Editor and reboot your system to apply the changes.

<!-- affiliate ads begin -->
<a href="https://versadesk.pxf.io/c/5597632/1815678/21290" target="_top" id="1815678">
  <img src="//a.impactradius-go.com/display-ad/21290-1815678" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://versadesk.pxf.io/i/5597632/1815678/21290" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

---

---

### **Using the PowerShell Command**

1. Search for the **Windows Powershell** in the Windows search box and select **Run as Administrator.**![PowerShell Run as Admin](https://www.malwarefox.com/wp-content/uploads/2020/10/PowerShell-Run-as-Admin.jpg)
2. Type or copy & paste this command and hit the enter key: **_Set-MpPreference -DisableRealtimeMonitoring 0_**![Enable MS defender with Powershell](https://www.malwarefox.com/wp-content/uploads/2020/10/Enable-MS-defender-with-Powershell.png)

<!-- affiliate ads begin -->
<a href="https://ephamedtechinc.pxf.io/c/5597632/2137213/26400" target="_top" id="2137213">
  <img src="//a.impactradius-go.com/display-ad/26400-2137213" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://ephamedtechinc.pxf.io/i/5597632/2137213/26400" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

---

### **Using Windows Settings**

1. Right-click on the windows start icon and choose Settings from the list.![Settings](https://www.malwarefox.com/wp-content/uploads/2020/10/Settings.png)
2. Select **Update & Security** settings.![Update and Security](https://www.malwarefox.com/wp-content/uploads/2020/10/Update-and-Security.png)
3. From the left-pane choose **Windows Security**![launch windows security](https://www.malwarefox.com/wp-content/uploads/2020/10/launch-windows-security.png)
4. Next, click on **Virus & threat protection**.![Choose virus & threat protection](https://www.malwarefox.com/wp-content/uploads/2020/10/Choose-virus-threat-protection.png)

5. Navigate to Virus & threat protection settings and click on **Manage settings**.![manage V&T settings](https://www.malwarefox.com/wp-content/uploads/2020/10/manage-VT-settings.png)
6. Toggle the switch to turn on the Microsoft Defender **real-time protection**.![turn On the Real Time protection](https://www.malwarefox.com/wp-content/uploads/2020/10/turn-On-the-RT-protection.png)

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2049369/7443" target="_top" id="2049369">
  <img src="//a.impactradius-go.com/display-ad/7443-2049369" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2049369/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1934288/19272" target="_top" id="1934288">
  <img src="//a.impactradius-go.com/display-ad/19272-1934288" border="0" alt="https://techidaily.com" width="300" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1934288/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

---

### **Disable the Third-Party Security App**

The “Windows Defender blocked by Group Policy” error can also be caused if any third-party application has conflicts with the Defender. So, if you really require Windows Defender to run, try disabling the third-party antimalware or antivirus application and then launch the Defender app.

[How to Choose Best Antivirus for Windows 10](https://tools.techidaily.com/malwarefox/products/)

---

## Final Words

These are the top working solutions to fix the Windows Defender blocked by Group Policy error. If you apply the steps correctly, you would be able to run the Defender application eventually. However, if the problem persists even after trying the above methods, you can get the robust security solutions like **[Malwarefox](https://tools.techidaily.com/malwarefox/products/)**, that can provide better protection than the Microsoft Defender.

**Why my Windows Defender is turned off?** 

Windows Defender on your system can be turned off because of the various reasons like any third-party security app is conflicting with it, or a malware attack has infiltrated and modified the settings to disable it.

**Where is Windows Defender in group policy?** 

To edit the Windows Defender settings in the group policy editor, you can follow this path: **Local Computer Policy > Administrative Templates > Windows Components > Windows Defender Antivirus.** In the latest Windows version, the name of the Windows Defender is changed to **Microsoft Defender.** On those systems, the path to be followed is: **Local Computer Policy > Administrative Templates > Windows Components > Microsoft Defender Antivirus**.

### Leave a Comment [Cancel reply](https://tools.techidaily.com/malwarefox/products/)

Comment

Name Email 

Save my name, email, and website in this browser for the next time I comment.

Δ

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
<li><a href="https://screen-mirroring-recording.techidaily.com/new-in-2024-level-up-your-livestream-game-using-obs-youtube-and-twitch/"><u>[New] In 2024, Level-Up Your Livestream Game Using OBS, YouTube & Twitch</u></a></li>
<li><a href="https://visual-screen-recording.techidaily.com/updated-2024-approved-professional-video-capture-techniques-mastering-movs-on-win10/"><u>[Updated] 2024 Approved Professional Video Capture Techniques Mastering MOVs on Win10</u></a></li>
<li><a href="https://instagram-video-recordings.techidaily.com/updated-in-2024-insta-story-mastery-adjusting-focus-like-a-pro/"><u>[Updated] In 2024, Insta Story Mastery Adjusting Focus Like a Pro</u></a></li>
<li><a href="https://some-guidance.techidaily.com/2024-approved-streamline-editing-how-to-load-music-in-inshot/"><u>2024 Approved Streamline Editing How to Load Music in InShot</u></a></li>
<li><a href="https://tech-hub.techidaily.com/can-you-utilize-chatgpt-for-smart-home-automation-controls/"><u>Can You Utilize ChatGPT for Smart Home Automation Controls?</u></a></li>
<li><a href="https://win-updates.techidaily.com/easy-steps-to-capture-your-epic-lol-moments-a-beginners-guide/"><u>Easy Steps to Capture Your Epic LoL Moments: A Beginner's Guide</u></a></li>
<li><a href="https://win-updates.techidaily.com/effortless-migration-how-to-sync-your-huawei-nova-9-with-a-windows-or-mac-pc/"><u>Effortless Migration: How to Sync Your Huawei Nova 9 with a Windows or Mac PC</u></a></li>
<li><a href="https://hardware-help.techidaily.com/find-and-install-updated-zebra-printer-drivers-on-your-windows-machine-easily/"><u>Find and Install Updated Zebra Printer Drivers on Your Windows Machine Easily</u></a></li>
<li><a href="https://win-updates.techidaily.com/how-to-effortlessly-take-screenshots-with-your-htc-smartphone/"><u>How To Effortlessly Take Screenshots with Your HTC Smartphone</u></a></li>
<li><a href="https://fox-links.techidaily.com/in-2024-capturing-the-unseen-gopro-hero-vs-nikons-km-170/"><u>In 2024, Capturing the Unseen GoPro HERO vs Nikon's KM-170</u></a></li>
<li><a href="https://driver-download.techidaily.com/new-release-download-the-most-recent-amd-radeon-pro-w5700-drivers-for-windows-11107/"><u>New Release: Download the Most Recent AMD Radeon Pro W5700 Drivers for Windows 11/10/7</u></a></li>
<li><a href="https://win-updates.techidaily.com/simple-tutorial-on-reverting-google-chrome-mozilla-firefox-and-microsoft-edge-back-to-their-original-state/"><u>Simple Tutorial on Reverting Google Chrome, Mozilla Firefox and Microsoft Edge Back to Their Original State</u></a></li>
<li><a href="https://win-updates.techidaily.com/step-by-step-guide-installing-and-setting-up-services-using-msi-package-manager/"><u>Step-by-Step Guide: Installing and Setting Up Services Using MSI Package Manager</u></a></li>
<li><a href="https://win-updates.techidaily.com/top-8-secure-browser-add-ons-enhance-safety-with-chrome-protectors-like-malwarefox/"><u>Top 8 Secure Browser Add-Ons: Enhance Safety with Chrome Protectors Like MalwareFox</u></a></li>
<li><a href="https://win-updates.techidaily.com/top-picks-the-ultimate-christmas-card-creation-apps-for-stunning-holiday-images-2022-edition/"><u>Top Picks: The Ultimate Christmas Card Creation Apps for Stunning Holiday Images - 2022 Edition</u></a></li>
<li><a href="https://win-updates.techidaily.com/top-rated-youtube-summary-tools-and-apps-the-ultimate-guide/"><u>Top Rated YouTube Summary Tools & Apps: The Ultimate Guide</u></a></li>
<li><a href="https://ai-video-tools.techidaily.com/updated-2024-approved-free-flv-video-editing-software-top-picks/"><u>Updated 2024 Approved Free FLV Video Editing Software Top Picks</u></a></li>
</ul></div>

