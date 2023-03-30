# smart fades

Finds and performs the shortest fade in/fade out necessary to the start and end of an audio file in order for there to be a seamless loop (no discernable click).

The algorithm uses wavelet decomposition to assess the continuity of the signal at its loop points. We start by applying a fade to the start and end of the audio file, and we find the Daubechies (db4) wavelet transform of the last few samples concatenated with the first few. If the maximum of the wavelet transform is below a certain threshold, then the fade is considered to be of sufficient length and is written to the output file. If not, we repeat with a longer fade length.

## usage

`python smartfade.py [filename]`

output is saved as output.wav

## dependencies

Requires Python 3.10, librosa and PyWavelet. Python 3.11 is unsupported by numba at the moment, which is a dependency of librosa, so specifically 3.10 is necessary. The current anaconda distribution comes with 3.10 so I'd recommend using that, though this compatibility issue should be alleviated soon.