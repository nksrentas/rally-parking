# Rally Parking

Single-file top-down parking game. 15 stages across 6 circuits, Normal/Hard
difficulty, rain, night, ice, valet runs, rolling tires, pedestrians, truck
stages, daily challenge, and a coin-powered Garage for car skins.

**Play it:** [live on GitHub Pages](https://nksrentas.github.io/rally-parking/)

No build, no deps, one HTML file. Open `index.html` in any modern browser.

## How to play

- **Drive** with `W`/`A`/`S`/`D` or arrow keys.
- **Handbrake:** `Space`.
- **Reset a stage:** `R`.
- **Mute:** button on the HUD.

Park the pink car on the green spot. Align the arrow, stop moving, hold for
half a second. Stars come from time, precision, and clean runs (no bumps).

Touch controls for phones and tablets appear automatically. Works down to
~480px.

## Features

- **15 stages** grouped into 6 circuits: Rookie, City, Precision, Elements,
  Mayhem, Boss.
- **Normal / Hard** difficulty. Hard = tighter parking tolerance and 2-hit
  damage cap. Separate records and ghosts per tier.
- **Weather and conditions:** rain slips the car, ice slips harder, night
  drops a headlight cone.
- **Valet Rush:** multi-drop stages where you chain three parked cars in a
  row without resetting the timer.
- **Rolling tires** that bounce off walls and hurt you on contact.
- **Pedestrians** that walk across the lot. Hit one = instant DNF.
- **Ghost replay** of your best run per stage, per difficulty.
- **Leaderboard** with 30 seeded ghost drivers + your real runs.
- **Daily Challenge** picks one stage per local date. Streak counts
  consecutive days played.
- **Garage (shop):** earn coins (10 per star on first clear), spend them
  on car skins.
- **Boss stage** (L15 Championship): night + rain + valet + truck + traffic.

## Built with

- Plain HTML + CSS + JavaScript. No framework.
- Canvas 2D rendering. Bicycle-model car physics.
- Web Audio for engine hum, thud, chime.
- localStorage for save data, quota-aware (drops ghosts if we overflow).
- SAT collision for cars, circle-vs-AABB for tires and pedestrians.

## Tech notes

- Entire game is one `index.html` file. No build step. Drop it on any
  static host and it runs.
- `CIRCUITS`, `LEVELS`, `SKINS` arrays at the top of the file are the
  whole content layer. Add a stage by appending one object to `LEVELS`
  and including its id in a circuit's `levels` array.
- Save shape versioned as `parking.zen.save.v1` in localStorage. Migrations
  are handled defensively in the loader so old saves still work as new
  features land.
