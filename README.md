# Mikael Asfaw

**Founder & Chief Engineer | Edge Systems, Embedded Compute & Multimodal AI | 19+ Patents**

San Carlos, California · [LinkedIn](https://www.linkedin.com/in/mikael-asfaw-72723a2b/) · [GitHub](https://github.com/mikaellum)

---

## Summary

Founder and chief engineer building system-level edge-AI hardware for assistive technology and physical security—multimodal perception, embedded compute, sensor fusion, and on-device auditory guidance. Transitioning from a decade of production audio/acoustics at Apple, Google, Meta, Snap, Waymo, Tesla, Alarm.com, and 1X into embedded vision, FPGA DSP, inertial sensing, and edge-AI architecture. Inventor on 19+ pending and granted U.S. patent matters.

**What we’re building now.** An IP-backed wearable edge platform that fuses vision, infrared, inertial sensing, microphones, and on-device compute for contextual awareness and auditory guidance. Product and system details remain private; selected inventions are under pending U.S. patent filings.

**How the technical foundation is expanding.** Part-time Dartmouth M.Eng. work deepens the stack into MIPI CSI-2 camera pipelines, Sobel edge detection, AXI-Stream I2S/FIR DSP, SPI IMU calibration, UART-to-BLE telemetry, and edge-AI perception architecture. Those capabilities feed the company work above—and strengthen every tool in this repository.

This site centers on **R&D tools and projects**: practical methods for prototyping, measuring, and validating audio, sensing, and embedded systems.

---

## Capabilities & Skills

| Domain | Capabilities |
|--------|----------------|
| Audio & Acoustics | Transducer design, microphone arrays, loudspeakers, spatial audio, beamforming, direction of arrival, echo control, acoustic measurement and validation |
| Vision, Sensors & Edge | MIPI CSI-2 / D-PHY, SCCB / I2C camera control, AXI4-Stream video, FPGA camera pipelines, Gaussian blur / Sobel edge detection, RGB / HDMI, SPI IMU bring-up, sensor calibration, multimodal perception, edge-AI system architecture |
| Embedded Systems & FPGA DSP | Embedded Linux, real-time signal processing, VHDL, I2S audio, AXI-Stream / AXI FIFOs, fixed-point FIR, SPI / UART / USART / I2C, ADC, GPIO, BTLE / Nordic UART Service, ESP32-C3, STM32, hardware/software bring-up |
| On-Device Intelligence | Deep learning for perception and classification, compact / small language model concepts at the edge, TensorFlow-class tooling, evaluation under constrained compute and power |
| Programming, ML & Data | Python, C, C++, VHDL, MATLAB, TensorFlow, NumPy, Pandas, SciPy, scikit-learn, librosa, statistical analysis and manufacturing analytics |
| Modeling & Hardware | Git, Xilinx Vitis/Vivado, FPGA platforms, Raspberry Pi, STM32, COMSOL, SPICE, SolidWorks, FEA, oscilloscopes, logic analyzers |

---

## R&D Tools & Projects

### Table of Contents
- [Loudspeaker LPM Simulation Tool](#loudspeaker-lpm-simulation-tool)
- [Loudspeaker Magnetics Simulation Tool](#loudspeaker-magnetics-simulation-tool)
- [Embedded Systems, FPGA Audio DSP, and Machine Vision](#embedded-systems-fpga-audio-dsp-and-machine-vision)
- [Audio Test App](#audio-test-app)
- [Machine Learning Models to Classify Music Genre](#machine-learning-models-to-classify-music-genre)

---

### Loudspeaker LPM Simulation Tool

Browser-based loudspeaker linear-parameter (LPM) simulator for comparing two driver/system designs side by side before hardware builds. Highlights include:

- **Dual-system compare** — edit two loudspeakers in parallel and see differences immediately
- **Enclosure types** — closed-back, bass-reflex, and passive-radiator models per speaker
- **Response plots** — frequency response (SPL), cone excursion, impedance, and port velocity / passive-radiator excursion
- **Derived constants** — design quantities such as `Vas`, `fs`, `Qts`, `BL`, sensitivity, thermal limits, and related enclosure/port parameters
- **Interactive dashboard** — live plots and a calculated-constants table as parameters change

Runs locally or on remote hosts (including Raspberry Pi-class deployments). Implementation details are proprietary.

**Demo:** [Loudspeaker LPM (MP4)](videos/loudspeaker_lpm_2026-08-07.mp4)

<video src="videos/loudspeaker_lpm_2026-08-07.mp4" controls width="100%"></video>

<details>
<summary><strong>Stills</strong></summary>

![Simulator](images/loudspeaker-lpm-app-still.png)

</details>

---

### Loudspeaker Magnetics Simulation Tool

Finite-element magnetics workflow for loudspeaker motor design—iterate the magnetic circuit from geometry before cutting metal. Highlights include:

- **Voice-coil geometry** — turn count, DC resistance, dimensions, and moving mass from wire and bobbin inputs
- **Motor force factor** — estimate `BL` and related electromotive properties from pole, magnet, and coil layout
- **Mass & packaging** — motor mass and volume for system-level trade studies
- **Field visualization** — flux-density heat maps of the motor domain
- **Stroke behavior** — non-linear `BL(x)` curves across excursion for motor linearity checks

Implementation details are proprietary.

**Demo:** [Loudspeaker Magnetics (MP4)](videos/loudspeaker_magnetics_2026-08-07.mp4)

<video src="videos/loudspeaker_magnetics_2026-08-07.mp4" controls width="100%"></video>

<details>
<summary><strong>Stills</strong></summary>

![Motor Design](images/loudspeaker-magnetics-app-still.png)

</details>

---

### Embedded Systems, FPGA Audio DSP, and Machine Vision

Dartmouth graduate embedded / FPGA lab work spanning an **STM32F042 Nucleo-32** (STM32F042K6) and a **Xilinx Zybo Z7-20 (Zynq)** platform in Vivado / Vitis—bare-metal C on the MCU side, plus FPGA streaming audio DSP and real-time machine-vision pipelines, with Digilent Analog Discovery / WaveForms validation where applicable.

**STM32F042 Nucleo**
- **Toolchain & debug** — J-Link / GDB bring-up, firmware flash, and VS Code remote debug workflows
- **GPIO & instrumentation** — LED I/O characterization with WaveForms scope / wavegen; breadboard probing of MCU pins
- **USART** — alternate-function pin mux, interrupt-driven RX callbacks, and `printf`-style host logging
- **Clocks, SysTick & PWM** — internal clock configuration, exception/callback patterns, PWM duty-cycle control, RC filtering, and LED dimming
- **ADC & sampling** — sample-time / input-impedance tradeoffs, interrupt and **DMA** capture paths, Nyquist checks, timer-triggered sampling, and digital filtering
- **SPI sensing** — LIS3DH accelerometer over SPI with logic-analyzer decode, interrupt-driven acquisition, and orientation plots
- **BTLE bridge** — UART-to-BTLE character loopback and streaming accelerometer data to a web device CLI
- **Fixed-point DSP** — moving-average → fixed-point FIR, offset/scale calibration in Q-format, plus code-size and processing-time tradeoffs vs. floating point

**Xilinx Zynq — AXI-Stream I2S audio DSP**
- **AXI-Stream I2S wrappers** — VHDL transmitter / receiver with RTL schematics, testbenches, and timing closure through metastability fixes in the I2S path
- **Streaming datapath** — dual AXI-Stream FIFOs between record and play paths, wired with PS, AXI IIC (codec control), and an Integrated Logic Analyzer for on-chip debug
- **Hardware audio pass-through** — AD3 scope validation of clean sine pass-through (matched frequencies, no glitches) plus time- and frequency-domain loopback / noise-floor checks
- **Selectable FIR filters** — button-selected low-pass, high-pass, band-pass, and band-stop FIR blocks (per audio channel) inserted between record and play FIFOs
- **System verification** — spectrum sweeps, two-tone scope captures, Bode / attenuation plots, and real music/speech listening checks across all four filter modes

**Xilinx Zynq — FPGA-based machine vision (Pcam 5C)**
- **Camera → HDMI pass-through** — Digilent **Pcam 5C** (OmniVision **OV5640**) on Zybo Z7-20; Vivado hardware + Vitis C++ bring-up to drive live camera output over HDMI (timing/constraint fixes for a clean display image)
- **Sensor datapath tracing** — photons → CIS / ADC → **MIPI CSI-2** / **D-PHY** → SCCB camera control → AXI4-Stream video transport (VDMA, demosaic, timing) → RGB/DVI → HDMI
- **Real-time edge detection** — hardware `blur_edge_detect` path with BRAM line buffers, 3×3 windowing, **Gaussian blur**, and **Sobel** Gx/Gy edge maps; board switches (SW2 / SW3) toggle live among raw, grayscale/Gaussian, and Sobel edge-detect HDMI output
- **Latency & resources** — block-level transient and steady-state latency estimates (e.g. ~51 µs end-to-end at 150 MHz / 1920-wide / 3×3 kernels) plus post-implementation utilization and power context on the Zynq fabric

<details>
<summary><strong>Stills</strong></summary>

![Nucleo bench setup](images/stm32-nucleo-bench-setup.jpg)

![SPI LIS3DH logic decode](images/stm32-nucleo-spi-lis3dh.jpg)

![Accelerometer free-rotation](images/stm32-nucleo-accel-orientation.jpg)

![Fixed-point calibrated accel UART](images/stm32-nucleo-fixed-point-accel.png)

![Vivado Zynq I2S + FIR block design](images/fpga-zynq-i2s-fir-block-design.png)

![AXI-Stream I2S simulation](images/fpga-axis-i2s-sim-waveform.png)

![AD3 audio pass-through](images/fpga-ad3-audio-passthrough.png)

![Spectrum sweep passthrough](images/fpga-spectrum-sweep-passthrough.png)

![FIR filter Bode (dB)](images/fpga-fir-bode-db.png)

![Zybo Pcam HDMI passthrough](images/fpga-vision-zybo-pcam-hdmi-passthrough.png)

![Grayscale / Gaussian and Sobel outputs](images/fpga-vision-grayscale-and-sobel.png)

![Sobel edge-detect HDMI output](images/fpga-vision-sobel-hdmi-output.png)

![Pcam to HDMI signal flow](images/fpga-vision-pcam-hdmi-signal-flow.jpg)

![Pcam HDMI Vivado block design](images/fpga-vision-pcam-hdmi-block-design.jpg)

![Pcam signal tracing](images/fpga-vision-pcam-signal-tracing.jpg)

![Edge-detect architecture](images/fpga-vision-edge-detect-architecture.jpg)

![Edge-detect Vivado block design](images/fpga-vision-edge-detect-block-design.jpg)

</details>

---

### Audio Test App

Python measurement toolkit—and browser dashboard—for loudspeaker and audio-system validation on real hardware. Highlights include:

- **Stimulus generation** — noise and exponential sweeps for system excitation
- **Play / record** — drive an output while capturing from selected input devices (or record alone)
- **Loudspeaker characterization** — frequency response, distortion, and related impulse-response views from sweep captures
- **Microphone tests** — DUT mic measurements against a reference path, with optional speaker flattening so the mic—not the playback chain—is what you score
- **Microphone calibration** — convert digital levels to SPL using a known calibrator tone
- **Speaker equalization** — measure-and-correct workflows to flatten a reference loudspeaker for cleaner mic work
- **Speech quality (MOS)** — non-intrusive MOS-style scoring on speech WAV files (no clean reference transcript required)
- **Capture analysis** — waveform, spectrum, spectrogram, and level statistics on recorded takes

Runs on lab benches and remote hosts (including Raspberry Pi-class deployments). Implementation details are proprietary.

**Demo:** [Audio Test App (MP4)](videos/audio_test_app_2026-08-07.mp4)

<video src="videos/audio_test_app_2026-08-07.mp4" controls width="100%"></video>

<details>
<summary><strong>Stills</strong></summary>

![Farina Sweep](images/audio-test-app-still.png)

</details>

---

### Machine Learning Models to Classify Music Genre

Short-clip music-genre classifiers (TensorFlow NN and SVM) trained on audio features via librosa. Architecture is sound; F1 settled around 0.41–0.47 on a noisy multi-genre mashup dataset.

<details>
<summary><strong>Architecture & results</strong></summary>

**Requirements:** Python 3.12.2, numpy, pandas, pickle, scikit-learn, tensorflow, librosa

Trained ~100 epochs (accuracy ~0.96, loss ~0.194 on training metrics).

![TensorFlow Neural Network Architecture](images/tf_architecture.png)

![TensorFlow Confusion Matrix](images/tf_NN_Confusion_matrix.jpg)

![SVM Confusion Matrix](images/SVM_Confusion_matrix.jpg)

Paper: [ML_FinalProject_Team-2.pdf](papers/ML_FinalProject_Team-2.pdf)

</details>

---

## Education

- **Dartmouth College** — M.Eng. Computer Engineering (Part-Time, In Progress), Mar 2025 – Mar 2027  
  Featured: *[How Mikael Asfaw Used Dartmouth’s Online M.Eng. to Bridge Hardware, Software, and AI](https://blog.coursera.org/stories/how-mikael-asfaw-used-dartmouths-online-meng-to-bridge-hardware-software-and-ai/)*  
  Selected project themes: Pcam 5C / MIPI CSI-2 machine-vision pipelines with Gaussian blur and Sobel edge detection on Zybo Z7-20, Zynq AXI-Stream I2S audio with selectable FIR filtering, STM32 embedded IMU bring-up and fixed-point calibration, and edge-AI perception-system architecture.
- **University of Southern California** — M.S. Mechanical Engineering, Aug 2012 – May 2013
- **University of Southern California** — B.S. Mechanical Engineering, Aug 2008 – May 2012

---

## Selected Patent Portfolio

19+ pending and granted U.S. and international matters spanning context-aware systems, microphone arrays, spatial audio, beamforming, acoustic sensing, electroacoustic transducers, bone conduction, and embedded signal processing.

### Context-Aware, Edge-AI & Adaptive Audio
- Pending U.S. App. No. 19/560,372 — *Head-Mounted Device with Contextual Awareness*
- U.S. 11,586,407 — Audio data manipulation based on display orientation
- U.S. 11,620,976 — Acoustic echo cancellation based on display orientation
- U.S. 11,340,861 — Audio data manipulation based on microphone orientation

### Microphones, Wind Noise & Acoustic Sensing
- U.S. 12,413,887 — Sintered filter material and grille design to mitigate wind noise
- U.S. 10,887,713 — Microphone defect detection
- U.S. 10,028,045 — Combined microphone and lighting device

### Beamforming, Binaural Audio & Spatial Processing
- U.S. 10,897,672 — Speaker beam steering using microphone-array and depth-camera input
- U.S. 11,044,568 — Head-wearable apparatus for binaural audio generation
- U.S. 10,567,898 — Binaural audio generation in wearable devices
- U.S. 11,361,781 — Dynamic beamforming to improve SNR in head-worn devices

### Speaker Systems & Transducer Architecture
- U.S. 10,687,146 / 10,194,248 — Speaker with flex-circuit acoustic radiator
- U.S. 10,178,469 — Damping spring for transducer systems
- WO 2023/172256 — Speaker with integrated pressure sensor and barometric vent

### Bone Conduction & Wearable Audio
- U.S. 9,998,829 — Bone-conduction transducer with enhanced low-frequency performance
- U.S. 9,936,301 — Composite yoke for a bone-conduction transducer
- U.S. 9,766,481 — Closed-loop audio processing for bone-conduction systems

Full schedule and claim-level summaries available upon request.

---

### Author

Author: [Mikael Asfaw](https://www.linkedin.com/in/mikael-asfaw-72723a2b/)  
License: [Proprietary — see LICENSE.md](LICENSE.md)  
Created: Feb 18, 2025  
Updated: Aug 8, 2026
