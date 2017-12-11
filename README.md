# pycochleagram 
Generate cochleagrams natively in Python. Ported from Josh McDermott's MATLAB code. 

## Installation
If anyone knows how to setup Python packages for distribution (or otherwise 
how to handle imports for Python code that isn't packaged but is still shared), please let me know. Until then, using these modules can be a bit painful. 

1) Download or clone this git repository containing the pycochleagram source code.
2) Add the path of the folder containing the pycochleagram source code to your $PYTHONPATH environment variable. For instance, if pycochleagram was downloaded to `~/Dev/pycochleagram/`, you could add the following to your .bashrc:
```export PYTHONPATH="~/Dev/pycochleagram/:$PYTHONPATH"```
3) Imports should work like `from pycochleagram import cochleagram as cgram`. Let me know if you have issues with this (at some point I'll turn this code into a proper package).

## Demo
There are a few demos in `demo.py`. To run these demos, navigate to the root of the project folder and run `python demo.py`. Note, you can enable audio playback with `python demo.py -p`, but be warned that this can get very loud. 

## Overview:
**Note**: Numpy/Scipy's FFT implementation can be ridiculously slow for certain sized inputs. You can install pyfftw to get around this issue, but this must be done on a singularity container on OpenMind. 

This package contains four main modules:
+ *erbfilter*: Functions for generating ERB-cosine filters. These functions
are available in the MATLAB implementation. 
+ *subband*: Functions for performing subband decomposition using filterbanks made with `erbfilter`. These functions are available in the MATLAB implementation. 
+ *cochleagram*: Convenience methods for quickly generating cochleagrams. Also, provides functions for cochleagram inversion (i.e., generating a signal waveform from a cochleagram). These methods are not readily available in the MATLAB implementation. This is intended to help you get started.
+  *utils*: Provides a collection of helpful methods for working with cochleagram generation, including some plotting and audio playback functions, as well as some fft-like methods that allow for easy switching between fftpack (numpy/scipy) and fftw. **NOTE**: when working with pyaudio and the audio playback functions in `utils`, the sound output can be **very loud**. Take caution when working with this method.

##TODO:
+ convert docstrings to np format
+ build and format docs
+ put docs on github
+ test padding (pad_factor)
+ sensible parameters for downsampling?
+ clean up old and deprecated methods
+ write readme
+ python compatibility issues
+ erb filters fails with certain arguments: 
`N: 680, sample_factor: 15, signal_length: 2433, sr: 32593, low_lim: 147, hi_lim: 16296, pad_factor: None`
