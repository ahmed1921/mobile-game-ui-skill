# Motion and VFX for game UI

Motion is how a game UI talks back. A static screen can be correct and still feel dead. This file
says what moves, how long, with which curve, which effects go with it, and why. Numbers are
starting points drawn from platform motion guidance and game practice; tune them on a real phone.

Contents: the four jobs of motion · timing and easing · the principles that matter · recipes by
moment · the VFX kit · layering a reward · sound · restraint · building it (HTML and Unity) ·
checklist.

## The four jobs of motion

Every animation on a screen should be doing one of these. If it does none, cut it.

1. **Answer.** "I felt that tap." Press states, toggles, a refusal shake. Must start within one
   frame and finish in about 100 to 200 ms.
2. **Explain.** "This came from there." A panel grows out of the button that opened it, coins fly
   from the chest to the counter, a card slides to the slot it now fills. Motion shows cause.
3. **Point.** "Look here next." A pulse on the one thing the player can do now, a red dot that
   pops in, a hand that shows the gesture. One pointer per screen.
4. **Reward.** "That was worth it." Stars stamping in, a number counting up, rays behind a prize.
   The only job that may take a second or more, because the player is not waiting to act.

A fifth, quieter one: **keep the world alive.** Characters breathe, flags wave, a glow turns
slowly. It tells the player the game is running, not frozen. Keep it slow and small.

## Timing and easing

| What | Duration | Curve | Notes |
|------|----------|-------|-------|
| Button press down | 60 to 100 ms | ease-out | Move 3 to 5 px down or scale to 0.94 to 0.96. |
| Button release | 120 to 180 ms | back-out (overshoot about 1.5) | The small bounce is what reads as "juicy". |
| Toggle, tab switch | 120 to 200 ms | ease-out | The knob moves; the colour changes with it. |
| Popup in | 200 to 300 ms | back-out, from scale 0.8 and 0 opacity | Scrim fades in over the same time. |
| Popup out | 120 to 180 ms | ease-in | Leaving is always faster than arriving. |
| Screen change | 250 to 400 ms | ease-in-out | Old screen out and new one in may overlap. |
| List items arriving | 150 to 250 ms each, 30 to 60 ms apart | ease-out | Stagger from the top or from the tapped item. Cap the total near 600 ms. |
| Number count-up | 400 to 800 ms | ease-out | Fast at first, slowing into the final value. Tick sound on steps. |
| Bar fill | 300 to 600 ms | ease-out | A lighter "ghost" bar can trail behind on loss. |
| Currency fly to counter | 500 to 800 ms in all | burst out fast, hang, ease-in to the target | 5 to 12 pieces, 40 to 60 ms apart. |
| Star or stamp | 250 to 350 ms each, 200 to 300 ms apart | scale 2.4 to 1 with a small overshoot | One beat per star. A flash or ring on the landing frame. |
| Attention pulse | 1.2 to 1.8 s loop | ease-in-out | Scale 1 to 1.05, or a ring that grows and fades. |
| Idle breathing | 2 to 4 s loop | ease-in-out | 2 to 6 px or 1 to 2 percent. |
| Refusal shake | 250 to 350 ms | 3 to 4 swings, shrinking | Sideways 6 to 10 px. Add the reason in words. |

Rules behind the table:

- **Nothing that answers a tap may take longer than about 500 ms** before the player can act
  again. Long celebrations must be skippable by a tap.
- **Things that arrive ease out** (fast start, soft landing). **Things that leave ease in.** Never
  use linear motion except for spinning, scrolling and progress that truly is steady.
- **Overshoot is for arrivals of solid objects** (buttons, cards, stars). Fades, scrims and text
  do not bounce.
- **Pick four or five durations and reuse them** across the game. Consistency reads as quality
  more than any single clever animation.
- **Bigger travel needs more time.** A full-screen slide can take 400 ms; a 4 px press cannot.
- **Run UI motion on unscaled time**, so menus still move while the game is paused.

## The principles that matter (from the classic twelve)

- **Anticipation.** A small move the other way before the big one: a chest squats and shakes
  before it bursts, a button dips before a panel flies out. It makes the player look in time.
- **Squash and stretch.** A landing star flattens for two frames, a pressed button widens a
  touch. Keep volume: wider means shorter.
- **Follow-through and overlap.** Parts do not stop together. The panel lands, then its title
  settles, then the buttons pop in 40 ms apart. Ribbons and tails lag behind.
- **Slow in and out.** That is easing. See the table.
- **Staging.** One thing moves at a time where it matters. Dim or still everything else.
- **Exaggeration.** Game UI is theatre. Scale pops from 0.5 or 2.4, not from 0.95.
- **Secondary action.** Sparkles, dust and a glow support the main move. They never lead.
- **Timing gives weight.** Heavy and important things move slower and land harder.

## Recipes by moment

**Entering a screen.** Background first (instant or a fast fade), then the top bar slides down,
side rails slide in from their edges, the main subject pops in the centre, the primary button
arrives last with the biggest overshoot. 600 to 900 ms in all. Play the long version once per
session; afterwards the screen arrives settled.

**A versus or clash moment.** Two sides slide in from opposite edges and stop short of each
other. A badge stamps between them (scale 3 to 1). On its landing frame: a white flash across the
screen (to about 85 percent and out over 400 ms), one or two rings that expand and fade from the
badge, and a short screen shake (4 to 7 px, 300 ms). Then the HUD fades in.

**Opening a chest or pack.** Anticipation: the chest shakes, a glow under it grows (400 to 800 ms,
or as long as the player holds). Impact: a white flash, the lid snaps open with squash. Burst:
particles and light rays out of the opening. Reveal: prizes rise one by one, best last, each with
its rarity colour in the rays behind it. Collect: prizes shrink into their counters, which count
up. Give a skip from the second chest onward.

**Winning a level.** Freeze or slow the game for a beat. The title drops in at a slant with a
ribbon. Stars stamp in one at a time, each with its own sound, pitch rising. Reward tiles pop in
with numbers counting up. Level bar fills; if it levels up, it flashes and resets. The one
onward button arrives last and pulses. Confetti falls for two seconds, then stops.

**Losing.** Colder and slower. Desaturate or darken the scene, let ash or dust drift, no bounce on
the title. Show what was still earned, then one clear way to try again. Do not punish with a long
unskippable sequence.

**Spending and upgrading.** The cost flies or drains out of the counter (it ticks down), the thing
bought flashes white for two frames, scales up 10 to 15 percent and settles, a ring of sparkles
goes off, and the changed number is shown beside the old one with an arrow before it settles.
An upgrade that can be afforded pulses gently; one that cannot stays still.

**A skill tree.** Nodes that can be bought breathe. Lines to owned nodes carry a moving dashed
light toward the next node. The chosen node sits in a slow spinning halo. Buying sends a pulse
down the line to the nodes it unlocks, which pop their lock off.

**Gaining currency in play.** A number floats up from the source and fades (600 ms), coins arc to
the counter, the counter icon punches (scale 1.2 and back in 150 ms) on each landing, the number
counts up.

**Red dots and badges.** Pop in with overshoot once. Do not loop them forever; a slow pulse every
few seconds is enough. Clear them the instant the player has seen the thing.

**Combos and praise.** A word bursts in at a slant near the action ("Great!", "7 hits!"), holds
for 500 ms, drifts up and fades. Size and colour grow with the streak.

## The VFX kit

A small, reusable set covers nearly every UI moment in the top games.

| Effect | Looks like | Used for |
|--------|-----------|----------|
| Rays | A fan of soft wedges turning slowly behind a subject | Prizes, heroes, the chosen item. Colour them by rarity. |
| Sparkles | Four-point stars that twinkle (scale and fade, slightly turning) | Premium items, "new", idle shine on a ready button. |
| Shine sweep | A tilted white band crossing a surface every few seconds | Buttons that can be pressed, rare frames, a maxed node. |
| Glow | A soft blurred copy behind a shape, pulsing | Selection, affordance, energy. |
| Ring pulse | An outline that expands and fades | "Tap here", an impact, a notification. |
| Flash | The whole screen or one object goes white for 1 to 3 frames | Impacts, purchases, reveals. Keep it short. |
| Burst | 8 to 20 particles thrown out and fading | Collecting, popping, unlocking. |
| Confetti | Coloured strips falling with a wobble | Wins. Stop after a couple of seconds. |
| Coins and gems in flight | The currency icon, in small copies, on arcs | Any gain. Always end at the counter. |
| Floating numbers | "+25" rising and fading | Gains and damage. Colour by kind. |
| Trails | A fading streak behind a mover | Fast flyers, a slash. End the trail on impact. |
| Embers, ash, dust | Small slow particles drifting up or down | Mood: fire for mythic, ash for defeat, dust on landing. |
| Screen shake | The whole view jolts and settles | Heavy impacts only. A few pixels, under 400 ms. |
| Hit-stop | Everything holds for 2 to 6 frames | The instant of a big hit or a kill, before the burst. |

Colour the effects from the UI palette, not from white alone: gold for coins, the rarity colour
for item reveals, the faction colour for a side. Additive blending on dark backgrounds, normal
blending on light ones (additive light vanishes on white).

## Layering a reward, back to front

1. Scrim (the world dims to 50 to 70 percent).
2. Rays, turning.
3. Glow or halo.
4. The prize itself, popping in.
5. Sparkles and burst particles.
6. Title and numbers.
7. The button onward.
8. Confetti over everything, short-lived.

Each layer starts 60 to 120 ms after the one before. That offset is what makes it feel rich
rather than busy.

## Sound goes with motion

Every motion that answers the player has a sound, even a tiny one. A press click, a soft whoosh
for panels, a rising tick for count-ups, a chime per star with pitch going up, a coin clink on
each landing (vary the pitch slightly so ten coins do not sound like a machine). Silence right
before a big reveal makes it land harder. Haptics follow the same beats: a light tap on press, a
heavier one on a stamp or a purchase.

## Restraint

- **The more common an action, the simpler its feedback.** A button pressed two hundred times a
  session gets a 100 ms dip, not a firework.
- **One loud thing at a time.** If three things pulse, nothing is pointed at.
- **Match the genre.** Calm puzzles and story games use soft, slow, small motion. Arcade and
  casino go loud. Horror and realism barely move.
- **Loops must be quiet.** Anything that repeats forever should be slow and low-contrast, or it
  becomes a headache.
- **Never block.** The player can always tap through.
- **Offer reduced motion.** Honour the system setting: keep fades and colour changes, drop shakes,
  flashes and large moves. Avoid flashing more than three times a second for anyone.
- **Budget.** On a phone keep UI particles in the low hundreds, reuse pooled objects, and do not
  animate layout every frame.

## Building it

**In an HTML mockup:** CSS keyframes with `cubic-bezier(.34,1.56,.64,1)` for back-out, `ease-out`
for arrivals, `animation-fill-mode: both` with a delay per element for staggered entrances. Use
the separate `translate`, `scale` and `rotate` properties in keyframes so they add to an element's
own `transform` instead of replacing it. Rays are a `repeating-conic-gradient` with a radial mask,
rotating. A shine sweep is a tilted white strip moving across a clipped parent. Rings are a
bordered circle scaling up while fading. Gate the long intro behind a session flag so it plays
once.

**In Unity:** see [unity-build.md](unity-build.md). Tween RectTransforms and CanvasGroups on
unscaled time; keep a small library of named tweens (press, pop-in, stamp, fly-to) and particle
prefabs (burst, sparkle, confetti) and call them everywhere. Put moving parts on their own canvas
so a pulse does not rebuild the whole screen.

## Checklist

- Does every tap get an answer within a frame?
- Does each new thing show where it came from?
- Is exactly one thing asking for attention?
- Do arrivals ease out and exits ease in, with exits shorter?
- Is the reward sequence layered, timed in beats, and skippable?
- Are loops slow and quiet?
- Does each motion have a sound?
- Is there a reduced-motion path?
