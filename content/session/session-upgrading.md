+++
title = 'Upgrading From Older Releases'
weight='4'
+++

If you have been using Mobius for some time, you will probably have created several *Track Setups* and *Presets*.  When you first run the most recent Mobius release, all existing Setups are converted into Sessions, and any existing Presets are coverted into *Overlays*.  An overlay is a set of parameter values that may be placed "on top of" the parameters in the session.  Using overlays is a complex topic that is described in detail in [This Document](../overlays).

The former *Tracks* menu item has been replaced by *Sessions* and the former *Presets* menu item has been replaced by *Overlays*.  Under these menus you will see the names of the sessions and overlays much like they were in the old menus.

It should be noted that in older Mobius releases, changing a *Setup* was a relatively light weight
operation.  You could change Setups at any time, even during the middle of a song you were performing.  Sessions should be thought of as heavier things that are changed less often.  Changing a session may cause audio artifacts, particularly if the session includes audio or midi content that needs to be loaded into the tracks.  Since sessions control the order and type of each track, changing a session could cause a track that is actively playing something to be deleted.  Often changing sessions was done only to change a few parameters such as the track's input and output ports, and mixer levels.  There are other ways to do that now.

