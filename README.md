# Introduction
I've recently had some issues with my checkra1n jailbreak and I thought I'd share my experience and how I fixed my problems.

*Typos and various errors are expected. If noticed please open an issue or create a PR. Especially if it's an issue with any Suggested Tweak's pricing.*

*If you have any suggestion, please open an issue.*

#### Information on my device
+ Device: iPhone X GSM
+ Version: iOS 14.4
+ Jailbreak: checkra1n 0.12.4 beta (latest)

# Issues
## Stuck in "Right before trigger" and black screen
I've had an issue using checkra1n-cli 0.12.3 on Linux which caused my terminal to freeze on "Right before trigger (this is the real bug setup)" and caused my phone to go completely black.

Holding the power button didn't work and unplugging it from my computer didn't either.

Luckily, though, the device is not bricked or compromised in any way! All you need to do is [force restart the phone](https://support.apple.com/en-gb/guide/iphone/iph8903c3ee6/ios)

## Stuck in DFU (Recovery Mode)
I once started the jailbreak process on Linux and it gave up on me. It outright decided to not detect that my phone entered DFU mode, so it got stuck.

The only advice I could find online was to [force restart my phone](https://support.apple.com/en-gb/guide/iphone/iph8903c3ee6/ios), which I’d already tried multiple times.
What actually worked for me, though, was using a third party application to get me out of DFU.

The application that I'd used is called [iMazing](https://imazing.com/guides/how-to-get-iphone-ipad-out-of-recovery-mode). I was pretty skeptical and thought that it'd be hiding the "Exit DFU mode" button behind a paywall like other apps, but it didn't. I hit the button, the phone restarted and I was out of the DFU loop.

Someone also suggested [this](https://www.eelphone.com/solution/ipad-recovery-mode.html) application in [this comment](https://github.com/checkra1n/BugTracker/issues/462#issuecomment-607635760) on an issue in checkra1n's BugTracker which, allegedly, does the same and is free as well.

## Tweaks interacting with the SpringBoard and more suddenly not working / No tweak settings in the Settings app
I’ve not found an actual fix for this, yet. I’ve only had this issue once and I’ve tried pretty much everything but I, unfortunately, had to "Restore" my system, which is not a factory reset, it's checkra1n's way to say removing all the tweaks and restoring the rootfs (removing the jailbreak completely)

I have, though, opened an [issue](https://github.com/checkra1n/BugTracker/issues/2153) on checra1n's BugTracker, hopefully it'll be picked up at some point.

I must say that doing this actually kept all of my tweaks settings, for some reason, so every time I installed a tweak it would already be set up the way it was before restoring (even repos inside of Cydia and Zebra).

That being said, you should [back up your tweaks](#backing-your-tweaks-up) and your [repos](#backing-up-your-repos), just to be safe.

Here’s some things that you may try before completely removing your jailbreak.

⚠️ *Backup your repos and tweaks before trying these.* ⚠️

+ Reinstalling PreferenceLoader (or installing it if missing)
+ Downgrading PreferenceLoader
+ Reinstalling Cydia Substrate
+ Downgrading Cydia Substrate
+ Reinstalling Cydia Safemode Substrate
+ Downgrading Cydia Safemode Substrate
+ Installing RespringCacheFix
+ https://www.reddit.com/r/jailbreak/comments/dwgkzg/tutorial_how_to_fix_tweaks_not_showing_in/ (and comments)

## Restore error: General
I've had this issue when trying to fix [another issue](#stuck-in-dfu-(recovery-mode)), which then lead to [Yet Another Issue](#stuck-in-"right-before-trigger"-and-black-screen), yay.

The fix to this issue is rather easy, all you have to do is connect your phone to a machine that can run checkra1n and rejailbreak like you usually would but this time tick the "Safe Mode" box.

![Safe Mode Box Ticked Image](https://i.imgur.com/LW7PYQT.png)

----

# How-To
In this section I will explain how to do specific things like backing your repositories and tweaks up.

## Backing your repos up
Backing your repositories up is really simple, if you have [Zebra](https://getzbra.com/).

*As far as I know restoring repositories with Zebra won't bring them back to Cydia!*

Every time you launch Zebra it will check for changes in Cydia's repositories (and other managers as well, such as Installer) and ask you if you want to get the new repositories, you just confirm and all the repositories from Cydia will now be in Zebra as well.

All that's left to do is the following:
1. Head over to Zebra's Sources section
2. Tap "Edit" in the top right corner
3. Tap the Share button in the top left corner
4. You can now save the file with Files, Filza (not recommended if you plan on restoring your phone as you most probably won't be able to access that location without Filza) or even send it on instant messaging apps such as WhatsApp or Telegram.

*To save with Files or Filza scroll down and press "Save to Files" or "Save to Filza"*

Once that's done you're good to go!

## Restoring your repos
Restoring your repos is even easier than [backing them up](#backing-up-your-repos)! You will still need [Zebra](https://getzbra.com/) for this process, though.

All you need to do is find your "sources" file, whether you saved it with Files, sent it on Telegram or saved it in the cloud.
Most of the times to open the file with another app you can simply press it and hold down until a menu pops up, you either tap "Open with" or "Share", then you scroll the second row until the end, tap "More" and tap "Zebra".

*In the case of Telegram it's even easier, you tap on it, it's going to open the file, you tap on the share icon in the top right corner and do the same as above.*

Once that's done all your repositories will be back inside of Zebra.

Unfortunately there's no method that I'm aware of to copy your repositories from Zebra to Cydia like you can do the other way around, so you might be stuck with Zebra.

## Backing your tweaks up
I'm afraid the best that can be done without access to the Terminal, as of now, is saving all your tweak names. Tweaks settings seems to be stored like system settings (don't quote me on that) which means they will be kept if you restore your system, meaning removing the jailbreak, NOT factory reset, but you probably can't save them and share them around as files.

To save your tweak names you either need [Zebra](https://getzbra.com/) or to take many screenshots.

### Zebra Method
1. Open Zebra
2. Tap on Packages
3. Tap the Share button on the top left corner
4. I've had no luck with uploading my list directly to Telegram, so I gave up to saving it as a file on my phone tapping on "Save to Files". (Saving to Filza is probably not a good idea, as you would probably not be able to access that folde through Files in the future)

### Terminal Script method
If you want to save your tweaks in a way that makes it easier to restore them and have access to the terminal on your device and to internet then you can use [this script](https://github.com/My-ThrowAwayAccount/Scripts/blob/main/TweaksBackup/TweaksBackup.sh) that I've created.

You can run this command to download and execute the script automatically.
```sh
wget -Nnv https://raw.githubusercontent.com/My-ThrowAwayAccount/Scripts/main/TweaksBackup/TweaksBackup.sh && bash TweaksBackup.sh
```
Typing "1" twice, the first time to agree running the script (after reading carefully the warning message) and the second time to back your packages (and tweaks) up

## Restoring your tweaks
Restoring your tweaks depends on the way you've saved them. 

### Zebra/Screenshots Method
If you've taken screenshots or saved a list with Zebra all you have to do is open any tweak manager (Cydia, Zebra, Installer, Sileo, etc.) and manually install the tweaks.
*Keep in mind that some are libraries or dependencies and will be installed automatically when installing the tweaks that need them*

### Terminal Script method
If you've used [my script](https://github.com/My-ThrowAwayAccount/Scripts/blob/main/TweaksBackup/TweaksBackup.sh) to back your tweaks up, though, you will need to run it again and type "1" and "2". The first time to agree on running the script (after reading carefully the warning message) and the second time to reinstall the packages (and tweaks).

You can run this command to download and execute the script automatically.
```sh
wget -Nnv https://raw.githubusercontent.com/My-ThrowAwayAccount/Scripts/main/TweaksBackup/TweaksBackup.sh && bash TweaksBackup.sh
```

----

# Suggested Tweaks
There are some tweaks that I found useful and I would like to suggest them here.


| Name                                                                                                         	| Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                	| Price 	|
|--------------------------------------------------------------------------------------------------------------	|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|-------	|
| [Shuffle](https://www.ios-repo-updates.com/repository/creaturesurvive-s/package/com.creaturecoding.shuffle/) 	| The most important feature of this tweak, at least for me, is that it creates 3 settings inside of the Settings app:<br>Tweaks, Apps and System Apps.<br>These settings are grouped and at the top of the Settings, allowing for easy access.<br>The tweaks, apps and system apps are then removed from the bottom of the Settings.                                                                                                                                                                                                                                                                                                                                                                                                                                        	| Free  	|
| [Barmoji](https://repo.packix.com/package/com.cpdigitaldarkroom.barmoji/)                                    	| This tweak makes use of the empty bar under the keyboard in newer devices to show some emojis.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             	| Free  	|
| [Evil Scheme](https://repo.dynastic.co/package/evilscheme)                                                   	| This tweak makes it possible to override defaults when doing certain actions.<br>It can override the mail client, the package manager and even the default browser!<br>You might say it's not a big deal, since that has been here for a while. But this behaviour is shown in Spotlight too!<br>Meaning that whenever you search for something using Spotlight (the bar that appears scrolling down in the home screen)<br>the default app will no longer be Safari, but the browser that you prefer.<br>This actually supports custom apps and more.                                                                                                                                                                                                                     	| Free  	|
| [PowerModule](https://repo.packix.com/package/com.muirey03.powermodule/)                                     	| This is the best Control Centre addition that I've ever used. It doesn't add too much but it's very useful.<br>It lets me respring my device with just one button. And if I want to be sure to not accidentally do it a confirmation box can be enabled.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   	| Free  	|
| [BioProtect XS](https://limneos.net/bioprotectxs/)                                                           	| This tweak lets you set a passcode for specific apps.<br>You could also use Touch ID or Face ID, too, but I find this especially useful as iPhone Xs can't have passcodes when jailbroken with checkra1n.<br>So I can passcode protect basically every application on my phone.<br>A session can be enabled through the tweak's settings, meaning that if I type my passcode once I won't need to do it again until I lock my screen.<br>A way to quickly re-lock without locking your screen is by adding the control to the Control Centre.<br>Another useful feature is that this can actually block Settings pages and Control Centre controls, too.<br>Meaning that as long as the phone is jailbroken I can block the wifi section off with a passcode, for example. 	| $2.29 	|
| [AppStore++](https://cokepokes.github.io/depiction/appstoreplus.html)                                        	| This tweak lets you downgrade applications as well as block updates for them (on an app-per-app basis).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    	| Free  	|
| [NewTerm 2](https://chariz.com/get/newterm)                                                                  	| This tweak works on iOS 14 and lets you have a local terminal right on your phone.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         	| Free  	|
| [OpenSSH](https://www.ios-repo-updates.com/repository/cydia-telesphoreo/package/openssh/)                    	| This tweak creates an SSH server listening on port 22, allowing you to execute SSH commands from your computer, controlling your phone. Managing tweaks and more.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          	| Free  	|
| [Cr4shed](https://repo.packix.com/package/com.muirey03.cr4shed/)                                             	| This tweak will notify you whenever an application crashes and many times will even be able to tell you what caused the crash.<br>If it can't you'll have a useful error message to send the app developer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                	| Free  	|
| [iCleaner](https://ib-soft.net/)                                                                             	| This tweak will clean up space on your phone.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              	| Free  	|
| [Filza](https://www.ios-repo-updates.com/repository/tigisoftware/package/com.tigisoftware.filza/)            	| This is one of the most known file manager and, in my opinion, one of the best.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            	| Free+ 	|
