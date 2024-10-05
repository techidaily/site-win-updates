---
title: "1. Enhancing Network Security: Expert Guide to Setting Firewall Policies Using VBScript, PowerShell, and Advanced Installer"
date: 2024-09-28T16:54:03.357Z
updated: 2024-10-05T17:21:52.141Z
tags:
  - application-packaging-training
categories:
  - advancedinstaller
description: "This Article Describes 1. Enhancing Network Security: Expert Guide to Setting Firewall Policies Using VBScript, PowerShell, and Advanced Installer"
thumbnail: https://thmb.techidaily.com/3b9684531fbf23c2641f6279330c8cba0c78b446e63ca3e1151548a8f471104b.jpg
---

## 1. Enhancing Network Security: Expert Guide to Setting Firewall Policies Using VBScript, PowerShell, and Advanced Installer

>  Disclaimer: This post includes affiliate links
>
>  If you click on a link and make a purchase, I may receive a commission at no extra cost to you.
>

## Firewall

To make the environment more secure it’s important to properly define and configure the firewall of your machines. However, there might be times when a specific executable must be added as an exception to the Inbound or Outbound rules of the firewall in order to have access.

In this article, let’s have a look at how you can configure firewall rules via MSI with Advanced Installer, VBScript and Powershell.

### Firewall rules with VBScript

Although you can use the **HNetCfg.FwAuthorizedApplication** object with VBScript to define firewall rules, the easiest method is to call the [**netsh.exe**](https://learn.microsoft.com/en-us/windows-server/networking/technologies/netsh/netsh-contexts "netsh.exe") utility that it’s included in Windows. This command-line utility allows you to modify the network configuration of a certain machine that is currently running. One of the commands available for netsh is **advfirewall** which allows you to change to the netsh advfirewall context. Jumping further into the context, you can type 

netsh advfirewall firewall

Copy

Into a cmd window and this will give you the following options:

?          	- Displays a list of commands.
add        	- Adds a new inbound or outbound firewall rule.
delete     	- Deletes all matching firewall rules.
dump       	- Displays a configuration script.
help       	- Displays a list of commands.
set        	- Sets new values for properties of a existing rule.
show       	- Displays a specified firewall rule.

Copy

So basically if we want to add a firewall rule we can use:

netsh.exe advfirewall firewall add rule name=FRIENDLYNAME dir=IN/OUT action=ALLOW/DENY program=PATHTOEXE enable=YES/NO profile=domain

Copy

If we want to remove a firewall rule we can use:

netsh.exe advfirewall firewall delete rule name=FRIENDLYNAME

Copy

Now that we are aware of how netsh is working with firewall rules, let’s assume we have a HelloWorld.exe that we want to add to the inbound firewall and we want to allow everything. With VBScript we can produce the following:

Dim WshShell
Dim programPath2, programfiless, programfiles
Set WshShell = CreateObject("Wscript.Shell")
programfiless=WshShell.ExpandEnvironmentStrings("%ProgramFiles(x86)%")
programfiles=WshShell.ExpandEnvironmentStrings("%ProgramW6432%")
ProgramPath2 = programfiless & "\Program Files (x86)\Caphyon\Firewall App\HelloWorld.exe"
WshShell.Run "netsh.exe advfirewall firewall add rule name=HelloWorld dir=in action=allow program=" & chr(34) & ProgramPath2 & chr(34) & " enable=yes profile=domain ", 0, False

Copy

This VBScript performs the following actions:

* Dim WshShell: Declares a variable named WshShell to hold a reference to the Windows Script Host Shell object.
* Dim programPath2, programfiless, programfiles: Declares variables to store the paths of program files.
* Set WshShell = CreateObject("Wscript.Shell"): Creates an instance of the Windows Script Host Shell object.
* programfiless = WshShell.ExpandEnvironmentStrings("%ProgramFiles(x86)%"): Retrieves the path of the "Program Files (x86)" folder using the %ProgramFiles(x86)% environment variable.
* programfiles = WshShell.ExpandEnvironmentStrings("%ProgramW6432%"): Retrieves the path of the "Program Files" folder using the %ProgramW6432% environment variable.
* ProgramPath2 = programfiless & "\\Program Files (x86)\\Caphyon\\Firewall App\\HelloWorld.exe": Concatenates the program file path with the specific file name to create the full path of the executable file "HelloWorld.exe".
* WshShell.Run "netsh.exe advfirewall firewall add rule name=HelloWorld dir=in action=allow program=" & chr(34) & ProgramPath2 & chr(34) & " enable=yes profile=domain ", 0, False: Runs the netsh.exe command to add a firewall rule named "HelloWorld" with the specified properties. The command allows incoming traffic (dir=in), allows the specified program (program=) with the path of "HelloWorld.exe", enables the rule (enable=yes), and applies the rule to the domain profile.

Next, open Advanced Installer and navigate to the Custom Actions Page. In here, search for the **Launch attached file** and select the location of the VBScript. Next, configure the custom action to execute as shown below:

![Launch attached file](https://cdn.advancedinstaller.com/img/configure-firewall-rules-with-custom-actions/addfwCA.png "Launch attached file")  

As a best practice it’s also important to remove the firewall rule during the uninstallation. For that, it means we need another Custom Action and a different VBScrit to remove our rule. The VBScript code is:

Dim WshShell
Set WshShell = CreateObject("Wscript.Shell")
WshShell.Run "netsh.exe advfirewall firewall delete rule name=HelloWorld"

Copy

After that, follow the same exact steps as above and configure the custom action as following:

![configure the custom action](https://cdn.advancedinstaller.com/img/configure-firewall-rules-with-custom-actions/remfwCA.png "configure the custom action")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2151884/7443" target="_top" id="2151884">
  <img src="//a.impactradius-go.com/display-ad/7443-2151884" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2151884/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Firewall rules with PowerShell

While **netsh** is still available and widely used by the community, starting with Windows 8.1 you can use the buit-in **NetSecurity** PowerShell module to manage firewall operations.

In general, there are 85 commands available in this module that you can use in Windows 10/11, but we are only interested in two of them. To add a firewall rule you can simply do:

$HelloWorldLocation = ${env:ProgramFiles(x86)} + "\Caphyon\Firewall App\HelloWorld.exe"
New-NetFirewallRule -Program $HelloWorldLocation -Action Allow -Profile Domain -DisplayName “HelloWorld” -Description “Block Firefox browser” -Direction Inbound

Copy

To remove a firewall rule is even simpler as we only use the [Remove-NetFirewallRule](https://learn.microsoft.com/en-us/powershell/module/netsecurity/remove-netfirewallrule?view=windowsserver2022-ps "Remove-NetFirewallRule") PowerShell cmdlet:

Remove-NetFirewallRule -DisplayName "HelloWorld"

Copy

Next, open Advanced Installer and navigate to the Custom Actions Page. In here, search for the **Run PowerShell script file** and select the location of the PowerShell script. Next, configure the custom action to execute as shown below:

![Run PowerShell script file](https://cdn.advancedinstaller.com/img/configure-firewall-rules-with-custom-actions/addfwPSCA.png "Run PowerShell script file")  

To also add the remove firewall PowerShell script, follow the same steps as above and do the following configurations:

![remove firewall PowerShell script](https://cdn.advancedinstaller.com/img/configure-firewall-rules-with-custom-actions/remfwPSCA.png "remove firewall PowerShell script")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2100530/7443" target="_top" id="2100530">
  <img src="//a.impactradius-go.com/display-ad/7443-2100530" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2100530/7443" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Firewall rules with Advanced Installer

If you don’t like to code, Advanced Installer made it much simpler to add firewall rules. First, navigate to the [Windows Firewall](https://tools.techidaily.com/advancedinstaller/products/)[page](https://tools.techidaily.com/advancedinstaller/products/).

Next, click on **New Rule**. This will open a new window in which you can define the necessary details for your exception:

![Windows Firewall page](https://cdn.advancedinstaller.com/img/configure-firewall-rules-with-custom-actions/advfw.png "Windows Firewall page")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/2135408/19272" target="_top" id="2135408">
  <img src="//a.impactradius-go.com/display-ad/19272-2135408" border="0" alt="https://techidaily.com" width="120" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/2135408/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

As you can see, you can easily choose the direction, display name, program path, protocol and other settings directly from the GUI. In our case we wanted to mimic the above usages of netsh and PowerShell and left everything as before in the GUI.

And that is it, Advanced Installer will automatically create the exception during the installation and during the uninstallation it will remove the exception from the firewall, not needing to create two separate actions for it.

![remove the exception from the firewall](https://cdn.advancedinstaller.com/img/configure-firewall-rules-with-custom-actions/advfw2.png "remove the exception from the firewall")  

<!-- affiliate ads begin -->
<a href="https://aligracehair.sjv.io/c/5597632/1918719/19272" target="_top" id="1918719">
  <img src="//a.impactradius-go.com/display-ad/19272-1918719" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://aligracehair.sjv.io/i/5597632/1918719/19272" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

All you have to do is build and install the MSI package. After the installation, if we check the Inbound rules, our rule is there:

![check the Inbound rules](https://cdn.advancedinstaller.com/img/configure-firewall-rules-with-custom-actions/inbound.png "check the Inbound rules")

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
<li><a href="https://facebook-video-recording.techidaily.com/new-in-2024-best-practices-in-embedding-real-time-videos-from-fb/"><u>[New] In 2024, Best Practices in Embedding Real-Time Videos From FB</u></a></li>
<li><a href="https://facebook-videos.techidaily.com/new-in-2024-transforming-your-profile-into-a-showstopper/"><u>[New] In 2024, Transforming Your Profile Into a Showstopper</u></a></li>
<li><a href="https://fox-access.techidaily.com/updated-metavision-quest-selecting-the-most-advanced-vr-headset-for-2024/"><u>[Updated] Metavision Quest Selecting the Most Advanced VR Headset for 2024</u></a></li>
<li><a href="https://extra-guidance.techidaily.com/2024-approved-mastering-the-art-of-google-podcast-upload/"><u>2024 Approved Mastering the Art of Google Podcast Upload</u></a></li>
<li><a href="https://win-updates.techidaily.com/cant-delete-mcafee-from-your-system-successful-steps-to-fully-eliminate-mcafee-antivirus/"><u>Can't Delete McAfee From Your System? Successful Steps to Fully Eliminate McAfee Antivirus</u></a></li>
<li><a href="https://buynow-marvelous.techidaily.com/comparing-tablet-devices-based-on-central-processing-unit-capabilities/"><u>Comparing Tablet Devices Based on Central Processing Unit Capabilities</u></a></li>
<li><a href="https://win-updates.techidaily.com/easy-steps-to-successfully-downloading-tunes-on-your-lg-smartphone/"><u>Easy Steps to Successfully Downloading Tunes on Your LG Smartphone</u></a></li>
<li><a href="https://fox-friendly.techidaily.com/flamenco-finch-frolic-for-2024/"><u>Flamenco Finch Frolic for 2024</u></a></li>
<li><a href="https://phone-solutions.techidaily.com/how-to-bypass-frp-on-asus-by-drfone-android-unlock-remove-google-frp/"><u>How To Bypass FRP on Asus</u></a></li>
<li><a href="https://iphone-unlock.techidaily.com/in-2024-what-does-jailbreaking-apple-iphone-6s-i-do-get-answers-here-drfone-by-drfone-ios/"><u>In 2024, What Does Jailbreaking Apple iPhone 6s i Do? Get Answers here | Dr.fone</u></a></li>
<li><a href="https://win-updates.techidaily.com/resolving-connection-issues-compatibility-between-iphones-phone-manager-and-itunes-version-121/"><u>Resolving Connection Issues: Compatibility Between iPhone's Phone Manager and iTunes Version 12.1</u></a></li>
<li><a href="https://win-updates.techidaily.com/step-by-step-guide-recognizing-and-stopping-malicious-programs-via-task-manager/"><u>Step-by-Step Guide: Recognizing and Stopping Malicious Programs via Task Manager</u></a></li>
<li><a href="https://win-updates.techidaily.com/step-by-step-guide-safeguarding-your-facebook-presence-against-hacking-and-privacy-breaches/"><u>Step-by-Step Guide: Safeguarding Your Facebook Presence Against Hacking and Privacy Breaches</u></a></li>
<li><a href="https://win-updates.techidaily.com/top-5-stunning-websites-that-echo-the-vibe-of-lastfm/"><u>Top 5 Stunning Websites That Echo the Vibe of Last.fm</u></a></li>
<li><a href="https://win-updates.techidaily.com/top-6-image-enhancement-software-picking-the-best-from-various-platforms/"><u>Top 6 Image Enhancement Software Picking the Best From Various Platforms</u></a></li>
</ul></div>

