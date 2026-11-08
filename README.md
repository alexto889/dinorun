# Orange Dino Run

A simple endless-runner browser game: a cute orange dinosaur jumping over green cacti on an orange background, with navy outlines and text for contrast.
Built with plain HTML, CSS and JavaScript (no build step, no dependencies).

## Controls

- **Space / Up arrow / tap:** jump (also starts or restarts the game)
- **Hold Down arrow:** duck on the ground, or fall faster in the air
- On-screen **Jump** and **Duck** buttons are provided for touch devices

## Levels

| Level | Score | What changes |
|---|---|---|
| 1 | 0–299 | Single cacti, gentle speed |
| 2 | 300–999 | Faster, with double cacti |
| 3 | 1000+ | Fastest, with triple cacti and flying birds (jump the low ones, duck under the high ones) |

The background deepens in colour at each level, and a banner announces each level-up. The high score is saved in the browser.

## Leaderboard (Supabase)

After a game ends, players can save their score under a nickname. The Top 10 is shown under the game.

- Table: `public.dino_scores` (`player_name`, `score`, `level`, `created_at`) with row-level security.
- Anyone can read scores and add one (nickname 1–16 characters, score 0–99999, level 1–3). Updates and deletes are blocked.
- The Supabase URL and publishable key in `index.html` are meant to be public. Do not put a secret or service-role key in this repo.
- Scores are submitted from the browser, so a determined player could still submit a fake score. For a stricter leaderboard, validate scores in a Supabase Edge Function.

## Run locally

Open `index.html` in any modern browser.

## Deploy to Vercel

1. Sign in at [vercel.com](https://vercel.com) and choose **Add New > Project**.
2. Import the `alexto889/dinorun` GitHub repository.
3. Leave the settings as they are: Framework Preset **Other**, no build command, no output directory.
4. Click **Deploy**.

`vercel.json` adds clean URLs and basic security headers. Every push to `main` redeploys automatically.
