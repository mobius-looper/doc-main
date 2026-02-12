+++
title = 'Loop Switch Confirmation'
weight='5'
+++

In prior builds you would request switch confirmation by selecting from
a special set of options for the *Switch Quantize* parameter.

* Confirm
* Confirm Subcycle
* Confirm Cycle
* Confirm Loop

Now, *Switch Quantize* has the same set of options that any other quantization
parameter has.

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

If you want to add a level of confirmation to that, set the new parameter *Switch Confirm* which will appear in the UI as a checkbox right next to *Switch Quantize*.

When you upgrade to bild 46 and were using one of the old *Confirm* options, this box will be automatically checked.

The behavior is identical, it is just the way you go about asking for it is different.

Besides allowing quantization parameter to have a consistent set of options (and there will be more in the future), this also makes it easier to introduce the notion of confirmation into other things besides loop switch.

