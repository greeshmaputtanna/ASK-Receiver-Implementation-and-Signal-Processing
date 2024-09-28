# ASK Receiver Implementation and Signal Processing


## Overview

This project involves designing an Amplitude Shift Keying (ASK) receiver with non-coherent demodulation using GNU Radio and MATLAB. It focuses on understanding RF signal processing, demodulation techniques, and dealing with noisy environments. The project is divided into two main sections:

- **Section 1:** ASK receiver implementation in GNU Radio.
- **Section 2:** Signal demodulation and analysis in MATLAB.

---

## Learning Objectives

- Implement an ASK receiver with non-coherent demodulation.
- Plot and interpret spectrum measurements.
- Apply RF filtering techniques.
- Process signals under noisy conditions.

---

## Section 1: ASK Receiver Implementation (GNU Radio)

In this section, the ASK receiver is implemented using GNU Radio. The receiver employs a non-coherent detection method, eliminating the need for local oscillator synchronization.

### Receiver Block Diagram

- **Variable Settings:**
  - Frequency (`freq`): 904.48 MHz
  - Sample Rate (`samp_rate`): 2.4 Msps

- **Block Configuration:**
  - **RTL-SDR Source:**
    - Frequency: 904.48 MHz
    - RF Gain: 20 dB, IF Gain: 40 dB, BB Gain: 20 dB
  - **Band Pass Filter:**
    - Low Cutoff: 18 kHz, High Cutoff: 22 kHz
    - Transition Width: 500 Hz, Window: Hamming
  - **Low Pass Filters:** Multiple stages for decimation and noise reduction.
  - **Signal Visualization:**
    - QT GUI Time Sink
    - QT GUI Frequency Sink
    - QT GUI Waterfall Sink

### Instructions

1. Implement the ASK receiver using the block diagram.
2. Visualize the plots from the GNU Radio QT GUI blocks showing the time domain, frequency domain, and waterfall plots.
   
---

## Section 2: Signal Demodulation and Analysis (MATLAB)

In this section, demodulate the received ASK signal and process it using MATLAB. The steps mirror the GNU Radio implementation but require adjustments for MATLAB.

### Signal Acquisition (GQRX)

1. Open **GQRX** and set:
   - Sampling Rate: 2 Msps
   - Central Frequency: 904 MHz
2. Capture and record 5–9 seconds of I/Q data.
3. Play back the recording to verify that the signal is correctly captured.

### MATLAB Tasks

#### 2.1 Initial Analysis

- Load the recorded I/Q data into MATLAB.
- Plot the magnitude spectrum and spectrogram.
- Identify the frequency band of the desired signal.

#### 2.2 Noise Reduction using Band Pass Filter

- Design and apply a Band Pass Filter (BPF) matching the frequency band identified earlier.
- Plot the filtered signal's spectrum and the real part of the signal (`f[n]`).

#### 2.3 Non-coherent Demodulation

- Compute `d[n] = abs(f[n])`.
- Resample `d[n]` by a factor of 10,000 and plot the result.
- Design and apply a Low Pass Filter (LPF) with a cutoff of 10 Hz to remove high-frequency components.
- Plot the final demodulated signal plot.

---

## Tools & Software

- **GNU Radio** with QT GUI components
- **GQRX** for I/Q data capture
- **MATLAB** for signal processing and demodulation

---
