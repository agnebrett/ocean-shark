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

The app is live on GitHub Pages: **https://agnebrett.github.io/ocean-shark/**

It's a full PWA — open that URL on your phone and add it to your home screen (iOS: Share → Add to Home Screen; Android: menu → Add to Home screen / Install app). It launches fullscreen with its own icon and works offline after the first load.

### How deployment works

GitHub Pages serves the branch `claude/health-challenge-tracker-jwa112`, which hosts two apps: Fretwork at the site root and the health-challenge tracker at `/health-challenge/`. Every push to this branch (`claude/guitar-chord-quiz-app-r1tl1x`) triggers `.github/workflows/deploy.yml`, which merges it into the Pages branch — so Fretwork changes go live automatically without touching the tracker.
