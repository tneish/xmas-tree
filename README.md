# xmas-tree

## Headend
Headend is [OfficialIncubo/BeatDrop-Music-Visualizer](https://github.com/OfficialIncubo/BeatDrop-Music-Visualizer)

(BeatDrop with Spout integration - updated). Can use Milkdrop plugins and code 'shaders' in real-time. Nice!

With [tneish/spout_receiver](https://github.com/tneish/spout_receiver)

(Uses Processing 4 to receive from Spout, then captures 200 pixels in a 'tree shape' and sends them over the network)

## In-tree
Raspberry Pi Pico W running CircuitPython, [rpi_pico_neopixel_receiver](https://github.com/tneish/rpi_pico_neopixel_receiver).

(Receives pixel RGBW values from headend and displays them on Neopixels)

I tried first with an RPi4 using SMI (secondary memory interface) (see [tneish/rpi_neopixel_smi](https://github.com/tneish/rpi_neopixel_smi)) but there was too much jitter/interference from the OS and drivers messing with the SMI transfers.

Note RPi dropped SMI starting with RPi 5, and RPi OS starting with Bookworm runs many upstream kernel drivers in ARM which mess even more with DMA/SMI so it's a dead-end.

RPi Pico W (RP2040) with WiFi and PIOs is much more suited.


### Bandwidth
160-180kbps for 200 pixels at ~30fps.

RPi Pico W with Circuitpython and PIOs works just fine.
