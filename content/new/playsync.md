+++
title = 'MIDI Tracks and PlaySync'
weight='5'
+++

**PlaySync** is a concept that applies only to MIDI tracks at this time, though some aspects of it may apply to audio tracks in the future.  It replaces the earlier *follower* options.

We usually think of *synchronization* during recording.  Making a loop that synchronizes with the host, or another track.  And once recording is over, synchonization ends, and the loop plays.

PlaySync is a form of synchronization that happens *after* loops are recorded.  It allows MIDI tracks to automatically respond when other tracks are recorded, or stop and start.

It is most useful for pre-recorded MIDI loops used as background material, such as a drum pattern or bass line.

To use PlaySync, you first decide what this track is following.  It may either be the Transport or the Leader Track.  When this sync source starts and stops, the MIDI track will also start and stop.  More importantly, when the MIDI track starts it will *resize itself* so that its tempo matches the source tempo.  

To configure PlaySinc, in the Session editor, select the midi track, and the *Follow* category.
 
#### Play Sync Source

This field determines what if anything the track will follow.  If it is none, the
track behaves normally and is under manual control.

If it is set to *Transport* the track will follow the transport.

If it is set to *Leader* the track will follow another audio or MIDI track.  This will usually be the *default leader* shown in the UI.  The default leader many change manually or automatically, and every time it changes the follower will resize itself to match the new leader.

A MIDI track may also have a *fixed leader* that does not change.  What leader a track will follow is specified under the *Sync* category in the session editor in the field labeled *Leader*.  When this is set to *Default* it will follow whatever leader is currently selected in the UI.  When this is set to a track number it will only follow the numbered leader.

#### Follow Start

This is the most important option and is usually checked.   When checked this track will start whenever the Transport or leader track starts **and** it will immediately just the the track's tempo to match the source.

#### Follow Start Muted

This is the same as *Follow Start* except that the track will start in Mute mode and must be manually unmuted.
This is used when you want to get the track resized and started playing, but you want more control over when it is audible.

#### Follow Stop

When checked the track will *Stop* whenever the source stops.  If the track was following the *default leader* it will also stop when the leader track is *Reset* or when the leader assignment is taken away leaving no default leader.

This is usually checked when Follow Start is checked.  If it is unchecked it means that it will keep playing
after the sync source is stopped or reset.

#### Follow Mute

When checked the track will *Mute* and *Unmute* at the same time as the sync source.

#### Examples

One handy way to use PlaySync is to audition MIDI loops.  Load a few MIDI files into track loops and have that track configured for PlaySync with the Transport.  Now, whenever you start or stop thetransport the MIDI track will play its loop.  Whenever you change the transport tempo, the MIDI track will also adjust to follow the new tempo.

You might use this to start a MIDI background pattern and adjust its tempo until it feels right.  Then make this track the *default leader* and record other tracks to play along with it.

The other common way to use PlaySync is for an automatic background patern that starts immediately after a track is recorded.  When you begin recording the MIDI follower is stopped and waits for recording to finish.  When recording finishes the track starts playing immediately in sync with the leader track, and using the same tempo.




