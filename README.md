# DSB--SC-MODULATION-AND-DEMODULATION-USING-PYTHON

__AIM__:

To generate a Double Sideband Suppressed Carrier (DSB-SC) signal in Python (Google Colab), transmit it (optionally add noise), and recover the message using coherent (synchronous) demodulation with a low-pass filter. Observe time and frequency domain waveforms and measure demodulation performance

__APPARATUS REQUIRED__:

Google Colab (or any Python environment)

Python libraries: numpy, matplotlib, scipy (scipy.signal)

__Theory__:

DSB-SC signal: s(t) = m(t) · cos(2πf_c t)
Coherent demodulation: multiply received s(t) by a synchronized carrier cos(2πf_c t) then low-pass filter (LPF) to remove double-frequency components:

r(t) = s(t)·cos(2πf_c t) = m(t)·cos²(2πf_c t) = 0.5 m(t) + 0.5 m(t)·cos(4πf_c t)
LPF extracts 0.5·m(t) → scale by 2 to recover m(t).

__Procedure__:

1) Import libraries and set parameters
2) Define message and carrier signals
3) Generate DSB-SC signal (modulation)
4) View spectra (FFT) of message and DSB-SC
5) (Optional) Add noise
6) Coherent demodulation (multiply by synchronized carrier)
7) Low-pass filter to recover message

__Program__:

```import numpy as np
import matplotlib.pyplot as plt
Am = 6.2
fm = 474
Ac = 12.4
fc = 4740
fs = 47400
t=np.arange(0, 3/fm, 1/fs)
m = Am*np.cos(2*3.14*fm*t)
plt.subplot(3,1,1)
plt.plot(t,m)
c = Ac*np.cos (2*3.14*fc*t)
plt.subplot(3,1,2)
plt.plot(t,c)
s1=(Ac+m)*np.cos(2*3.14*fc*t)
s2=(Ac-m)*np.cos(2*3.14*fc*t)
s=s1-s2
plt.subplot(3,1,3)
plt.plot(t,s)
```

   __Tabulation__:

<img width="1161" height="608" alt="image" src="https://github.com/user-attachments/assets/680e6562-fd00-4de7-ac65-de36f07e7aa8" />

   __Output__:

<img width="554" height="413" alt="image" src="https://github.com/user-attachments/assets/79419346-b856-4748-baa0-e7c0c6ddd02c" />

   __Result__:

   Thus the DSB-SC-AM Modulation is generated using python and the output is verified.
   
