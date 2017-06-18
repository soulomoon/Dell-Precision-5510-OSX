# Dell-Precision-5510-OSX
Dell-Precision-5510 i7-6820HQ HD530 16G-DDR4 4k-Screen Sata3-SSD-512G DELL-DW1560  
This repo is based on
[darkhand repo](https://github.com/darkhandz/XPS15-9550-Sierra)  
[darkhand's old README.md](https://github.com/soulomoon/XPS15-9550-Sierra)  
# Installation(redo before every update)
Add the node under to the CLOVER/config.plist/Devices(Enable it to boot)
```
 <key>FakeID</key>
 <dict>
     <key>IntelGFX</key>
     <string>0x12345678</string>
 </dict>
```
# AfterInstallation
## More kext
copy `AfterInstallation/MoreKexts-LE` to `/Library/Extensions/`  
run `AfterInstallation/MoreKexts-LE/VoodooPS2Daemon/_install.command`  
then run command to rebuild the whole kextcache  
```
sudo rm -rf /System/Library/Caches/com.apple.kext.caches/Startup/kernelcache
sudo rm -rf /System/Library/PrelinkedKernels/prelinkedkernel
sudo touch /System/Library/Extensions && sudo kextcache -u /
```

## To enable 4K display with hd530(redo after every update)
run command   
```
sudo perl -i.bak -pe 's|\xB8\x01\x00\x00\x00\xF6\xC1\x01\x0F\x85|\x33\xC0\x90\x90\x90\x90\x90\x90\x90\xE9|sg' /System/Library/Frameworks/CoreDisplay.framework/Versions/Current/CoreDisplay
sudo codesign -f -s - /System/Library/Frameworks/CoreDisplay.framework/Versions/Current/CoreDisplay
```
remove /CLOVER/config.plist/Devices/FakeId to unlimit hd530 graphic memory
## To better HWP configuration(you should root to do it)
modify  
`/System/Library/Extensions/IOPlatformPluginFamily.kext/Contents/PlugIns/X86PlatformPlugin.kext/Contents/Resources/Mac-A5C67F76ED83108C.plist`
to be the same as  
`AfterInstallation/Mac-A5C67F76ED83108C.plist`  
run command to rebuild kextcache  
`sudo touch /System/Library/Extensions && sudo kextcache -u /`

