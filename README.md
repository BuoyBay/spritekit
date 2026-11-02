# 2D sprites and animation

A focused source-only 2D scene package extracted from the common needs demonstrated
by the Strout scrolling, platform, RPG and layered-drag studies. Import `spritekit`.
It provides shared scene/camera/animation/rendering behavior rather than a native
SpriteSurface or GPU engine.

## Install

From a Buoy consumer project with BPM installed:

```sh
bpm add spritekit --git https://github.com/BuoyBay/spritekit.git --rev refs/heads/main
```

BPM records the resolved commit in its lockfile. Keep that lockfile with the
consumer project for reproducible installs.

## API at a glance

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

## Build from source

With the native `build-packages` driver from [devtools](https://github.com/BuoyBay/devtools)
on your `PATH`, run from this checkout:

```sh
build-packages --root "$PWD" --compile-consumer spritekit
```

The driver checks source targets and compiles an import consumer. See the
[API guide](docs/API.md) for behavior, limits and any host prerequisites.

## Local Buoy setup

On your own machine, install Buoy and run:

```sh
buoy ai init --both
```

## Contributing

[Contributing](CONTRIBUTING.md) · [License](LICENSE)
