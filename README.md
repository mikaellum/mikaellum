# General Information

This repository houses highlights the acoustic engineering tools
present within this personal github account. Highlights from other 
repository heads is not displayed here.

### Author

Author: [Michael Asfaw](https://www.linkedin.com/in/michael-asfaw-72723a2b/)\
Date: Feb 18, 2025

## Loudspeaker LPM Simulation Tool

### About

A browser accessible loudspeaker linear parameter design application

### Requirements

    * Python 3.12.3
    * flask
    * numpy
    * waitress
    * python-dotenv
    * bokeh
    * loudspeaker
    * loudspeakerBokehPlotter

### About

The files in this repository are written to specify a loudspeaker
from it's linear parameters.

### Installation

To install, run this command in bash

```bash
git clone https://github.com/mikaellum/loudspeaker-app-py.git
```

### Execution

For getting the sever up

```shell
python3 server.py
```

On a browser

[Loudspeaker](http://localhost:8000/)

### Outputs

The output html app looks *similar* to:

![Web-page](loudspeakerSimulator.png)

## Loudspeaker Magnetics Simulation Tool

### About

A browser accessible loudspeaker linear parameter design application

### Requirements

    * Python 3.12.2
    * pyfemm
    * numpy
    * math

The files in this repository are written to help design
a loudspeaker motor systems.

### Installation

To install, run this command in bash

```bash
git clone https://github.com/mikaellum/loudspeaker-magnetics-pyFEMM.git
```

### Execution

For getting voice coil properties

```shell
python3 VoiceCoil.py Rdc NumLayers WireDiameter IACS BobbinDiameter SpecGravity insThick
```

Using the output from the voice coil properties, can calculate the motor properties

```shell
python3 Motor.py Ag Ph Pr Pcr Pbh Pbr Wh Vch Vcw Vco Mh Mw Bm Nturns WireGuage SoftSteel Magnet R M_domain M_motor M_vc times_x times_y Xmax N
```

### Outputs

output for voice coil *similar* to:

```
Design Width: 0.22[mm]
Design Height: 6.02[mm]
Number of Turns of the Voice Coil: 83
Mass of the Voice Coil: 0.41[g]
```

output for the motor *similar* to:

```
Rdc of the voice coil is: 5.14[Ohm]
BL of the motor is: 2.18[T*m]
Mass of the Motor is: 112.61[g]
Total Volume of the Motor is: 16.29[cc]
```

the output plots flux density heat-map are *similar* to:

![Heat-Map](BL.bmp)

the output plots for the non-linear BL are *similar* to:

![BL(x)](BLx.jpg)

## Speech Mean Opinion Score Using PESQ MOS

### About

Python code to determine PESQ-MOS of a degraded audio file to an original
for both wideband and narrowband applications

### Requirements

    * Python 3.12.2
    * pesq
    * scipy
    * matplotlib

The files in this repository are written to help get the
PESQ MOS scores for speech (telephony standard).

### Installation

To install, run this command in bash

```bash
git clone https://github.com/mikaellum/PESQ-MOS-py.git
```

### Execution

For getting the MOS score values

```shell
python3 mosScore.py original degraded
```

To visualize the spectrogram of the *.wav* files

```shell
python3 plotSpecgram.py file nfft noverlap cmap figWidth figHeight
```

### Outputs

output for the MOS scores is *similar* to:

```
The narrow band MOS is:  4.38
The wide band MOS is:  4.33
```

the output specgram for the orignal speech file is *similar* to:

![originalSpeech](originalSpeech.png)

the output specgram for the degraded speech file is *similar* to:

![degradedSpeech](degradedSpeech.png)

