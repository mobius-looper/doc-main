+++
title = 'Realign'
weight='7'
+++

The Realign and MuteRealign functions have not changed their behavior, but the way in
which they are quantized is different.

In prior builds, the timing of a *Realign* was controlled with the parameter
named *Realign Unit* which had these values:

* Loop
* Bar
* Beat
* Now
* SyncUnit

This parameter is now called *Realign Quantize* which has all of the standard
options for quantization:

* Off/None
* Subcycle
* Cycle
* Loop
* Marker
* SyncStart
* Beat
* Bar
* LeaderSubcycle
* LeaderCycle
* LeaderLoop
* LeaderMarker

The default value for *Realign Quantize* is now *Off* which is the equivalent of the previoius option *Now*.  It means that the loop is realigned instantly without waiting.

Because some of the options include *Leader* quantization points, there is a fallback parameter named *Realign Quantize Fallback* that is used when there is no leader.  It has all of the same options except the leader points.

#### Realign Correction

This parameter is the same as it was in prior builds.  There are two possible values:

* Start
* Nearest

The correction option is used when the loop being realigned is *larger* then the loop it is realigning with.  For example a leader loop that has 1 cycle, and a follower loop has 4 cycles.

When *Realign Correction* is set to *Start* it means that the follower loop will always move
to a location within it's first cycle that matches the leader loop location.

When *Realign Correction* is set to *Nearest* the follower loop will move to a location within whichever cycle the follower is currently playing.  The location that is nearest to the current location, that is aligned with the leader.

When the follower loop is *smaller* than the *leader*, *Realign Correction* does not apply.
In that case the current leader location is *wrapped* to calculate the corresponding location in the follower loop.  

#### Track Realign vs. Transport Realign

There are two sets of functions and parameters with *Realign* in their names.

*Realign* forces a track to move so that it becomes aligned with the Transport.

*TransportRealign* forces the Transport to move so that it becomes aligned with a track.

The choice of which one to use depends mostly on whether the transport is generating MIDI clocks to send a sequencer that is making audible sounds.  In that case you may have a preference for which one of the two sound sources has to jump to a new location to bring both into alignment.





