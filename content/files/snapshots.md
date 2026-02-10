+++
title = 'Snapshots'
weight='1'
+++

Snapshots are are usually stored within the session folder under a folder named *snapshots*.
If you use *Export* from the Snapshot menu, you will be prompted for a location for
the snapshot.

Each snapshot is itself a folder that will have a generated name.  This name is a text
representation of the date and time that the snapshot was created.  For example:

    2025-11-11_09-22-37

Within the snapshot folder will be a file named *content.xml*.  This is called the
snapshot *manifest file*.  It contains information about the tracks contained in the
snapshot and the names of the files that contain loop content.  You should not edit the
manifest file as it may corrupt the snapshot.

Loop content will be stored in one or more independent files with extension .wav for audio loops and .mid for midi loops.  For example:

  track-1-loop-1.wav
  track-3-loop-1.mid
  track-7-loop-1.wav

The file names include the track and loop numbers from which the file was generated.

If enabled you may also see files generated for each loop layer.

  track-1-loop-1-layer-2.wav

It is not necessary to understand the file system structure for snapshots, but this can
be useful if you want to load the snapshot files into another application for
inspection or modification.




