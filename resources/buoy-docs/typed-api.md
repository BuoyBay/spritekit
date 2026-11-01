---
title: "spritekit typed API"
summary: "Source-derived public signatures, properties, parameters, defaults, and return values."
category: "Reference"
order: 21
types: ["SpriteActor", "SpriteCamera", "SpriteScene"]
dependencies: []
symbols: ["SpriteActor", "SpriteCamera", "SpriteScene"]
related: ["api.md", "getting-started.md", "index.md"]
---

# spritekit typed API

Generated from the package source declarations. Platform guards are shown where present; inherited members are documented on the base type. See the [API contracts](api.md) for behavior and limitations.

## SpriteCamera

`Public Class SpriteCamera`

Top-left camera in world units. Larger viewports anchor at zero.

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `X` | `Double` | Yes | No | — | — |
| `Y` | `Double` | Yes | No | — | — |
| `Width` | `Double` | Yes | No | — | — |
| `Height` | `Double` | Yes | No | — | — |

### Constructor

`Public Sub Constructor(worldWidth As Double, worldHeight As Double, width As Double, height As Double)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `worldWidth` | `Double` | `ByVal` | Required |
| `worldHeight` | `Double` | `ByVal` | Required |
| `width` | `Double` | `ByVal` | Required |
| `height` | `Double` | `ByVal` | Required |

Returns: no value.

### MoveTo

`Public Sub MoveTo(x As Double, y As Double)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `x` | `Double` | `ByVal` | Required |
| `y` | `Double` | `ByVal` | Required |

Returns: no value.

### CenterOn

`Public Sub CenterOn(x As Double, y As Double)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `x` | `Double` | `ByVal` | Required |
| `y` | `Double` | `ByVal` | Required |

Returns: no value.

### ScreenX

`Public Function ScreenX(worldX As Double) As Double`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `worldX` | `Double` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Double` |

### ScreenY

`Public Function ScreenY(worldY As Double) As Double`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `worldY` | `Double` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Double` |

### WorldX

`Public Function WorldX(screenX As Double) As Double`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `screenX` | `Double` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Double` |

### WorldY

`Public Function WorldY(screenY As Double) As Double`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `screenY` | `Double` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Double` |

## SpriteActor

`Public Class SpriteActor`

Mutable actor; dimensions and motion change only through checked methods.

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Tint` | `Color` | No | No | — | — |
| `Visible` | `Boolean` | No | No | `True` | — |
| `X` | `Double` | Yes | No | — | — |
| `Y` | `Double` | Yes | No | — | — |
| `Width` | `Double` | Yes | No | — | — |
| `Height` | `Double` | Yes | No | — | — |
| `Depth` | `Double` | Yes | No | — | — |
| `FrameIndex` | `Integer` | Yes | No | — | — |

### Constructor

`Public Sub Constructor(x As Double, y As Double, width As Double, height As Double, depth As Double, tint As Color)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `x` | `Double` | `ByVal` | Required |
| `y` | `Double` | `ByVal` | Required |
| `width` | `Double` | `ByVal` | Required |
| `height` | `Double` | `ByVal` | Required |
| `depth` | `Double` | `ByVal` | Required |
| `tint` | `Color` | `ByVal` | Required |

Returns: no value.

### Place

`Public Sub Place(x As Double, y As Double)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `x` | `Double` | `ByVal` | Required |
| `y` | `Double` | `ByVal` | Required |

Returns: no value.

### SetDepth

`Public Sub SetDepth(depth As Double)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `depth` | `Double` | `ByVal` | Required |

Returns: no value.

### SetVelocity

`Public Sub SetVelocity(xPerSecond As Double, yPerSecond As Double)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `xPerSecond` | `Double` | `ByVal` | Required |
| `yPerSecond` | `Double` | `ByVal` | Required |

Returns: no value.

### SetFrames

`Public Sub SetFrames(frames As Array Of Picture, secondsPerFrame As Double)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `frames` | `Array Of Picture` | `ByVal` | Required |
| `secondsPerFrame` | `Double` | `ByVal` | Required |

Returns: no value.

### CurrentPicture

`Public Function CurrentPicture() As Picture`

No parameters.

#### Returns

| Type |
| --- |
| `Picture` |

### CheckAdvance

`Public Sub CheckAdvance(deltaSeconds As Double)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `deltaSeconds` | `Double` | `ByVal` | Required |

Returns: no value.

### Advance

`Public Sub Advance(deltaSeconds As Double)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `deltaSeconds` | `Double` | `ByVal` | Required |

Returns: no value.

### Contains

`Public Function Contains(worldX As Double, worldY As Double) As Boolean`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `worldX` | `Double` | `ByVal` | Required |
| `worldY` | `Double` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Boolean` |

## SpriteScene

`Public Class SpriteScene`

Stable insertion-order ties; all scene operations are synchronous.

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Count` | `Integer` | Yes | No | — | — |

### Constructor

`Public Sub Constructor(capacity As Integer = 4096)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `capacity` | `Integer` | `ByVal` | `4096` |

Returns: no value.

### Add

`Public Sub Add(actor As SpriteActor)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `actor` | `SpriteActor` | `ByVal` | Required |

Returns: no value.

### Remove

`Public Function Remove(actor As SpriteActor) As Boolean`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `actor` | `SpriteActor` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Boolean` |

### Clear

`Public Sub Clear()`

No parameters.

Returns: no value.

### OrderedSprites

`Public Function OrderedSprites() As Array Of SpriteActor`

No parameters.

#### Returns

| Type |
| --- |
| `Array Of SpriteActor` |

### Advance

`Public Sub Advance(deltaSeconds As Double)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `deltaSeconds` | `Double` | `ByVal` | Required |

Returns: no value.

### VisibleSprites

`Public Function VisibleSprites(camera As SpriteCamera) As Array Of SpriteActor`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `camera` | `SpriteCamera` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of SpriteActor` |

### HitTest

`Public Function HitTest(screenX As Double, screenY As Double, camera As SpriteCamera) As SpriteActor`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `screenX` | `Double` | `ByVal` | Required |
| `screenY` | `Double` | `ByVal` | Required |
| `camera` | `SpriteCamera` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `SpriteActor` |

### Draw

`Public Sub Draw(g As IGraphics, camera As SpriteCamera)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `g` | `IGraphics` | `ByVal` | Required |
| `camera` | `SpriteCamera` | `ByVal` | Required |

Returns: no value.
