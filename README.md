# Dell-Precision-5510-OSX
* Dell-Precision-5510 i7-6820HQ HD530 16G-DDR4 4k-Screen Sata3-SSD-512G DELL-DW1560  
* currently on macOS Sierra (Version 10.12.6)
* This repo is based on
[darkhand repo](https://github.com/darkhandz/XPS15-9550-Sierra)  
* [darkhand's old README.md](https://github.com/darkhandz/XPS15-9550-Sierra/tree/fffd216d05be57256c2aac7ddafacb343bad0e69)  
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
* copy `AfterInstallation/MoreKexts-LE` to `/Library/Extensions/`  
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

## BackLight Saving
see  
[Laptop backlight control using AppleBacklightInjector.kext](https://www.tonymacx86.com/threads/guide-laptop-backlight-control-using-applebacklightinjector-kext.218222/)    
**Saving and restoring backlight level across restarts**  
set `config.plist/SystemParameters/BacklightLevel=0`  
to prevent clover insert default value, so you can save yours

