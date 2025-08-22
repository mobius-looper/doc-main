+++
title = 'Parameter Layers'
weight='3'
+++

A *parameter* is something that controls how Mobius behaves.  A parameter consists of two things, a *name* and a *value*.  One of the most frequently used parameters is named *Quantize* which may have the values *Off*, *Subcycle*, *Cycle*, and *Loop*.  Giving a parameter a value is called *assigning* or *setting* or *defining* the parameter.  In some cases we also use the term *including* a parameter when something may contain a parameter value or it may not.

The session includes almost all of the parameters in the system.  Only a very few called *system parameters* are found outside the session.  

To understand how sessions and parameters behave, it is helpful to think
of parameter values as being organized into several **layers**.  Each layer may have any number of parameter values in it.   When a function or script needs the value of a parameter it searches through
each layer from top to bottom until it finds a value.  If a value does
not exist in one layer, it moves to the layer below it, and continues
until it finds a value.    

There is always one layer at the bottom called the *session defaults layer* that contains values for all parameters.  For simple uses of Mobius, this may be the only layer you need.   All tracks share the same default parameter values.   Usually though you will want some tracks to use different parameter values than other tracks.  Each track has a collection of parameters called the *track override layer*.  When a track includes a value in it's override layer, that value is used instead of the value found in the session defaults layer.  Tracks do not need to override every parameter, only the ones that need to be different from what is in the default layer.

Beyond the session defaults and the track override layers, there are two additional layers that may be inserted into this stack of layers.  The *session overlay* and the *track overlay*.  The session overlay sits between the session defaults and the track overrides, and the track overlay sits above the track overrides.

Before we go any further, it should be stressed that there is no requirement to use session or track overlays.  In fact, it is recommended that you do **NOT** use them unless you need them.  If you are new to Mobius, ignore overlays for now.  Just set all of the parameters in the session defaults layer and where necessary override a few parameters in each track.   The only reason you might see track overlays is if you have upgraded a previous installation where all of the former *Presets* will have been converted into track overlays.  This is discussed in more detail in the [Using Parameter Overlays](../overlays) document.

As shown in the following diagram, the session defaults and session overlay is shared by all tracks, but each track may have it's own track overrides and a track overlay.

![Parameter Layers](../parameter-layers-2.svg)

Briefly, the main reason to use either form of overlay is when you need to temporarily swap in a different
set of parameters quickly and without introducing audio artifacts which may happen if you were changing the entire session.  If you needed to change 10 different parameters at the same time, rather than writing a script,
or pushing 10 different buttons on your MIDI controller, you could collect all ten parameter values into one overlay and activate it with one button.  This is approximately how *Presets* used to work which is why Presets have been converted into track overlays.  The **problem** with presets is that they contained a great many parameter values and you had to use all of them if you were going to use a Preset.  If for example you had 5 presets being used by different tracks, and you decided that *Empty Loop Action* needed to be the same in all tracks, you would have to edit all 5 presets.  Using track overlays, you would just not include *Empty Loop Action* in your overlay and the system would always get the value from the session defaults layer.  An overlay can contain as few as one parameter or as many as all of them, it's up to you.  

Appologies if this sounds confusing, but all of this exists mostly to simulate the behavior of what used to be called *Track Setups* and *Presets* which were used by a few advanced users in older releases.  It is not necessary to understand any of this to begin using Mobius.

