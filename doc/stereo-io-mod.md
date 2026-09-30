# Stereo I/O Mod (optional)

A stock Audrey II has two mono output jacks and no audio input. The firmware does
listen to the Daisy Seed audio inputs though: left and right are summed and fed
into the feedback loop alongside the internal noise. If nothing is connected to
the inputs, nothing changes.

So adding an input is a hardware-only mod. Two common approaches:

1. **Add one TRS input jack on the side (easiest).** Keep the existing mono
   outputs and mount a panel-mount stereo (TRS) jack in the side of the case.
   It doesn't touch the matrix, so it only needs three wires:
   - Tip (Left) → Synthux pin 16
   - Ring (Right) → Synthux pin 17
   - Sleeve → GND

   A mono (TS) cable also works: it simply feeds the left input.
2. **Swap the two mono jacks for TRS jacks.** Desolder the original mono jacks
   and replace them with stereo Thonkiconns (PJ366ST), giving one stereo output
   and one stereo input on the same footprint.

The audio pins 16–19 are on the side of the Daisy where the Synthux pin
numbers match the Seed pin numbers.

## Option 2 on the Designer PCB: what changes

> **Fit warning:** the stereo Thonkiconn (PJ366ST) does not sit in exactly the
> same place as the original mono jack, so the centre of the jack ends up
> slightly off from the original hole. This mod has not been tested with the
> official Audrey II faceplate. Check the alignment before soldering, and be
> ready to enlarge the panel holes slightly if needed.

On the Designer PCB each jack footprint sits in a matrix slot. A slot's data pad
is wired from the numbered pin at the bottom of its column to a Synthux pin.
A TRS jack's Ring has its own isolated pad, which you bridge to the data pad of
the unused slot next to it. That slot's pin is then wired to the Daisy like any
other.

| Jack | Signal      | Jack pin | Matrix slot      | Synthux pin | Stock build     |
| :--- | :---------- | :------- | :--------------- | :---------- | :-------------- |
| Out  | Left Out    | Tip      | 76               | 18          | 76 → 18 (keep)  |
| Out  | Right Out   | Ring     | 71 (bridged)     | 19          | was 77 → 19     |
| Out  | Ground      | Sleeve   | neighbouring GND | –           | –               |
| In   | Left In     | Tip      | 77               | 16          | –               |
| In   | Right In    | Ring     | 72 (bridged)     | 17          | –               |
| In   | Ground      | Sleeve   | neighbouring GND | –           | –               |

In short, once the two TRS jacks are fitted in slots 76 and 77:

- **Bridge 2 pads:** Ring pad of 76 → slot 71, and Ring pad of 77 → slot 72.
  Short jumper wires on the back of the PCB work well.
- **Move 1 wire:** the existing wire from 77 → 19 moves to 71 → 19.
  The 76 → 18 wire stays as it is.
- **Add 2 wires:** 77 → 16 and 72 → 17.
- **Ground:** the Thonkiconn's long Sleeve pin can be bent over to reach the GND
  pad of the neighbouring footprint and soldered there. No extra ground wire
  is needed.

For the full step-by-step guide with photos (desoldering tips, the routing
diagram, bridging and the ground mod), see
[Audio I/O Mod: Upgrading to Stereo TRS](https://github.com/jonwaterschoot/Feedback-Gardenscpr-for-Synthux-Audrey-II#audio-io-mod-upgrading-to-stereo-trs)
by Jon Waterschoot.

> Input level: the summed input is added straight into the feedback loop, so a
> hot stereo source can drive it harder than a mono one. Start with the source
> volume low.
