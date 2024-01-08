### Exercises

**Exercise 12.1. Suitable ADC Type for Each Requirement:**
   - Fast Sampling Rate and Low Resolution: Flash ADC.
   - Slow Sampling Rate but High Resolution: Delta-Sigma ADC.
   - Slow Sampling Rate and Moderate Resolution: Successive Approximation Register (SAR) ADC.

**Exercise 12.2. Signal to Quantization Noise Ratio for a Bipolar Tone Signal:**
   - A 12-bit ADC has 2^12 = 4096 quantization levels.
   - Range of signal = 6V - (-4V) = 10V.
   - Quantization step size = 10V / 4096 ≈ 0.00244V.
   - Signal to Quantization Noise Ratio (SQNR) can be approximated as 6.02 * number of bits + 1.76 dB = 6.02 * 12 + 1.76 dB ≈ 74.0 dB.

**Exercise 12.3. C Program for ADC Sampling Rate of 500 ksps:**
   - [Program specific] This would involve configuring the ADC's control registers to set the sampling rate to 500 kilo-samples per second (ksps).

**Exercise 12.4. Data Acquisition from Two Different Sensors with Different Sampling Rates:**
   - Configure ADC module 0 for two sequencers: one for the temperature sensor (1 Hz) and another for the light sensor (100 Hz).
   - Triggering Source: For the temperature sensor, a periodic timer trigger could be used due to the low frequency. For the light sensor, a more frequent timer or an internal ADC trigger can be used.
   - Assign different priorities and configure the ADC sequencers to sample at the respective rates.
