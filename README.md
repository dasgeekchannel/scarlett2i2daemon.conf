# scarlett2i2daemon.conf
This is a configuration to remove random static and interference from Scarlett 2i2 in Linux. Edit /etc/pulse/daemon.conf

Test in Arch Linux and Ubuntu 18.04+

This configuration has fixed the random static noise that would occur when opening one or more applications that grabbed microphone or audio like Zoom, Telegram, OBS, Mumble etc.

You can use this file as a guide to set your Scarlett 2i2 Interface Up and make the changes to your file manually (please backup your daemon.conf first). Or you can backup your current daemon.conf and replace it with this file.

Please note that you need to remove the ';' in front of the lines you change if you do it manually. Otherwise the lines will be ignored. 

This is all thanks in part to the Arch wiki which provided some of these configs. If you have other configs that worked please submit them. https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Static_noise_when_using_headphones
The other changes I've made are through trial and error and some random config files I found in forums for other devices. I finally found a balance of quality sound and static free. I hope this helps.

Type $ sudo nano /etc/pulse/daemon.conf
*Note you can substitute nano for vi or vim if you're awesome enough

Make the changes you see here on Github in the daemon.conf file to your daemon.conf file. 
Save and restart computer
Success

## Get Settings Manually for 'Other' USB Interface Devices like PreSonus, etc.
- Run this command: $ pactl list sinks
- You will see a list of 'all' audio interfaces. Scroll through terminal to find 'Name' that matches the interface you're configuring (Example: Scarlett, PreSonus)
- Output pactl list sinks command to a text file if it helps. $ pactl list sinks > audio.txt to output to a txt file. 
- In the pactl list sinks output look for "Sample Specification" 
- As an example for PreSonus Studio 2/4 it shows:
  - s32le 2ch 96000hz
- Make a copy of your current daemon.conf in case you mess anything up.
- Next open editor for daemon.conf (Ex: sudo nano /etc/pulse/daemon.conf)
- Head to section of daemon.conf (default-sample-format = , default-sample-rate =, alternate-sample-rate =, default-sample-channel =
- Edit those sections listed above to match the output in Sample Specification. 
(Example PreSonos 2/4)
- default-sample-format = s32le
- default-sample-rate = 96000
- alternate-sample-rate = 44100 *note this is not from output file but generic alternate to use.
- default-sample-channels = 2

# Additional changes
-default-fragments = 2
-default-fragement-size-msec = 250

- CTRL + X to save changes to file.
- Reboot
- Success
