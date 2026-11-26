---
name: mobile-game-ui
description: Design original mobile game GUI the way top-grossing games do, and build it in Unity. Use this whenever the user asks to design, redesign, mock up, restyle, critique or implement any mobile game screen, HUD, menu, popup, button set or UI art direction (home or lobby, stage map, battle HUD, results, hero or card collection, shop, upgrade screens), asks how a hit game lays out its UI, wants an HTML mockup of a game, or wants a mockup turned into Unity UI (uGUI or UI Toolkit). Also use it for game icons (app icon, currency, item, skill and tab icons), UI animation, VFX and reward moments, and for explaining why a game UI pattern works. Use it even when the user only says "make the UI look better" or "design the GUI". Pairs with game-ui-patterns (screen taxonomy and motion specs) and unity:ui-ugui (engine API details).
---

# Mobile Game UI: design it, then build it in Unity

Good mobile game UI is not decoration. It is a small set of conventions that hundreds of millions of
players already know, dressed in a look that belongs to one game. Your job is to keep the conventions
and invent the look.

Notes on how top games in each genre lay out their screens are in
[references/top-games.md](references/top-games.md).

## Workflow

1. **Frame the job.** Find out, or decide and state: genre, orientation, the one thing the player does
   most, and which screens are in scope. If a codebase exists, read how its UI is built first, but
   treat its current look as replaceable unless the user says to keep it. Users who ask for a design
   usually want a fresh one, not their existing screen tidied up.
2. **Pull the conventions.** Read [references/layout-patterns.md](references/layout-patterns.md) for the
   screen types in scope, and the matching genre group in
   [references/top-games.md](references/top-games.md). If the request is unusual or the user wants proof,
   look at live references too (see "Looking at real games" below).
3. **Pick the weight of the UI from the feeling the game sells.** A calm sorter wants almost no
   chrome; a casino wants gold everywhere; a shooter wants thin grey. The table is in
   [references/why-it-works.md](references/why-it-works.md). Getting this wrong makes a correct
   layout feel like the wrong game.
4. **Set the visual system before drawing any screen.** Read
   [references/visual-design.md](references/visual-design.md) and write down: colour roles, shape
   language, outline and depth rule, two fonts, icon style. One system, every screen.
5. **Design the icons as one set and the motion with the layout.** Icons carry most of the
   meaning, so draw them together ([references/icons.md](references/icons.md)). Decide what moves
   on each screen and what it explains ([references/motion-and-vfx.md](references/motion-and-vfx.md)).
   A mockup that does not move is half a design.
6. **Mock up first.** Build the screens as an HTML mockup at the game's real aspect ratio, using the
   game's own character and world art where it exists. A mockup costs minutes; a Unity rebuild costs
   hours. Show the home screen and the main gameplay screen at minimum, since they carry the identity.
7. **Look at what you made.** Render it and inspect each screen at full size before showing it.
   Check for overlaps, clipped text, things hidden behind other things, and icons that do not read.
   Fix, then show. Never hand over a design you have not seen rendered.
8. **Build in Unity only after the user approves the mockup.** Read
   [references/unity-build.md](references/unity-build.md). Port the system (palette, sprites, fonts,
   components) first, then screens. Check in the Game view at three aspect ratios.

## The rules that held across the top games

These hold in nearly every top game. Break one only on purpose.

1. **One primary action per screen, and it is the biggest, warmest thing on it.** PLAY, FIGHT, SPIN,
   CONTINUE. It sits where the thumb rests: bottom centre in portrait, bottom right in landscape.
   Warm colours (yellow, orange, green) on a cooler screen. Nothing else on the screen competes.
2. **The top edge is for what you own.** Player badge and level top-left, currency pills top-right,
   each with an icon, a number, and usually a "+" to buy more. Settings lives in a top corner.
3. **Colour carries meaning, and the meaning never changes between screens.** One colour for "go
   forward", one for "spend or upgrade", one for danger and notifications (red), and the standard
   rarity ladder (grey, green, blue, purple, gold, then red or rainbow above). A multi-colour UI reads
   as designed when every colour has a job. It reads as noise when colours are picked per screen.
4. **The game world is the background.** Menus sit on top of the base, the board, the hero or a
   themed scene, not on flat panels. The hero or the meta scene takes the middle of the home screen.
5. **During play the UI gets out of the way.** HUDs live on the edges and corners. The centre belongs
   to the game. Status the player checks (health, moves, timer, goal) goes top; things the player
   presses (boosters, cards, abilities) go bottom, inside thumb reach.
6. **Things you spend sit next to what they buy.** Elixir under the cards, gold beside the build
   buttons, moves beside the board.
7. **Everything tappable looks tappable.** Chunky shapes, a darker bottom lip or drop shadow, an
   outline, a pressed state. Minimum 44 pt (about 9 to 10 mm) targets with gaps between them.
8. **Text is short, heavy and outlined.** Display type with a dark stroke so it reads on any
   background. Numbers are abbreviated (12.4K, 3.2M). Labels are one or two words.
9. **Locked things say how to unlock them.** A padlock alone teaches nothing. "Clear stage 9" does.
10. **Red dots drive navigation.** A badge on any button that has something to claim or new to see,
    carried up to the tab that contains it.
11. **Rewards are a show.** Results and reward moments get the full screen, rays, a big slanted title,
    stars or chests that stamp in one beat at a time, then a single button onward.
12. **Design every state.** Normal, pressed, disabled with the reason, locked, selected, new,
    affordable and not affordable, empty, full.

13. **Build with pictures and motion, not rows of text.** If a screen reads like a settings page,
    turn its rows into nodes, cards, icons and bars.
14. **Every motion has a job:** answer a tap, show where something came from, point at the next
    thing, or reward. Arrivals ease out, exits ease in and are shorter, nothing blocks a tap for
    more than half a second.
15. **Show the risk and the goal as objects.** A tray that fills, a wall bar, a row of pips. Players
    read objects faster than counters.
16. **Put numbers where they act.** Costs on buttons, hit points over enemies, gate effects on the
    gate. A number far from its subject needs a label; a number on it does not.
17. **Icons are one family with one light and one outline,** tested as black silhouettes at real
    size. Colour is never the only signal.
18. **Explain by convention, surprise by style.** Keep what players already know (gear, red dot,
    currency top-right, big button starts play) and spend originality on the look.

## Looking at real games

Do this when the user asks for references, when the genre is one you have not designed for, or when
you doubt a convention.

- Store pages show a game's screens without a login. Many store shots are marketing art, so look at
  several per game and read the ones that show a real screen.
- interfaceingame.com has real in-game captures grouped by game and by screen type.
- gameuidatabase.com is the deepest library but sits behind a human check. Ask the user to pass it;
  do not try to get around it.
- Study layout, hierarchy and colour roles. Never copy a specific game's art, characters, logo or
  exact look. The conventions are shared by everyone; the look must be the user's own.

## What to hand over

For a design task: the mockup, plus a short note with the visual system (colour roles with hex
values, fonts, shape rules), what each screen's primary action is, and what you assumed.
For a build task: what was built, how it was checked (which aspect ratios, on device or not), and
what was not checked.

## Reference files

| Read | When |
|------|------|
| [references/layout-patterns.md](references/layout-patterns.md) | Laying out any screen: wireframes for home, map, HUDs by genre, results, collection, shop, popups |
| [references/visual-design.md](references/visual-design.md) | Choosing colours, shapes, type, icons, depth, motion; avoiding the common ugly results |
| [references/top-games.md](references/top-games.md) | Wanting evidence, or designing in a specific genre |
| [references/motion-and-vfx.md](references/motion-and-vfx.md) | Animating anything: timings and curves, recipes per moment (screen entry, chest, win, loss, upgrade, skill tree), the VFX kit, layering a reward, sound, restraint |
| [references/icons.md](references/icons.md) | Designing the app icon or any in-game icon set: families, anatomy, currency conventions, badges, sizes, how to draw and test |
| [references/why-it-works.md](references/why-it-works.md) | Explaining or choosing between options: the hand, the eye, habit, motivation, mood and audience, honest use |
| [references/unity-build.md](references/unity-build.md) | Building or fixing the UI in Unity |
