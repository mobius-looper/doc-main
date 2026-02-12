+++
title = 'MIDI Tracks and PlaySync'
weight='5'
+++

**PlaySync** is a concept that applies only to MIDI tracks at this time, though some aspects of it may apply to audio tracks in the future.  It replaces the earlier *follower* options.

We usually think of *synchronization* during recording.  Making a loop that synchronizes with the host, or another track.  And once recording is over, synchonization ends, and the loop plays.
PlaySync is a form of synchronization that happens *after* recording or loading a MIDI track.  .  It allows MIDI tracks to automatically respond when other tracks are recorded, or stop and start.

It is most useful for pre-recorded MIDI loops used as background material, such as a drum pattern or bass line.

To use PlaySync, you first decide what this track is following.  It may either be the Transport or the Leader Track.  When this sync source starts and stops, the MIDI track will also start and stop.  More importantly, when the MIDI track starts it will *resize itself* so that its tempo matches the source tempo.  

In the Session editor, select the midi track, and the *Follow* category.

#### Play Sync

This field determines what if anything the track will follow.  If it is none, the
track behaves normally and is under manual control.

If it is set to *Transport* the track will follow the transport.



