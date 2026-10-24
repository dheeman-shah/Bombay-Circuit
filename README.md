# Switchyard Sprint

**A neon night-freight runner where every track switch, jump, slide, and coin brings you closer to graduation.**

**Live demo:** https://switchyard-1.vercel.app/

Switchyard Sprint is a browser-based arcade runner built around a night-time railway-yard aesthetic. Dodge hazards, collect coins, complete environmental crash quizzes, and race a friend to clear all three levels.

## Contents

- [Gameplay](#gameplay)
- [Controls](#controls)
- [How a run works](#how-a-run-works)
- [Race room](#race-room)
- [Tech stack](#tech-stack)
- [Run locally](#run-locally)
- [Configuration](#configuration)
- [Deploy to Vercel](#deploy-to-vercel)
- [Project structure](#project-structure)
- [Known limitations and testing](#known-limitations-and-testing)

## Gameplay

- **Three-lane running:** switch tracks to avoid incoming hazards.
- **Jump and slide:** jump barriers and slide under overhead gantries.
- **Coins and progression:** collect coins, build your score, and progress through three levels.
- **Environmental crash quizzes:** answer a quiz after a crash and continue according to the game's rules.
- **Checkpoints and race standings:** track progress during a run and compare race results.
- **Personalisation:** choose an outfit and keep track of your best score, coin total, and runs.
- **Race room:** enter a player name and room code to race a friend. The in-game instructions specify a target of 280 coins across all three levels, while surviving the crash quizzes.
- **Sound and pause controls:** toggle sound, pause, resume, restart, or return to the menu.
- **Graduation screen:** completing all three levels leads to the game's degree-certificate screen.

> The public demo exposes the race-room interface. Actual multiplayer synchronisation depends on the project's configured realtime backend and should be tested with two separate browser sessions before being described as fully operational.

## Controls

| Action | Keyboard | Touch |
|---|---|---|
| Switch track | `←` / `→` | Swipe left / right |
| Jump | `↑` or `Space` | Use the in-game touch gesture |
| Slide | `↓` | Use the in-game touch gesture |
| Pause | `P` or `Esc` | Use the in-game controls |

## How a run works

1. Open the [live game](https://switchyard-1.vercel.app/) and select **Start run**.
2. Use the controls to move between lanes and avoid barriers and gantries.
3. Collect coins and cleanly dodge obstacles to improve your score and multiplier.
4. When a crash quiz appears, answer the environmental question.
5. Continue through the three levels and use checkpoints/standings to track progress.
6. Review your run ticket, score, distance, coins, and dodges at the end.
7. Replay, start a new run, or use the race-room flow to compete with a friend.

The exact scoring, quiz, and progression rules are defined by the game code; this README intentionally does not claim unverified scoring formulas.

## Race room

1. Open the game in two separate browsers or devices.
2. Each player enters a name and the same room code.
3. Join the room, then use **Start race** as directed by the interface.
4. Compare progress and standings. The stated race goal is to clear all three levels and collect 280 coins while surviving the crash quizzes.

**Multiplayer verification:** run this test before the hackathon demo:
- Open two independent sessions (not just two tabs sharing the same session state).
- Join with the same room code.
- Start the race and confirm both players appear.
- Confirm that progress/standings update on both clients.
- Refresh one client and test reconnect behaviour.
- Try an invalid room code and a disconnected network.

If these checks fail, describe multiplayer as a prototype/interface rather than a working realtime feature.

## Tech stack

Based on the deployed web version and project setup:

- **HTML, CSS, JavaScript** — browser interface and game logic
- **Canvas** — runner/game rendering
- **Supabase Realtime** — intended room-state synchronisation, when configured
- **Vercel** — deployment and hosting
- **Git and GitHub** — source control and collaboration

Update this section if the final repository uses a different library or backend.

## Run locally

This is a static browser application, so a Node.js build step may not be required unless the repository includes additional tooling.

1. Install Git and, if you use the optional local server command below, install Node.js.
2. Clone your GitHub repository:

   ```bash
   git clone <https://github.com/dheeman-shah/Bombay-Circuit.git>
   cd <https://drive.google.com/file/d/1hbGVjxHkrC0e1_PqXxCxrB5fGhiaiNKX/view?usp=drive_link>
   ```

3. Keep the project files together, including `index.html`, `config.js`, and `vercel.json` if they are present.
4. Start a local static server. One option is:

   ```bash
   npx serve .
   ```

5. Open the local URL printed in the terminal.

If `npx` is not available, install Node.js LTS and reopen your terminal. Alternatively, use a static-server extension in your editor.

## Configuration

If your project uses Supabase for race rooms:

1. Open the Supabase project used by the app.
2. Find the project URL and **publishable/anon key** in the Supabase API settings.
3. Add them to the configuration file expected by the application (the starter version uses `config.js`).
4. Use only the public browser key in frontend code. **Never put a Supabase `service_role` key or any other secret in `config.js` or commit it to GitHub.**
5. Verify the required Realtime tables/channels and Row Level Security policies match the code.
6. Test room creation/joining and live updates in two independent sessions.

## Deploy to Vercel

1. Push the project to a GitHub repository.
2. Sign in to [Vercel](https://vercel.com/) and choose **Add New → Project**.
3. Import the repository.
4. For a static HTML/CSS/JS project, select the appropriate static/no-build configuration. If the project has a build script, use the build command and output directory defined by its package configuration.
5. Add any required environment variables in Vercel Project Settings. If the current app reads `config.js` directly, make sure the deployed configuration is set up safely.
6. Deploy, open the production URL, and test the game on desktop and mobile.
7. After each code change, check the Vercel deployment status and test the deployed build—not only the local copy.

## Project structure

The starter project has used files such as:

```text
.
├── index.html       # Game interface and browser-side logic
├── config.js        # Client configuration (if used)
├── vercel.json      # Vercel routing/deployment configuration (if used)
└── README.md        # Project documentation
```

The actual repository may contain additional assets or scripts. Update this tree to match the final committed files.

## Known limitations and testing

- A visible room-code form does not, by itself, prove realtime multiplayer works. Verify the complete two-player flow before presenting it as production-ready.
- The exact configuration requirements depend on the final `config.js` and backend setup.
- This README is based on the public deployment and the project details available; the source repository has not yet been inspected, so the file list, backend implementation, and local startup steps should be checked against the actual code.

## Team

## Team

Built by a team of three for a hackathon.

| Team Member | Role | Responsibilities |
|---|---|---|
| Member 1 — [Taksh Jain] | Game Developer | Core gameplay mechanics, obstacle generation, collision detection, scoring, coins, quizzes, and level progression. |
| Member 2 — [Dheeman Shah] | UI/UX & Creative Designer | Visual identity, game interface, HUD, menus, animations, character customisation, and responsive design. |
| Member 3 — [Darshan Rangdale] | Backend & Integration Engineer | Multiplayer integration, backend configuration, code integration, GitHub version control, Vercel deployment, testing, and documentation. |

### Collaboration

All three members collaborated to develop, integrate, and test Switchyard Sprint within the hackathon timeline.
