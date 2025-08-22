+++
title = 'Transport Master Tracks'
weight='4'
+++

To control the tempo of the transport from a track, the track must be made the *Transport Master*.  There are two ways to accomplish this, the first is by configuring the track's *Sync Source* parameter in the session.

![Transport Master Configuration](../transport-master.png)

Most of the names in the *Sync Source* menu represent things that generate sync pulses.  The name *Master* is a special case that means that this track would like to sync with the Transport, but it wants to **control** the transport tempo rather than following it.

For old Mobius users, this is similar to the old *Sync Mode* parameter value named *Out*.

When a track using *Sync Source Master* is finished recording, the length of the track is analyzed and converted into a tempo to give to the transport.  The formula for calculating the tempo is somewhat complex, but is obvious in most cases for shorter loops where it behaves much like *tap tempo*.  For long loops of many seconds, it is influenced by the *Bars Per Loop* parameter which will divide long loops into smaller sections before deriving the tempo.  The resulting tempo will then be constrained by the *Min Tempo* and *Max Tempo* parameters in the same way as using the *Tap* button in the transport element.

When a track is the Transport Master, the transport will be started automatically as soon as the track finishes recording.  If the *Send Midi* transport parameter is also checked, this will begin generating MIDI clocks.

#### Multiple Tracks with Sync Source Master

There can only be one Transport Master track at a time.  If you have several tracks configured with *Sync Source Master*, the first one recorded will become the transport master, and the others will revert to synchronizing with the Transport itself.

This is different than old Mobius behavior where if a track used SyncMode=Out and there was already an OutSyncMaster, it would switch to using *Track Sync* instead.

#### Changing the Transport Master Track

The track that is considered the transport master may be changed at any time by
sending the *SyncMasterTransport* function to the desired track.  When that happens, the
length of the new track determines the transport tempo.  Even tracks that did not use *Sync Source Master* can request to become the transport master.

The master track may also be *disconnected* from the transport.  Disconnection may be requested by sending the *SyncMasterTransport* function to a track that is already the transport master.  In other words, the *SyncMasterTransport* function toggles the state of being the transport master.

A track may also be disconnected from the transport if the active loop is reset, or if the track switches to a loop that is empty.  

Once a the transport master track is disconnected, another master will be automatically
selected if that track is configured with a *Sync Source* of *Master* and it is changed to have an active loop that is not empty.  This may be done by re-recording an empty loop, or switching from an empty loop to a loop that is not empty.  This is called making the track "available".  Only tracks that have *Sync Source* *Master* will be automatically selected as the master.  A track that does not use *Master* can only become the master by sending it the *SyncMasterTransport* function manually.  

#### Editing the Transport Master Track

While a track is connected to the transport, changes made to the track that
alter it's size may result in a corresponding change to the transport's tempo.
Not every change to
a track will result in a transport tempo change.  If you enlarge the
track using "rounding" functions like Multiply, InstantMultiply, or
Insert, or use forms of quantization, the fundamental beat length of the track
will remain the same and the transport tempo will not change.
Examples of changes that will change the fundamental beat length are Unrounded Multiply
and Unrounded Insert without any quantization.

If you reset the loop in the master track, or switch to a loop that is empty, this
does not automatically reassign the master track and will not alter the transport
tempo.  The track enters a state of being disconnected from the transport and the transport is allowed to run at it's current tempo.  If you then switch to a non-empty loop or re-record a new loop in the master track, it will reconnect to the transport and possibly change it's tempo.

