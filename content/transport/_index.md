+++
title = "The Transport"
type = "chapter"
weight='3'
+++

The *Transport* is a new feature in build 30.   It is responsible for the generation of MIDI clocks that can be used to synchronize with external hardware devices or other applications, and is the primary mechanism for recording multiple tracks that play in synchronization with each other without drifting apart.

What the Transport does can be difficult to talk about, depending on
your history with Mobius.  For those that are relatively new, the
Transport may seem obvious.  All DAWs have a similar concept: a tape-like
timeline with a tempo, time signature, a metronome, and control buttons like *Play*
and *Stop*.  Some of the more sophisticated hardware loopers do as
well.

For those that have used Mobius for a long time, the need for the transport may
not seem obvious.  Tracks have long been able to generate MIDI clocks and synchronize
with each other, so why would you be interested in something new that does the same thing?

I'm going to start by describing how the transport can be used from the perspective
of someone new to Mobius, without any preconcieved notions about how things were done in the past.
Later there is a section intended for older users that compares the transport with older, similar
features and explains why you might wish to use the transport instead.

### Transport Basics

Fundamentally, the transport is like a metronome.   You give it a tempo, start it, and while it
is running it will generate *pulses* or *beats* at that tempo.   You can use these beats for several
things, but mostly they are used to start and stop the recording of a track at exact times.

Simple metronomes only generate beats at a defined tempo.  But it is usually desireable to think
about music in larger units of time.  No one turns to their band and says "let's play a 48
beat blues!".  Beats are usually combined into larger units called *measures* or *bars*, and bars
are then combined into even larger units called *songs* or in our case *loops*.

The Transport allows you to define three units of time: *beat*, *bar* and *loop*.
When you create a synchronized recording you can choose to start and stop the recording
on any of these three time units.  The reordings may not all be exactly the same length but they
will all share the same *fundamental beat length*.

These concepts should be familiar to anyone that has experience using a DAW.  Synchronizing
things with the Mobius transport is very much like synchronizing with the plugin host.  It's just
that the transport lives inside Mobius and that gives us more control over how it behaves.
