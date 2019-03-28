# ELC325-Matlab-Simulink-Project
Simulation of the performance of different modulation schemes, BPSK, QPSK, FSK, QAM(16-64) in an AWGN environment.

## To reproduce the Figures
1. Open MATLAB
2. Choose Simulink from the toolbar 
3. Write "bertool" in the command window
4. In theoritcal tab
  * Set Eb/No -10:1:10
  * Choose Modulation type (PSK, QAM or FSK)
  * Choose Modulation order (2 for BPSK and FSK, 4 for QPSK, 16 for QAM16, 64 for QAM64)
  * Press Plot
5. In Monte Carlo tab
  * Set Eb/No -10:1:10
  * Press browse and choose the model.slx
  * Set Ber variable Name to "ber"
  * Press Run

## Modulation Schemes

### General Parameters
```
Random Integer:
  Intial Seed = 37    Samples per frame = 100

AWGN Channel:
  Intial Seed = 67    Eb/No (DB) = Eb/No

Error Rate Calculation:
  Output data = Port

Sink Block Parameters:
  Variable name = ber   Save format = Array   Save 2-D signals as = 2-D array

For Raised Cosine:
  Error Rate Calculation:
    Recieve delay = 10 ( to align it with the Symbols Out signal )
```

### BPSK Modulation Scheme
Binary Phase Shift Keying (BPSK) is a two phase modulation scheme, where the 0’s and 1’s in a binary message are represented by two different phase states in the carrier signal: θ=0∘ for binary 1 and θ=180∘ for binary 0.

##### Parameters
```
Random Integer:
  M-ary Number = 2
  
AWGN:
  Number of bits per symbol = 1   ( to represent 2 numbers we need 1 bit )  
```
#### Schematic
<p align="center">
  <img src="/Output/BPSK/Schematic.png">
</p>

#### BER performance figure [BER versus Eb/No ranging from -10 to 10 dB]
<p align="center">
  <img width="500" height="500" src="/Output/BPSK/BER.PNG">
</p>
  <h4> Scatter plot of the symbols </h4>
<p align="center">
  <img src="/Output/BPSK/Before_AWGN.PNG" height="400" width="400"> <img src="/Output/BPSK/After_AWGN.PNG" height="400" width="400">
</p>

### After applying a Raised-Cosine pulse shaping
#### Schematic
<p align="center">
  <img src="/Output/BPSK/[Raised_Cosine]Schematic.png">
</p>

<p align="center">
  <img width="500" height="500" src="/Output/BPSK/[Raised_Cosine]BER.png">
</p>
  <h4> Scatter plot of the symbols </h4>
<p align="center">
  <img src="/Output/BPSK/[Raised_Cosine]Before_AWGN.png" height="400" width="400"> <img src="/Output/BPSK/[Raised_Cosine]After_AWGN.png" height="400" width="400">
</p>

***

### QPSK Modulation Scheme
Quadrature Phase Shift Keying (QPSK) is a form of Phase Shift Keying in which two bits are modulated at once, selecting one of four possible carrier phase shifts (0, 90, 180, or 270 degrees.

##### Parameters
```
Random Integer:
  M-ary Number = 4
  
AWGN:
  Number of bits per symbol = 2   ( to represent 4 numbers we need 2 bits ) 
  
Modulator:
  Phase offset = pi/2
  
Demodulator:
  Phase offset = pi/2
```

#### Schematic
<p align="center">
  <img src="/Output/QPSK/Schematic.png">
</p>

#### BER performance figure [BER versus Eb/No ranging from -10 to 10 dB]
<p align="center">
  <img width="500" height="500" src="/Output/QPSK/BER.PNG">
</p>
  <h4> Scatter plot of the symbols </h4>
<p align="center">
  <img src="/Output/QPSK/Before_AWGN.PNG" height="400" width="400"> <img src="/Output/QPSK/After_AWGN.PNG" height="400" width="400">
</p>

### After applying a Raised-Cosine pulse shaping
#### Schematic
<p align="center">
  <img src="/Output/QPSK/[Raised_Cosine]Schematic.png">
</p>

<p align="center">
  <img width="500" height="500" src="/Output/QPSK/[Raised_Cosine]BER.png">
</p>
  <h4> Scatter plot of the symbols </h4>
<p align="center">
  <img src="/Output/QPSK/[Raised_Cosine]Before_AWGN.png" height="400" width="400"> <img src="/Output/QPSK/[Raised_Cosine]After_AWGN.png" height="400" width="400">
</p>

***

### FSK Modulation Scheme
Frequency-shift keying (FSK) is a method of transmitting digital signals. The two binary states, logic 0 (low) and 1 (high), are each represented by an analog waveform. Logic 0 is represented by a wave at a specific frequency, and logic 1 is represented by a wave at a different frequency.

##### Parameters
```
Random Integer:
  M-ary Number = 4
  
AWGN:
  Number of bits per symbol = 2   ( to represent 4 numbers we need 2 bits ) 
  
Modulator:
  Phase offset = pi/2   Samples per symbol = 17 (To prevent aliasing from occurring in the output signal, set the sampling frequency greater than the product of M and the Frequency separation parameter. Sampling frequency is Samples per symbol divided by the input symbol period)
  
Demodulator:
  Phase offset = pi/2   Samples per symbol = 17
```

#### Schematic
<p align="center">
  <img src="/Output/FSK/Schematic.png">
</p>

#### BER performance figure [BER versus Eb/No ranging from -10 to 10 dB]
<p align="center">
  <img width="500" height="500" src="/Output/FSK/BER.PNG">
</p>
  <h4> Scatter plot of the symbols </h4>
<p align="center">
  <img src="/Output/FSK/Before_AWGN.PNG" height="400" width="400"> <img src="/Output/FSK/After_AWGN.PNG" height="400" width="400">
</p>

### After applying a Raised-Cosine pulse shaping
#### Schematic
<p align="center">
  <img src="/Output/FSK/[Raised_Cosine]Schematic.png">
</p>

<p align="center">
  <img width="500" height="500" src="/Output/FSK/[Raised_Cosine]BER.png">
</p>
  <h4> Scatter plot of the symbols </h4>
<p align="center">
  <img src="/Output/FSK/[Raised_Cosine]Before_AWGN.png" height="400" width="400"> <img src="/Output/FSK/[Raised_Cosine]After_AWGN.png" height="400" width="400">
</p>

***

### QAM Modulation Scheme
Quadrature amplitude modulation (QAM) is a method of combining two amplitude-modulated (AM) signals into a single channel, thereby doubling the effective bandwidth.there are two carriers, each having the same frequency but differing in phase by 90 degrees (one quarter of a cycle, from which the term quadrature arises). 

### QAM16

##### Parameters
```
Random Integer:
  M-ary Number = 16
  
AWGN:
  Number of bits per symbol = 4   ( to represent 16 numbers we need 4 bits ) 
  
Modulator:
  M-ary Number = 16   Normalization method = Average Power
  
Demodulator:
  Normalization method = Average Power
```

### Schematic
<p align="center">
  <img src="/Output/QAM16/Schematic.png">
</p>

#### BER performance figure [BER versus Eb/No ranging from -10 to 10 dB]
<p align="center">
  <img width="500" height="500" src="/Output/QAM16/BER.PNG">
</p>
  <h4> Scatter plot of the symbols </h4>
<p align="center">
  <img src="/Output/QAM16/Before_AWGN.PNG" height="400" width="400"> <img src="/Output/QAM16/After_AWGN.PNG" height="400" width="400">
</p>

### After applying a Raised-Cosine pulse shaping
#### Schematic
<p align="center">
  <img src="/Output/QAM16/[Raised_Cosine]Schematic.png">
</p>

<p align="center">
  <img width="500" height="500" src="/Output/QAM16/[Raised_Cosine]BER.png">
</p>
  <h4> Scatter plot of the symbols </h4>
<p align="center">
  <img src="/Output/QAM16/[Raised_Cosine]Before_AWGN.png" height="400" width="400"> <img src="/Output/QAM16/[Raised_Cosine]After_AWGN.png" height="400" width="400">
</p>

***

### QAM64

##### Parameters
```
Random Integer:
  M-ary Number = 64
  
AWGN:
  Number of bits per symbol = 6   ( to represent 64 numbers we need 6 bits ) 
  
Modulator:
  M-ary Number = 64   Normalization method = Average Power
  
Demodulator:
  Normalization method = Average Power
```

### Schematic
<p align="center">
  <img src="/Output/QAM64/Schematic.png">
</p>

#### BER performance figure [BER versus Eb/No ranging from -10 to 10 dB]
<p align="center">
  <img width="500" height="500" src="/Output/QAM64/BER.PNG">
</p>
  <h4> Scatter plot of the symbols </h4>
<p align="center">
  <img src="/Output/QAM64/Before_AWGN.PNG" height="400" width="400"> <img src="/Output/QAM64/After_AWGN.PNG" height="400" width="400">
</p>

### After applying a Raised-Cosine pulse shaping
#### Schematic
<p align="center">
  <img src="/Output/QAM64/[Raised_Cosine]Schematic.png">
</p>

<p align="center">
  <img width="500" height="500" src="/Output/QAM64/[Raised_Cosine]BER.png">
</p>
  <h4> Scatter plot of the symbols </h4>
<p align="center">
  <img src="/Output/QAM64/[Raised_Cosine]Before_AWGN.png" height="400" width="400"> <img src="/Output/QAM64/[Raised_Cosine]After_AWGN.png" height="400" width="400">
</p>

***
