# LSTM-Biometric-sequences-recognition
##Introduction
The purpose of this document is to identify a procedure for the proper recognition of the correct motion sequences, through the use of machine learning techniques.
##The problem
The input data comes from the acquisition of a series of motion tracking devices (accelerometers) worn by the subject while performing a series of predefined assembly operations.
In particular, six sensors were positioned (3 for each upper limb), and by measuring the instantaneous accelerations and the spatial orientation of the same, they allow to reconstruct the rotation triads relating to the sensors.

They have been made available to 10 series of measures in .csv format with 10Hz sampling rate, with an average duration of about 380/400 sec.
Of these series of measures, 8 are relative to the correct movements, while 2 refers to the erroneous sequences.
The objective of the analysis is to identify a modeling and classification procedures to allow, with sufficient precision, automatically distinguish a correct sequence from the incorrect.

##Critical issues
The reduced number of sequences available does not allow a classical supervised learning approach / unsupervised (clustering), given the number of input parameters and the variability of the acquisition conditions (variable length of the sequences, internal sample variance due to differences in the speed of execution of the same sequence and differences in the posture of the subject). Precisely for this reason it is not possible to refer to a sequence "ideal" defined a priori, since it is subject itself to contingent conditions, which would create a high variance in comparison with the successive acquisitions, considerably increasing the margin of error.
We have therefore decided to use a new approach that exploited the ability of some deep neural network models (Deep phased-LSTM networks) to generalize in a very effective way sequences of multivariate data.

##Classification of subsequences
To make sure that the algorithm could learn and generalize the input sequence, we have divided each original sequences into n subsequences of fixed length, through a rolling window with width 128 samples.

##Results
The analysis produced significantly positive results. Despite the reduced number of samples to train the  model, it was possible to recognize with a good approximation the incorrect correct sequences (see. Figure 3), in a completely automatic way and without any a priori mathematical definition of the sequence, with a good robustness to capture errors (variable length of sequences) and the intrinsec variance of the system under observation (low precision in the repeatability of the measure due to the human factor).

In Figure 4 it has been reported the normalized error respect to the objective function, where it can be seen in the correct sequences, the procedure was reproduced with an 80% accuracy (the negative spikes are present in correspondence of the end of the motion sequence).

##Future developments
The advantage of being able to code a sequence of movements, with a short learning time, allows the correct sequence identification even without the support of specialized technical skills.

A further benefit of this solution consists in the possibility to classify the sub-sequences using the neural activation values of the predictive model. Doing so it is possible to compress with a minimum loss of resolution (ie by keeping more than 80% of the original information) each sequence of 128 samples x 18 parameters, using only a vector of 4 floating point elements, with a compression ratio of 1:576.

With an higher number of acquisitions the spectral analysis, the variance and mean value of the error (see. Figure 6) can also be used for a classification of the types of error in the sequences, allowing to intervene in a targeted manner on posture errors, fatiguing and/or dangerous movements.