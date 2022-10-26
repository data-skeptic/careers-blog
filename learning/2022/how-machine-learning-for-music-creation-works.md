# How Machine Learning for Music Creation Works

Machine learning is beginning to make giant strides in music. Google’s Magenta now has several ML models for creating music from scratch. Open AI’s Jukebox is equally conducting intensive research on building a machine learning model that creates music with lyrics.

But how did we get here? In this article, we will discuss the bolts and nuts of building a machine learning model for music generation. It all begins with data.

## MIDI Files

There is no machine learning, and by extension, artificial intelligence without data. By definition, machine learning is the ability of a machine to perform tasks it was not hard-coded to do. This only happens after the model has learned hidden patterns in a given data. 

A MIDI (Musical Interface Digital Interface) file is a type of file that stores the metadata of audio files rather than the actual audio file. It indicates the notes that are played, when they are played, the volume, how long a note was played for, its loudness, and so on. They are the data machine learning algorithms are trained on to create musical sounds. MIDI files are lesser in size than an MP3 file because they don’t try to record the sound as audio information, instead, they store intrinsic information about a song melody.

Initially, MIDI files were exclusively used by musicians and producers. It served as a way to store musical data dynamically. This resulted in the sharp development of electronic musical instruments and musical software in the 1980s.

Today, MIDI has made creating music easier. One can create a melony from the comfort of their home by just playing around with chords and sound arrangements. Since MIDI files do not store the song but rather the melody information, they can be easily tweaked to create other sounds. 

Since the standardization of MIDI in 1983, MIDI has become so critical in creating, storing, and sharing music. Today, [<ins>some say</ins>](https://en.wikipedia.org/wiki/MIDI) that MIDI is to music as USB is to computing.

## How AI Learns from MIDI files

MIDI files are trained on a machine learning model like a natural language processing (NLP) task. The machine learning model receives the MIDI file as a sequence of input and predicts the next note for each time step. The widely used machine learning algorithms for these tasks are Recurrent Neural networks (RNNs), specifically transformers. Some others use autoencoders.

To give a high-level explanation, transformers learn sequential patterns by noting the relationship between the immediate past step and other steps. Having learned from a wide array of data, it can predict the next best note, and the next until the music is complete.

  

## Extracting Audio Features for Machine Learning

Another method of applying machine learning to audio files is feature extraction. A music signal is a representation of sound made up of three properties: speed, frequency, and amplitude.

The speed is defined by how far a signal travels by unit time. The frequency is the number of vibrations per time. While the amplitude is the maximum distance a signal wave travels from its equilibrium point.

Typically, most music signals we see, such as the ones in audio editing software, are represented in the time domain. However, extracting features from signals is done in the frequency domain. This is because the frequency domain separates the unique frequencies represented throughout the music. It has clearer information of the signal and is widely used for audio feature extraction and noise filtering. To convert the sound signal from a time domain to the frequency domain, a Fourier transform is done.

![](https://lh4.googleusercontent.com/m2gi4bFgw2o7DmlVAQ13yc27QKIM7RhxjMY_ltbU8wdk1nun-lHPej-OGQFT0Aet8y4B-HvdWJLisbS-QqLGTFeAz-NdfI7k3SfjjzEqBK1dXbTl28R4lNiQRVrX889Z626QphbT4LJZk6ltmLxZfcLf5z6dj1aOifBvDp-3nMb5-4AfkG7wDpXBig)

Source: [<ins>Polytechnic Hub</ins>](https://www.polytechnichub.com/difference-time-domain-frequency-domain/)

## Windowing Explained

When performing the fast Fourier transform on a signal, there is a possibility that data may be lost. The signals are first broken into small chunks called frames. But if a frame does not have an integer number of periods, the endpoints of the frame (which are discontinuous) will not be accurately transformed. They are rather transformed to some higher frequency in the frequency domain. In other words, after the Fourier transform, the endpoint frames in the time domain leak to new higher frequencies in the frequency domain. This is called spectral leakage.

Windowing is used to solve the spectral leakage problem. It is done by applying a window function to the frame before the Fourier transform is done. Windowing simply takes off the discontinuities at the endpoints of the signals, thus, eliminating spectral leakage. A popular window function is the Hann window function, named after the Australian meteorologist Julius von Hann.

After windowing, the Fourier transform can then be done without frame loss. The output of the Fourier transform is called a spectrum of frequencies which can be visualized using a spectrogram. Machine learning models extract features better from spectrogram representations, than time-domain waveforms which is why it is an important step in sound feature extraction. The figure below is an example of a spectrogram. 

![](https://lh6.googleusercontent.com/GyKsGEzDsBRBKF1eytixrMMqr-AL5qdhbwoAobjNY2MOxhOszrl9ZVkPnvKkRMJ6tCtZGiuHKbSfWW4xI_gQhXzWsld9XWmiqxN02YFAobdMJNd4HBt9OGFOde4SMCNUegHwz9oPhKo8IFA_mqQpbpT0TX1oWJEyl__R8QfcAweK5R4QeoJA5pgibw)

Source: [<ins>Wikipedia</ins>](https://en.wikipedia.org/wiki/Spectrogram)

  

## Mel Scale

The Mel scale is another improved representation of audio signals. At its core, it transforms sound frequencies to a scale similar to how we humans perceive sounds. The general rule of thumb is that humans perceive lower frequencies better than higher frequencies. Thus, we can easily distinguish between 50 and 100 Hz sounds  but cannot distinguish between 1100Hz and 1150Hz.

The formula for converting a frequency spectrum to a Mel Scale is given by:

m = 1127 * log(1 + f100)

Where f is the frequency is Hz. By converting signals to the Mel scale, we enable machine learning models interpret sound frequencies just the way our ears do.

## Mel Frequency Cepstral Coefficients

Mel frequency cepstral coefficients (MFFCs)  is one of the most important methods used for speech recognition, audio classification, noise removal and other speech processing techniques. MFFCs succinctly captures sound details with an array of numbers. The numbers in the arrays, which are called cepstral coefficients, tell us where the spectral energy is mostly concentrated.

Machine learning tends to perform well when trained on MFFCs. It is thus widely used for many machine learning tasks with audio data. You can use the [<ins>Librosa library in Python</ins>](https://librosa.org/doc/latest/index.html) to get your hands dirty with these concepts.

## Tying it all Together

I understand there has been a couple of fancy words thus far. But, the application of these concepts has been profound over the years. It has greatly advanced the field of music information retrieval (MIR), audio processing, and voice translation models. As an example, Google is building a multilingual speech-to-speech translation model called [<ins>Translatotron 2 model</ins>](https://ai.googleblog.com/2021/09/high-quality-robust-and-responsible.html). At the low level, the model receives audio data in Spanish in the form of a spectrogram. This is trained on an attention-based model and then outputs a spectrogram in English. You can read more about this model [<ins>here</ins>](https://ai.googleblog.com/2021/09/high-quality-robust-and-responsible.html).