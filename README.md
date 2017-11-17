# Dell-Precision-5510-OSX
* Dell-Precision-5510 i7-6820HQ HD530 16G-DDR4 4k-Screen Sata3-SSD-512G DELL-DW1560  
* currently on macOS Sierra (Version 10.12.6) ([For high sierra, take a look here](https://github.com/scottsanett/M5510-4K-High-Sierra-Installation))
* This repo is based on
[darkhand repo](https://github.com/darkhandz/XPS15-9550-Sierra)  
* [darkhand's old README.md](https://github.com/darkhandz/XPS15-9550-Sierra/tree/fffd216d05be57256c2aac7ddafacb343bad0e69)  
# Attention!
* Check if your bios version is 1.2.21
* You have to go through some steps if you want to boot in version 1.2.25 and above, please check [here](https://github.com/wmchris/DellXPS15-9550-OSX/blob/master/Tutorial_10.12_Step7.md#osx-doesnt-boot-anymore-after-firmware-upgrade-to-1225-or-higher) 
# Installation(redo before every update)
* Add the node under to the CLOVER/config.plist/Devices(Enable it to boot)
```XML
 <key>FakeID</key>
 <dict>
     <key>IntelGFX</key>
     <string>0x12345678</string>
 </dict>
```
# AfterInstallation
## More kext
* copy `AfterInstallation/MoreKexts-LE/LE` to `/Library/Extensions/`  
* run
```shell
AfterInstallation/MoreKexts-LE/VoodooPS2Daemon/_install.command
```  
* run command to rebuild the whole kextcache  
```shell
sudo rm -rf /System/Library/Caches/com.apple.kext.caches/Startup/kernelcache
sudo rm -rf /System/Library/PrelinkedKernels/prelinkedkernel
sudo touch /System/Library/Extensions && sudo kextcache -u /
```

## Enable HDMI  
adding node under /System/Library/Extensions/AppleGraphicsControl.kext/Contents/PlugIns/AppleGraphicsDevicePolicy.kext/Contents/Info.plist/Information Property List/IOKitpersonalities/AppleGraghicsDevicePolicy/ConfigMap  
```XML
<key>Mac-A5C67F76ED83108C</key>
<string>none</string>

```
To make it work(you may need repeat it after an system update)
```shell
sudo kextcache -u /
```
## To enable 4K display with HD530(would be disable when updating the system, redo it after every update)
* !!!attention:(if you want to update your system, you have to add /CLOVER/config.plist/Devices/FakeId back to where it was, then redo the shell command after update, and remove it again)

* run command   
```shell
sudo perl -i.bak -pe 's|\xB8\x01\x00\x00\x00\xF6\xC1\x01\x0F\x85|\x33\xC0\x90\x90\x90\x90\x90\x90\x90\xE9|sg' /System/Library/Frameworks/CoreDisplay.framework/Versions/Current/CoreDisplay
sudo codesign -f -s - /System/Library/Frameworks/CoreDisplay.framework/Versions/Current/CoreDisplay
```
* remove /CLOVER/config.plist/Devices/FakeId to unlimit hd530 graphic memory

## To better HWP configuration(you should root to do it)
* modify  
`/System/Library/Extensions/IOPlatformPluginFamily.kext/Contents/PlugIns/X86PlatformPlugin.kext/Contents/Resources/Mac-A5C67F76ED83108C.plist`
to be the same as   
`AfterInstallation/Mac-A5C67F76ED83108C.plist`  
* run command to rebuild kextcache  
```shell
sudo touch /System/Library/Extensions && sudo kextcache -u /
```

## BackLight Saving(This solution is invalid in 10.12.6, and the fix is unknown)
see  
[Laptop backlight control using AppleBacklightInjector.kext](https://www.tonymacx86.com/threads/guide-laptop-backlight-control-using-applebacklightinjector-kext.218222/)   
[apple-backlight-injector-brightness-not-saved](https://www.tonymacx86.com/threads/apple-backlight-injector-brightness-not-saved.222952/page-14#post-1516295)  
**Saving and restoring backlight level across restarts**  
You have to turn on Automatically ajust brightness in System Peferences -> Displays

