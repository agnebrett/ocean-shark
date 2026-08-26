# Fretwork

A phone-friendly quiz app for memorizing acoustic guitar chord fingerings — all 22 common and semi-common open-position shapes plus the four essential barre chords — so the shapes are automatic before you ever pick up the guitar.

It's a single self-contained HTML file: no install, no build step, no server. Open `index.html` in any browser (it's designed phone-first).

## How it works

The path has 7 levels, each unlocked by finishing the one before it. Every level has three stages:

1. **Learn** — each chord is shown as a diagram with its fingering, a memory tip, and a quick name-recognition check.
2. **Recognize** — pick the right diagram out of three for a named chord, and name diagrams shown to you. Requires ≥70% first-try accuracy to pass; anything you miss is requeued until you get it right.
3. **Build** — a blank fretboard. Tap where the fingers go (and flag muted strings), then get graded with green/red dots and shown the correct shape.

Once a level is fully complete, its chords enter the **Review** pool — a spaced-repetition-style mixed quiz that surfaces your weakest shapes first. There's also a **Chord book** reference of every shape.

Progress is saved in your browser (`localStorage`), so it persists between visits on the same device.

## The chords

| Level | Chords |
|---|---|
| 1 · Open the door | E, A, D |
| 2 · Minor moods | Em, Am, Dm |
| 3 · Campfire pair | G, C |
| 4 · Blues sevenths | E7, A7, D7 |
| 5 · More sevenths | G7, C7, B7 |
| 6 · Color chords | Fmaj7, Cadd9, Dsus4, Asus2 |
| 7 · The barres | F, F♯m, Bm, B♭ |

## Using it on your phone

Any of these works:

- Enable GitHub Pages for this repo (Settings → Pages → deploy from the default branch) and open the URL on your phone. Add it to your home screen and it behaves like an app.
- Or just open `index.html` directly from the file system in a mobile browser.
