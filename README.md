# dell-5510-OSX
MacOS clover boot
# Installation
Add the node under to the CLOVER/config.plist/Devices(4k needed)
```
 <key>FakeID</key>
 <dict>
     <key>IntelGFX</key>
     <string>0x12345678</string>
 </dict>
```
# AfterInstallation
* to enable 4K display with hd530
run command 
```
sudo perl -i.bak -pe 's|\xB8\x01\x00\x00\x00\xF6\xC1\x01\x0F\x85|\x33\xC0\x90\x90\x90\x90\x90\x90\x90\xE9|sg' /System/Library/Frameworks/CoreDisplay.framework/Versions/Current/CoreDisplay
sudo codesign -f -s - /System/Library/Frameworks/CoreDisplay.framework/Versions/Current/CoreDisplay
```
remove /CLOVER/config.plist/Devices/FakeId to unlimit hd530 graphic memory
* To better HWP configuration
modify `/System/Library/Extensions/IOPlatformPluginFamily.kext/Contents/PlugIns/X86PlatformPlugin.kext/Contents/Resources/Mac-A5C67F76ED83108C.plist`
to be the same as 
`AfterInstallation/Mac-A5C67F76ED83108C.plist`

