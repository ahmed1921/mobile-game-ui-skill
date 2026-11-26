# Building the UI in Unity

For Unity 6 and later. Read the project's existing UI code first and follow how it is built (prefabs
or code-built, its own helpers, its skin or theme asset). API details change between versions, so
when a call matters, check the manual for the project's Unity version or load the unity:ui-ugui or
unity:ui-uitk skill.

Contents: which UI system · canvas setup · safe area · anchoring · sprites · text · theme and
components · from mockup to Unity · screen structure · motion · lists · performance · testing.

## Which UI system

- **uGUI (Canvas, Image, TextMeshPro)** is what Unity's own comparison page recommends for runtime
  game UI, and it is what most shipped mobile games use. It has in-scene authoring, world-space UI,
  particle and shader freedom, and Animation or tween control. Default to it.
- **UI Toolkit (UXML, USS)** is the alternative for menu-heavy, data-driven screens: style sheets,
  data binding, flexbox layout. It is weaker for custom shaders, per-element effects and timeline
  animation. Reasonable for settings, inventories and long lists.
- Both can live in one project. Do not migrate an existing UI from one to the other as part of a
  restyle; restyle in the system the project already uses.

## Canvas setup

- One root canvas per layer: world HUD, menus, popups, overlay effects. Render mode
  **Screen Space - Overlay** unless particles or 3D models must sort inside the UI, then
  **Screen Space - Camera** with a UI camera.
- **Canvas Scaler:** UI Scale Mode = Scale With Screen Size. Reference resolution 1920 x 1080 for
  landscape or 1080 x 1920 for portrait. Screen Match Mode = Match Width Or Height with Match = 1
  (height) for landscape and 0 (width) for portrait, so extra screen length on tall phones becomes
  extra room instead of scaling everything.
- Leave Pixel Perfect off on anything that moves.
- EventSystem with the Input System UI Input Module when the project uses the new Input System.
- Set `Application.targetFrameRate = 60` at start; mobile defaults to 30 and UI feels heavy there.

## Safe area

Controls stay inside the safe area; backgrounds and full-bleed art ignore it. Put all interactive
UI under one panel that tracks `Screen.safeArea`:

```csharp
using UnityEngine;

[RequireComponent(typeof(RectTransform))]
public class SafeArea : MonoBehaviour
{
    Rect _last;
    void OnEnable() => Apply();
    void Update() { if (Screen.safeArea != _last) Apply(); } // rotation and foldables change it

    void Apply()
    {
        _last = Screen.safeArea;
        var rt = (RectTransform)transform;
        Vector2 min = _last.position, max = _last.position + _last.size;
        min.x /= Screen.width; min.y /= Screen.height;
        max.x /= Screen.width; max.y /= Screen.height;
        rt.anchorMin = min; rt.anchorMax = max;
        rt.offsetMin = rt.offsetMax = Vector2.zero;
    }
}
```

## Anchoring

- Anchor every element to the corner or edge it belongs to: top bar to the top, play button to the
  bottom-right, side stacks to their sides. Never leave HUD pieces centre-anchored with offsets.
- Stretch only backgrounds, bars and scroll areas.
- Design at the reference resolution, then check 16:9, 19.5:9 or wider, and 4:3. On 4:3 the middle
  shrinks; on wide phones it grows. Corner-anchored layouts survive both.
- Layout Groups are fine for building a row once. For anything that changes at runtime, set
  positions yourself or disable the group after the first layout (see performance).

## Sprites

- **9-slice everything that resizes.** One rounded-rectangle sprite with borders set in the Sprite
  Editor, Image Type = Sliced, covers every panel, pill and button size.
- **Tint white art.** Author shapes in white or light grey and colour them with `Image.color`. One
  white rounded rect plus one outline sprite plus one shadow sprite gives the whole multi-colour
  sticker style from three textures, and a palette change costs nothing.
- Build depth from layers: shadow or lip image, body image, top highlight image, icon, label.
  Keep the lip and highlight as child images so one prefab serves every colour.
- Import as Sprite (2D and UI), mip maps off, compression ASTC on mobile (6x6 for painted art, 4x4
  where outlines must stay crisp), and pack UI sprites into Sprite Atlases grouped by screen so each
  screen draws in a few batches.
- Author icons and frames at twice the size they appear at the reference resolution, no larger.
- Rays, glows and gradients are small greyscale sprites, tinted and rotated or scaled by code.

## Text

- TextMeshPro for all text (it ships inside the uGUI package in Unity 6).
- One SDF font asset per face. Outline and shadow come from **material presets** (for example
  "Display-Outline-Ink"), never from editing a text object's own material instance, which breaks
  batching. Thick outlines need extra padding in the font asset, around 10 percent of the sampling
  size, or the stroke clips.
- Add fallback font assets for other scripts before localising. Static atlas for Latin, dynamic for
  large character sets.
- Use auto-size with a minimum and maximum on labels that get translated; leave 30 to 40 percent
  spare width.
- Update numbers with `SetText("{0}", value)` or cached strings, and only when the value changes.
  Count-ups change the text every frame, so keep those labels on their own small canvas.
- Abbreviate large numbers in one shared helper (1,240 then 12.4K then 3.2M).

## Theme and components

Port the visual system before any screen:

- A **theme asset** (ScriptableObject) holding the ink colour, surface colours, every role colour,
  the rarity ladder, class colours, the font assets and material presets, and the shared sprites.
  Screens read colours from the theme by role name, never by hard-coded value.
- A small **component kit**, as prefabs or builder functions matching the project's habit:
  primary button, secondary button, round icon button, currency pill, dark plate, light card,
  badge (red dot with count), progress bar with ghost segment, tab, ribbon title, item or hero card,
  popup frame. Every screen is assembled from these.
- Each component implements its states once: normal, pressed, disabled, selected, locked.

## From mockup to Unity

| In the HTML mockup | In uGUI |
|--------------------|---------|
| Fixed 1280 x 720 canvas | Canvas Scaler reference resolution; multiply mockup px by 1.5 for 1920 x 1080 |
| `border-radius` + background colour | 9-sliced white rounded sprite, tinted |
| Solid border | 9-sliced outline sprite on top, tinted ink |
| Hard offset shadow | Copy of the body sprite offset down, tinted ink, drawn first |
| Inset highlight and lip | Two child images (top band, bottom band) with low alpha |
| Text stroke | TMP outline material preset |
| Linear gradient background | Small gradient sprite stretched, or a UI gradient shader |
| Conic rays, glow | Greyscale sprite, tinted, rotated by a tween |
| Flex row with gap | Anchored positions, or a Layout Group disabled after first layout |
| `position: absolute` | Anchor to the matching corner plus anchoredPosition |
| CSS keyframe pulse, bob, pop | Tween on scale or position |
| Inline SVG icon | Sprite exported from the SVG at 2x, white, tinted |

Rebuild the mockup's structure, not its pixels: same anchors, same hierarchy of importance, same
colours by role.

## Screen structure

- One prefab or builder per screen; a small UI manager keeps a stack (push, pop, replace) and owns
  the back action. Popups are a second stack above screens.
- Keep view code separate from game state: the screen subscribes to state changes and renders; it
  does not own the data.
- Heavy screens (shop, collection) load on demand rather than living in the first scene.
- A full-screen opaque menu should stop the world camera rendering behind it.

## Motion

- Use a tween library (DOTween, PrimeTween, LitMotion) or small coroutines for UI motion. Avoid an
  Animator on UI that is idle most of the time: an Animator dirties its canvas every frame even when
  nothing visibly changes.
- Put the standard motions in the components: press scale 0.95 and spring back, popup scale-in,
  count-up, fly-to-pill, star stamp, pulse for ready state.
- Animate transforms and alpha (CanvasGroup), not layout properties.
- Honour a reduced-motion setting from one place.

## Lists and scrolling

- Long lists recycle their cells (a pooled scroll list) instead of instantiating every row.
- Use RectMask2D for scroll clipping; it is cheaper than Mask because it does not use the stencil
  buffer. Use Mask only for non-rectangular shapes.
- Pooling: disable the object first, then reparent it into the pool, so the hierarchy is dirtied once.

## Performance rules

From Unity's own UI optimisation guidance; these matter most on phones.

- **Split canvases by how often they change.** Any change inside a canvas rebuilds that canvas's
  batches. Static frames on one canvas, counters and bars on another, per-unit world labels on a third.
- **Turn off Raycast Target** on every image and label that is not itself a button, and remove the
  Graphic Raycaster from canvases that take no input.
- **Avoid nested Layout Groups** on live UI. Each dirty child walks up the hierarchy to find its
  layout root.
- **Hide by disabling the Canvas component**, not the GameObject, when the UI will come back soon;
  it skips the rebuild on return.
- **Invisible is not free.** An image with alpha 0 is still drawn; disable it.
- **Watch overdraw.** Stacked full-screen translucent images are the usual cause of slow menus.
- **Batch by atlas and material.** Mixed materials and text between images break batches; check the
  Frame Debugger.
- Assign the Event Camera on world-space canvases so Unity does not search for the main camera.
- Hundreds of floating numbers or health bars belong in a pooled, batched or GPU-instanced renderer,
  not one canvas object each.

## Testing

- Game view at three aspects (16:9, 19.5:9 or 20:9, 4:3) and the Device Simulator for notches.
- Read every screen at arm's length on a real phone; text that looked fine in the editor is often
  too small.
- Profiler UI module and Frame Debugger for batches and rebuilds on the busiest screen.
- Capture each screen and compare it side by side with the approved mockup before calling it done.

## Build checklist

- [ ] Canvas Scaler set; all controls under the safe area panel; everything corner-anchored.
- [ ] Theme asset holds every colour and font; no hard-coded colours in screens.
- [ ] Sprites 9-sliced, atlased, tinted from white.
- [ ] Text uses TMP material presets; fallbacks added if localising.
- [ ] Non-interactive graphics have Raycast Target off; canvases split static from dynamic.
- [ ] Every button has pressed and disabled states; locked items state their unlock condition.
- [ ] Checked at three aspect ratios and compared against the mockup.

## Lessons from porting an HTML mockup 1:1

Learned on a full port of a 13-screen mockup (2026-11). They apply whenever "match the mockup
exactly" is the bar.

- **Convert, do not rebuild by hand.** Measure the rendered mockup in a headless browser, bake each
  distinct visual to a sprite (9-slice the plain boxes), write the layout as data, and let an
  editor script build the prefabs. Hand-built screens drift; a converter can be re-run.
- **Colour space decides whether see-through UI matches.** A browser blends in display (sRGB)
  values; a Linear-space Unity project blends in linear light, so translucent panels come out
  lighter. Either use Gamma colour space, or draw the UI with a stacked camera whose shaders write
  display values and convert the frame before and after. Opaque pixels match either way.
- **Fonts need their kerning and ligatures.** A TextMesh Pro font made in code has neither; text
  comes out a few pixels wider than the browser's. Import the font features.
- **Browsers on a Mac draw letters slightly bolder** than the font file. A small face dilate per
  font size matches it.
- **Write the browser's line breaks into wrapped text** and turn wrapping off, or Unity will break
  lines one word away from the mockup.
- **CSS animation rules are not "add on top".** While an animation is in effect its value replaces
  the element's own: an animated opacity replaces a resting opacity of 0, and `transform`
  keyframes stand in for the element's whole transform. The separate `translate`, `scale` and
  `rotate` properties do add to it. A player that multiplies instead will lose flashes and
  shockwaves that rest at opacity 0.
- **Compare frames, not impressions.** Capture the Game view in Play mode and the mockup at the
  same moment (pause the browser's animations at a time, seek the Unity animations to it) and
  compute the pixel difference. Looking is not enough; neither is a still frame.
- **Parts that change look with game state need every look drawn.** Let the mockup draw itself
  from a state object, export it once per state, and keep each part once per look. The game then
  only switches looks. Text and numbers are set at run time; art is never approximated.
- **Bind by what the mockup shows,** and warn when a part is missing, so a changed mockup cannot
  break a screen silently.
- **Test on a copy of the save.** Back the save up before Play and restore it after, including any
  cached copy the game keeps in memory.
