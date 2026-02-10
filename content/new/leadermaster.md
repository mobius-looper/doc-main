+++
title = 'Master and Leader'
weight='1'
+++

The concepts of a *Master* track and a *Leader* track are not new, but the terms used when talking about them and how they behave is different.

The *Master* track was formerly known as either the *Transport Master* or *Sync Master*.    There can be only one master track at a time, though you can pick any track to be the master, and you can change the master track at any time.

As before what makes the master track special is that it is in control over the *Transport*.  When you make a track the *Master* several things can happen.  The exact behavior is configurable (of course) but usually assigning the Master immediately changes the transport tempo and starts it running.  The Transport can then be used for other things like generating MIDI clocks, or providing synchronization pulses but the tempo of these things is being controlled by a track.

The *Leader* track was formerly known as the *Track Sync Master*.   What is new is that there
can be more than one leader.  There is usually a *Default Leader* which is what *Track Sync Master* used to be.  But in addition, each track may explicitly specify the leader it wants by number.  I expect most will not care about fixed leaders, but as Mobius moves more into the realm of MIDI and  pre-recorded backing tracks, there can be a need to divide tracks into groups, and each of those groups may have different ideas about what leadership means.

Until you find a use for this, you can continue thinking of the *Default Leader* as simply **The** *Leader*.  There is only one at a time and it can be selected manually or automatically.

To visualize these concepts I strongly recommend you include the Leader/Master indiciator
in the track strip.   The words *Leader* and *Master* will appear and disappear as the track accepts or loses those states.  From *Display->Manage Layouts->Docked Track Strip* drag the word *masters* from the right side to the left.  What you see in the left panel are the names of the elements that will be dispayed in the track strips along the bottom of the Mobius window.  You can also click-drag items in this list to change their order.

### Manual Selection

The function names used to select the leader or master have changed.  I tried to make the upgrade process smarter about fixing existing bindings to have the new names, but be on the lookout for this.  If you had a MIDI binding to *Track Sync Master* that suddenly doesn't seem to work, the upgrade may not have found the binding.  You will need to edit the binding, use the *Change Action* button and select the new name.

The name changes were:

```
Old Name                  New Name

SyncMasterTrack           Leader
SyncMasterTransport       TransportMaster

```

### Leader Elections

Previously the *Track Sync Master* was selected automatically as tracks were recorded.  This could be controlled with the parameter displayed as "Track Master Select" which had values *Manual*, *Accept*, *Preferred*, and *Never*.

If that track was then reset, a different track could be chosen depending on the parameter displayed as *Track Master Reset* which had values *Stay* and *Move*.  Most people left this as *Move* which meant the Track Sync Master could jump around as you recorded and reset tracks.

This mechamism still exists, but the names around that have changed, and it now applies
to both the *Default Leader* and the *Master*.

The new parameters are:

```
Name                            Values

Leader Acceptance               Manual, Accept, Preferred, Never
Master Acceptance               Manual, Accept, Preferred, Never

Leader Election After Reset     true/false
Master Election After Reset     true/false
```

The concept I'm going for here is that leaders have to be *elected* which is a process
of polling each of the tracks to determine which one wants to be the leader the most.

A track may choose to *accept* the election, or it may *never* want it, or it may really, really *prefer* it over all the other tracks.  It thinks it's better than the other tracks, the bastard.

Some tracks are apathetic and will only accept the election if you *manually* force it to.

There are various reasons why a leader election may be held.  An election is always held when a new loop is recorded.  If there is already a leader at that time, it has priority and will remain the leader.  If there is no leader all tracks are examined from left to right.  Any tracks that are *Preferred* are chosen first, followed by any tracks that simply *Accept*.    If there is more than one track of the same level (Preferred vs. Accept) then the one with the lowest number is chosen.

But there are other reasons where it may make sense to hold a new election.  The most common is when the current leader is *Reset*.  Since this track can no longer provide any synchronization servies to other tracks, an election may be held.  But you may want to allow the track to retain it's leadership status after a Reset.  Perhaps the loop is just being cleared in preparation for a new recording, and once that recording finishes you want this track to continue being the leader.  This can be controlled with the *Leader Election After Reset* checkbox.  When this is off, no election is held when the leader is reset and the leader stays where it is.  If this is on, a different track may be automatically chosen as the new leader.

Other election triggers are likely to be added in the future.  Anything that causes a track to suddenly have a new loop or lose an existing loop could potentially trigger an election.  This includes:

  * Switching from a full loop to an empty loop
  * Switching from an empty loop to a full loop
  * Loading or dropping a file
  * Using a *loop copy* function

As mentioned, the election process applies to both selecting a *default leader* as well as the *transport master*.
The difference is that in a newly created Session, tracks will have *Leader Acceptance* set to *Accept* but they have *Master Acceptance* set to *Manual*.  You alomst always want to start with automatic leader selection, but since master selection is more consequential, it starts out being manual.

### Leader/Master in Scripts

If you were using the old names in a script, I added an *aliasing* mechanism where the new names would be automatically replaced at runtime.  This worked in a few of my test scripts, but if you notice scripts not working, you may need to change these names.  I recommend you do this anyway, just to avoid future confusion because they will no longer be used in documentation.  The names will be removed from all the statues, and never used again in polite conversation.  They are dead to us.

Similarly, if you were using script varibles to find out which track had these states, one of those variable names changed:

```
Old Name                  New Name

trackSyncMaster           leader
transportMaster           transportMaster
```

In addition there are some new variables that won't be of interest until you start using multiple leaders.

**hardLeader**

A track variable containing the number of the fixed leader for this track.  If the value is zero, it means this track is using the default leader.

**trackLeader**

A track variable containing the *effective* leader for this track.  This will be the same as *hardLeader* if it is non-zero.  If *hardLeader* is zero, it will be same as *leader*.


I don't think anyone was using the parameters related to automatic leader and master selection.  But those have changed as well.   But these didn't just change names, they also changed what the values mean.  If you used any of these the script logic will need to be rewritten.

```
Old Name                  New Name

trackMasterSelect         leaderAcceptance
trackMasterReset          leaderResetElection
```
