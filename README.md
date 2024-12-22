# xmas-tree

## Headend
Headend is [OfficialIncubo/BeatDrop-Music-Visualizer](https://github.com/OfficialIncubo/BeatDrop-Music-Visualizer)

(BeatDrop with Spout integration - updated). Can use Milkdrop plugins and code 'shaders' in real-time. Nice!

With [tneish/spout_receiver](https://github.com/tneish/spout_receiver)

(Uses Processing 4 to receive from Spout, then captures 200 pixels in a 'tree shape' and sends them over the network)

## In-tree
Raspberry Pi Pico W running CircuitPython, [rpi_pico_neopixel_receiver](https://github.com/tneish/rpi_pico_neopixel_receiver).

(Receives pixel RGBW values from headend and displays them on Neopixels)


### Bandwidth
160-180kbps for 200 pixels at ~30fps.

RPi Pico W with Circuitpython and PIOs works just fine.
