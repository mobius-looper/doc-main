+++
title = 'Manage Sessions'
weight='2'
+++

The *Manage Sessions* window allows you to view all of the sessions that have been saved
and perform a few operations on them.

![Session Manager Window](../session-manager.png)

If this is a new installation, there will be a single session named "Default".
If you have used older versions of Mobius 3, all of the *Setup* definitions from prior builds will have been converted into sessions with the same name.   The session that is currently being used will have the word "Active" in the Status column.

The window contains one large table listing all of the saved sessions.  If you highlight a row and right click the mouse, a popup menu appears.

![Session Manager Menu](../session-manager-menu.png)

The *Load* item will load the session from the file system and make it the active session.  In the past, Setups were relatively light-weight things, consisting of little more than a few parameter definitions.  Sessions should be thought of as heavier things since they can contain content as well as parameters.   You normally would not change sessions often, and when you do tracks that are currently playing something may be removed or replaced.

This differs from how Setups were used.  It was common to use Setups just as a convenient way to
adjust all the track volume levels, or IO ports, or sync modes on the fly during live performance.
This can still be done but once sessions contain content this can result in audio glitches.
To replicate the old Setup behavior, you should use *overlays* instead.

When you load a session from this window, it also becomes the *Startup Session* and will be automatically loaded the next time you start Mobius.  

The *Copy* item allows you to make a full copy of the session, you are prompted to enter a new unique name.  This is similar to what other systems might call **Save As**.  Once you have made a copy, you can then load and edit the session parameters without impacting the original session.

The *New* item will create a new session without copying any state from an existing session.  The session will be initialized with default parameter values and track counts.  **NOTE:** This is where many applications have the notion of a "template" that can be used as the basis for new sessions.  This is being considered but is not yet available.  If you want to make a session that looks like one you already have, use Copy.

The *Rename* item will prompt you for a new session name.  Session names are not signifant for the behavior of Mobius, they just provide a way to identify sessions designed for a particular use.

The *Delete* item will delete a saved session.   Once sessions become containers of content as well as partameters you should be careful about deleting them, since content may be lost.   Deleting the session named "Default" is not allowed.
