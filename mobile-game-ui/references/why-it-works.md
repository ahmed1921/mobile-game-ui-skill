# Why the patterns work

The other references say what top games do. This one says why, so the rules can be bent with
judgment instead of copied. Each reason ends in a "so" line: the design consequence.

Contents: the hand · the eye · memory and habit · motivation · mood and audience · honest use ·
turning reasons into decisions.

## The hand

- **Most phone use is one thumb or a cradle.** A survey of 1,333 people (Hoober) saw 49 percent
  holding one-handed, 36 percent cradling, 15 percent two-handed. A measured comfortable
  right-thumb area is roughly a 27 to 41 mm radius from the thumb's base. Grips change with the
  game: portrait casual is mostly one thumb, landscape is two.
  *So:* primary actions sit in the lower half in portrait and in the lower corners in landscape.
  Things only read (currencies, goals, timers) go to the top, which is hard to reach but easy to
  see.
- **Bigger and nearer targets are faster to hit** (Fitts' law). Speed falls off quickly below
  about 9 to 10 mm.
  *So:* the most frequent action is the biggest button and nearest the thumb. Minimum 44 pt
  targets with gaps. Dangerous actions (spend premium currency, quit) are smaller and further
  away, never under a resting thumb.
- **Fingers cover what they touch.**
  *So:* feedback appears above or beside the finger (a lifted card, a tooltip above the press),
  and the thing dragged is offset upward.
- **A HUD past five or six live controls stops being playable** (Fortnite's mobile design
  guidance).
  *So:* collapse the rest into one menu, or show controls only when they apply.

## The eye

- **The eye lands on the largest, brightest, warmest, moving thing first.** Everything on a
  screen is ranked by those four, whether the designer ranked it or not.
  *So:* give the primary action all four, and take them away from everything else. If two things
  are both big and yellow, neither is primary.
- **Colour is read before shape, shape before text.**
  *So:* a colour means one thing everywhere (green = spend or go, red = danger or new, gold =
  reward). Text is the last resort and stays to one or two words.
- **Contrast against the background makes things readable**, and game backgrounds are busy.
  *So:* heavy type with a dark outline or a plate behind it; a scrim behind popups; panels a
  clear step lighter or darker than the world.
- **Things that are close or look alike are seen as a group** (Gestalt proximity and similarity).
  *So:* a cost sits on its button, a count sits on its icon, related chips share a pill. Space
  separates groups better than lines do.
- **People scan, they do not read.** In portrait the scan runs top strip, centre, bottom action.
  *So:* status on top, subject in the middle, action at the bottom. That is the skeleton of
  nearly every screen in the sample.
- **Motion in the corner of the eye pulls attention hard.**
  *So:* use it for exactly one thing per screen, and keep idle loops slow.

## Memory and habit

- **Players spend most of their time in other games** (Jakob's law). They arrive knowing that
  currency is top-right, settings is a gear, a red dot means "new", the big button starts play.
  *So:* keep the conventions, invent the look. Breaking a convention costs every new player a
  moment of confusion, which is expensive in the first minute.
- **Recognition is easier than recall.**
  *So:* show the options (cards, icons, a tree) instead of making players remember them. Show the
  cost on the button. Show the unlock rule on the lock.
- **Working memory holds only a few items.**
  *So:* one decision per screen, three to five choices, one primary action. Long lists get
  filters or tabs.
- **Consistency builds trust fast; one inconsistency breaks it.**
  *So:* one button shape, one radius, one outline weight, one set of durations.

## Motivation

- **People speed up as a goal gets closer** (the goal-gradient effect), and progress already
  granted makes a goal feel started (endowed progress).
  *So:* show progress as a bar or a row of pips, never only as a number. Start bars a little
  filled. Show the next reward at the end of the bar.
- **Seeing "one step away" motivates.** A 2024 study on Wordle found the first near-solution
  raised motivation and lowered frustration.
  *So:* after a loss, show how close it was (wave 6 of 8, boss at 12 percent) and one concrete
  way to close the gap.
- **Anticipation is half of a reward.** The moment before the reveal is felt as strongly as the
  prize.
  *So:* stage rewards: a beat of build-up, the reveal, then the count-up. See
  [motion-and-vfx.md](motion-and-vfx.md).
- **Unpredictable rewards hold attention longer than fixed ones.**
  *So:* chests and drops are engaging; be open about odds and never tie them to deceptive
  near-misses (see "Honest use").
- **Losses weigh about twice as much as equal gains.**
  *So:* "keep your streak" and "revive to keep going" are strong; use them sparingly and never
  with a hidden timer or a tiny decline button.
- **Collections want to be completed.**
  *So:* show the empty slots. A roster with silhouettes for unowned heroes sells itself.
- **Autonomy, mastery and purpose keep people for months**, long after reward tricks fade.
  *So:* the UI should make choices feel like the player's own (squad building, talent paths),
  show mastery (stars, ranks, bests) and point at a goal (the next land, the next boss).
- **Every action needs a reaction.** Feedback is what makes an input feel like it mattered.
  *So:* no silent buttons, no numbers that change without moving.

## Mood and audience

The weight of the UI is chosen by the feeling the game sells, before any pattern is applied.

| Feeling sold | UI weight | Palette | Type | Motion |
|--------------|-----------|---------|------|--------|
| Calm, tidy, "stress relief" (sort, logic, mahjong) | Almost none: three header items, one booster row | Pale or one soft hue; the pieces carry the colour | Rounded, medium weight | Soft, slow, small |
| Bright fun (match, merge, blast, casual battlers) | Medium: pills, chunky buttons, mascots | Saturated, multi-colour with fixed roles | Heavy rounded with dark outline | Bouncy, generous |
| Thrill and luck (slots, casino, looters) | Heavy: gold frames, meters, flashing wins | Purple or red with gold | Fat gradient display type | Constant, loud |
| Power fantasy (RPG, idle, squad) | Medium to heavy: frames, rarity, stats | Dark base, jewel accents | Condensed or angular, metallic touches | Sharp, weighty |
| Strategy and scale (4X, builders) | Dense: many small pills and icon stacks | Earthy or steel with a faction accent | Compact sans | Brisk, functional |
| Realism and tension (shooters, sports) | Thin and translucent | Grey, desaturated, one accent | Condensed capitals | Minimal, fast |
| Romance and prestige (story, premium) | Almost invisible | Dark, cinematic | Thin serif or light sans | Slow fades |

Audience matters as much: older puzzle players are sold "large tiles" and high contrast; young
action players accept dense HUDs; a broad casual audience needs everything readable at arm's
length and playable with one thumb.

## Honest use

The same psychology can respect players or exploit them. The difference is whether the player
would agree with the design if they saw how it worked.

- Show real prices, real timers and drop odds. No fake countdowns.
- The decline button is as easy to find as the accept button.
- Random outcomes must not be dressed up as near-wins. A near-miss from skill is feedback; a
  staged near-miss from a random roll is manipulation.
- Spending premium currency asks once before it happens.
- Red dots mean something real. A badge that never clears teaches players to ignore all of them.
- Children's games and real-money mechanics have legal rules; check them for the target market.

## Turning reasons into decisions

When a layout question comes up, ask in this order:

1. What is the one thing the player does here, and is it the biggest warm thing near the thumb?
2. What must they see to decide, and is that all that is on screen?
3. Does every colour, shape and badge mean what it means everywhere else?
4. Will a first-time player recognise it from other games?
5. What moves when they act, and what does that motion explain?
6. What feeling is this game selling, and is the UI the right weight for it?
7. Would the player be fine with how this works if they saw it explained?
