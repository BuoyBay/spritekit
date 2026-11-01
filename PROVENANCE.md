# SpriteKit provenance

This is a new independent implementation of common scene requirements exposed by
this repository's Buoy studies:

- `examples/strout/blasteroids`: world/view conversion and bounded drawing.
- `examples/strout/platform`: explicit simulation separate from Canvas paint.
- `examples/strout/rpg`: depth ordering and camera bounds.
- `examples/strout/drag-demo`: reverse-order hit testing of layered objects.
- `examples/strout/twofive`: retained model state and independently timed effects.

Those studies originated from [Joe Strout's REALbasic examples](https://strout.net/info/coding/rb/intro.html).
No legacy source, binary, artwork or native SpriteSurface implementation was
copied into this package. Existing study files were not changed.

API details were written from the installed Buoy 0.72.0 reference pages:
`arrays.md`, `canvas.md`, `graphics.md`, `igraphics.md`, `picture.md`, `timer.md`
and `input-events.md` under `/usr/share/buoy/docs/documentation`. In particular,
Array.Sort's documented stable comparator contract supplies tie preservation.
Actual compiler verification, package import checks and raster tests determine
what this implementation supports; a feature appearing in a source example does
not establish that this package implements it.
