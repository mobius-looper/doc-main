+++
title = "Files"
type = "chapter"
weight='2'
+++

Mobius uses the computer's file system to store many things.  Internal files that
are part of the installation package are stored in a standard installation folder
and may be replaced after every installation.

User configuration and loop content are normally stored in a folder of your choice
to make it easier to browse and make backups.  It will never be replaced after
installing a new Mobius version.  This is called the *User File Folder*, which
may be abbreviated as *UFF*.

## User File Folder

One of the first things you should do after installing Mobius for the first time
is setting the User File Folder.  This folder will be used to store the files related
to *Sessions*, *Snapshots*, *Scripts*, and all other things that are not part of the
core application.  

This is a common concept among audio applications.  If you are familar
with Ableton Live, this is conceptually similar to what Ableton calls
the *User Library*.

To set the user file folder, open the *File* menu and select *User File Folder*.
A popup window will appear showing the current location.  You can type in the path
to the folder, or click the *Browse* button to popup a standard file browser.

## What Hapens If You Don't?

The concept of the UFF was added in Mobius build 42, so most of you have not been
using it.  In these early releases, user content was stored in folders under what the
OS calls the *application support folder* which is created automatically as part
of the installation.

For Windows users this is:

    c:/Users/<yourname>/AppData/Local/Circular Labs/Mobius

For Mac users this is:

    /Users/Library/Application Support/Circular Labs/Mobius

To ease the transition to the UFF, Mobius will look in *both* locations
for sessions, scripts, and other user files.  Sessions stored in the default location
will continue to be managed there, but any new sessions you create will be stored
in the UFF.  

## What Happens If You Change It?

**Important:** If you have been using a user file folder for awhile, and change it
to a new location, the current release of Mobius **will not copy** the contents of
the old folder to the new one.  If you want your old configurations and content to
exist in the new location, it must be copied manually.   This will be fixed
in a later release.

