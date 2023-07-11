# Wav2Vec2.0-hindi

## Data 
Swayam video lectures aligned with transcription. 3 splits of this data worth:
1. 15 mins 
2. 1 hour 
3. 2 hour

## Comparisons

From each of the data points above, we can understand the improvements in the Wav2Vec2.0 model. For a better comparision we also test it against a GMM-HMM model built with Kaldi. The Word-Error rates(WER)% for each split came out to be as follows:
1. Kaldi - 10 Hours - 29.79% WER
2. W2V - Pretrained - 87.66% WER
3. W2V - 15 Mins fine tuning - 62.70% WER
4. W2V - 1 Hour fine tuning - 50.13% WER
5. W2V - 2 Hour fine tuning - 39.8% WER

### Post-processing 

After manually going through the outputs of the final W2V model, decision to post-process the output was taken because the errors were minor and the ASR output was correct pronunciation-wise but due the different accent of the Indian speakers W2V was not able to map to the correct words due to lack of a language model. 3 types of post-processing features were used:
1. Removing repitions.
2. Removed filled pauses.
3. Since wav2vec has no language model, using edit distance to edit minor changes when the transcription was almost correct.

### Results after post-processing

Kaldi - Actual - 29.79% WER
Kaldi - Post-processed - 29% WER
W2V - Actual - 39.8% WER
W2V - Post-processed - 32.4% WER
