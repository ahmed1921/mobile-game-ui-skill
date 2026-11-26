# Icons: app icon and in-game icons

Icons carry more meaning per pixel than anything else in a game UI. A player reads a coin, a
lock, a sword or a red dot long before any word. This file covers the store icon, then the icons
inside the game, then how to draw and test them.

Contents: what the top 150 app icons do · app icon rules · in-game icon families · one style for
the whole set · anatomy of an item icon · currencies and resources · navigation and system icons ·
badges and states · sizes · how to draw one · testing · common failures.

## What the top 150 app icons do

Studied on one sheet (US top-grossing and top-free games, 2026-11-27), counted by eye:

| Kind | Share | Examples of the idea |
|------|-------|----------------------|
| One character face or bust | about 45% | An angry king, a grinning mascot, a worried heroine |
| The core game object | about 25% | A candy, a mahjong tile, a block cluster, an 8-ball, dice |
| The mechanic in miniature | about 12% | A runner between "+1" and "x2" gates, sort tubes, a bus and a crowd |
| A logotype | about 12% | Casino brands, big licences |
| Plain geometry | about 6% | A tilted square, a pawn, arrows, a number grid |

What they share:

- **One subject**, cropped tight, filling 70 to 90 percent of the square and often cut off by the
  edge, so it feels larger than its frame.
- **Faces look at you**, in three-quarter view, with big eyes and an open mouth. Strong emotion
  beats a neutral pose.
- **Warm subject on a cool ground.** The most common background is a sky-blue gradient, with the
  subject in yellow, orange or red. Casino icons invert this: gold on purple or red. Realistic
  shooters go dark and grey. Brainy puzzles go white.
- **Light from the top left**, a soft rim light, and a dark outline or halo that cuts the subject
  from the ground.
- **No words** unless the word is the brand. Numbers appear only when they are the mechanic.
- **Seasonal skins.** Santa hats, snow and pumpkins get painted in during events. The icon is part
  of live operations, not a fixed logo.

## App icon rules

- **One idea, not five.** Do not try to explain the whole game. Show the genre at a glance,
  because players pick by genre they already like.
- **A silhouette that reads at 32 px and still looks good at 1024.** No thin lines, no small
  detail, no low contrast, no small text.
- **Same visual language as the game's UI and screenshots.** A match between icon, store page and
  first screen raises installs; a mismatch feels like a trick.
- **Fit the audience.** Cute for casual, sharp and dark for midcore, clean for brain games.
- **Make several and test them.** The winner is often an odd variant nobody on the team favoured.
  Polish after the test, not before.
- **Check it where it lives:** on a busy wallpaper, in light and dark mode, inside the platform's
  rounded mask, next to competitors in a search list.

## In-game icon families

| Family | Job | Typical look |
|--------|-----|--------------|
| Currency and resources | "What I own" | Small, rendered, glossy objects: coin, gem, bolt, ticket |
| Items and rewards | "What I can get" | A rendered object in a rarity frame, with a count |
| Skills and powers | "What I can do" | A bold symbol in a round or square well, a cooldown sweep over it |
| Navigation tabs | "Where I can go" | A chunky object per place: house, sword and shield, book, shop stall, scroll |
| System | "How the app works" | Flat single-colour glyphs: gear, pause, close, back, sound, info |
| Status and class | "What kind this is" | A tiny glyph in a coloured disc: sword for melee, target for ranged, star for magic, heart for support |
| Badges | "Something changed" | Red dot, "!", count, lock, check, "NEW", an up arrow |

Two drawing styles live side by side in almost every hit, and that is correct:

- **Rendered icons** (currencies, items, tabs) are little illustrations with volume. They are the
  toys of the game and should feel collectable.
- **Glyph icons** (system, class, small labels) are flat, one or two colours, heavy strokes. They
  must never compete with the toys.

## One style for the whole set

Decide these once and hold them for every icon:

1. **View angle.** Front-on with a slight tilt, or three-quarter from above. Never mix.
2. **Light.** Top left. Highlight top left, shadow bottom right, on every icon.
3. **Outline.** One colour (a dark tint of the palette, not pure black) and one weight relative
   to size (about 4 to 6 percent of the icon's width). Thicker outside, thinner or none inside.
4. **Shading steps.** Base, one shade, one highlight. Three values are enough at 64 px.
5. **Corner softness.** Rounded and chunky, or sharp and faceted. Match the buttons.
6. **Saturation.** Icons are a touch more saturated than panels, less than the primary button.
7. **Padding.** The object fills about 80 percent of its box, optically centred (a sword leaning
   right sits a little left of centre).

Design the set together on one sheet. An icon that looks fine alone can be too close in shape to
its neighbour.

## Anatomy of an item icon

Back to front:

1. **Frame** in the rarity colour (grey, green, blue, purple, gold, then red or rainbow), with a
   darker lip at the bottom. Give each rarity a shape cue too (corner notches, a crown, a glow),
   so colour is never the only signal.
2. **Backdrop**: a soft radial light in a paler tint of the frame colour. Rays for the top tiers.
3. **Object**: one clear silhouette, tilted 10 to 20 degrees for energy.
4. **Outline and inner lines**.
5. **Highlight**: a hard white glint on the top-left edge, one small sparkle on premium items.
6. **Overlays**: count bottom-right in outlined digits, level top-left in a dark pill, a lock or
   check in a corner, a red dot top-right.

## Currencies and resources

Players already know these. Use the convention and spend originality on the style.

| Meaning | Convention |
|---------|-----------|
| Soft currency | A round gold coin, face-on or slightly tilted, with a stamped symbol |
| Hard currency | A faceted gem, most often purple, blue or green |
| Energy or stamina | A lightning bolt or a heart, in blue, yellow or red |
| Keys, tickets, tokens | The literal object, one flat colour family each |
| Experience | A star or "XP" in a rounded chip |
| Upgrade material | A themed object from the world (scrolls, shards, souls as a flame) |
| Time | A clock or hourglass |
| Premium or VIP | A crown |

Each currency owns one colour that appears nowhere else as a currency. A stack or pile of the
same icon means "more" (shop packs grow from a few coins to a chest to a vault).

## Navigation and system icons

- **Tab icons are objects with a label under them.** One or two words. The current tab is larger,
  lifted, and ringed or lit. Each tab can own a colour when the game's look is multi-colour.
- **System glyphs are the universal ones.** Gear, pause bars, X, a left chevron, a speaker, "i".
  Do not invent new shapes for these. Give them one stroke weight and put them in a button shape,
  since a bare glyph does not look tappable.
- **The close X sits top-right**, at least 44 pt, on the popup's corner and often half outside it.

## Badges and states

| Badge | Meaning | Look |
|-------|---------|------|
| Red dot | Something to see | 16 to 24 px red disc with a dark ring, top-right corner, half outside |
| Red dot with a number | How many | Same, wider; show "9+" past nine |
| "!" | Act now, free thing | Red disc with a white mark |
| Green up arrow | Can upgrade | Green disc, dark ring |
| Lock | Not yet | Dark disc with a white padlock, plus words saying how to unlock |
| Check | Done, owned, in squad | Green disc with a dark tick |
| Crown or star | Maxed, top tier | Gold |
| "NEW" | Unseen | A small slanted ribbon |
| Sale tag | Discount | A red or pink slanted flag with the percent |

A dimmed, desaturated icon means "not available". A grey icon with a lock means "locked". They
are different states; do not use one look for both.

## Sizes

- Design at 512 or 1024 px, export at 2x and 3x of the size used.
- Smallest in use: about 24 pt for inline glyphs, 32 to 40 pt for currencies in pills, 48 to 64 pt
  for tab and booster icons, 72 to 128 pt for item tiles.
- Anything tappable has a 44 pt target even when the drawing is smaller.

## How to draw one

1. **Name the meaning in two words** ("more soldiers"). If it takes a sentence, it needs a label,
   not a cleverer icon.
2. **Thumbnail six silhouettes** in solid black at the final size. Pick the one a stranger names
   fastest.
3. **Block flat colour**: two or three hues, one of them owned by this icon's meaning.
4. **Add the shade and the highlight** from the top-left light.
5. **Outline** at the set's weight.
6. **Add one accent**: a glint, a sparkle, a motion tick. Then stop.
7. **Shrink to the real size** and fix what turned to mush: fatten thin parts, widen gaps, delete
   detail.

For mockups, draw icons as small SVGs: a few rounded shapes, a stroke in the ink colour with
round joins, one white highlight shape. For shipping, render them as sprites from the same
masters so the whole set stays consistent.

## Testing

- **Silhouette test.** Fill it black. Can you still tell a sword from an axe from a potion?
- **Blur and greyscale test.** Blur it a little, or drop the colour. Still readable?
- **Size test.** Look at 64 px and 32 px. If it is a blob, simplify.
- **Neighbour test.** Put the whole set in a row. Any two that could be mistaken at a glance get
  redrawn. Shared silhouettes cause wrong taps.
- **Ground test.** Place it on the lightest and darkest panels it will sit on.
- **Colour-blind test.** Remove red-green difference. Rarity and state must still read by shape.

## Common failures

- A detailed illustration shrunk down instead of an icon designed small.
- Mixed view angles or light directions across a set.
- Outline weight that changes from icon to icon.
- Pure black outlines on a colourful UI (use the palette's dark ink).
- A new, private symbol for a universal action.
- Meaning carried by colour alone.
- Icons with no label for abstract ideas (stats, modes, talents). Pair an icon with one or two
  words until players have learned it.
- Placeholder icons from different kits: three styles on one screen reads as unfinished.
