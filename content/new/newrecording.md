+++
title = 'The Recording Process'
weight='2'
+++

The way you go about creating a synchronized recording has changed significantly.   You can accomplish the same things as you did before, but the parameters you set to do that will be different.

This is the first phase of a multi-phase project that will bring the *Transport* into a much more prominent role as the hub of synchronization services.  What is described in this document will evolve a little more in the near
future, but most of what is presented will remain the same.

In previous releases, the first step in configuring the recording process was to choose a *Sync Source* for each track.  The possible values for this parameter were:

* None
* Transport
* Track
* Host
* Midi
* Master

When synchronizing with *Transport*, *Host*, or *Midi* the start of the recording and it's length
would be determined by the *Sync Unit* parameter which could be *Beat*, *Bar*, or *Loop*.

When synchronizing with *Track*, the start and length of the recording would be determined
by the *Track Sync Unit* parameter with values *Subcycle*, *Cycle*, and *Loop*.

The *Master* option was a confusing special case.  It meant "if there is no master, let the track record freely
and become the master, but if there is a master, synchronize with the Transport".

The *Sync Source*, *Sync Unit*, and *Track Sync Unit* parameters are now gone.  In addition the way you request *threshold* recording is different.

### New Recording Model

The new model for synchronized recording is centered around three main concepts:

1) How long do you want the loop to be
2) When do you want recording to start
3) How should the new loop play along with the host or other tracks

These three concepts can be more succintly called: *Length*, *Start*, and *Alignment*

#### Record Unit

The most important recording parameter is *Record Unit*, which defines how long you
want the loop to be.

Conceptually, it combines the three older parameters *Sync Source*, *Sync Unit*, and *Track Sync Unit*
into one.  The posssible values are:

* Free
* Sync Beat
* Sync Bar
* Sync Loop
* Leader Subcycle
* Leader Cycle
* Leader Loop

When you select *Free*, this is the same as what happened when you set *Sync Source* to *None*.
The track will have no fixed record unit, it may be any length you want.

When you select one of the three *Sync* values, you will be recording units defined by the Transport.
This is the same as what hapened when you set *Sync Source* to *Transport* and used a *Sync Unit*.

Note that in build 46 it is still possible for tracks to directly synchronize with either the *Host*
or with MIDI clocks.  Other than pointing out how to do this below I won't be mentioning it much because
in the next build synchronzing with the host or MIDI will be done a different way, it will be configured
as an aspect of the transport rather than something tracks use directly.  So whenever you see a value starting
with *Sync* you can assume it applies to both the Transport and to the Host.  You're syncing with the Transport,
but the Transport is in turn being controlled by the host.

When you select one of the three *Leader* values, you will be recording units defined by another track.
This is the same as what hapened when you set *Sync Source* to *Track* and used a *Track Sync Unit*.

There is no equivalent to *Master* here.  Any track may become the master track, it does not matter
how it was recorded.

#### Record Start

The second most important recording parameter is *Record Start*.  This defines when you want
recording to begin.  The possible values are:

* Wait for Record Unit
* Immediate
* Threshold
* Sync Start
* Sync Beat
* Sync Bar
* Leader Subcycle
* Leader Cycle
* Leader Loop

In prior releases, when a recording started and how long it lasted had to be the same thing, either a *Sync Unit* or a *Track Sync Unit*.   If *Sync Unit* was *Bar* it had to both start and end on a bar.  But what was less convenient, is if *Track Sync Unit* was *Loop* you could create a loop that was the same size as another but you would have to wait for that loop to play *all the way to the end* before you could start recording.

A major new feature in build 46 is that when a recording starts and how long it is are independent things.  You can record a full loop length from another track, but you can start anywhere you want.

The default value is *Wait for Record Unit*.  This will make recording behave like it did in prior releases.  You have to press the Record button a little bit ahead of the unit you want to record, the track will enter *Synchronize* mode waiting for the host or track to reach that unit, then recording begins.

I expect the most common alternatives to *Wait for Record Unit* will be *Immediate* and *Threshold*.   The others have less obvious use, they're there mostly because *Record Start* is basicaclly just a form of quantization and those are quantization points you can use in other places.  But there are a few potentially interesting use cases, you may wish to start recording when the leader reaches the end, but then only record 4 bars.  Something you can't do when both start and length are locked to the same unit.

#### Late Start Adjstment

This parameter controls the third primary characteritic of sync recording: *alignment*.

I decided to label this *Late Start Adjustment* because that is probably the most common way
to think about it, but what it is doing is making sure that the loop you just recorded will
align properly with whatever it is you are listening to at the time of recording.

Why you might think of this as *late start* is due to a common issue with the old method for
sync recording.  You had to always remember to press the Record button a little bit ahead of the
host bar, or the leader start point, so that Mobius had time to figure out where that was and wait for it.
But if you pressed Record very close to the "downbeat" of the external loop, it might be too late.  The host
had already crossed a bar boundary so you have to wait for the next one before recording can begin.  It doesn't matter how close you were, if you were even a millisecond late you would have to wait a full bar or loop length before
the recording could begin.

What you can do now is set *Record Start* to *Immediate*.  Recording will always begin as soon as you press Record, it doesn't matter if you are before or after the bar.

Being flexible about the start time causes a problem however.  The loop you record will always end up being some multiple of host bars long, but it won't start where the host thinks the downbeat of a bar is.  If a host bar is 4 beats long and you start recording on beat 3 rather than 1, the entire loop will be shifted 2 beats relative to what the host is playing.  You won't notice this immediately after recording the loop, but if you ever stop and restart the host and Mobius from location zero, they will be out of alignment.

To solve this problem the *Late Start Adjustment* parameter has an option called *Start Pad*.  There are a few others but they're not completely working yet so I don't talk about them yet.

Note that in the examples I will usually talk about synchronizing with the host, but the same issue applies
when you are syncing with another track, or with an external drum machine that is feeding us MIDI clocks.

#### Padded Recording

Finally we get to what is probably the most significant enhancement in this release: padded recordings.

When you want to record some number of host bars, but want to start in the middle of a bar, Mobius will inject empty space or "padding" at the start of the loop so that what you end up with will stay in alignment with the host.  It's as if you had pressed Record exactly on the downbeat of the bar you're in but decided not to play anything until the middle of the bar.  It's going back in time to make the recording start when it should have, not where you were when you pressed Record.

This BTW is something the RC-505 does as well.  You can be pretty sloppy about when you press Record.  If you're late it won't force you to wait all the way to the end of the loop, it starts immediately and injects empty space at the front to make up for the lost time.

For EDP users, this is more like TimeCopy followed by Multiply than a Record.  An empty loop is instantly created that is the right size, and Overdub/Multiply immediately starts inside that.  

You might be wondering, if we can go back in time and pretend Record was pressed exactly when the bar started, can we put whatever I was playing at the time in the loop rather than just empty space?  This is something I've seen referred to as "retroactive recording" in other places.  The answer is no, not yet, but it's comming soon.

To get padded recording, set the *Late Start Adjustment* parameter to *Start Pad*.




























