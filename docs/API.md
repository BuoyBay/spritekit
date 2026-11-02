# SpriteKit 0.1.0

A focused pure Buoy 2D scene package extracted from the common needs demonstrated
by the Strout scrolling, platform, RPG and layered-drag studies. Import `spritekit`.
It provides shared scene/camera/animation/rendering behavior rather than a native
SpriteSurface or GPU engine.

## API

- `SpriteCamera(worldWidth, worldHeight, viewportWidth, viewportHeight)` owns a
  top-left world viewport. `MoveTo` clamps it to the world; a viewport larger
  than the world anchors at zero. `CenterOn`, `ScreenX/Y` and `WorldX/Y` provide
  positioning and inverse translations. There is no zoom or wrapping.
- `SpriteActor(x, y, width, height, depth, tint)` is a rectangular world object.
  `Place`, `SetVelocity` and `SetDepth` validate before mutation. `Visible` and
  `Tint` are writable (Nil tints reject). `X/Y/Width/Height/Depth/FrameIndex` are read-only.
- `SetFrames(pictures, secondsPerFrame)` owns a copy of the ordered frame list;
  pictures themselves remain shared references. An empty list restores colored
  rectangle rendering. Nil frames reject; a frame list has at most 4096 entries.
  Calling it resets the animation. `CurrentPicture` returns Nil for no frames.
- `SpriteScene(capacity = 4096)` owns strong references to actors. `Add` rejects
  Nil/duplicates/full scenes; `Remove` reports whether the actor was present;
  `Clear` releases membership. Actors can belong to multiple scenes, so callers
  must avoid advancing the same actor through multiple scenes unintentionally.
- `OrderedSprites()` returns a fresh array sorted by increasing depth. Equal
  depths retain scene insertion order through Buoy's stable comparator sort.
  Removing then adding an actor assigns a later position in that tie order.
- `VisibleSprites(camera)` culls invisible actors and rectangles outside the
  viewport, preserving drawing order. `HitTest(screenX, screenY, camera)` returns
  the last drawn rectangle containing that point, or Nil. All containment and
  intersection boundaries are half-open. Picking tests rectangles, not alpha.
- `Advance(deltaSeconds)` on actor/scene applies velocity in world units per
  second and advances animation by elapsed frame durations. The finite delta
  must be in `0..1`. Long gaps must be capped/subdivided by the caller. Scene
  advancement preflights every actor so a bounds failure cannot move an earlier
  actor first. Invisible/offscreen actors still advance. Floating-point frame
  boundaries have ordinary Double rounding behavior; exact binary durations are
  useful for deterministic tests.
- `Draw(g As IGraphics, camera)` clips to the viewport and draws in stable order.
  Each actor draws its current Picture scaled to its dimensions, or a rectangle
  using Tint. Tint does not multiply Picture colors. Graphics state is balanced
  with Save/Restore even on an exception. Draw does not clear the background.

## Bounds, ownership and rendering

A scene capacity is `1..4096`. Actor coordinates/depth have magnitude at most
`1e9`, velocities at most `1e6`, dimensions in `(0,1e6]`. Camera world dimensions
are `(0,1e9]`, viewport dimensions `(0,1e6]`; CenterOn accepts magnitude `999e6`
to leave room for its translation. Frame durations are `1e-6..3600` seconds.
Containment query coordinates accept magnitude up to `1.001e9`, covering the
full extent of an actor at the maximum position and size. Nonfinite values reject. Rendering and picking allocate sorted snapshots; there
is no spatial tree or tile cache. Actors and pictures are shared mutable objects;
the array copies protect membership/order, not concurrent object mutation. All
operations require one owning thread. No callbacks run during simulation.

IGraphics can target a live Canvas or Picture.Graphics. The runtime's documented
Windows limitation for partially transparent drawing onto offscreen Pictures
still applies; on-screen and offscreen alpha behavior need platform QA. This
package does not change the runtime. It does not retain a Canvas paint Graphics
beyond its callback.

## Verify and run

The [sprite demo](../examples/library-studies/impact/sprites/main.bui) renders a scrolling world, a moving animated Picture sprite and clickable layering.
Interactive appearance/input and other-platform runtime behavior are not covered
by compiler checks. See [provenance](../PROVENANCE.md).

Future layers include spatial indexing, tile caching, input routing, collision,
fixed-step accumulation and texture atlas rectangles. The separate physics work
can compose with actor placement without a direct dependency. No GPU performance,
3D/QD3D, sprite mask or full legacy API compatibility is promised.
