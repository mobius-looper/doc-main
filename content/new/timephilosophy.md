+++
title = 'Changes in Time'
weight='1'
+++

Before we dive into how or why Mobius does certain things, I'd like to share some general
thoughts thoughts about how I would like to start thinking about time.

There are two time-sensitive concepts in Mobius that are related, but are not the same: *Quantization* and *Synchronized Recording*.

Quantization is what determines when something will happen.  It is the selection of a *moment* in time when an action will occur.

Synchronized Recording is the process of creating a recording whose length is controlled.  It is the selection of a *span* of time. 

These two concepts can be thought of more generally as *points* and *units*.

A *point* is a moment in time and a *unit* is a length of time.

#### Units

In music, there are a few standard time units, the ones most used by audio applications
or hardware devices are the *beat* and the *measure* or *bar*.  Measure and bar mean the same thing
but I will always use the term bar because it is shorter and I like alliteration.  Almost every
modern application or device that can synchronize with something else uses *beats* at a *tempo*
as the fundamental unit of measure.

Mobius has historically not emphasized beats and bars.  Instead it used more abstract
units of measure derived from the EDP: *subcycle*, *cycle*, and *loop*.

If you are a solo performer that does not play along with any other sound sources, such as host
tracks or drum machines, this difference in units may not matter.    But if you do, these two
different unit systems complicate the way things are configured and cause confusion. (See, I told
you I liked alliteration).

Almost all Mobius users use Mobius as a plugin inside a host, or synchronize it with other things.
These other things know nothing about what a subcycle, cycle, or loop is.  They only speak in beats,
tempos, and time signatures.

While you can create a loop where a subcycle corresponds to a beat and a cycle corresponds to a bar,
it is almost never used that way.  Cycles are arbitrarily long, it could be a beat, a bar, a verse,
or an entire song.  Subcycles simply take that arbitrary span of time and carve it up into more arbitrary
divisions of 4 or 8 or 17 or whatever it was left at the last time.  It takes planning to make meaningful
use of cycles and subcycles.

Beats and bars have much more well defined meanings.  You can record a loop of any length and
we can make an educated guess about what that means.  It looks like 2 4/4 bars at 90.5bpm.   It may be wrong
but you can adjust it by adding or removing bars until the tempo feels right.  This is what you must do
if you want Mobius to generate MIDI clocks at a tempo.  And once you do that it means all loops
have beats and bars.  You may choose to use subcycles and cycles if want, but loops
will always have beats and bars at a tempo, that are computed automatically.

#### Points

Points are not as well defined as units.  Some points have the same name as units, there are points for
beat, bar, subcycle, cycle, and loop.  But since points are moments in time and not spans of time,
a bar technically has two points, the start point and the end point.  For most units there is no practical
difference.  The end point of one bar is the start point of the bar after it, so you only ever care about bar start points.  The one exception is the unit *loop*.  In a few cases it is important to distinguish between the *start* of the loop and the *end* of the loop.   So when talking about loops the points *start* and *end* are meaningful.

The *subcycle* is arguably more of a point than a unit.  Cycles and loops have a relatively obvious length.
Subcycles are just a point in a cycle and you can change them any time after recording, unlike beats and bars which are fixed.  

But points do not have to correspond to recording units.  They can just be random locations in a loop that you might find interesting, and choose to give it a name.  I have started using the term *Marker* for user defined points.  In future builds you will be able to drop markers anywhere within a loop.  These markers can be given names like "verse" and "chorus".

So while there are a small number of units that have well defined lengths and are used to create recordings.  There can be many points within that recording that provide a structure to the recording.    The distance between two points is not necessariy a unit, they are just two independent moments in time. 

#### Sources

Points and units have to come from somwehere.  A loop in a track, the host transport, MIDI clocks.    So part of using a point or a unit is also saying where it came from.

When you choose a quantization point for a Mobius action, you have so far only been able to choose points that reside within the loop you are performing that action in.  You may want to perform an action when a different track reaches it's end point, or when the host transport reaches it's next bar.

So when selecting points for quantization, you should be able to select anything that has a point with that name.   It does not matter if that point is inside the loop or outside.

You can also think about quantization points in a way that a modular synth module would think about CV pulses.  The module needs to do something at a certain moment in time, and it waits until it receives a pulse to do that.  Where that pulse came from doesn't matter, you can patch in any source of pulses.

#### The Future

Going forward, Mobius will start having a much greater emphasis on the traditional units, *beat*, *bar*, and *tempo*, because that is what everything else uses.

As you read the following sections on quantization and recording, you will start seeing these terms in more places than you did before.

The unification of these unit systems is not yet complete, and there will be further adjustments in the comming months.

For recording the notion of how long a recording is (the units) and when it starts (the point) will
be different things.  There are relatively few recording units, but there can be many points that cause
recording to start.























































