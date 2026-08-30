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

The page is plain static HTML — anyone with the URL can use it, no accounts. Shared data lives in a free Firebase Realtime Database, which the page reads and writes over plain HTTPS (REST + server-sent events for live updates; no SDK). Each device picks its identity once ("Who are you?"), remembered in that browser.

### One-time setup

1. **Create the database** (free, needs a Google login):
   - Go to <https://console.firebase.google.com> → **Create a project** (any name, Analytics off is fine).
   - In the project: **Build → Realtime Database → Create database** (any location, **locked mode**).
   - Open the **Rules** tab, replace the contents with the following, and hit **Publish** (don't use "test mode" — its rules auto-expire after 30 days):

     ```json
     {
       "rules": {
         ".read": true,
         ".write": true
       }
     }
     ```

   - On the **Data** tab, copy the database URL shown at the top — it looks like `https://YOUR-PROJECT-default-rtdb.firebaseio.com`.
2. **Wire it in**: paste that URL into the `FIREBASE_DB_URL` constant near the top of the `<script>` in `index.html`.
3. **Host the page**: make the repo public (Settings → General → Danger Zone → Change visibility), then Settings → **Pages** → deploy from the default branch, root folder. The app will be at `https://<user>.github.io/ocean-shark/health-challenge/`.

### Caveat

The rules above mean anyone who has the database URL can read and write the data. For a friends' challenge whose worst-case attack is someone forging Eddie's workout scores, that's an acceptable trade for zero-login simplicity — just don't put anything sensitive in it.
