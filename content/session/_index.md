+++
title = "Sessions"
type = "chapter"
weight='1'
+++

A **Session** is a collection of configuration settings that is saved on the file system.  When you start Mobius, a session is loaded into memory and when you shutdown Mobius the current contents of the session may be saved.  You can save any number of sessions but when you use Mobius, you are always using one *active* session.

Most audio applications have a similar concept, usually also called *sessions* or *projects* or *templates*.

If you are familar with Mobius 2.5, the Session is a replacement for the **Track Setup**, the **Preset**, and most of what were formerly called **Global Parameters**.    The session contains all of the *parameters* that control how Mobius responds to actions, and and how each track uses audio, MIDI, and synchronization services.

You would typically design several sessions to accomodate different performance styles and environments.  Often a session would be used for a single "song" within a larger performance.  Or you might use different sessions for different hardware you want to connect.  Or for differences when using Mobius standandalone and using it as a plugin.

Though not available yet, the Session is also where you will store audio and MIDI track content, replacing the Mobius 2.5 concept of the **Project**.

Sessions do **not** containg bindings or scripts.  Those are configured separately and are used across sessions.

## Session Management

Sessions are accessed from the main menu item named unsurprisingly **Sessions**   There are two sub-items **Edit Session** and **Manage Sessions**.  *Edit Session* is where you make changes to the currently active session.  *Manage Sessions* is where you can view and organize your collection of sessions.

#### Where are Sessions?

Sessions are stored in directories (folders) on the file system.  It is not currently possible to
specify where those directories are, though that is planned for future releases.  Currently they are under the user's application support directory.  For Windows users this is:

    c:/Users/<yourname>/AppData/Local/Circular Labs/Mobius/sessions

For Mac users this is:

    /Users/Library/Application Support/Circular Labs/Mobius/sessions

Within the sessions directory will be subdirectories whose names are the same as the session name.
For this reason, sessions must have names that are allowed as file system directory names.  Special characters such as / \ $ or .  are not allowed.

You may wish to make a copy of the session directories as a backup, or when changing computers.

Within each session directory there will always be a single file named "session.xml".
In future relases, when sessions are allowed to contain audio and Midi content, the .wav or .mid
files with that content will also be found here.
Other supporting files such as session-specific scripts and bindings will also be stored here.

