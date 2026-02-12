+++
title = 'Transport Improvements'
weight='6'
+++

The transport now behaves more consistently when it is connected to a *master* track.  The parameters *Manual Start* and *Manual Stop* can be used to control whether the transport should start automatically when it gains a Master.

The *TransportStart* and *TransportStop functions still exist but may now be quantized.

The *TransportTap* function may be used in a binding if you would like to perform tap-tempo from a MIDI controller.

The *TransportRealign* and *TransportMuteRealign* functions can be used to force the *transport* to realign itself with the master track.  The normal *Realign* function works in the other direction, it forces a track to realign with the transport.

To confgure the transport, bring up the Session editor, click the *Globals* tab and select the *Sync->Transport* category.

#### Tempo, Min Tempo, and Max Tempo

The tempo you enter will become the initial tempo of the transport when mobius starts or when the session is reloaded.

This also becomes the *goal tempo* when the transport resizes itself to match a new master track.  When analyzing the tempo of the master track, it will find one that resides between the *Min Tempo* and *Max Tempo* values.  If there is more than one option it will choose the one that is closest to the goal tempo.

#### Beats Per Bar

This defines the bar lengh of the transpor, and helps guide the automatic tempo selection that happens when a Master track is elected.  It is important to set this before you begin recording tracks so we can make a better estimation
of the freely recorded track's tempo after recording.

It is usually left at 4, but it may be 3 or 7 or any other time signature you want to be using during recording.

#### Bars Per Loop

When the transport runs, it will continually play a virtual loop that is 1 bar long. You may wish to increase the number of bars in this virtual loop to give you a longer span of time to use for quantization and synchronization.

#### Send MIDI Start/Stop/Clocks

When this is checked, Mobius will send MIDI Start and stop realtime messages to a connected device whenever the transport starts and stops.  It will also generate MIDI clocks at the current transport tempo.

#### Send Clocks When Stopped

When checked, MIDI clocks will continue being sent at the transport tempo, even when it is stopped.

#### Manual Start

When checked, the transport will redefine its tempo whenever a master track is connected, but it will not start playing automatically.  You must manually start it when ready using the *TransportStart* command.  When the transport is finally started, it will not necessarily start from the beginning.  If a Master is defined, the transport will immediately realign it's playback location with the master track and send a MIDI *Song Position* message containing it's new location.

### Manual Stop

When this is unchecked, the transport will pause whenever the master track is unassigned, or wenever the master track is reset or switches to an empty loop.

If you would like the transport to continue when these things happen, check *Manual Stop*.  When checked you must stop the transport manually using the *TransportStop* function.

#### Start Quntize

When set to *None* the transport will start immediately when asked.

When set to *Master Cycle* or *Master Loop, the transport will wait until the master track reaches those locations before starting.  This is most useful when the transport is generating MIDI clocks and you want the external device to staart playing its pattern at exectly the same time as a master point so they are aligned.

#### Realign Quantize

#### Stop Quantize

#### Stop Quantize Fallback

