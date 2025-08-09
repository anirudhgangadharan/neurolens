NeuroLens -Whitepaper  

Executive Summary

NeuroLens is a real‑time, camera‑based system for estimating cognitive load and stress from facial dynamics. It uses non‑invasive computer vision methods to track blink parameters, eyelid closure, brow and lip muscle proxies, and gaze stability. Composite scoring heuristics map these features to probabilistic indicators of cognitive and emotional states. All design choices are grounded in peer‑reviewed literature (see numbered references).

Introduction

Real‑time estimation of mental states has applications in safety‑critical operations, adaptive human–computer interaction, and health monitoring. While gold‑standard measures involve EEG, EMG, and dedicated eye‑tracking hardware, NeuroLens aims to deliver useful approximations using only a consumer‑grade webcam.

Metric Rationale & Implementation

1. Blink Rate

Reference link: 1, 2, 7

Why: Blink rate decreases under sustained visual or cognitive load, increases in some arousal/fatigue states.

How measured: Eye Aspect Ratio (EAR) threshold; blinks counted in a 60 s sliding window.

2. PERCLOS (Percentage of Eyelid Closure)

Reference link: 4, 5, 6

Why: Validated predictor of drowsiness and reduced alertness.

How measured: Cumulative closed‑eye time in 60 s window.

3. Average Blink Duration

Reference link: 5, 6, 7

Why: Longer blinks correlate with fatigue/microsleeps.

How measured: Mean duration of closures <1000 ms.

4. Brow Tension

Reference link: 8, 9

Why: Corrugator supercilii activation is linked to stress, negative affect, and effort.

How measured: Vertical displacement of brow landmarks relative to eye center.

5. Lip Tension

Reference link: 9, 10

Why: Lip compression often accompanies negative emotion or cognitive effort.

How measured: Inverse of normalized mouth openness.

6. Gaze Stability

Reference link: 11, 12, 13

Why: High fixation stability and reduced saccade frequency occur in high‑load cognitive tasks.

How measured: Mean gaze point velocity over 2 s.

Composite Scores

Cognitive Load (CL)

CL = 0.5 * blinkFactor + 0.35 * fixFactor + 0.15 * browFactor

blinkFactor: suppression from baseline blink rate.

fixFactor: fixation stability from gaze velocity.

browFactor: brow furrow proxy.

Stress Level (SL)

SL = 0.4 * browFactor + 0.25 * blinkDeviation + 0.2 * lipTension + 0.15 * avgBlinkNorm

browFactor: corrugator activation.

blinkDeviation: departure from baseline blink rate.

lipTension: pressed lips.

avgBlinkNorm: normalized blink duration.

Calibration Protocol

Record 60 s neutral baseline.

Adjust EAR and gaze thresholds.

Collect labeled task data (NASA‑TLX, PANAS, STAI).

Limitations

Webcam tracking is less precise than physiological sensors.

Metrics can be context‑dependent.

Validation across demographics and devices is needed.

References (Vancouver style with links)

Stern JA, Boyer D, Schroeder D. Blink rate: a possible measure of fatigue. Hum Factors. 1994;36(2):285‑297. Available from: https://doi.org/10.1177/001872089403600209

Bentivoglio AR, Bressman SB, Cassetta E, Carretta D, Tonali P, Albanese A. Analysis of blink rate patterns in normal subjects. Mov Disord. 1997;12(6):1028‑1034. Available from: https://doi.org/10.1002/mds.870120629

Jap BT, Lal S, Fischer P, Bekiaris E. Using EEG spectral components to assess algorithms for detecting fatigue. Expert Syst Appl. 2009;36(2):2352‑2359. Available from: https://doi.org/10.1016/j.eswa.2007.12.043

Dinges DF, Grace R. PERCLOS: A valid psychophysiological measure of alertness as assessed by psychomotor vigilance. Federal Highway Administration; 1998. Available from: https://rosap.ntl.bts.gov/view/dot/39775

Morris TL, Miller JC. Electrooculographic and performance indices of fatigue during simulated flight. Biol Psychol. 1996;42(3):343‑360. Available from: https://doi.org/10.1016/0301-0511(95)05165-8

Schleicher R, Galley N, Briest S, Galley L. Blinks and saccades as indicators of fatigue in sleepiness warnings: looking tired? Ergonomics. 2008;51(7):982‑1010. Available from: https://doi.org/10.1080/00140130701817062

Caffier PP, Erdmann U, Ullsperger P. Experimental evaluation of eye‑blink parameters as a drowsiness measure. Eur J Appl Physiol. 2003;89(3‑4):319‑325. Available from: https://doi.org/10.1007/s00421-003-0807-5

van Boxtel A, Jessurun M. Amplitude and temporal profile of the EMG response of the corrugator supercilii muscle to pleasant and unpleasant pictures. Psychophysiology. 1993;30(6):627‑636. Available from: https://doi.org/10.1111/j.1469-8986.1993.tb02081.x

Larsen JT, Norris CJ, Cacioppo JT. Effects of positive and negative affect on electromyographic activity over zygomaticus major and corrugator supercilii. Psychophysiology. 2003;40(5):776‑785. Available from: https://doi.org/10.1111/1469-8986.00078

Ekman P, Friesen WV. Nonverbal leakage and clues to deception. Psychiatry. 1969;32(1):88‑106. Available from: https://doi.org/10.1080/00332747.1969.11023575

Henderson JM. Eye movement control during visual object processing: Fixation selection in humans and macaques. Vision Res. 2003;43(9):1181‑1191. Available from: https://doi.org/10.1016/S0042-6989(03)00062-6

Rayner K. Eye movements in reading and information processing: 20 years of research. Psychol Bull. 1998;124(3):372‑422. Available from: https://doi.org/10.1037/0033-2909.124.3.372

Ahlstrom U, Friedman‑Berg FJ. Using eye movement activity as a correlate of cognitive workload. Int J Ind Ergon. 2006;36(7):623‑636. Available from: https://doi.org/10.1016/j.ergon.2006.04.002

Fairclough SH, Houston K. A metabolic measure of mental effort. Biol Psychol. 2004;66(2):177‑190. Available from: https://doi.org/10.1016/j.biopsycho.2003.10.001

NASA Human Performance Research Group. Task Load Index (TLX) v1.0. NASA Ames Research Center; 1986. Available from: https://humansystems.arc.nasa.gov/groups/TLX/
