---
title: "1. Enhancing Network Security: Expert Guide to Setting Firewall Policies Using VBScript, PowerShell, and Advanced Installer"
date: 2024-10-05T00:02:26.041Z
updated: 2024-10-11T00:06:32.148Z
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

<!-- affiliate ads begin -->
<span id="1516072">
					<video width="864" height="1536" style="cursor:pointer"
           poster="//a.impactradius-go.com/display-clicktoplayimage/1516072.png"
           onclick="if(!this.playClicked){this.play();this.setAttribute('controls',true);this.playClicked=true;}">
	   <source src="//a.impactradius-go.com/display-ad/16446-1516072">
	   <img src="//a.impactradius-go.com/display-clicktoplayimage/1516072.png" style="border: none; height: 100%; width: 100%; object-fit: contain">
	</video>
	<div style="width:540px;text-align:center"><a href="javascript:window.open(decodeURIComponent('https%3A%2F%2Flaganoo.pxf.io%2Fc%2F5597632%2F1516072%2F16446'), '_blank');void(0);">Click here</a></div>
</span>
<img height="0" width="0" src="https://imp.pxf.io/i/5597632/1516072/16446" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

As a best practice it’s also important to remove the firewall rule during the uninstallation. For that, it means we need another Custom Action and a different VBScrit to remove our rule. The VBScript code is:

Dim WshShell
Set WshShell = CreateObject("Wscript.Shell")
WshShell.Run "netsh.exe advfirewall firewall delete rule name=HelloWorld"

Copy

After that, follow the same exact steps as above and configure the custom action as following:

![configure the custom action](https://cdn.advancedinstaller.com/img/configure-firewall-rules-with-custom-actions/remfwCA.png "configure the custom action")  

<!-- affiliate ads begin -->
<a href="https://appsumo.8odi.net/c/5597632/2111968/7443" target="_top" id="2111968">
  <img src="//a.impactradius-go.com/display-ad/7443-2111968" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://appsumo.8odi.net/i/5597632/2111968/7443" style="position:absolute;visibility:hidden;" border="0" />
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

<!-- affiliate ads begin -->
<a href="https://review-au.sjv.io/c/5597632/2098701/14409" target="_top" id="2098701">
  <img src="//a.impactradius-go.com/display-ad/14409-2098701" border="0" alt="https://techidaily.com" width="120" height="90"/>
</a>
<img height="0" width="0" src="https://review-au.sjv.io/i/5597632/2098701/14409" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

To also add the remove firewall PowerShell script, follow the same steps as above and do the following configurations:

![remove firewall PowerShell script](https://cdn.advancedinstaller.com/img/configure-firewall-rules-with-custom-actions/remfwPSCA.png "remove firewall PowerShell script")  

<!-- affiliate ads begin -->
<a href="https://unicoeye.pxf.io/c/5597632/2134490/18498" target="_top" id="2134490">
  <img src="//a.impactradius-go.com/display-ad/18498-2134490" border="0" alt="https://techidaily.com" width="728" height="90"/>
</a>
<img height="0" width="0" src="https://unicoeye.pxf.io/i/5597632/2134490/18498" style="position:absolute;visibility:hidden;" border="0" />
<!-- affiliate ads end -->

### Firewall rules with Advanced Installer

If you don’t like to code, Advanced Installer made it much simpler to add firewall rules. First, navigate to the [Windows Firewall](https://tools.techidaily.com/advancedinstaller/products/)[page](https://tools.techidaily.com/advancedinstaller/products/).

Next, click on **New Rule**. This will open a new window in which you can define the necessary details for your exception:

![Windows Firewall page](https://cdn.advancedinstaller.com/img/configure-firewall-rules-with-custom-actions/advfw.png "Windows Firewall page")  

As you can see, you can easily choose the direction, display name, program path, protocol and other settings directly from the GUI. In our case we wanted to mimic the above usages of netsh and PowerShell and left everything as before in the GUI.

And that is it, Advanced Installer will automatically create the exception during the installation and during the uninstallation it will remove the exception from the firewall, not needing to create two separate actions for it.

![remove the exception from the firewall](https://cdn.advancedinstaller.com/img/configure-firewall-rules-with-custom-actions/advfw2.png "remove the exception from the firewall")  

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
<li><a href="https://digital-screen-recording.techidaily.com/new-advanced-strategies-for-capturing-fb-chats-for-2024/"><u>[New] Advanced Strategies for Capturing FB Chats for 2024</u></a></li>
<li><a href="https://fox-cloud.techidaily.com/new-in-2024-how-to-add-and-record-audio-to-powerpoint/"><u>[New] In 2024, How to Add & Record Audio to PowerPoint</u></a></li>
<li><a href="https://youtube-blog.techidaily.com/n-2024-imovie-clip-integration-into-youtubes-vast-network/"><u>[New] In 2024, IMovie Clip Integration Into YouTube's Vast Network</u></a></li>
<li><a href="https://facebook-video-footage.techidaily.com/updated-how-to-delete-comments-from-youtube-with-minimal-hassle/"><u>[Updated] How to Delete Comments From YouTube with Minimal Hassle</u></a></li>
<li><a href="https://win-updates.techidaily.com/convert-and-enjoy-movies-on-ipod-touch-effortless-video-format-modification-tools/"><u>Convert and Enjoy Movies on iPod Touch: Effortless Video Format Modification Tools</u></a></li>
<li><a href="https://win-updates.techidaily.com/convert-blu-ray-movies-into-playstation-3-compatible-format/"><u>Convert Blu-Ray Movies Into PlayStation 3 Compatible Format</u></a></li>
<li><a href="https://win-updates.techidaily.com/exploring-the-ins-and-outs-of-msi-academy/"><u>Exploring the Ins and Outs of MSI Academy</u></a></li>
<li><a href="https://mondly-stories.techidaily.com/finding-common-ground-beyond-words-in-couples/"><u>Finding Common Ground Beyond Words in Couples</u></a></li>
<li><a href="https://location-social.techidaily.com/how-to-leave-a-life360-group-on-honor-magic-6-without-anyone-knowing-drfone-by-drfone-virtual-android/"><u>How To Leave a Life360 Group On Honor Magic 6 Without Anyone Knowing? | Dr.fone</u></a></li>
<li><a href="https://win-updates.techidaily.com/repackaging-strategies-revitalizing-your-clickonce-software/"><u>Repackaging Strategies: Revitalizing Your ClickOnce Software</u></a></li>
<li><a href="https://win-updates.techidaily.com/step-by-step-guide-restore-your-data-using-the-top-rated-lg-optimus-g-pro-recovery-software/"><u>Step-by-Step Guide: Restore Your Data Using the Top Rated LG Optimus G Pro Recovery Software</u></a></li>
<li><a href="https://instagram-videos.techidaily.com/the-top-10-stealthy-story-audiences/"><u>The Top 10 Stealthy Story Audiences</u></a></li>
<li><a href="https://techno-recovery.techidaily.com/unlock-the-potential-of-microsofts-bing-imagination-engine-a-step-by-step-guide-to-crafting-ideal-pictures/"><u>Unlock the Potential of Microsoft's Bing Imagination Engine: A Step-by-Step Guide to Crafting Ideal Pictures</u></a></li>
<li><a href="https://win-howtos.techidaily.com/windows-10-error-code-0x80070426-quick-fixes-and-tips/"><u>Windows 10 Error Code 0X80070426: Quick Fixes & Tips</u></a></li>
</ul></div>

