Description
===========

TemporalSoften filter for VapourSynth.

TemporalSoften2 averages *radius* * 2 + 1 frames. A pixel is included
in the average only if the absolute difference between it and the
middle frame's corresponding pixel is less than the threshold. If the
*scenechange* parameter is greater than 0, TemporalSoften2 will not
average frames from different scenes.

This version was originally written by Chikuzen.


Usage
=====

::

   focus2.TemporalSoften2(clip clip[, int radius=4, int luma_threshold=4, int chroma_threshold=8, int scenechange=0, int mode=2])

Allowed values (ranges are inclusive):

- radius: 1..7
- luma_threshold: 0..255
- chroma_threshold: 0..255
- scenechange: 0..254
- mode: 2

The two thresholds can't both be 0.

If *scenechange* is greater than 0, the Miscellaneous Filters plugin
included with VapourSynth is required.


Compilation
===========

::

   mkdir build; cd build
   meson ..
   ninja
