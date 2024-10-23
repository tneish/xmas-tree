# xmas-tree

milkdrop -> spout -> neopixel array capture --wifi (RTP)--> neopixel driver (in tree)

**Milkdrop**
Presets for 200 pixels on a tree.. [1]

**Spout**
https://leadedge.github.io/spout-projects.html

**Time-sync**
RTP/Airplay server [2]

**neopixel array capture**
Spout receiver [5]

**Bandwidth**
4 strings * 50 pixels = 200 pixels
24bits per pixel * 200 pixels = 4.8kb (600B)  [4]
14+20+8+12 Eth/IP/UDP/RTP overhead = 654B
1Mbit WiFi PHY * 70% (wifi overhead) = 700kbps =~ 7.5ms per frame (~130fps)

**neopixel driver in tree**
Needs RTP (airplay server) [2]
RPi Pico W fast enough? [3]


------
[1] Milkdrop
https://github.com/mvsoft74/BeatDrop

https://github.com/milkdrop2077/MilkDrop3/tree/main
(based on BeatDrop)

https://github.com/leadedge/BeatDrop
(BeatDrop with Spout integration)

https://github.com/OfficialIncubo/BeatDrop-Music-Visualizer
(BeatDrop with Spout integration - updated)

https://github.com/projectM-visualizer/
https://sourceforge.net/projects/milkdrop2/

Writing milkdrop presets 
https://web.archive.org/web/20130825023759/http://www.milkdrop.co.uk/guide.htm#gettingstarted
https://www.geisswerks.com/milkdrop/milkdrop_preset_authoring.html

[2]
https://nto.github.io/AirPlay.html#audio-rtpstreams
https://github.com/mikebrady/shairport-sync
http://www.tuneblade.com/


[3] RPi Pico W speeds
https://forums.raspberrypi.com/viewtopic.php?t=339512

[4]
https://learn.adafruit.com/adafruit-neopixel-uberguide/advanced-coding

[5]
https://github.com/leadedge/ofSpoutDemo
