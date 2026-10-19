<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/hero-dark.png">
    <img src=".github/assets/hero.png" alt="poke.me.at landing page" width="880">
  </picture>
</p>

<h1 align="center">poke.me.at</h1>

<p align="center"><strong>Planning poker that starts in ten seconds.</strong></p>

<p align="center">
  <img src="https://img.shields.io/badge/status-building-171717?style=flat-square" alt="Status: building">
  <img src="https://img.shields.io/badge/license-source--available-404040?style=flat-square" alt="License: source-available">
  <img src="https://img.shields.io/badge/self--host-supported-525252?style=flat-square" alt="Self-host: supported">
  <img src="https://img.shields.io/badge/part%20of-me.at-737373?style=flat-square" alt="Part of me.at">
</p>

<p align="center">
  <a href="#features">Features</a> ·
  <a href="#how-it-works">How it works</a> ·
  <a href="#screenshots">Screenshots</a> ·
  <a href="#built-with">Built with</a>
</p>

Every planning-poker tool I have used wanted an account before it would let me share a link, and most of them anchored the room by showing the first vote. I built poke.me.at the way I want a stand-up to go: open a room, paste the link into the call, everyone picks a card in private, reveal, talk about the outliers, next story.

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/overview-dark.svg">
    <img src=".github/assets/overview.svg" alt="poke.me.at at a glance: a room is a link, cards stay face down until the reveal, the numbers that matter, rooms gone after a quiet day" width="880">
  </picture>
</p>

## Why poke.me.at

| The usual tool | poke.me.at |
| --- | --- |
| Sign up before you can share | A room is a link; join with a name |
| Votes visible as they land | Cards stay face down until the reveal |
| The host only facilitates | The host votes too, or spectates for a round |
| Rooms pile up in an account | A room expires a day after it goes quiet; nothing is kept |

## Features

- **Five decks**: Fibonacci, modified Fibonacci, T-shirt sizes, powers of two, linear 1 to 10. Every deck has a question mark and a coffee cup.
- **Private votes, one reveal**: nobody sees anyone else's card until the host reveals, or until the last vote lands with auto-reveal on.
- **The numbers that matter**: the spread, the average, the median, the range, and the deck card nearest the average.
- **Host controls**: edit the story, reveal, next round, hand hosting over, remove a stray participant.
- **Spectators**: step out for a round without leaving the room.
- **Round history**: earlier rounds and their outcomes stay on the side panel for the retro.
- **Concurrency-safe**: every write is a compare-and-set, so two phones voting in the same half-second both land.
- **Free, ad-supported**: one clearly labelled ad slot per page. The default is a first-party card for another me.at product; a third-party network, if enabled, is asked for non-personalised ads only.

## How it works

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/flow-dark.svg">
    <img src=".github/assets/flow.svg" alt="How poke.me.at works: open, join, vote, reveal" width="880">
  </picture>
</p>

A room is one small JSON object in a key-value store with a day-long sliding expiry, renewed by every write. Each participant holds a minted secret in their own browser; the server keeps only its hash. The page polls the room while the tab is visible and writes each action's response straight into the view, so your own card is on screen the moment you tap it.

## Screenshots

<table>
  <tr>
    <td width="50%"><picture><source media="(prefers-color-scheme: dark)" srcset=".github/assets/hero-dark.png"><img src=".github/assets/hero.png" alt="Landing page"></picture><br><sub>The landing page: open a room or join one with its code.</sub></td>
    <td width="50%"><picture><source media="(prefers-color-scheme: dark)" srcset=".github/assets/room-dark.png"><img src=".github/assets/room.png" alt="A revealed round"></picture><br><sub>A revealed round: the spread, the summary figures and every vote, with host controls on the side.</sub></td>
  </tr>
</table>

## Built with

<p>
  <img src="https://img.shields.io/badge/Next.js-16-000000?style=flat-square&logo=nextdotjs&logoColor=white" alt="Next.js 16">
  <img src="https://img.shields.io/badge/React-19-171717?style=flat-square&logo=react&logoColor=white" alt="React 19">
  <img src="https://img.shields.io/badge/TypeScript-5-262626?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript">
  <img src="https://img.shields.io/badge/Tailwind%20CSS-4-404040?style=flat-square&logo=tailwindcss&logoColor=white" alt="Tailwind CSS 4">
  <img src="https://img.shields.io/badge/Upstash-Redis-525252?style=flat-square&logo=upstash&logoColor=white" alt="Upstash Redis">
</p>

- Next.js 16 (App Router), React 19, TypeScript
- Tailwind CSS 4
- oRPC with TanStack Query
- Upstash Redis (memory store in development)

## Part of the me.at family

poke.me.at is one of my [`*.me.at`](https://me.at) apps. They share one design system, one account, and one app shell. Development happens in a private monorepo; this repository is the project's public-facing home.

## License

Source-available. See [LICENSE](LICENSE).
