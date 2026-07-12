# Rhythm Cook

A single-file HTML rhythm game where you cut ingredients to the beat. Watch the chef demo, then play along — every slice must land right on the rhythm. Built with vanilla HTML/CSS/JS and Web Audio API.

## Quick Start

Open `kitchen-rhythm-game.html` in any modern browser. No build, no dependencies, no server required.

## How to Play

1. Pick a level from the level select screen
2. An ingredient slides in from the right — watch the chef demo the cutting rhythm
3. The chef's cuts appear as blue circles scrolling on the beat track
4. After the demo, it's your turn — orange circles approach the hit zone
5. **Click anywhere or press any key** right as a circle hits the strike zone
6. Slice all ingredients in the level to progress

### Scoring

| Rank    | Timing    | Points |
|---------|-----------|--------|
| Perfect | Within 90ms   | 100 x combo |
| Good    | Within 170ms   | 50 x combo |
| Miss    | Beyond 220ms   | -10 HP |

Combo multiplies your score — keep the streak going. Perfect hits restore health, missed cuts drain it. Reach 0 HP and it's game over.

### Controls

- **Click / Tap / Any key** — slice
- **Escape** — return to level select
- **Mute button** — toggle sound

## Features

### 20 Levels, 14 Ingredients
Progress through 20 levels spanning BPM 90 to 190. Each level features unique vegetables — bread, cucumber, carrot, tomato, bell pepper, onion, zucchini, celery, radish, cabbage, leek, green bean, lettuce, and eggplant — all drawn as inline SVGs with dynamic cut marks.

### Synth-Powered Soundtrack
Every level has its own musical style generated in real time via Web Audio API — from chill Am kitchen grooves to hardcore DnB. No audio files, everything is synthesized:
- 20 unique styles with distinct chord progressions, melodies, and drum patterns
- Kick, snare, clap, hi-hat, open hat, crash cymbal
- Sawtooth bass, detuned leads, sine pads, triangle arpeggiators
- Dynamic compressor to prevent clipping
- Cut accents sync precisely to the rhythm grid

### Difficulty Progression
- Levels 1–4: 90–125 BPM, up to 5 cuts per ingredient, straight rhythms
- Levels 5–10: 130–150 BPM, syncopation, compound patterns
- Levels 11–14: 135–160 BPM, fast 16th-note runs
- Levels 15–20: 165–190 BPM, 6 ingredients per level, complex rhythms up to 13 cuts

### Progress System
- Progress is saved to localStorage
- 70% accuracy required to unlock the next level
- Best scores per level are tracked
- Reset progress button available

### Visual Polish
- Kitchen scene with tiled wall, wooden counter, window, and steam effects
- Scrolling beat track with animated hit/miss feedback
- Knife swings with rotation and scale animation
- Sliding ingredient entrance/exit transitions
- Confetti effects on level completion

## Tech Stack

- **No frameworks** — vanilla HTML, CSS, JavaScript
- **Web Audio API** — all music and sound effects are generated at runtime
- **SVG** — ingredients and chef character are inline vector graphics
- **localStorage** — persistent progress saving
- **Single file** — the entire game is self-contained in one HTML file

## Development

The game is contained in a single file:

```
kitchen-rhythm-game.html   # The complete game
```

Key architecture:
- **BGMusic class** — handles all audio synthesis, scheduling, and rhythm alignment
- **Game state machine** — `levelIntro → slidingIn → demo → transition → userTurn → foodComplete → slidingOut`
- **Beat system** — pattern arrays use beat fractions (e.g. `[0, 0.5, 1, 1.5]`) that map to precise musical grid positions
- **Phase-based timing** — each phase has a start time and duration, all driven by a single `requestAnimationFrame` loop

## License

MIT

## Author

由胡竞文制作 — [GitHub](https://github.com/hujingwen1025/Rhythm-Cook)
