The accompanying files contains the "Online English copy-typing" data
and auxiliary files for running analyses reported in

Neil Dhir, Mathias Edman, Álvaro Sánchez Ferro, Tom Stafford, & Colin
Bannard (2020). Identifying Robust Markers of Parkinson's Disease in
Typing Behaviour Using a CNN-LSTM Network. CoNLL 2020

This includes key identity and timing information for copy-typing of
15 English sentences by 100 people with Parkinson's disease and 130
controls.

The typing data is in CoNLL_2020_Online_English.csv. Columns for this
are as follows:

key: the key pressed
response_id: unique identifying code for this participant typing this
target sentence
response_content: response for this sentence as typed in full
participant_id: unique ID for participant
sentence_id: identifier for target sentence
sentence_content: target sentence as displayed to the participant
diagnosis: 1=Typist has had a diagnosis of Parkinson's disease;
0=Typist has not had a diagnosis of Parkinson's disease
keydown: Timestamp for press of key in milliseconds
keyup: Timestamp for release of key in milliseconds

Columns for MedicationInfo.csv are as follows:

TypingID: unique ID for participant
MEDICATED: 1 if the participant had taken medication for management of
Parkinson's disease on the day of participation. 0 otherwise.

online_english_fold_all.csv contains information about the data folds
used in analyses reported in the paper. The columns are as follows:


Participant_ID - unique ID for participant
Sentence_ID - identifier for target sentence
fold - the data fold for this participant typing this sentence.

NOTE: The following interpolation step was performed in order to deal
with occasional single keydown or keyup events that were lost during
online data collection:

1. If a keyup event had no paired keydown timestamp then a) if it was
the first key in the sentence then the missing keydown timestamp was
set to be the keyup time for that key minus the median keyhold time
for that participant and sentence. Otherwise b) the missing keydown
timestamp was set to be the timestamp of the last keydown plus the
interval between the keyup timestamps for the last and the current
key.

2. If a keydown event had no paired keyup timestamp then a) if it was
the first key in the sentence then the missing keyup timestamp was set
to be the keydown time for that key plus the median keyhold time for
that participant and sentence. Otherwise b) the missing keyup
timestamp was set to be the timestamp of the last keyup minus the
interval between the keydown timestamps for the last and the current key.

