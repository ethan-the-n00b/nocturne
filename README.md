# Nocturne — Room 804

A desktop-first interactive hotel room experience built with plain HTML, CSS, and JavaScript.

## Run locally

Open this folder in VS Code and launch `index.html` with Live Server.

## Room interactions

- **Lamp:** cycles warm, cool, and dim lighting.
- **Tablet:** opens the Focus Session panel. Choose 25, 50, or 90 minutes, or enter a custom duration from 1–180 minutes. Start, pause, resume, and reset the timer.
- **Speaker:** opens Music & Ambience. Choose generated rain, wind, or room hum, or select a local audio file from your device. Local audio is not uploaded.
- **Balcony door:** switches to the balcony scene inside the same page, keeping Aster and tour progress in place.
- **Fullscreen icon:** toggles browser fullscreen where supported.

The focus timer includes a progress bar with break markers every 25 minutes. At each marker, focus pauses and offers a five-minute balcony break. The balcony counts down and returns to the room automatically when the break ends. A browser cannot force its tab to the foreground or prevent switching to other tabs/apps; if hidden, the page can only resume navigation when the browser lets it run or when the user returns.

## Files

- `index.html` — check-in / entry screen
- `room.html` — interactive Room 804
- `balcony.html` — compatibility redirect to the in-page balcony scene
- `style.css` — all layout and styling
- `script.js` — room interactions, focus timer, and audio controls
- `assets/` — room artwork and supporting images


Latest update: the balcony uses the clean background-only city artwork. Focus sessions show a centered countdown and progress bar, with five-minute balcony breaks scheduled every 25 minutes of focused work. Break timing is stored in the current browser tab's session storage so it survives navigation between the room and balcony pages.


### Focus milestones and balcony breaks
- The focus timeline marks 25%, 50%, and 75% of the selected session.
- Reaching a milestone pauses focus and offers a five-minute balcony break.
- The balcony countdown returns to the room automatically when the break ends. If browser notifications are already allowed, a return reminder is also shown.
- Browsers do not allow a website to force its tab to the foreground or switch away from other apps. The page can navigate its own tab back to the room, but the user may need to select that tab.
- Balcony scenery uses the clean, background-only `city-night.png` asset, not the room composite.

## Latest update: balcony image quality + session rewards
- The balcony now uses a clean crop of the original 1648 × 912 background-only city artwork (`assets/balcony-city-hq.png`). The transparent margins were cropped without resampling, retaining the original source pixels.
- The focus setup includes an optional goal field and a self-chosen completion reward. The goal and reward are saved for the current browser session and shown when the focus session completes.
- Reward options are intentionally small, user-chosen breaks rather than points or streak pressure.


## Aster — hotel guide
- Aster's welcome tour appears automatically the first time Room 804 is opened.
- Use **Next** to move through the short introduction or **Skip tour** to close it.
- The **Hotel Guide** button in the top-right corner replays the tour at any time.
- Four cropped portrait expressions are stored in `assets/aster-*.png` and used during dialogue.
- The tour completion state is saved in browser local storage as `nocturneAsterTourSeen`.


## Latest update: persistent Aster tour and unified scenes
- Room 804 and the balcony now switch inside `room.html`; the guide portrait and dialogue stay mounted while changing scenes.
- During the welcome tour, Aster highlights the object she is describing. The guest must interact with the lamp, tablet, speaker, and balcony door before continuing. The balcony step asks the guest to return inside before the tour proceeds.
- A tour-version key makes the updated welcome tour appear once for existing testers, while future visits use the Hotel Guide replay button.
- Generic status toasts are unsigned. Only Aster's direct personal notes, such as the balcony-break encouragement, carry `— Aster🌙`.
- `index.html` (the invitation) was left byte-for-byte unchanged.
