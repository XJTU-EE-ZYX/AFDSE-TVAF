[Uploading README.md…]()
# AFDSE-TVAF Evaluation Packages

This material supports the paper "An Adaptive Frequency-Down-Shifting Method for
Synchrophasor Measurement in P-Class PMUs Based on the Time-Varying
Amplitude-Frequency Model".

It provides the algorithm framework, the amplitude-frequency responses of the
three designed FIR filters of Table II, and, for each evaluation, one CSV
holding the summary values printed in the paper (maximum errors, step-response
times, and the RTDS/MATLAB comparison). The test signal of each evaluation is
specified in the README of its folder, to the extent that the original test
definition fixed it.

The material is organized as six independent MATLAB folders:

1. static frequency-deviation evaluation (Fig. 3, Table III);

2. static harmonic evaluation (Fig. 4, Table IV);

3. dynamic modulation evaluation (Fig. 5, Table V);

4. dynamic frequency-ramp evaluation (Fig. 6, Section IV-D);

5. dynamic amplitude- and phase-step evaluation (Fig. 7, Table VI);

6. RTDS measurement evaluation (Fig. 9, Table VII).

Each folder collects the material of one evaluation. The framework file
documents the processing sequence; its periodic-extension and filtering stages
are represented by documented interfaces.

* Test signal. The folder README states the test signal of that evaluation as
  fixed by the original test definition (waveform, sampling rate, record length
  and sweep parameters; for the RTDS test, the signal condition and the
  measurement chain).

* Algorithm framework. `AFDSE_TVAF_Pseudocode.m` states the processing
  sequence of AFDSE-TVAF in MATLAB form: finite-length Hilbert transform,
  time-varying amplitude and frequency, adaptive frequency down-shifting,
  real-coefficient low-pass extraction of the fundamental, phase recovery
  through a second Hilbert transform, and frequency differencing for ROCOF,
  together with the TVE, FE and RFE definitions used in the evaluation.

* Designed filters. `filters/filter_responses.csv` in each folder gives the
  amplitude-frequency responses of the three linear-phase FIR low-pass filters
  of Table II - the synchrophasor, frequency and ROCOF branches - derived from
  the P-class TVE, FE and RFE limits. Their lengths are 391, 701 and 802 taps,
  with -1 dB passband edges at 9.5, 8.0 and 7.1 Hz and -40 dB stopband edges at
  47.1, 45.1 and 40.3 Hz for a 10-kHz sampling rate. The table lists the
  magnitude in dB, relative to the DC gain of each filter, at 150 log-spaced
  frequencies from 1 Hz to 5 kHz (the frequency range of Fig. 1) plus the six
  -1 dB and -40 dB edge frequencies of Table II; these are the curves of Fig. 1.

* Reported values. `results/` holds a single CSV that reproduces the summary
  values of the corresponding paper table or text passage: maximum errors
  (Tables III-V and Section IV-D), step-response times (Table VI) and the
  RTDS/MATLAB comparison (Table VII). Where the paper normalizes an error to
  its P-class limit and reports the base-10 logarithm, the CSV gives the
  maximum itself, the applicable limit, and that logarithm, so that the printed
  table can be recomputed from the file.

