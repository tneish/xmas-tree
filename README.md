# xmas-tree

Click the Youtube link below to see a demonstration.

[![Youtube video of Xmas tree 2024 - Avicii](http://img.youtube.com/vi/vdlD6q25GiM/0.jpg)](http://www.youtube.com/watch?v=vdlD6q25GiM "Xmas tree 2024 - Avicii")

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

### Delay & Jitter Compensation
There is a configurable delay in the headend (up to 2secs due to memory in RPi Pico receiver, default 0 secs).
If used, audio needs to be delayed with the same value.
Audio can be delayed for local playback at the head-end, or cast using e.g. Airplay with a jitter buffer targeting the same delay.
"Frames" will be timestamped on the headend and queued on the Pico, waiting to be displayed.
The delay should be large enough to cover WiFi delay + jitter.
Headend keeps a rolling window of delay samples (~20seconds) to compensate for WiFi delay (to get as close to configured delay as possible, to sync with audio delay).

The compensation mechanism worked OK with RPi4 as neopixel receiver but with the RPi Pico there seems to be some inaccuracies with the clocking I haven't yet bothered to investigate.

In practice my WiFi delay + jitter has been low enough to set the delay to 0 and avoid delaying audio playback.

