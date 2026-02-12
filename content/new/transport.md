+++
title = 'Transport Improvements'
weight='6'
+++

The transport now behaves more consistently when it is connected to a *master* track.  The parameters *Manual Start* and *Manual Stop* can be used to control whether the transport should start automatically when it gains a Master.

The *TransportStart* and *TransportStop functions still exist but may now be quantized.

The *TransportTap* function may be used in a binding if you would like to perform tap-tempo from a MIDI controller.

The *TransportRealign* and *TransportMuteRealign* functions can be used to force the *transport* to realign itself with the master track.  The normal *Realign* function works in the other direction, it forces a track to realign with the transport.

As you familiarize yourself with the ways in which the transport can be controlled, it is helpful to think of the transport as if it were a track playing a drum sequence.  The transport has a tempo and a length and a location just like a track.  And when it is sending MIDI to a sequencer it behaves like a track playing a drum pattern, or a bass line, or a chord progression.

When you think of it like a track making sounds of it's own, there is a need to control when it starts and stops and aligns just as you would with any other track.

To confgure the transport, bring up the Session editor, click the *Globals* tab and select the *Sync->Transport* category.

#### Tempo, Min Tempo, and Max Tempo

The tempo you enter will become the initial tempo of the transport when mobius starts or when the session is reloaded.

This also becomes the *goal tempo* when the transport resizes itself to match a new master track.  When analyzing the tempo of the master track, it will find one that resides between the *Min Tempo* and *Max Tempo* values.  If there is more than one option it will choose the one that is closest to the goal tempo.

#### Beats Per Bar

This defines the bar lengh of the transport, and helps guide the automatic tempo selection that happens when a Master track is elected.  It is important to set this before you begin recording tracks so we can make a better estimation
of the freely recorded track's tempo after recording.

It is usually left at 4, but it may be 3 or 7 or any other time signature you want to be using during recording.

If the transport generates MIDI clocks, it should match the time signature of the pattern the external sequencer is playing.


#### Bars Per Loop

When the transport runs, it will continually play a virtual loop that is 1 bar long. You may wish to increase the number of bars in this virtual loop to give you a longer span of time to use for quantization and synchronization.

If the transport generates MIDI clocks, it should match the number of bars in the pattern the external sequencer is playing.

#### Send MIDI Start/Stop/Clocks

When this is checked, Mobius will send MIDI Start and stop realtime messages to a connected device whenever the transport starts and stops.  It will also generate MIDI clocks at the current transport tempo.

#### Send Clocks When Stopped

When checked, MIDI clocks will continue being sent at the transport tempo, even when it is stopped.

#### Manual Start

When checked, the transport will redefine its tempo whenever a master track is connected, but it will not start playing automatically.  You must manually start it when ready using the *TransportStart* command.  When the transport is finally started, it will not necessarily start from the beginning.  If a Master is defined, the transport will immediately realign it's playback location with the master track and send a MIDI *Song Position* message containing it's new location.

#### Manual Stop

When this is unchecked, the transport will pause whenever the master track is unassigned, or wenever the master track is reset or switches to an empty loop.

If you would like the transport to continue when these things happen, check *Manual Stop*.  When checked you must stop the transport manually using the *TransportStop* function.

#### Start Quntize

This parameter controls when the *TransportStart* function will happen.  It is typically
used when you also have *Manual Start* enabled.  When *Manual Start* is disabled, *Start Quantize* is usually irrelevant because the transport starts automatically with the master.

The possible values are:

* None
* Master Cycle
* Master Loop

When set to *None* the transport will start immediately when asked.

When set to *Master Cycle* or *Master Loop* the transport will wait until the master track
reaches one of those two points.

Controlling when the transport starts is mostly useful when it is also generating MIDI clocks
to send to an external drum machine or sequencer.  Since those devices make sounds, you may
need to control when they start being audible.

If there is no master track, *Start Quantize* is ignored, and the transport starts immediately.

#### Realign Quantize

This parameter controls when the *TransportRealign* and *TransportMuteRealign* functions happen.  It is conceptually simialr to *Realign* and *MuteRealign* use in tracks, but it effects the transport only.

When you realign the transport, what you are doing is making the transport move to a location that matches the master track.   You may wish to do this if you think what the tracks are doing is fine, but it is the transport and the MIDI clocks it is generating are out of alignment.

Realigning the transport will cause it to jump to a location that matches the master track, and this will also send a MIDI *Song Position* message to bring an external drum machine or sequencer back into alignment with the track.

Quantizing when this happens can be useful if you want this sudden jump to happen at a musically useful time relative to what the master track is doing.

The possible values for *(Transport) Realign Quantize* are:

* None
* Master Cycle
* Master Loop

#### Stop Quantize

This parameter controls when the *TransportStop* function happens.  It is normally used only when *Manual Stop* is enabled.  It may have these values:

* None
* Master Cycle
* Master Loop
* Transport Start
* Transport Beat
* Transport Bar

Like *Start Quantize*  you may choose to time the stopping of the transport with a location in the master track.

But unlike *Start Quantize*, since the transport is running and advancing through a timeline, it is also possible to quantize stop to a location in the transport itself.

Controlling when the transport stops is useful when MIDI clocks are being generated and you want to wait until the external drum machine or sequencer reaches a good stopping point in its pattern before stopping.

#### Stop Quantize Fallback

Transport Stop Quantize is the only parameter where it makes sense to have a fallback.

If there is a master track, locations in the master can be used to determine when it stops.

If there is no master track, then then locations in the transport itself can be used.



