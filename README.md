# Canal Tug

Tow cargo along English countryside canals.

A DualSlide game, built as a `.dsg` game file.

## Building

Needs the [DualSlide](../DualSlide) repository beside this one (it holds the
game SDK), the Arm GNU toolchain (`arm-none-eabi-gcc`), CMake, Ninja and
Python 3.

    cmake --preset default
    cmake --build --preset default

This writes `build/canal_tug.dsg`.

## Installing

Connect the DualSlide to a computer, copy `canal_tug.dsg` onto the DUALSLIDE
drive, and eject the drive.

## Details

| | |
| --- | --- |
| Identifier | `dualslide.canal-tug` |
| Version | 1.0.0 |
