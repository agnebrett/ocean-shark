# Vice Squad

A shared daily log for a group health challenge. Every night, each person answers three questions on a 0–10 scale (0 = virtuous, 10 = disgraceful):

1. Did you work out today?
2. Did you drink alcohol today?
3. Did you indulge another vice today?

Submissions land on a shared board everyone can see: each person gets three rows of small day-boxes (workout / alcohol / vices), colored on a green → yellow → orange → red ramp by their score. Missed days stay blank. A leaderboard ranks everyone by **Overall**, **Strong** (workout), **Sober** (alcohol), **Clean** (vices), and **Showed Up** (logging rate), and a personal page shows just your own track.

Other behaviors:

- **Backfill** — the date picker on the Log tab lets you submit any missed day back to when you joined. Resubmitting a day overwrites it.
- **Late joiners** — anyone can add themselves from the "Who are you?" dialog; their rows simply start at their join date on the same shared date track, so days always line up column-for-column.
- **Day rollover** is on US Eastern time.

## How it's hosted

The live, shared copy runs as a Claude artifact, which provides the multi-device shared database (`window.claude` → the `db` capability). Each device picks its identity once ("Who are you?"), remembered in that browser.

This file in the repo is the source of record for that artifact. Opened directly (file system or GitHub Pages), the page renders but shows a "live sync unavailable" banner — the shared store only exists when the page is served as the artifact on claude.ai. To change the app, edit `index.html` here and republish the artifact from it.
