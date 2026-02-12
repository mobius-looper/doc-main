+++
title = 'External Quantization'
weight='4'
+++

Quantization is fundamentally the ability to cause something to happen in the future.

You want to *Record*, or *Mute* or *NextLoop* but you don't want to do it now, you want to wait until something else happens.

Historically quantization has been limited to locations or *points* within the loop you are currently working with.  You could set the *Quantize* parameter to *subcycle*, *cycle*, or *loop*.  This meant that for those functions that obeyed quantization, the function would not happen immediately, it would be scheduled for the next subcycle or next cycle or the end of the loop, and when the loop playback position reached that point, the action would happen.

You can accomplish interesting things with that.  But in a world that involves multiple tracks playing at the same time, inside of a host application that is also doing things on a timeline, there are many other points in time that are useful for scheduling things.

Here, quantization behaves more like *synchronization*.  It is less about doing things on a grid, than it is about waiting for external events to happen.

There are many uses cases for this.  Two of the more common ones I've heard over the years are:

* Wait until the host reaches the start of it's 4 bar pattern, then start recording
* Unmute when the leader track reaches the end

In the past, we've used scripts for this sort of thing, but I'm looking for ways to do common things that don't always require you to break out the scripts.

In build 46, the available quantization points are now:

* Off/None
* Subcycle
* Cycle
* Loop
* Marker
* SyncStart
* Beat
* Bar
* LeaderSubcycle
* LeaderCycle
* LeaderLoop
* LeaderMarker

I'm not going to talk much about what *Marker* means yet, that's a future feature.  But you will start seeing that name in places.

What is not included here, is something I alluded to if you read the previous section on the [Changes in Time](timephilosophy.md).  All loops now have beats and bars.  You can ignore them if you want, but I think many are going to find those to be far more predictable quantization points than subcycles.  So this list will probably involve the ability to include *Beats* and *Bars* within loops as well as the sync source.

#### Quantize Fallbacks

As mentioned in the section on recording, whenever there is a parameter whose options include the word *Leader*, there will be another parameter with the name *Fallback* that is used when there is no leader.  For example, a track may usually want to quantize to *Leader Cycle* when when there is no leader, it will use the local *Cycle* point.

The quantization parameters and their fallbacks are:

```plaintext

  Quantize
  Quantize Fallback

  Switch Quantize
  Switch Quantize Fallback

  Realign Quantize
  Realign Quantize Fallback
```


  