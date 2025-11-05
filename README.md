# Gravitational Waves Open Science Center (GWOSC) Workshop 2025.
During the workshop, I gained hands-on experience with importing and working with time series data from different gravitational wave events, catalogs, and detectors. I learned how to transform time-domain data into the frequency domain using Fast Fourier Transforms, calculate the Power Spectral Density by averaging the squared moduli of the FFTs, and obtain the Amplitude Spectral Density by taking the square root of the PSD. I also explored visualizing the data through spectrograms and Q-transforms, which allowed me to examine the evolution of frequency content over time. Using PyCBC, I generated waveforms for merging binary systems with different approximants, masses, and arrival frequencies, enabling me to simulate and study a variety of astrophysical scenarios.

I further applied matched filtering techniques to identify known signals within whitened noise, learning the importance of preconditioning the data, accounting for filter wraparound, and interpreting the resulting SNR time series. Working with the GW170814 data, I implemented chi-squared tests to ensure that each p-bin contributed equally, helping to distinguish real signals from noise glitches, and re-weighted the SNR to account for deviations from Gaussian noise within the on-source window. Finally, I gained experience in Bayesian inference, including rejection sampling and running MCMC analyses using Bilby. For example, I ran Bilby on the GW150914 signal, fixing most parameters while allowing the chirp mass and a few others to vary, defining priors, and constructing a likelihood to perform the parameter estimation. These exercises collectively provided a deep, practical understanding of gravitational wave data analysis from raw time series to parameter inference.

Data files may be downloaded from [DCC G2300818](https://github.com/gw-odw/odw/blob/main/Challenge/README.md#:~:text=be%20downloaded%20from-,DCC%20G2300818,-using%20these%20links) using these links:

[challenge1.gwf](https://github.com/gw-odw/odw/blob/main/Challenge/README.md#:~:text=using%20these%20links%3A-,challenge1.gwf,-challenge2.gwf)
[challenge2.gwf](https://github.com/gw-odw/odw/blob/main/Challenge/README.md#:~:text=challenge1.gwf-,challenge2.gwf,-challenge3.gwf)
[challenge3.gwf](https://github.com/gw-odw/odw/blob/main/Challenge/README.md#:~:text=challenge2.gwf-,challenge3.gwf,-challenge3_2048hz.gwf%20%3C%2D%2D%20Downsampled)
[challenge3_2048hz.gwf](https://github.com/gw-odw/odw/blob/main/Challenge/README.md#:~:text=challenge3_2048hz.gwf) <-- Downsampled version of Challenge 3 file

## Challenge 1 (1 point)
Identify a loud binary black hole signal in white, Gaussian noise.

- Use the data file challenge1.gwf. The channel name is H1:CHALLENGE1.
- The data are white, Gaussian noise containing a simulated BBH signal.
1. Load the data into memory. What are the sampling rate and duration of the data?
2. Plot the data in the time-domain.
3. Plot a spectrogram (or q-transform) of the data, and try to identify the signal.
4. What is the time of the merger?

## Challenge 2 (2 points)
Signal in colored, Gaussian noise.

- Use the data file challenge2.gwf, with channel name H1:CHALLENGE2.
- The data contain a BBH signal with m1 = m2 = 30 solar masses, spin = 0.
1. What is the approximative time of the merger? (Hint: a plot of the q-transform could help)
2. Generate a time-domain template waveform using approximate SEOBNRv4_opt. with the same parameters as above. Plot this waveform.
3. Calculate a PSD of the data, and plot this on a log-log scale. Use axes ranging from 20 Hz up to the Nyquist frequency.
4. Use the template waveform and PSD to calculate the SNR time series. Plot the SNR time-series.
5. What is the matched filter SNR of the signal?

## Challenge 3 (4 points)
- Use the data file challenge3.gwf with channel H1:CHALLENGE3.
- These are real LIGO data from O2, though we've adjusted the time labels and added some simulated signals.
- The data contain a loud simulated signal with m1 = m2 = 10 solar masses.
1. What is the merger time of this signal?
2. What is the matched-filter SNR of this signal?

## Challenge 4 (8 points)
- Use the data file challenge3.gwf with channels H1:CHALLENGE3 and L1:CHALLENGE3.
- These are real LIGO data from O2, though we've adjusted the time labels and added some simulated signals.
- Any simulated signals have been added to both the H1 and L1 data
- All simulated signals have spin = 0 and m1 = m2, with m1 somewhere in the range 10-50 solar masses
1. Identify as many signals as you can. Watch out! These are real data, and so glitches may be present. Any correct detection is +1 point but any false alarms will count -1 point against your score. For each signal you find, list:
- The merger time
- The SNR
- Your estimate of the component masses
2. Identify as many glitches as you can. Make a spectrogram of each one.

3. For each simulated BBH you found, use bilby to compute a posterior distribution for the mass. You can fix the spin and mass ratio to make this run faster.
