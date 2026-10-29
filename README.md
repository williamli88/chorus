<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/banner-evening.jpg">
    <img src="assets/banner-day.jpg" alt="Chorus: because 'whose turn is it?' shouldn't take a group chat to settle." width="100%">
  </picture>
</p>

<h1 align="center">Chorus</h1>

<p align="center">
  <strong>The chore app for houses that keep score.</strong><br>
  Chorus deals out the chores, asks for a photo as proof, and keeps a ledger nobody can argue with.
</p>

<p align="center">
  <a href="https://chore-app-beta.vercel.app"><img alt="Live site" src="https://img.shields.io/badge/live-chore--app--beta.vercel.app-d4521f?style=flat-square"></a>
  <img alt="Status: private beta" src="https://img.shields.io/badge/status-private%20beta-2b1a0f?style=flat-square">
  <img alt="Source: private" src="https://img.shields.io/badge/source-private-735d3e?style=flat-square">
  <img alt="React 19" src="https://img.shields.io/badge/React-19-61dafb?style=flat-square&logo=react&logoColor=white">
  <img alt="Supabase" src="https://img.shields.io/badge/Supabase-Postgres-3ecf8e?style=flat-square&logo=supabase&logoColor=white">
  <img alt="Tailwind CSS 4" src="https://img.shields.io/badge/Tailwind-4-38bdf8?style=flat-square&logo=tailwindcss&logoColor=white">
</p>

---

I built Chorus for my own house. Chores rotate so nobody gets the oven twice in a row. Finishing one means photographing it, and every completion moves your credit for the month. Roommates trade chores with each other, and whoever finishes last at month end spins a wheel of dares the house wrote.

It's in daily use by one household. This repo is a showcase: the source code is private.

## See it work

These are recordings of the landing page's interactive demo, which runs on an invented house ("Alder Lane") with no real data.

<table>
  <tr>
    <td width="50%" valign="top">
      <img src="assets/board.gif" alt="The Board: tapping Prove it fires a camera flash, the row stamps, credit pops off and a leaf falls from the branch" width="100%"><br>
      <strong>The Board.</strong> Every open chore is a leaf on the branch. Prove one and the camera flashes, the row stamps, the credit pops, and a leaf falls.
    </td>
    <td width="50%" valign="top">
      <img src="assets/proof.gif" alt="Proving a chore: the photo ejects as a Polaroid, develops, and a Done stamp lands" width="100%"><br>
      <strong>Photo proof.</strong> An in-app camera, no uploads from the camera roll. The print develops, the stamp lands, and the month's credit counts up.
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <img src="assets/trade.gif" alt="A trade: the two sides cross over and recolour to their new owners" width="100%"><br>
      <strong>Trades.</strong> Offer your chores to a named roommate for theirs. Accept and both sides swap at once, priced in the same weights the ledger uses.
    </td>
    <td width="50%" valign="top">
      <img src="assets/wheel.gif" alt="Month end: last place is marked and a reel of dares spins to a stop" width="100%"><br>
      <strong>The Forfeit Wheel.</strong> At month end last place spins for a dare the house wrote and voted in, then has a week to film the proof.
    </td>
  </tr>
  <tr>
    <td colspan="2" align="center">
      <img src="assets/dark.gif" alt="Dragging the clock past sunset crossfades the app into a dark evening palette" width="50%"><br>
      <strong>After dark.</strong> The app computes sunset for the household's timezone and goes warm and dark on its own. No location permission needed.
    </td>
  </tr>
</table>

### New this fall

Recorded from the app's own components, running on demo data for the same invented house.

<table>
  <tr>
    <td width="50%" valign="top">
      <img src="assets/live.gif" alt="The Board live: roommates' colour dots glow, a roommate's proof photo drops onto the board with its tape landing last, rain runs down the nav bar, and the headline folds into a top bar on scroll" width="100%"><br>
      <strong>A house that feels lived in.</strong> Roommates' dots glow while they have the app open. When someone files a proof, it drops onto your board live. Rain runs down the nav bar's glass when it's raining outside, and the headline folds into the top bar as you scroll.
    </td>
    <td width="50%" valign="top">
      <img src="assets/morph.gif" alt="Tapping a proof photo on the Wall grows the whole Polaroid into a full-screen view and shrinks it back into its tile" width="100%"><br>
      <strong>Photo to full screen.</strong> Tap a print and the Polaroid itself grows out of its tile, then shrinks back when you close it. Built on the browser's View Transitions.
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <img src="assets/flipbook.gif" alt="Dragging across a recurring chore's flipbook scrubs through every Sunday's kitchen photo, from cluttered to clean" width="100%"><br>
      <strong>Flipbooks.</strong> Drag a finger across a recurring chore and flip through every proof of it in order, like a before-and-after.
    </td>
    <td width="50%" valign="top">
      <img src="assets/piles.gif" alt="Standings as leaf piles: flicking a pile scatters its leaves, which drift home and rebuild it" width="100%"><br>
      <strong>Standings as leaf piles.</strong> Each roommate's pile is as tall as their credit for the month. Flick one and it scatters, then rakes itself back up.
    </td>
  </tr>
  <tr>
    <td colspan="2" align="center">
      <img src="assets/recap.gif" alt="Month recap story cards: proofs filed, most-done chore, fastest proof, longest streak, a collage of the month's photos, then who spins the dare wheel" width="50%"><br>
      <strong>The month, wrapped.</strong> Full-screen story cards at month end: your most-done chore, fastest proof, longest streak, a collage of the month's photos, then the reveal of who spins the wheel. Saves as an image for the group chat.
    </td>
  </tr>
</table>

## What's in it

| | |
|---|---|
| **Rotation** | Weekly or every-N-days chores, dealt round-robin with per-chore offsets so chores on the same schedule don't all land on the same person. Only the current month is materialized. |
| **Credit ledger** | On time, late and missed each carry their own weight, scaled 1× to 3× by how bad the job is. Every total is summed fresh from an append-only ledger. |
| **Crews** | A chore can take several people. Each person photographs their own part, and the chore closes when the last shot lands, enforced by a database trigger rather than the client. |
| **Placeholder roommates** | The house's creator names the roommates up front, and they're real seats in the rotation from day one. Each person inherits their seat when they join. |
| **Governance** | Admin and member roles, invite codes that need an admin's approval, and an audit log of admin actions. |
| **Nudges** | Web push reminders through the day in the household's local time, plus notes, reactions and an activity feed. |
| **Leaf Season** | A seasonal edition with an autumn palette, ambient leaves on a canvas, and a dark palette that switches at local sunset. |
| **Live house** | Realtime presence shows who has the app open, and a roommate's proof lands on your board the moment it's filed. |
| **Real weather** | Open-Meteo, located from the household's time zone with no permission prompt. Wind blows the leaves harder and rain streaks the nav bar. |
| **Flipbooks & recaps** | Every proof of a recurring chore as a scrubbable flipbook, and a month-end recap in story cards that saves as a shareable image. |
| **Sound, off by default** | A paper shutter, a stamp thud and a wheel tick, synthesised in Web Audio with no audio files. |

## How it's built

There's no server of its own. Chorus is a static React bundle in front of a hosted Supabase project, and Postgres row-level security is the access control.

```mermaid
flowchart LR
  subgraph Client["Browser / home-screen PWA"]
    UI["React 19 + Vite<br/>Tailwind v4 tokens"]
    SW["Service worker"]
  end
  subgraph Supabase
    Auth["Auth<br/>Google, email"]
    DB[("Postgres<br/>RLS, RPCs, triggers")]
    Storage["Storage<br/>proof photos, dare clips"]
    RT["Realtime"]
    Cron["pg_cron<br/>reminders"]
    Edge["Edge function<br/>send-push"]
  end
  UI -- "supabase-js" --> Auth
  UI -- "queries + RPCs" --> DB
  UI -- "signed URLs" --> Storage
  RT -- "row changes" --> UI
  Cron --> DB
  DB -- "pg_net" --> Edge
  Edge -- "Web Push" --> SW
```

| | |
|---|---|
| **Frontend** | React 19, Vite 8 and Tailwind CSS 4, in plain JavaScript. A token-driven design system with a custom motion layer, and a custom `getUserMedia` camera. |
| **Backend** | Supabase: Postgres with row-level security, SECURITY DEFINER RPCs and trigger-enforced invariants. Plus Storage, Realtime, `pg_cron`, and a Deno edge function for Web Push. |
| **Quality** | Vitest suites for the round-robin rotation, ledger and streak math, crew proofs, trade balancing, standings, the month recap and flipbook reductions, seasonal sunset math, and copy-length budgets. Linted with oxlint. |
| **Shipping** | Static hosting on Vercel, installed as a PWA via Add to Home Screen. A Capacitor iOS build also exists. |

### A few things I'm proud of

- **The database enforces the rules, not the client.** A crew chore can't be marked done until every seat has filed a photo. A trigger refuses it, so an out-of-date phone can't close a chore on one person's word.
- **Fairness that stays honest.** Trades are priced in the same weights that pay credit, so trading away hard chores also trades away the credit.
- **A theme that follows the sun.** Sunset is computed from the household's timezone with NOAA's solar equations, with tests covering zones whose sunrise falls on the previous UTC day.
- **Designed for phones.** Swipe-back pages, thrown-and-settle sheets, a draggable nav pill on spring physics, and every interaction tuned for an installed iPhone.

## Access

Chorus is private and invite-only for now. To hear when there's room for another house, leave an email on [the live site](https://chore-app-beta.vercel.app).

---

<p align="center"><sub>© 2026 William Li. All rights reserved. The images and recordings in this repository may not be reused without permission.</sub></p>
