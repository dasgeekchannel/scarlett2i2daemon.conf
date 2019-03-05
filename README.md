# scarlett2i2daemon.conf
This is a configuration to remove random static and interference from Scarlett 2i2 in Linux. Edit /etc/pulse/daemon.conf

This configuration has fixed the random static noise that would occur when opening one or more applications that grabbed microphone or audio like Zoom, Telegram, OBS, Mumble etc.

You can use this file as a guide to set your Scarlett 2i2 Interface Up and make the changes to your file manually (please backup your daemon.conf first). Or you can backup your current daemon.conf and replace it with this file.

Please note that you need to remove the ';' in front of the lines you change if you do it manually. Otherwise the lines will be ignored. 

This is all thanks in part to the Arch wiki which provided some of these configs. If you have other configs that worked please submit them. https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Static_noise_when_using_headphones

Type $ sudo nano /etc/pulse/daemon.conf
*Note you can substitute nano for vi or vim if you're awesome enough

Make the changes you see here. 
Save and restart computer
Success
