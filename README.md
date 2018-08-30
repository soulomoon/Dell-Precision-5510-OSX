# Dell-Precision-5510-OSX
* Dell-Precision-5510 i7-6820HQ HD530 16G-DDR4 4k-Screen Sata3-SSD-512G (and Samsung SSD 960 EVO 500GB) DELL-DW1560  
* currently on macOS High Sierra (Version 10.13.5)
* This repo is based on
[scottsanett repo](https://github.com/scottsanett/M5510-4K-High-Sierra-Installation)   
# Installation(redo before every update)
* Add the node under to the CLOVER/config.plist/Devices(Enable it to boot)(After full installation, you may remove it again, since this set the memory usage of Intel graphic card to 31m)
```XML
 <key>FakeID</key>
 <dict>
     <key>IntelGFX</key>
     <string>0x12345678</string>
 </dict>
```
# HDMI
Inorder for hdmi to be able to output, you should add   
```
				<key>Mac-A5C67F76ED83108C</key>
				<string>none</string>
```  
under `ConfigMap->dict` in `/System/Library/Extensions/AppleGraphicsControl.kext/Contents/PlugIns/AppleGraphicsDevicePolicy.kext/Contents/Info.plist`  
and rebuild kext cache using 
`sudo kextcache -i /`  
