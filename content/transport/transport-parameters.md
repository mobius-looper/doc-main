+++
title = 'Transport Parameters'
weight='1'
+++

The transport supports a number of parameters to define how it generates synchronization pulses.
These are currently set in the [Session](session) but other more convenient ways will be provided
in the future.

![Transport Parameters](../parameters.png)

The most important transport parameters are:

* Default Tempo
* Beats Per Bar
* Bars Per Loop

The transport always generates beat pulses at a defined tempo.  There are several ways to define this
tempo, the session just defines the default or *starting* tempo the transport will have when you
bring up Mobius for the first time.  You may also define the tempo during performance by using **Tap Tempo** in the UI, or by recording a **Transport Master** track.  

The *Beats Per Bar* parameter defines the length of a bar in units of beats, and *Bars Per Loop* defines the length of a loop in units of bars.  The most common value for *Beats Per Bar* is 4.  The value of *Bars Per Loop* is often just 1 in which case a bar and a loop will be the same size.

#### Why "Bars Per Loop"?

For the same reason that multiple beats are almost always organized into measures or bars, multiple bars are often thought of as a larger unit of time: a 12-bar blues for example.  While the beats per bar will often stay the same from one performance to another, larger collections of bars will vary depending on the structure of the song you have in mind, or the backing track you are using.  It is not necessary to use Bars Per Loop, but you may find it convenient when recording long tracks.  If you record a track that is 2 minutes long at 4/4 time, it might conceptually be 12, 16, 24, or 32 bars long.  If you know that is what you are going to create ahead of time, you can set Bars Per Loop accordingly which can then assist in selecting synchronization points, rather than having to count bars as they play.   

