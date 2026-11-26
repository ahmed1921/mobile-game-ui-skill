# Layout patterns by screen

Wireframes show where things sit. Sizes are for a 1080 x 1920 portrait or 1920 x 1080 landscape
reference canvas. Keep all controls inside the device safe area; let backgrounds bleed to the edge.

Contents: thumb reach · home (portrait, landscape) · top bar · bottom tabs · stage map · HUD by
genre · results · collection and detail · shop · popups · upgrade and reward moments · checklist.

## Thumb reach decides placement

- **Portrait, one hand:** the bottom third is easy, the middle is fine, the top is a stretch. So:
  presses at the bottom, reading at the top.
- **Landscape, two hands:** both bottom corners are easy, the centre and top-centre are hard to reach
  and should hold information only. Left thumb moves or navigates, right thumb acts.
- Targets at least 44 pt (roughly 120 px on a 1080-wide canvas), 8 pt or more between them. The
  primary button is two to three times that.
- Keep five or six live controls on screen during play at most. More than that goes into a tray,
  a wheel or a second page.

## Home / lobby

The home screen answers "what do I do now?" in under a second. The answer is the big button.

Portrait (most casual and midcore games):

```
┌───────────────────────────────┐
│ (avatar Lv)   [⚡30] [♦150] [●3.3K +] ⚙ │  what you own
│ ┌events┐                 ┌offers┐│
│ │ icon │                 │ icon ││  side stacks: time-limited things,
│ │ icon │   LIVE SCENE    │ icon ││  each with a timer or red dot
│ │ icon │  hero / base /  │ icon ││
│ └──────┘   room / board  └──────┘│
│                                 │
│      [ chest ][ chest ][ pass ] │  optional progress strip
│   ┌───────────────────────────┐ │
│   │        PLAY  Lv 42        │ │  the one big warm button
│   └───────────────────────────┘ │
│ [shop] [heroes] [HOME] [clan] [events] │  five tabs, home raised
└───────────────────────────────┘
```

Landscape (builders, brawlers, shooters):

```
┌──────────────────────────────────────────────────────────┐
│ (avatar Lv XP)        LOGO / TITLE      [⚡] [♦] [●]  ⚙   │
│ [HEROES ]                                        [daily] │
│ [TALENTS]            HERO or BASE,               [chest] │
│ [SHOP   ]            centre stage                [event] │
│ [QUESTS ]                                                │
│                                          [ mode / stage ▸]│
│ [progress card]      [squad / power]     [    PLAY     ] │
└──────────────────────────────────────────────────────────┘
```

Rules:
- Left column navigates, right column holds gifts and timed things, bottom right is the play button
  with its mode or stage selector directly above or beside it.
- Give each destination its own colour and reuse that colour as the accent on the screen it opens.
- The middle stays free for the hero, base or scene. Do not fill it with panels.
- If there are more than about eight icons on the home screen, group them (one "Events" button that
  opens a list) instead of adding a third column.

## Top bar

`[avatar + level + XP] ........ [currency pill] [currency pill] [currency pill +] [settings]`

- A pill is: icon, number, optional green "+". Dark pill on busy backgrounds so the number reads.
- Order currencies from most common (left) to premium (right), or follow the genre habit.
- On inner screens the avatar is replaced by a back arrow and the screen title. Currencies stay in
  the same place on every screen so the player's eye never hunts.
- Animate changes: fly the reward to the pill, bump the pill, count the number up.

## Bottom tab bar (portrait menus)

- Three to five tabs. Home or Battle sits in the middle, larger or lifted.
- Each tab: icon above a one-word label; the selected tab grows, brightens and keeps its label.
- Locked tabs are shown greyed with the unlock level, not hidden.
- Swiping between tabs is expected in portrait games with five tabs.

## Stage select / world map

```
┌───────────────────────────────────────────────┬────────────┐
│ ←  [REGION RIBBON]  ★ 5/18          currencies │ STAGE 3    │
│ [reg]                                          │ enemies ▢▢▢│
│ [reg]      ②──┐        ④🔒──┐      (boss)     │ power vs   │
│ [reg]   ①─┘   └──③you──┘    └──⑤🔒──┘         │ rewards ▢▢▢│
│ [reg]     ★★★  ★★☆                             │ star goals │
│                                                │ [ FIGHT ⚡5 ]│
└───────────────────────────────────────────────┴────────────┘
```

- Nodes on a path. States must differ in shape as well as colour: cleared (number, stars), current
  (larger, pulsing ring, the player's marker on it), locked (padlock), boss (bigger, skull or crown).
- Stars under each cleared node. Total stars for the region near the title, with the next chest.
- Picking a node opens a detail panel or sheet: what you will fight, what you will win, how your
  power compares, and the fight button with its energy cost. The fight button sits in the same corner
  as the home screen's play button.
- Regions each get a colour and an emblem. Locked regions show their unlock condition.

## Gameplay HUD by genre

The player asks, in order: am I OK, what can I do, how far along am I.

**Lane or base defence, auto-battler (landscape):**

```
┌──────────────────────────────────────────────────────────┐
│ [♥ wall 1640/2000]     [WAVE 5/8 ●●●●◉○○☠]      [x1] [❚❚] │
│ [army 49/250]                                            │
│                                                          │
│   BASE          YOUR ARMY   ⚔   ENEMY WAVE               │
│                                                    (pwr) │
│ [● gold] [card][card][card][card]   hint     (pwr)(PWR)  │
└──────────────────────────────────────────────────────────┘
```

Health top-left, wave progress top-centre as pips with the boss marked, speed and pause top-right,
gold directly beside the build cards bottom-left, powers in a thumb arc bottom-right with the
strongest one largest. Free build spots glow in the selected card's colour.

**Card arena (portrait):** arena fills the screen; hand of four along the bottom; the resource bar
directly under the hand; next card small at the left; timer top-right; health on the objects.

**Match and puzzle (portrait):** top panel with goal, character, moves or timer; board; one row of
boosters with count badges. Newer games reduce the top panel to a thin strip.

**Roguelite (portrait):** XP bar across the top, timer centre, coins and kills under it, pause in a
corner; nothing at the bottom except the joystick. Level-up pauses the game and shows three cards.

**Shooter or action (landscape):** joystick left, action cluster in an arc right with the fire button
largest, minimap top corner, health bottom-centre or top-left, all of it movable by the player.

**4X builder:** resources along the top, tab row along the bottom, event stack on the right, the
build queue as small timers on the left; building actions appear as a small menu at the building.

Shared HUD rules:
- Enemy health bars only on things that matter (elites, bosses) or after damage.
- Damage numbers scale with the hit and change colour for crit and damage type. Merge rapid hits.
- A boss gets a named, full-width bar and an entrance card.
- When something is ready (ability, card affordable), it glows or pulses; when not, it is dim with
  the remaining time or missing cost shown on it.

## Results

```
┌──────────────────────────────────────────────────────────┐
│ VICTORY!  (big, slanted, lands first)        ★  ★  ★     │
│  stage name                              ┌─────────────┐ │
│                                          │ goal ✓  412 │ │
│   winning squad on a podium,             │ goal ✓  82% │ │
│   rays behind, confetti                  │ goal ✓ 3:42 │ │
│                                          │ rewards ▢▢▢▢│ │
│ [XP bar +120]                [↻] [x2 ad] [  CONTINUE  ]  │
└──────────────────────────────────────────────────────────┘
```

- Beats in order: title, stars one by one, stat rows counting up, rewards popping, XP filling.
  Each beat is short and a tap skips ahead.
- Tie each star to the goal that earned it, so the player learns how to get three.
- One way forward (warm colour), a replay, and at most one optional multiplier offer.
- Defeat uses the same layout, cooler colours, a tip about why, and Retry as the big button.

## Collection and detail (heroes, cards, gear)

```
┌──────────────────────────────────────────────────────────┐
│ ← HEROES 6/15   squad ◉◉◉🔒               currencies      │
│ [All][Melee][Ranged][Magic][Support] [sort]┌────────────┐ │
│ ▢ ▢ ▣ ▢ ▢                                  │ HERO on a  │ │
│ ▢ ▢ ▢ ▢ ▢   card = portrait, class chip,   │ stage, name│ │
│ ▢ ▢ ▢ ▢ ▢   level, rarity band, progress   │ tags, level│ │
│                                            │ stats +Δ   │ │
│                                            │ [toggle] [UPGRADE ●]│
└──────────────────────────────────────────────────────────┘
```

- Grid on one side, detail on the other (landscape) or grid above a bottom sheet (portrait).
- Card background or frame shows rarity; a small round chip shows class or element; both systems
  keep their colours everywhere in the game.
- Owned cards show level and upgrade progress; a full bar turns green and says "Upgrade".
- Locked cards stay visible, dimmed, with the price or the unlock condition in place of progress.
- Detail stats show the gain from the next upgrade in green beside the current value.
- The upgrade button carries its cost on it and turns red-priced or dim when unaffordable.

## Shop

- Tabs or one long scroll with section headers: offers first, then chests, premium currency, soft
  currency.
- Each product is a card: big item art, amount, a "best value" or bonus ribbon where true, and the
  price on a button at the bottom of the card. Free and ad-reward items show a timer.
- Show real prices and real odds. A confirm step for premium-currency spends.

## Popups

- Dim the screen behind to 50 to 70 percent; panel scales up from 90 percent.
- Title on a ribbon or header band in the destination's colour; close "X" top-right; one main button
  at the bottom, optional quiet secondary to its left.
- One popup at a time; queue the rest. Never during combat.
- Small confirmations are a bottom sheet in portrait rather than a centred panel.

## Talent or skill tree

```
┌──────────────────────────────────────────────────────────┐
│ TALENTS                                    [reset] [◈ 340]│
│  (crest) ARMY    (crest) CASTLE   (crest) GOLD  (crest) POWER│
│     ◉──┐            ◉──┐             ◉──┐          ◉──┐   │
│        ◉★           ◎ selected          ◉             ◉   │
│     ◉──┘            ◉──┘             ◉★─┘          ◉──┘   │
│        ◉               ◉                ◉             ◉   │
│     🔒                🔒               🔒             ◉   │
│ ┌─[icon] WAR CAMP  rank ▮▯▯▯▯▯   350 » 450   [UPGRADE ◈150]┐│
└──────────────────────────────────────────────────────────┘
```

- Branches side by side, each with a crest and a banner in its own colour.
- Nodes are round icon buttons on a zigzag path. The ring around a node fills with rank; pips under
  it count ranks; badges mark maxed (star), affordable (green arrow) and locked (padlock).
- Lines between nodes are dark until the next node is started, then lit in the branch colour with a
  moving pattern.
- No names or sentences on the tree. The selected node gets a detail panel along the bottom: big
  icon, name, one line, the value now and the value after, and the buy button with its price.
- The spend currency sits top-right and is the only currency shown.

## Upgrade and reward moments

- Level-up choice (roguelites): three cards side by side, rarity colour frames, icon, name, one line
  of effect, "new" or star rank. Game paused, darkened.
- Chest or pack opening: anticipation shake, burst, items revealed one at a time, summary grid.
- Hero upgrade: the stat that changed counts up and flashes green on the detail panel.

## More templates

**Tray-sort puzzle** (the hybrid-casual template, used by many current hits):

```
[coins]      Level 12      [pause]
+------------------------------+
|        goal picture     3/5  |   what is being filled or cleared
+------------------------------+
[ ][ ][ ][ ][ ][ ][ ]              holding tray: full tray = fail
  o  o  o  o  o                    supply: numbered or coloured pieces
  o  o  o  o  o
   (hint) (undo) (shuffle) (+)     boosters with count badges
```

Read order is the decision order: goal, risk, choices. The fail state is an object on screen.

**Lane or gate runner.** The lane from behind fills the screen. Effects are written on the world
in giant signed numbers (blue +1 and x2, red -5), hit points sit on enemies and barrels, the boss
has one bar at the far end. HUD: an avatar and two pills, or nothing.

**Merge with orders.** Pills on top (level star with bar, energy, coins, gems). An order strip:
customer portraits, wanted items, reward, a green Give button. The board below, a rounded panel
over the meta scene. Locked areas of the scene carry a sign and a price.

**Slots bar.** One fixed bottom bar: bet with minus and plus, a centred round SPIN, total win, max
bet. Jackpot meters stacked on top. Everything between is the machine. A win is a huge word with a
counting number plate and a small skip.

**Building panel (4X).** Slides up from the bottom as a card: title, one line of purpose, a
picture of what it affects, cost, a wide Upgrade button. The world stays visible above it.

**Story choice card.** A framed scene or tilted photo, a one-line dilemma, two buttons. Used by
merge and match games to sell the story between boards.

**Store screenshots.** A coloured caption band top or bottom, two to four words in heavy outlined
type, one verb per shot, the real screen under it, and a hand or mascot showing the gesture.

## Layout checklist

- [ ] One warm primary button, in the thumb corner, bigger than everything else.
- [ ] Currencies top, same place on every screen.
- [ ] Nothing interactive in the centre during play; nothing important under the notch or home bar.
- [ ] Every locked item says how to unlock it.
- [ ] Every colour used has a stated meaning and it matches the other screens.
- [ ] Longest text still fits (allow 30 to 40 percent growth for translation).
- [ ] Works at 16:9, 19.5:9 and 4:3.
