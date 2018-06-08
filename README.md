# Dell-Precision-5510-OSX
* Dell-Precision-5510 i7-6820HQ HD530 16G-DDR4 4k-Screen Sata3-SSD-512G DELL-DW1560  
* currently on macOS High Sierra (Version 10.13.5) ([For high sierra, take a look here](https://github.com/scottsanett/M5510-4K-High-Sierra-Installation))
* This repo is based on
[darkhand repo](https://github.com/darkhandz/XPS15-9550-Sierra)  
* [darkhand's old README.md](https://github.com/darkhandz/XPS15-9550-Sierra/tree/fffd216d05be57256c2aac7ddafacb343bad0e69)  
# Attention!
* Now using OsxAptioFix2Drv-64.efi
* You have to go through some steps if you want to boot, please check [here](https://github.com/wmchris/DellXPS15-9550-OSX/blob/master/Tutorial_10.12_Step7.md#osx-doesnt-boot-anymore-after-firmware-upgrade-to-1225-or-higher) 
# Installation(redo before every update)
* Add the node under to the CLOVER/config.plist/Devices(Enable it to boot)
```XML
 <key>FakeID</key>
 <dict>
     <key>IntelGFX</key>
     <string>0x12345678</string>
 </dict>
```
