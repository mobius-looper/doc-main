+++
title = 'Synchronized Recording'
weight='5'
+++

Tracks that are not the transport master track can synchronize with the transport
by setting their *Sync Source* to *Transport*.  New recordings in those tracks will begin
and end when the transport reaches the location specified by the *Sync Unit* parameter which may be either *Beat*, *Bar*, or *Loop*.  To synchronize with the transport it must be started, either manually with the *Start* button in the transport UI or automatically when a master track is connected.

Synchronizing with the Mobius transport is very much like synchronizing with a plugin host's transport.

For more on other forms of synchronization see the [Synchronization](../synchronization) chapter.
