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

## Accounts and leaderboard (Supabase)

Anyone can play and see the Top 10. Players sign in with a username and password to save their score.

- **Sign in / sign out:** the bar above the game. Passwords are stored by Supabase Auth in `auth.users`. A username maps to the email `<username>@dinorun.example.com`, a placeholder address that never receives mail.
- **Users:** `alex` (admin), `anna`, `alvin`, `alson` and `joey` were created with the initial password `password`. **Change it** from the Account button after signing in.
- **Admin:** an admin sees a user management panel to add users with an initial password. It calls the `manage-users` Edge Function, which checks the caller is an admin and uses the service-role key on the server only.

### Tables

| Table | Purpose |
|---|---|
| `auth.users` | Supabase's built-in user and password store |
| `public.profiles` | One row per user: username, display name, role (`admin` or `player`). Created automatically by a trigger on `auth.users`. |
| `public.dino_scores` | Scores, linked to `auth.users` through `user_id` |

### Access rules (row-level security)

- Anyone can read scores.
- Only a signed-in player can add a score, and only under their own user and username. Scores cannot be edited or deleted from the app.
- A player can read only their own profile. An admin can read all profiles. Roles can only be changed in the database.

### Security notes

- The Supabase URL and publishable key in `index.html` are meant to be public. Never put a secret or service-role key in this repo.
- In the Supabase dashboard, turn **off** "Allow new users to sign up" (Authentication > Sign In / Providers) so only admins can create accounts, and turn **on** leaked password protection.
- Scores are submitted from the browser, so a determined player could still submit a fake score. For a stricter leaderboard, validate scores in an Edge Function.

## Run locally

Open `index.html` in any modern browser.

## Deploy to Vercel

1. Sign in at [vercel.com](https://vercel.com) and choose **Add New > Project**.
2. Import the `alexto889/dinorun` GitHub repository.
3. Leave the settings as they are: Framework Preset **Other**, no build command, no output directory.
4. Click **Deploy**.

`vercel.json` adds clean URLs and basic security headers. Every push to `main` redeploys automatically.
