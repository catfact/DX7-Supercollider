# DX7-Supercollider
### My accurate Yamaha DX-7 clone. Programmed in Supercollider.

This is a super-exact clone of DX7 in SC environment. This project began with my internship at the STEIM during the last year; I was able to get my hands on an original DX7 synth and eventually found out that this instrument has this mystic / unusual sound. So I started fiddling with it and did some experiments with Supercollider. After a while, it became an obsession to play with it and started to copy parts of its synth mechanism just to flex my DSP muscles. Sooner, I found myself in this vast project to clone the entire thing. After 2-3 months of implementing process and lots of sleepless nights. I was able to clone the entire DX7 engine with very high accurate results. Other than the DX7’s vintage sound hiss, it is hard to distinguish between the clone and the original one on the same presets. For my use, I collected some 16384 (2^14) DX7 Sysex bank presets from the internet and converted it to some integer sequences to read it from Supercollider. I am also combining this clone with this 16384 preset package. Currently, I am using it with my sequencers to modulate its parameters, but for everyone's ease of use, I implemented a very basic function call. Which calls notes with this format: [Midi note, velocity, preset number]. Additional documentation is in the file. Have fun!

## Getting Started

make sure the DX7Clone.sc class is in your ~/.local/share/SuperCollider/Extensions/ directory.  Ensure DX7.afx is in ~/.local/share/Supercollider directory. then sclang DX7Clone_test.scd from anywhere.

### Prerequisites

The only requirement is to install the SC3-Plugins Ugen library because I use the FM7.ar Ugen at the heart of all operation.

[SC3-Plugins](https://github.com/supercollider/sc3-plugins)

### Sound Examples

Here are some sound examples which calls a random preset for each new node:

[Example 1](https://soundcloud.com/ewbta/dx-7-sc-clone-demo-2)

[Example 2](https://soundcloud.com/ewbta/dx7-clone-sounds)

You can try these kinds of example by running the code at the very end of the DX7.scd file.


### Basic MIDI implementation

It’s a very straightforward process; the preset number selection can be made by two different MIDI CCs. At total 128 * 128 = 16384 number is needed, which makes you able to choose the entire library of presets (2 ^ 14).

See DX7Clone_test.scd for practical example

## Author

* **Aziz Ege Gonul** - [My Personal Website](http://www.egegonul.com)

## Things to be implemented

* Real time parameter modulation
* Loading custom DX7 presets
* Some cosmetic updates.

## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE.md](LICENSE.md) file for details


## Acknowledgments

* Hat tip to John Chowning
* STEIM for letting me use their DX7 and espresso machine.
* and all the anonymous preset makers for the Yamaha DX7 (unsung heroes).
## addendum (emb)

i've refactored the original `DX7.scd` script into a class called `DX7Clone.sc`, allowing easier instantiation.

the class file can be installed anywhere SC looks for extensions.

## addendum (RV)

- load the preset file into memory on init
- untangled preset logic a bit
- added ‘channel’ to the noteParser so you can can independently play the same note with different preset (by putting on a different ‘channel’)
- Added DC blocker to note silence detection
- Add a method for noteFreeTimeout (-1 is no timeout)

**the data file `DX7.afx` must be installed at the top of the user's supercollider support directory (e.g. `~/Library/Application Support/Supercollider`)**


see `DX7Clone_test.scd` for example usage.


### TODO:
- help file
- move data file into a class
- various optimizations
