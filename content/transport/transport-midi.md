+++
title = 'Sending MIDI Clocks'
weight='3'
+++

The Transport now controls the way in which Mobius generates MIDI clocks, replacing the
older concept of *Out Sync Mode*.  Once the transport tempo is defined, and the transport is *started* MIDI clocks may or may not be generated.  If you want to generate MIDI clocks while the transport is running you must check the *Send Midi* parameter.  When this parameter is checked, a MIDI *Start* or *Continue* message is sent whenever the transport is started along with clocks at the transport's tempo.  When you stop the transport a MIDI *Stop* message is sent.

When the transport is stopped, you can choose whether or not to continue sending MIDI clocks.  It is usually benneficial to keep clocks going even while stopped so that you give external devices time to adapt to tempo changes before they are started.  Some older devices may be confused by that, in which case you can control this with the *Send Clocks When Stopped* parameter.

The *Manual Start* option is a more advanced topic that will be discussed in detail later.  If this option is checked, a MIDI *Start* message is not sent immediately when the transport is started, instead it waits for you to send it with the *MidiStart* action that may be bound to a footswitch or other trigger.

The *Min Tempo* and *Max Tempo* parameters are used when defining the transport tempo from a *Master Track*.  This is discussed later.

#### Metronome

While not available yet, the transport will support an optional metronome.  Like most metronomes it will play a short sample on each beat, bar, or loop point that the transport reaches once it has been started.  Also planned are "count in beats" which are common in other applications.  This is still under development so suggestions are welcome.

#### For Old Mobius Users

Talking about what the transport does and how it is used may be difficult for older Mobius users.  Mobius grew up without a transport and it evolved ways to accomplish the same things using different terminology.  
For older users, the simplest way to think of the transport is as a short empty track that you
record simply for the purposes of synchronizing other tracks.  This was a common technique in the past.
This empty track would be the Out Sync Master, it would generate MIDI clocks, and the other tracks
could synchronize with it using Track Sync.

Like an empty  track, the transport has a length, this length can be converted into
a clock tempo, and the length can be divided into smaller units.  The subdivisions of a track have been
called *Cycles* and *Subcycles*.  The transport uses the more familiar terms *Bars* and *Beats*.
Unlike a track, the Transport does not record or play any audibile content, and the tempo can
be more freely controlled.

Old-school loopers have come to think of a transport as a *bad thing*.  It is something that locks you into
a tempo and forces you to make loops that are of a pre-defined size.  They much prefer "first loop capability" where you can define the length of loops on the fly using any tempo or length they choose at the time.  It is important to understand that while the Mobius transport can be used to record loops of a pre-defined tempo and size, that is only one way to use it.  When you think about it, selecting a tempo using "tap tempo" is really no different than recording a "first loop".  You are defining a span of time with two presses of a button, and once that span of time is locked in, you can choose to synchronize with it.

What makes the Mobius transport different than synching with the plugin host transport, is that the tempo of the transport can be defined by recording a live audio track.  To do that, the track is configured to be the *Transport Master*.

