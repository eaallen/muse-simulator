> Markdown rendering of "Muse Simulator: Build Spec" (the .docx of the same name), generated for easy reading on GitHub.
> Screenshots referenced by this spec are indexed in `spec/screenshots/README.md`. The replica is drawn UI, built against those references.

# Muse Simulator: Build Spec

An interactive tour of the Muse phone app for the AvailaBooks course "Build With Muse"

Prepared for Eli Allen. November 3, 2026. Screenshots are the official Google Play listing images for Muse from Meta (demo data, safe for teaching).

## 1. What this is

The Muse Simulator replaces videos in the textbook. Where a normal textbook lesson would embed a video of the instructor using Muse, this book embeds a simulator setup instead: a clickable replica of the Muse phone app, loaded with a scenario that demonstrates that lesson's topics. Students do not watch someone else use Muse. They tap through it themselves: they send the messages, approve or deny the agent's actions, set the goal, and schedule the watch, all against scripted responses. It feels like the real app, but nothing is live, no account is needed, and every student gets the same safe demo data.

One simulator engine powers the whole book. Each lesson loads its own setup: the screens, cards, and scripted replies that demonstrate that lesson's topics. A lesson in the book runs text, then the simulator setup, then the student's own real activity in their Muse, in that order.

Where it fits in the course:

- Every lesson: the simulator setup is the demonstration step of the lesson, in place of a video.

- Chapter 1 (Getting Started with Muse): the first setups teach the map of the app, so a student who has not installed Muse yet can still do the lesson.

- Live lessons on Zoom: the instructor drives the same setup on screen share while students follow along on their own copies.

- Chapters 2 to 4: each setup previews the real move (approvals, scheduled watches, connectors, business work) before students do it for real in their own Muse.

## 2. Design principles

- Faithful, not fancy: the layout, tab bar, and cards copy the real app so skills transfer. Same five tabs: Chat, Feed, Ideas, Goals, Library.

- Mobile UI is the target: the replica copies the phone app at phone width. On a computer it sits in one centered phone-width column; on a phone it fills the screen. One layout serves both, and nothing gets redesigned per device.

- Light and dark, both first class: the replica ships with a full light theme and a full dark theme, matching the real app's own appearance setting. Dark is designed, not inverted.

- Lesson chrome lives outside the phone: the setup instructions, the checklist of goals for the setup, hints, and completion state render outside the replica, never inside it, so the phone stays a faithful copy of the real app.

- Scripted agent: every Muse reply is prewritten. No live AI, no surprises, no cost per run, and the lesson lands the same way every time.

- Demo data only: fictional people, inboxes, and cards. Nothing personal can leak because nothing personal exists in it.

- Short and finishable: the full tour takes about 20 to 30 minutes. Every mission ends with a visible done state.

- Works anywhere: one web page, usable on a phone, a tablet, or a desktop browser, embedded in the AvailaBooks course page.

- Forgiving: a wrong tap never breaks anything. The simulator nudges the student back to the path, and a Reset button restarts any mission.

- One engine, many setups: the same simulator shell loads a different scenario per lesson, so every lesson page in the book can carry its own demonstration without rebuilding anything.

## 3. How students use it: four modes

- Lesson setups (the main mode): each lesson's scenario demonstrates its topics as a small job with a goal and a checklist. The simulator checks each step off as the student does it.

- Guided Tour: the Chapter 1 setup doubles as a narrated walk through every main screen, one tap at a time, with a short note on what each element is for.

- Free Explore: the replica with the guardrails off, so a curious student can poke every tab and card.

- Check Yourself: three to five quick questions per chapter, answered by doing, not by multiple choice ("Show me where you would see what your agent did yesterday").

Navigation model: students move by tapping the replica's own controls (tab bar, cards, buttons, choice chips). Highlight rings show the suggested next tap in the Guided Tour and in lesson setups. Progress is stored in the page, so a student can stop and resume.

## 4. The screens

Each screen below lists what the real app does there, what the student does in the simulator, and the screenshot the replica is built from.

### 4.1 Main chat: where everything happens

In the real app, the main chat is the home base. The user talks to their agent like texting a friend, and work shows up inline: documents the agent filled out, reminders it set, follow-up questions it asks. In the simulator, the student sends a first message from a set of starter chips or the keyboard, watches the agent fill out a form from an email, and answers its follow-up question.

Main chat: the agent finds a form in email, fills it out, and follows up. (Google Play listing screenshot)

### 4.2 Approvals: approve what gets sent or spent

Muse asks before consequential actions. A checkout, an email send, or a booking arrives as a card the user can Allow or Deny. This is the trust core of the whole course, so the simulator gives it a full mission: read the card, check the item, the price, and the card on file, then decide. Denying is a valid, praised outcome when the details are wrong, and one mission plants a wrong detail on purpose.

Approval card: a checkout request with Deny and Allow. (Google Play listing screenshot)

### 4.3 Browser tasks inside chat

Muse can work in a real browser on the user's own cloud computer and shows its progress inside the chat, like picking seats for tickets it is tracking. In the simulator, the student starts the booking, watches the seat map step, and confirms the choice. The live browser itself is not replicated; the card and its states are.

Browser task card: selecting seats during a booking. (Google Play listing screenshot)

### 4.4 Connectors: connect the apps you already use

Connectors are how Muse reaches email, calendar, and other services, each with its own permissions the user can revoke. In the simulator, the student opens the connector list, reads what a Gmail connection would allow, and walks the connect flow to the permission step without anything real being connected.

Connectors screen: connected services and available ones. (Google Play listing screenshot)

### 4.5 Ideas: suggestions waiting for a yes

The Ideas tab holds things the agent offers to take on, written for that user. In the simulator, the student swipes through idea cards, accepts one (which starts a short scripted job), and dismisses one that does not fit.

Ideas: cards the agent offers to take on. (Google Play listing screenshot)

### 4.6 Documents and business work in chat

Muse produces real deliverables, documents, sheets, and plans, right inside the chat. The business growth example doubles as the Chapter 4 preview: in the simulator, the student asks for a growth plan, opens the document card, and approves the follow-up step the agent proposes.

Business chat: a growth plan delivered as a document. (Google Play listing screenshot)

### 4.7 Money in chat: spending and saving

With a finance connector, Muse can summarize spending, spot subscriptions, and suggest savings, checking before it cancels or spends anything. In the simulator, the student opens the finance tracker card and picks which suggested subscription to review.

Finance in chat: a spending summary and tracker card. (Google Play listing screenshot)

### 4.8 Goals: turn a goal into a plan

The Goals tab lists what the user is working toward, what the agent is tracking, and live progress. In the simulator, the student creates the course goal (the same one Chapter 1 asks for), watches tracking items appear, and checks progress the way Lesson 1 will review it.

Goals tab: tracking items, goals, and Create a goal. (Google Play listing screenshot)

### 4.9 Screens still to capture

The Play listing does not show every screen. For full coverage, capture these from a real phone before or during the build. Use a clean demo account or crop carefully: real captures show real personal data, and teaching assets should never carry it.

- Feed tab: the agent's scheduled posts for the user.

- Library tab: artifacts, documents, and media collected in one place.

- Chat list and a side chat: how separate topics stay separate.

- Composer with voice: dictation and a voice note in flight.

- Status screen (tap the avatar): Activity, Approvals, and Upcoming (scheduled tasks).

- Settings home: Connectors, Wallet, Secure credentials store, Permissions, Devices, Data controls.

- A proactive notification arriving on the phone's lock screen.

## 5. Feature support matrix

Support levels: Full means the student can really do it in the replica. Scripted means it works along a fixed path with prewritten outcomes. Shown means it appears and can be opened and read, but not operated. Out means v1 leaves it out on purpose.

| Feature | Support | Notes |
| --- | --- | --- |
| Sending and reading chat messages | Full | Core loop. Starter chips plus a free-type box that matches keywords to scripted replies. |
| Side chats and the chat list | Scripted | Student creates one side chat for a course topic and switches between chats. |
| Reactions and long-press message menu | Shown | Long-press shows the menu; reactions can be tapped in Free Explore. |
| Voice notes and dictation | Scripted | Hold-to-talk animates and drops in a canned transcript. No real microphone input in v1. |
| Choice chips and option cards in chat | Full | The same tap-to-answer pattern the real app uses. |
| Documents and artifacts in chat | Full | Cards open a readable replica document, like the growth plan. |
| Approval cards (Allow / Deny) | Full | Includes one planted wrong detail to teach card reading. |
| Proactive messages and notifications | Scripted | A banner arrives mid-mission; the student opens it and lands in the right chat. |
| Feed tab | Shown | Prewritten posts; the feed prompt card can be viewed, not edited. |
| Ideas tab (accept / dismiss) | Full | Accepting starts a scripted job; dismissing removes the card. |
| Goals tab (create, track, reorder) | Full | Create and complete states supported; drag reorder is Android-only in the real app and optional here. |
| Library tab | Shown | Lists the artifacts the student's missions produced. |
| Connectors list and connect flow | Scripted | Full walk to the permission step for Gmail and Calendar; nothing real connects. |
| Scheduled tasks, reminders, Upcoming | Full | Student sets a daily watch and sees it listed under Upcoming. |
| Activity log | Shown | The missions' own actions are written into a replica Activity list. |
| Memory: what Muse remembers | Scripted | A short scene: the agent recalls a preference, and the student corrects it. |
| Avatar and name (Identity) | Scripted | Student renames the demo agent and picks an avatar from presets. |
| Settings tour | Shown | Every settings row is present and tappable to a one-line explanation. |
| Browser tasks on websites | Scripted | Card states and the seat-picker step only; no live browsing. |
| Shopping and checkout with Wallet | Scripted | Ends at the approval card; payment itself is never simulated beyond the card. |
| Email and calendar actions | Scripted | One drafted email (with the agent sign-off from Chapter 2) and one calendar hold. |
| Business tools (Pages, ads, growth plan) | Scripted | The growth plan mission; ad account screens are Shown only. |
| Finance tracking | Shown | Spending card and subscription review, from demo data. |
| Health and fitness data | Out | Sensitive and personal; the course does not need it. Mentioned in the tour narration only. |
| WhatsApp side chats | Out | A phone-frame replica of WhatsApp is a second product. Listed as a v2 candidate. |
| Sharing into Muse from other apps | Shown | One tour stop: the share sheet with Muse as a target. |
| Chat search | Scripted | Search finds the planted message from an earlier mission. |

## 6. Lesson setups: the catalog

Each setup belongs to a lesson or topic cluster in the book and demonstrates that lesson's topics. Chapter 1 setups come first in the build order, because every later setup assumes the student knows the map of the app.

- Setup 1, First Five Minutes (Chapter 1): send a first message, name the agent, and visit each tab. Demonstrates chat, the tab bar, and Identity.

- Setup 2, Set Your Goal (Chapter 1): create the course goal in the Goals tab and watch tracking items appear. Demonstrates Goals, tracking, and progress.

- Setup 3, Ideas and the Feed (Chapter 1): accept one idea, dismiss one, and read the day's Feed posts, then find the result in the Library. Demonstrates Ideas, Feed, and Library.

- Setup 4, Connect Email and Set the Daily Watch (Chapter 2): walk the Gmail connect flow, set one narrow daily watch, and receive its proactive result. Demonstrates Connectors, scheduled tasks, Upcoming, and proactive messages.

- Setup 5, Draft, Approve, Send (Chapter 2): the agent drafts an email; the student reviews, edits, and approves it; the sent copy carries the agent sign off and the agent label. Demonstrates the draft and approve workflow, agent identity, and the Activity audit trail.

- Setup 6, Shopping with Approval (Chapter 2): two checkout cards arrive. One is clean; one has a wrong size and a higher price than quoted. Done when the clean one is allowed and the wrong one is denied for the right reason. Demonstrates approval cards and careful card reading.

- Setup 7, A Job on a Website (Chapter 2): track event tickets, get the price alert, and finish the seat selection inside a browser task card. Demonstrates browser tasks, price tracking, and confirmation cards.

- Setup 8, Scope It and Build It (Chapter 3): brief the agent on a small app, watch the scripted build steps, and test the result. Demonstrates briefing an outcome, iterating, and artifacts.

- Setup 9, Share It and Ship Again (Chapter 3): share the app link, read the feedback cards, and approve version two. Demonstrates sharing, feedback, and iteration.

- Setup 10, Run the Business Day (Chapter 4): a morning of small business work: a customer follow up drafted for approval, a follow up reminder that does not slip, and a growth plan document to review. Demonstrates business workflows under the same draft and approve rules.

Build status, November 3, 2026: all ten setups are built and flow tested end to end, including the four finished last: A Job on a Website, Scope It and Build It, Share It and Ship Again, and Run the Business Day. Free Explore ships with a sidebar matched to the real app, a RiveScript powered chat brain with realistic reply timing (emoji reaction, short reply, then the longer reply), browser speech to text on the mic where available, and labeled placeholder screens for views the simulator does not model. Every view that can be empty carries an Intentionally blank message so a quiet screen never looks broken.

## 7. Build approach: a custom web component

The simulator ships as a custom web component: one JavaScript file that registers a single element, <muse-simulator>. A lesson page embeds a demonstration by dropping in the tag with the setup it should load:

<muse-simulator setup="ch2-daily-watch"></muse-simulator>

- Encapsulated: the component renders inside its own shadow DOM, so the book page's styles cannot leak in and break the replica, and the replica's styles cannot leak out and disturb the book. It behaves the same on every page it is dropped into.

- Attributes configure it: setup (which lesson scenario to load), mode (setup, tour, or explore), and theme (light, dark, or auto). Changing the setup attribute swaps the scenario without reloading the page.

- Light and dark modes: colors are theme tokens (CSS custom properties) with a complete light set and a complete dark set. theme="auto" follows the student's own system setting (prefers-color-scheme) and switches live if they change it. The default is auto.

- Events report out: when a student finishes a setup, the component fires a muse-simulator-complete event with the setup id and the checklist result. The AvailaBooks page can listen for it, which is the hook the gradebook reporting question depends on.

- Guide panel and step events: the component renders a guide panel above the phone with the current instruction, the setup checklist, and hints. Setting guide="external" hides the built-in panel, and the host page renders its own from muse-simulator-step events, which carry the current instruction and checklist state on every change.

- Screens are data, not code: each setup's screens, cards, and scripted replies live in editable content files, so lesson text can be revised without touching the engine.

- Deterministic state machine: every setup is a list of steps with a trigger (tap target or message keyword) and an outcome. Reset restores the start state.

- Fallback: if scripts are blocked or the component fails to load, the lesson page shows the setup's screenshot and a text walkthrough instead, so the lesson never breaks.

- Accessibility: tappable targets at real phone sizes, text at readable sizes, every color cue paired with a label, and both themes checked for readable contrast.

- Privacy: the component collects nothing and sends nothing. Progress lives only in the student's browser.

## 8. Screenshot assets

- Eight official screenshots from the Google Play listing for Muse from Meta, downloaded November 3, 2026, and embedded above. They use Meta's demo data, so they are safe to print in course materials.

- Still wanted (see 4.9): Feed, Library, voice composer, chat list, status screen, Settings, and a lock-screen notification. Capture from a demo account, or replace with drawn mockups in the same style.

- In the simulator itself, the screenshots are reference art for the replica's layout. The shipped replica should be drawn UI (crisp at every size), using the screenshots as the layout source, not pasted images.

## 9. Acceptance criteria

- A new student can finish the Guided Tour plus Setup 1 in under 30 minutes with no instructions beyond what is on screen.

- Every tab in the replica opens; every setup can be completed and reset; no dead ends.

- The approval mission's planted error is findable from the card alone.

- The page loads and runs offline after first load, and embeds cleanly in the AvailaBooks course page: full screen on a phone, one centered phone-width column on a computer, with no horizontal scrolling at any width from 320 px up.

- Dropped into a plain test page with a single tag and no other code, the component loads its setup and runs; the host page looks identical with the component present or removed.

- Every setup is completed once in light mode and once in dark mode during testing, and the theme=auto setting follows a system switch without a reload.

- No real accounts, inboxes, cards, or personal data anywhere in the build.

## 10. Decisions for Eli

- Build order: Chapter 1 setups first (recommended), then one chapter of setups at a time as you write each chapter?

- Free Explore in v1, or setups and the tour only?

- Drawn replica UI (recommended) versus screenshot-based hotspots (faster to build, fuzzier on small screens)?

- Reporting: the component already fires a completion event per setup. Should the AvailaBooks page forward those events to the gradebook payload, matching the transcript grading work, or stay ungraded practice for v1?
