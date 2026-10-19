# idle.fm

Endless lofi and phonk radio, synthesized live in the browser with the Web Audio API. No audio files, no streams, no accounts, no tracking.

## Run

It's a single static file. Open `index.html` in a browser, or serve the folder:

```sh
npx serve .
```

Press **[ play ]**. Browsers only allow audio to start after a click.

## Stations

| Genre | Station | BPM |
|-------|---------|-----|
| lofi  | chill   | 78  |
| lofi  | focus   | 70  |
| lofi  | jazzhop | 88  |
| lofi  | 3am     | 64  |
| phonk | drift   | 130 |
| phonk | memphis | 84  |

`[lofi]` / `[phonk]` jump to a random station of that genre. `[ skip ]` generates a new track.

## How it works

Everything lives in the `Radio` class in `index.html`:

- `makeTrack()` picks a key, chord progression, drum/bass patterns, melody and title from a random seed.
- `tick()` schedules the next quarter-second of notes every 30 ms. When a track's bars run out, it crossfades into a new one.
- `kick()`, `snare()`, `epChord()`, `sub808()`, `cowbell()`… build each sound from oscillators, filtered noise and gain envelopes.
- `render()` updates the DOM from `state`. Elements are bound with `data-t`, `data-tune`, `data-genre` and `data-on` attributes.

## Deploy

Upload `index.html` to any static host (GitHub Pages, Netlify, Cloudflare Pages). There is no build step.
