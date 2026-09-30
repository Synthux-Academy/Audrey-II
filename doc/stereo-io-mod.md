# Stereo I/O Mod (optional)

A stock Audrey II has two mono output jacks and no audio input. The firmware does
listen to the Daisy Seed audio inputs though: left and right are summed and fed
into the feedback loop alongside the internal noise. If nothing is connected to
the inputs, nothing changes.

So adding an input is a hardware-only mod. Two common approaches:

1. **Add one TRS input jack.** Keep the existing mono outputs and wire a
   stereo (TRS) jack to Synthux pins 16 (Left / Tip) and 17 (Right / Ring),
   with the Sleeve to ground. A mono (TS) cable also works: it simply
   feeds the left input.
2. **Swap the two mono jacks for TRS jacks.** Desolder the original mono jacks
   and replace them with stereo Thonkiconns (PJ366ST), giving one stereo output
   and one stereo input on the same footprint.

The audio pins 16–19 are on the side of the Daisy where the Synthux pin
numbers match the Seed pin numbers:

| Signal    | Synthux pin |
| :-------- | :---------- |
| Left In   | 16          |
| Right In  | 17          |
| Left Out  | 18          |
| Right Out | 19          |

For a full step-by-step guide to option 2 (desoldering, matrix routing, bridging
the Ring pads and the ground mod), see
[Audio I/O Mod: Upgrading to Stereo TRS](https://github.com/jonwaterschoot/Feedback-Gardenscpr-for-Synthux-Audrey-II#audio-io-mod-upgrading-to-stereo-trs)
by Jon Waterschoot.

> Input level: the summed input is added straight into the feedback loop, so a
> hot stereo source can drive it harder than a mono one. Start with the source
> volume low.
