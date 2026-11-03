# Muse Simulator

A `<muse-simulator>` web component that replicates the Muse phone app for teaching. It is the hands on companion to the **Hire Your First Agent** course (AvailaBooks): an interactive, tap through replica that takes the place of videos in the textbook. Students run a lesson setup inside the simulator, then go do the same thing in their real Muse.

One JavaScript file, no dependencies (Free Explore loads the RiveScript library from a CDN for its chat brain, with a built in fallback interpreter if the CDN is unreachable).

## Quick start

```html
<script src="muse-simulator.js"></script>

<muse-simulator setup="ch1-first-five-minutes"></muse-simulator>
```

Open `index.html` for a self contained demo and test page with a setup picker, theme switcher, Free Explore toggle, and a live log of the events the component fires.

## Attributes

| Attribute | Values | What it does |
| --- | --- | --- |
| `setup` | a setup id (below) | Which lesson scenario to load. |
| `mode` | `setup` (default), `explore` | `explore` turns on Free Explore: open navigation, the sidebar, and a working chat bot. |
| `theme` | `light`, `dark`, `auto` (default) | `auto` follows the student's system setting and switches live. Both themes are fully designed. |
| `guide` | `panel` (default), `external` | `panel` renders the built in guide above the phone: one current goal with a dropdown for the rest, and the current instruction under it. `external` hides it so the host page can render its own guide from the step events. |

## Events

- `muse-simulator-complete`: fired when a student finishes a setup. Detail: `{ setup, title, chapter, checks, total }`.
- `muse-simulator-step`: fired whenever the guide state changes. Detail: `{ setup, title, chapter, step, instruction, checks: [{ label, done }], done }`.

## The ten lesson setups

Chapter 1, Getting Started with Muse:

1. `ch1-first-five-minutes` — First Five Minutes
2. `ch1-set-your-goal` — Set Your Goal
3. `ch1-ideas-and-feed` — Ideas and the Feed

Chapter 2, Automate the Boring Stuff:

4. `ch2-daily-watch` — Connect Email and Set the Daily Watch
5. `ch2-draft-approve-send` — Draft, Approve, Send
6. `ch2-shopping-approval` — Shopping with Approval
7. `ch2-website-job` — A Job on a Website

Chapter 3, Build and Ship Your App:

8. `ch3-scope-build` — Scope It and Build It
9. `ch3-share-ship` — Share It and Ship Again

Chapter 4, Run Your Small Business with Muse:

10. `ch4-business-day` — Run the Business Day

## Free Explore

In `explore` mode students can wander: the sidebar opens (tabs, side chats, settings), every view is reachable, and views the simulator does not fully model open a labeled placeholder screen instead of a dead end. Chat in Free Explore runs on a small RiveScript brain with realistic timing: an emoji reaction on the student's message, a short reply, a pause, then the longer reply. The mic button uses the browser's built in speech to text where available (Chrome, Edge, Safari) and falls back to a sample spoken line where it is not.

Views that are empty in a setup show an "Intentionally blank" message explaining what the real app shows there, so a quiet screen never looks broken.

## Reference

The build spec lives in [`spec/SPEC.md`](spec/SPEC.md): the concept, design principles, the screen by screen walkthrough, the feature support matrix, the lesson setup catalog, and the build approach. The screenshots the replica was built against are indexed in [`spec/screenshots/README.md`](spec/screenshots/README.md), including two captures from a real phone (the main chat and the sidebar, both in dark mode) alongside the official Google Play listing screenshots.

## Design notes

- The replica targets the mobile UI: one phone width layout that fills a phone screen and sits as a centered column on a computer. All interactions are taps; nothing depends on hover or a keyboard.
- Lesson chrome (instructions, goals, hints, completion) lives outside the phone in the guide panel, so the replica itself stays faithful to the real app, including dark mode details (plain text agent messages, icon only tab bar, the "is working" status).
- Everything is demo data. No real accounts, inboxes, cards, or personal information anywhere in the build.

Built for the Hire Your First Agent course by Elijah Allen, AvailaBooks.
