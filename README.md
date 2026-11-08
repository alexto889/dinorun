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

## Run locally

Open `index.html` in any modern browser.

## Deploy to Vercel

1. Sign in at [vercel.com](https://vercel.com) and choose **Add New > Project**.
2. Import the `alexto889/dinorun` GitHub repository.
3. Leave the settings as they are: Framework Preset **Other**, no build command, no output directory.
4. Click **Deploy**.

`vercel.json` adds clean URLs and basic security headers. Every push to `main` redeploys automatically.
