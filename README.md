# Dell-Precision-5510-OSX
* Dell-Precision-5510 i7-6820HQ HD530 16G-DDR4 4k-Screen Sata3-SSD-512G (and Samsung SSD 960 EVO 500GB) DELL-DW1560  
* currently on macOS Mojave (Version 10.14)
* This repo is based on
[scottsanett repo](https://github.com/scottsanett/M5510-4K-High-Sierra-Installation) and 
[darkhand repo](https://github.com/darkhandz/XPS-9550-Mojave)

# HDMI
Inorder for hdmi to be able to output, you should add   
```
				<key>Mac-A5C67F76ED83108C</key>
				<string>none</string>
```  
under `ConfigMap->dict` in `/System/Library/Extensions/AppleGraphicsControl.kext/Contents/PlugIns/AppleGraphicsDevicePolicy.kext/Contents/Info.plist`  
and rebuild kext cache using 
`sudo kextcache -i /`  
