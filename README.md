# LSTM-Biometric-sequences-recognition
##introduction
The purpose of this document is to identify a procedure for the proper recognition of the correct motion sequences, through the use of machine learning techniques.
The problem
The input data comes from the acquisition of a series of motion tracking devices (accelerometers) worn by the subject while performing a series of predefined assembly operations.
In particular, six sensors were positioned (3 for each upper limb), and by measuring the instantaneous accelerations and the spatial orientation of the same, they allow to reconstruct the rotation triads relating to the sensors.

They have been made available to 10 series of measures in .csv format with 10Hz sampling rate, with an average duration of about 380/400 sec.
Of these series of measures, 8 are relative to the correct movements, while 2 refers to the erroneous sequences.
The objective of the analysis is to identify a modeling and classification procedures to allow, with sufficient precision, automatically distinguish a correct sequence from the incorrect.
