# Visual design: making the look

The layout conventions are shared by every hit game. The look is what makes a game its own. Build
the look as a small system, write it down, then apply it without exceptions.

Contents: the system in six decisions · colour · shape and depth · type · icons · style families ·
motion · mockup recipe · common failures.

## The system in six decisions

Decide these before drawing any screen, and list them in the hand-over:

1. **Ink:** one dark colour for all outlines and dark plates. Not pure black; take a deep tone that
   matches the art's own outlines (deep indigo, plum, navy, warm brown).
2. **Surface:** what panels are made of. Light (cream, white) with dark text reads friendly and lets
   coloured content shine. Dark translucent plates suit HUDs over busy scenes. Most games use both:
   light cards in menus, dark plates in play.
3. **Role colours:** six to eight saturated hues, each with a job (below).
4. **Shape rule:** corner radius, outline width, and the depth trick, used on every element.
5. **Type:** one display face for titles, buttons and numbers; one plain rounded face for body text.
6. **Icon rule:** one stroke weight and corner style, or one filled-and-outlined style.

## Colour

Give every colour a job and keep the job on every screen.

| Role | Typical colour | Used for |
|------|----------------|----------|
| Go forward | Yellow or orange | PLAY, FIGHT, CONTINUE: the one primary action |
| Spend / upgrade / confirm | Green | Upgrade, buy, claim, "+" on currency, affordable |
| Navigate / secondary | Blue | Tabs, secondary buttons, your own side in battle |
| Danger / enemy / alert | Red | Enemy health, notification dots, unaffordable price, defeat |
| Premium / magic | Purple | Gems, epic rarity, magic class, ad or bonus offers |
| Each place in the game | Its own hue | The nav button, and the header of the screen it opens |
| Rarity ladder | Grey, green, blue, purple, gold, red | Do not reorder; players know it |

Method:
- Start from the game's art. Sample its outline colour for the ink and check the role colours sit
  well beside the characters.
- Keep saturation high and values spread: if two role colours look the same in greyscale, change one.
- One warm primary on a cool or neutral field. The play button should be the only large warm thing.
- Tint, do not invent: lighter and darker versions of a role colour for highlight band, lip and
  disabled state. Pastel tints of the role colours make good reward and stat tile backgrounds.
- Backgrounds are a single hue gradient with a quiet pattern (diagonal stripes, rays, dots) so they
  feel alive without competing.
- Text contrast: dark ink on yellow, green, cyan, pink and cream; white needs a dark outline on any
  mid-bright colour. Check small text at 4.5:1.
- Never rely on colour alone: pair it with an icon, a shape or a label (rarity name on the card,
  padlock on locked, check mark on done).

## Shape and depth

Pick one of these depth tricks and use it everywhere:

- **Sticker:** thick ink outline, hard offset shadow straight down in ink, a light band along the top
  inside edge and a darker lip along the bottom. Pressed state moves the element down by the shadow
  height. Bold, cheap to build, reads at any size.
- **Glossy pill:** vertical gradient, bright top highlight, soft drop shadow, thin darker rim. The
  casual puzzle look.
- **Flat with accent:** flat fills, no outline, one subtle shadow, strong type. The app-like look for
  calm puzzle, word and board games.
- **Material frame:** wood, stone, metal or parchment frames with painted highlights. The classic
  fantasy look; heavier to produce and easy to make dated.

Shape language:
- Big radii and round forms feel friendly; slanted plates and sharp notches feel fast and
  competitive; fine lines and small caps feel premium and calm.
- Give the game one signature shape (a pennant notch, a slanted edge, a scalloped badge) and reuse it
  on titles, tabs and ribbons.
- Slight rotations (one or two degrees) on nav tiles and titles add energy; never rotate body text.

## Type

- Display face: heavy and wide enough to carry an outline (rounded sans, chunky grotesque, or a
  themed face). White or yellow fill, ink stroke about a tenth of the text height, optional hard
  shadow below.
- Body face: a clean rounded sans at medium or semibold weight. No outline; put it on a surface.
- Sizes on a 1080-wide canvas: primary button 80 to 110, screen title 60 to 80, card name 30 to 36,
  body 28 to 32, small label 24 minimum.
- Numbers: use the display face, tabular if it has them, and abbreviate large values.
- Uppercase for buttons and titles, sentence case for descriptions.

## Icons

- Draw or choose one family. Mixed icon styles are the fastest way to look amateur.
- Every button gets an icon; important ones also get a one-word label.
- Currency icons are small illustrations (coin, gem, bolt) with an outline, reused at every size.
- Use real symbols players know: sword for attack, heart for health, shield for defence, padlock,
  gear, cart, chest, star, crown, skull for boss.

How to design a whole set, the anatomy of an item icon, currency conventions, badges, sizes, the
tests and the app icon are in [icons.md](icons.md).

## Style families seen in the top games

Use these as starting points, then make one decision of your own.

| Family | Looks like | Suits |
|--------|-----------|-------|
| Bold flat brawler | Saturated flat fields, thick outlines, slanted dark plates, yellow go button | Action, arena, battlers, anything competitive |
| Glossy casual | Candy colours, glossy pills, soft shadows, cute mascots | Match, merge, casual builders |
| Minimal hybrid-casual | Deep single-hue background, bright toy-like pieces, almost no chrome | Sort, block, tray puzzles |
| Dense midcore | Framed panels, many counters and timers, metallic accents | 4X, idle RPG |
| Light anime | White and translucent panels, thin line icons, large character art | Hero collectors, open-world RPG |
| Flat app | White or dark flat surfaces, one accent, system-like controls | Word, board, daily puzzle |
| Neon arcade | Black with glowing gradients | Rhythm, arcade |

## Motion

Motion is part of the design, not a finish. Specify it with the mockup.

- Buttons: scale to 0.95 on press, spring back; the primary button idles with a slow 3 to 4 percent
  pulse.
- Screens: panels slide or scale in over 200 to 300 ms with ease-out; exits are faster.
- Numbers count up; currency flies from the reward to the pill; bars drain with a trailing ghost.
- Rewards: rays rotate slowly, stars stamp in with overshoot one at a time, confetti falls.
- Ready states pulse or glow; cooldowns wipe radially with seconds shown.
- Keep idle loops slow (two to four seconds) and never animate text someone is reading.
- Offer reduced motion.

The full treatment (a timing table, recipes for each moment, the VFX kit, how to layer a reward,
sound, restraint) is in [motion-and-vfx.md](motion-and-vfx.md).

## Mockup recipe (HTML)

1. Fixed canvas at the game's aspect ratio (1280 x 720 landscape or 390 x 844 portrait).
2. Define the six decisions as CSS classes: ink, surface card, dark plate, button, role colours.
3. Put the game's real art in: world as background, characters large, monsters and buildings where
   they belong. Draw UI chrome and icons fresh; do not reuse UI kit art from another style.
4. Build home, then the main gameplay screen, then results, map and collection.
5. Link the screens so the flow can be clicked through.
6. Render, inspect every screen at full size, fix overlaps and clipping, then show it.

## Game UI, not app UI

The fastest way to disappoint is to deliver a tidy list. Rows of name, description, progress bar and
button are how an app is built. A game screen is built from pictures first:

- **Icons carry the item, words explain one item at a time.** Give every talent, upgrade, quest and
  reward its own icon. Show icon, state and rank on the item; put the name, the sentence and the
  price in one detail panel for the item that is selected.
- **Structure is drawn, not tabled.** A talent screen is a tree or path of nodes joined by lines that
  light up as they are earned. A campaign is a road. A collection is a wall of cards.
- **State is graphic.** A ring that fills for rank, pips for steps, a gold ring and star for maxed, a
  green arrow badge for "you can afford this", a padlock for locked. No "3 / 5" where pips will do.
- **Things move.** Available nodes pulse, earned paths have energy running along them, the selected
  item sits on slowly turning rays, backgrounds twinkle or drift, the buy button breathes. A still
  screen reads as a form.
- **Rarity and rank change the object, not just its colour.** Common is plain. Rare gets a shine
  sweep. Epic gets sparkles. Legendary gets a living gold border, rays behind the art and a crown.
  Mythic burns, with a moving fire border, a dark backdrop and embers. Rank shows as stars on the
  card. A player should spot the best card in a grid without reading.
- **Give art room.** Show the whole character in the card with space around it. A face cropped to
  fill the frame, with chips stacked on top of it, reads as cramped.
- **Text colour.** Dark fill text on buttons looks heavy and dated. Button labels and prices are white
  with a dark outline; text on light panels is a coloured tone from the palette, not near-black.
- **Navigation is colourful.** Each tab keeps its own colour whether selected or not. Mark the
  current one with size and a ring, never by greying the others.

Test: cover the text on the screen. If you can still tell what each thing is and what state it is
in, it is game UI.

## Common failures

- **An app in a game's clothes.** Lists of text rows with small buttons. See the section above.

- **One-hue UI.** Everything navy and gold. It is consistent but dead. Fix with role colours.
- **Rainbow without roles.** Many colours, no meaning. Fix by assigning jobs and removing the rest.
- **Reskinning the old screen.** Asked for a new design, delivered the current layout with new paint.
  Start from the conventions and a blank canvas instead.
- **Chrome fighting the game.** Heavy frames and panels covering the scene. Remove panels until only
  the edges carry UI.
- **Everything is important.** Five buttons the same size. Make one big, the rest small.
- **Icons that do not read.** Tiny, mixed styles, or abstract shapes. Use known symbols at 40 px and up.
- **Unseen output.** Designing blind and shipping overlaps. Always look at the render first.
- **Copying one game.** Borrowing a specific game's characters, logo, or exact palette and shapes.
  Take structure from many games; make the look new.
