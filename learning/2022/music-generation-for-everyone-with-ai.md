# Music Generation for Everyone with AI

In recent years, AI has transformed many industries, and the music industry is not an exception. While its major achievements in music may not be in mainstream media, today, the technology can do as much as generating music from scratch. This blog post takes a look at some machine learning tools that can be used to create music. We’d play around with some of these tools or identify music/sounds they have generated in the past.

## Some AI Tools that create Music

Before deciding on which tool to discuss, I searched for open-source AI tools that can be used to create music melodies. Google’s Magenta seemed to be one of the most prominent results. I also found Open AI Jukebox, another open-source AI tool for music creation.

There were some commercialized AI tools I found as well. One was AIVA and the other was Soundraw. We’d talk about each of these.

1.  ## Magenta
    

Magenta is an open-source AI project by Google for generating music. Its primary objective is the showcase the creativity of AI systems.

Magenta has many open-source projects for creating music. With Magenta Studio, you can generate different variations of music without writing a line of code. 

Magenta Studio has different plugins for music generation. Some may require input MIDI files while others may not. For instance, the Interpolate plugin takes in two MIDI files and combines them uniquely to generate a new beat. Whereas, the Generate plugin generate beats without an input MIDI file.

If you want to get granular with the tool, you can do so with JavaScript using the Magenta.js API or with Python using the Magenta python package. With Python, install magenta package using pip then you can use the NoteSequence class to make sounds on your own. Magenta has different RNN models. The three most popular are:

* MusicVAE: This is an autoencoder that generates new notes on its own.
    
* MelodyRNN: This receives a note sequence and generates a pattern continuation.
    
* Music Transformer: This uses a transformer to generate coherent sound for 60 seconds.
    

Now let’s use MelodyRNN to create music sound. In this [<ins>Jupyter Notebook</ins>](https://colab.research.google.com/notebooks/magenta/hello_magenta/hello_magenta.ipynb), you’d find the code that explains how to use Magenta RNN models. As earlier mentioned, MelodyRNN creates a continuation of a tone. I tweaked the codes to create a continuation of the popular ‘Twinkle twinkle little stars’ poem.  

Here is the result…

I tried using the MusicVAE model. The MusicVAE model creates as many samples of music tone as you desire. It does not require any previous tone but rather creates a new tone from scratch. I used the MusicVAE model to create the following tones…

  

Note that songs created on Magenta are under the CC0 license which means whatever sound you create with the tool is recognized as yours.

2.  ## Open AI Jukebox
    

Jukebox is a tool by Open AI for creating audio with basic lyrics. Their generative model uses an autoencoder to generate new sounds. An autoencoder has two parts: the encoder and the decoder. The encoder compresses the input data to a smaller dimension while the decoder learns how to reconstruct the compressed data to the original input file. 

In the same vein, the Jukebox autoencoder was trained by initially compressing the input sequences of the input file (done by the encoder), generating some ‘noise’ in a lower-dimensional space, and then upsampling it back to the initial audio (done by the decoder). This way, it learns how to create music from little or nothing. The model was trained on 1.2 million songs of which 50% were in English. They also captured the lyrics and metadata of the songs during pairing.

It is worthy of note that generating music with Jukebox is compute-intensive, hence it is strongly advised to use a powerful GPU or use a less powerful model to generate the music. You can tweak different settings before generating your song. The platform allows you to either create the song from scratch or generate a continuation from another song. You can also define the lyrics you want or allow Jukebox to create the lyrics itself (although the generated lyrics are usually not perfect).

I ran a [<ins>code</ins>](https://colab.research.google.com/drive/1sJda9v46gNzBc7m59MP5zn63AWc-axCY?usp=sharing) written by [<ins>YouTuber Broccaloo</ins>](https://www.youtube.com/c/Broccaloo) to create a 30-second music with Jukebox, changing a few parameters. This was the result..

Because I used a low-compute model, the song was not so nice. Watch this video to listen to nice [<ins>music</ins>](https://www.youtube.com/watch?v=q21I7YO-MEs&ab_channel=GabeMillerMusic) from Jukebox.

3.  ## AIVA
    

AIVA is another great tool for creating soundtracks. Their algorithm was trained on over 30,000 music melodies from reputable artists. AIVA is one of the most commercial tools used for music generation. While they have different cadres of subscriptions, there is also a free plan that allows you to create music beats off other songs. You however have no copyrights to the soundtrack and cannot use it for monetization purposes.

To create a track, create an account and select a song profile which you want your generated track to stem from. Alternatively, you can upload MIDI or MP3 files of your desired soundtrack. You will then be prompted to select the key signature you want the output file to be, the kind of emotions you want to soundtrack to pass across, and the duration of the soundtrack. After completing the settings, AIVA creates completely new soundtracks in a few minutes. You can also edit the generated soundtrack to your taste. Check out this [<ins>YouTube playlist</ins>](https://www.youtube.com/playlist?list=PLv7BOfa4CxsHAMHQj0ScPXSbgBlLglRPo) to see other songs created with AIVA.

4.  ## Soundraw
    

Soundraw is yet another AI tool used for creating royalty-free music. The tool also has a plugin that you can connect to PremierPro for video soundtracks. You can use Soundraw to create music without creating an account but the generated cannot be downloaded until you subscribe to their plan. After subscribing to one of their plans, you can easily create sounds by setting the theme of the song (whether for the vlog, jungle, games, corporate, etc), the mood (whether happy, exciting, emotional, relaxing, etc), the length, the tempo, the tempo, etc. You can also edit the output song and use it for any purpose.

Watch this video to see how to create a movie soundtrack with Soundraw and Adobe Premiere Pro.

## In Conclusion

In conclusion, I should mention that using these tools to create good music requires some knowledge of music. You should understand what notes are, how to mix instruments and beats, how to create melody, and so on. Only then can you wield these tools to their maximum potential.

For Magenta and Toolbox, you may also need some coding experience, particularly Python. You may also require a decent understanding of RNNs. This will enable you to use transfer learning methods to train their already created models for new possibilities. If, however, you are using commercial tools such as AIVA or Sundraw, creating music can take as low as five minutes. You only need to create an account, subscribe to a plan, and customise the AI prompt to create sounds that suit your need.