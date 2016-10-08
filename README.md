**Step 1:**

**UEFI:**

Open Disk Utility and select either your USB drive or the drive you are installing Clover on, on the right side select the Partition tab and click the Current layout and change it to 1 partition then click the Options button at the bottom and select GUID Partition Table, name it whatever you want (in the example I named mine as USB) and format it as Mac OS Extended (Journaled).

![](http://ddi.hopto.org:3000/attachments/3c641ace-4202-4dd0-9e45-6fc254f27645)

**Legacy:**
Same way as UEFI except select MBR instead of GUID under options.

You should already have the Install OS X Yosemite.app in your Application folder, right click on it and Show Package Content, navigate to \Content\Resources\ and open terminal and type sudo then drag and drop the createinstallmedia executable from the folder you just navigated to the terminal window then type --volume and drag and drop the USB volume you just formatted to the terminal window then type --applicationpath and drag and drop the Install OS X Yosemite.app from the Applications folder into the terminal window then type --nointeraction, so the complete command you should see in terminal is :
```
sudo /Applications/Install\ OS\ X\ Yosemite.app/Contents/Resources/createinstallmedia --volume /Volumes/USB --applicationpath /Applications/Install\ OS\ X\ Yosemite.app --nointeraction
```

Hit Enter and wait a few minutes for it to say Complete

![](http://ddi.hopto.org:3000/attachments/a3294e64-c782-4a24-a007-9baf1fb6612a)

Now you should have a USB installer created by using the correct method which is Apple's way

![](http://ddi.hopto.org:3000/attachments/64ebe8ba-3ee5-45e9-8868-9d71b9b0c6b5)

**Step 3:**

Now to install Clover (as UEFI) on the USB Installer, download the latest Clover installer from 
http://sourceforge.n.../cloverefiboot/ and open it and click Continue, Click Continue again, Click Change Install Location:

![](http://ddi.hopto.org:3000/attachments/3930c5c8-7779-45fa-869c-1239e39f9392)

Select your USB Installer you just made and click Continue

![](http://ddi.hopto.org:3000/attachments/e26fb5ee-c868-4273-878c-11584549ddbb)

Click Customize and check mark the following 
 
**UEFI Only:**

![](http://ddi.hopto.org:3000/attachments/7bf5ff98-4b74-4dfc-bc8c-1c9a4198b8b0)

and the following

![](http://ddi.hopto.org:3000/attachments/41c8cf3f-5476-4830-99dd-4e13998df79a)

**Legacy Install:**

![](http://ddi.hopto.org:3000/attachments/fec69083-68ab-43bc-868f-7f443193337d)

Click Install and wait for it to finish the install, you will see a EFI volume show up on your desktop

![](http://ddi.hopto.org:3000/attachments/3930c5c8-7779-45fa-869c-1239e39f9392)

![](http://ddi.hopto.org:3000/attachments/e4cf1b7c-42ab-4122-a00d-bd9e15827187)

**Step 4:**

Now its time to add all the kext, patched DSDT (if you use one) and SSDT (if you use one) the required kext is FakeSMC, 10.10 shown in below pic but add a new folder and name it 10.11 for El Captian.

![](http://ddi.hopto.org:3000/attachments/eec69ac6-c232-43d4-ae75-699f371bc419)

**Step 5:**

Now for probably the hardest part for most user is correctly making your Clover config.plist, you can do this multiple way by using Clover Configurator https://www.dropbox....urator.zip?dl=0 by doing it manually by using Xcode or Plist Editor Pro, but do not and I say again do not use texteditor that comes with OS X. using the correct things in your config are going to be different for most users depending on your system specs so I will just provide an example that I use and a link to Clover's wiki for a description for all choices  http://clover-wiki.z...plist-structure.

![](http://ddi.hopto.org:3000/attachments/9bef5174-7afc-41a6-947e-bbbdec9d8eae)

**Additional Step (optional 10.10 only!!!!!):**

If you want to use Disk Utility to mount and dismount the EFI partition for post install and editing your config.plist following these simple steps:

a.) Open terminal and type the following command:
```
defaults write com.apple.DiskUtility DUDebugMenuEnabled 1
```

b.)  Open Disk Utility and click Debug in the menu bar at the top of the screen and Click Show Every Partition.

![](http://ddi.hopto.org:3000/attachments/d6efdf25-44c1-4abe-912c-228954554610)

c.)  Now just highlight the EFI partition on the left side of Disk Utility and click the mount button.

![](http://ddi.hopto.org:3000/attachments/5de1d5af-ba8e-40b9-9b71-256e17c577f3)
