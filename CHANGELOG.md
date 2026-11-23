# What's new in Oriel

## 4.0.0 — the first stable version

Oriel 4.0.0 brings together everything of 3.4.0 to 3.8.0, and it is no longer a beta.

- **A real time left**: the estimate counts only the work being done (not the time spent waiting for free memory)
  and is shown as a **range**, also before an analysis starts.
- **The profile in view**: Analyze and Settings say what Oriel is using, for example "Pro · RTX 5070 Ti · GPU" or
  "Light · CPU", and warn when there is an NVIDIA card but the CPU is being used.
- **Searchable first**: Oriel first makes every file searchable (shots and visual search) and then does the heavy
  analysis. Analyze shows "Searchable now".
- **Check for updates**: one button at the top looks for a new version right away; Oriel also checks once a day.
  Notices are in Settings › Notices.
- **Four tabs**: Search · Library · Review · Analyze, with Help and Settings as icons, and **Simple / Advanced**
  mode (Simple, the default, hides the technical parts).
- **A new panel** for Premiere Pro, After Effects and DaVinci Resolve: results first, the filters folded into one
  line, one label per thumbnail.
- **Review does the safe part for you**: fixed safe rules settle the clear cases (an identical new copy goes to the
  rejected folder, never deleted; short possibly sensitive ranges are blocked; a source found next to a file is
  filled in). Every automatic decision is logged with **Undo**, and "Apply to all similar" settles a group at once.
- **Search by meaning** (multilingual, with a free local model): finds descriptions that mean what you wrote, even
  in other words. It is prepared in one visible batch in Analyze, with Pause and Stop, on the GPU or the CPU.
- **From playhead line** in Premiere Pro: searches for the subtitle line under the playhead, from an SRT file beside
  the project. Read-only.
- **Terms of use**: they no longer say "beta", so Oriel asks you to agree to them once more.
- **Notifications**: green (done) and information notices fade by themselves after about 8 seconds; with the
  mouse over one it waits, and it goes on when the mouse leaves. Red (error) and yellow (warning) ones stay until you
  close them with the X. The same in the app and in the three panels; the history is in Settings › Notices.
- Updating: a stable version counts as newer than any beta, so every beta finds 4.0.0 through Check for updates.

## 3.8.0 beta — search by meaning

- **Search by meaning** (multilingual, with a free local sentence model): the Search tab also finds Oriel's
  descriptions by what they mean, not only by their words, and the shot catalogue your agent writes is searched the
  same way (`catalog-search`). The hard filters do not change.
- **Topics** for catalogue lines (`catalog-write` "topics": 1-3 of a small closed list — what a shot can
  illustrate). Agents write them; with the private topic list switched on for a client, existing lines get them
  automatically.
- **One visible batch** in Analyze ("Search by meaning" → Prepare), with Pause and Stop; it uses the GPU when there
  is one and also works on the CPU. New lines get their vector when they are written.
- **Review**: short possibly sensitive ranges are blocked by themselves whatever the confidence, with Undo.
- **Analyze**: in Simple, the automatic intake shows a link to Review instead of the full list; the reasons are
  shown in your language.

## 3.7.0 beta — Review decides the safe cases by itself

- **Review is more automatic**: with fixed rules (always the safe side) Oriel itself sends an identical duplicate's
  new copy to the rejected folder (never deleted), blocks short possibly sensitive ranges and keeps the rest of the
  file available, fills in a source it finds next to a file (.info.json, a registered URL, a Commons page), and
  marks footage as modern only when its name says a present-day year. Early colour photos are never "modern".
  When a project uses a copy, the new copy is sharper, the marks cover most of the file or the confidence is low,
  the case is yours, with the reason.
- **"Approved automatically"** lists every decision (what, why, when) with **Undo**. Files the rules settled but
  that would have to move wait in one "ready" card that asks first; files a project uses where they are are listed
  apart and never moved.
- **"Apply to all similar"** gives your decision to the cases like it, after a confirmation with the count.
- Agents: `review_list` / `review-list` and `review_decide` / `review-decide <case> auto | source | block`, with the
  same rules; the doubtful cases stay yours.
- **"From playhead line" in Premiere Pro**: the playhead of the active sequence and the project's SRT in
  6_DOCUMENTS (the part's SRT for P01…P11, the full one for the VIDEO FINAL). When no SRT fits, the chip says so.
  Read-only. Still hidden in After Effects.
- **Simple Search** shows the results right after the filters (project, result filters and selection are in
  Advanced). **Panels**: the results come first and the filters fold into one "Filters (n)" line; one label per
  thumbnail. **Analyze** for a client with GPU analysis off shows no time estimate.

## 3.6.0 beta — Oriel in four tabs

- **Four tabs: Search · Library · Review · Analyze.** Help and Settings are icons at the top right, next to the
  client, Simple/Advanced and "Check for updates". A status bar at the bottom shows the profile, the library disk,
  "GPU analysis off for this client" when it applies, and the version.
- **Search**: one big bar with two modes, **Describe** and **From script** (it replaces the Script tab); chips for the
  part's era, place, person, side, Videos/Images and **Approved only**. Every result shows its catalogue status
  (Approved / Provisional / Unverified) and the suggested crop.
- **Library**: a side menu (Browse, All media, Collections, Sources, People), people as a filter, catalogue status
  cards, browse by year and by place or topic, and the synced folders with their status.
- **Review**: only what needs your decision, one card per case with 2–3 buttons, filters by type and how many files
  were approved by themselves. Dangerous actions still ask first; deletions go to the Recycle Bin.
- **Analyze**: one card, "Searchable now: X of Y · ~N h left" with a range, Pause/Stop, folded details, the notice
  for a client with GPU analysis off, and "Next in line".
- **Simple / Advanced**: Simple hides the technical parts without removing any function; your choice is remembered.
  Simple is the default.
- **Panels (Premiere Pro, After Effects, DaVinci Resolve, 420 px)**: tabs with icon and name, a minimal header with
  client and project, results as a list. In DaVinci Resolve, the **"From playhead line"** chip searches with the
  subtitle line under the playhead (not shown in Premiere Pro or After Effects, which cannot read it reliably).
- Accessibility: visible keyboard focus, higher-contrast field borders, text of at least 11–12 px and named icon
  buttons.
- Nothing was removed: every old tab opens its new place, and the agent commands (CLI and MCP) are unchanged.

## 3.5.0 beta — Oriel as your agent's database

- **A shot catalogue written by your AI agent**: one line per shot (file and range, what is seen, real year, place,
  side, people each with a written source and date, marks with their position, title cards / black tails, photo
  passes / animated photos / dramatizations / AI, archive or modern). A person without a written source is refused:
  a face is never a source. Lines stay provisional until the project is approved.
- **Search by the narration's phrase** (`catalog-search`): the part's era is a hard filter, people only through
  their source, at most ~6 shots per source and part (copies of the same newsreel count as one source), no title
  cards, black tails, filler statues, undated compilations or anything that looks like bodies, and a suggested crop
  per source or per mark position.
- **Gaps before placing** (`catalog-gaps` with the SRT), batch commands from a file (`catalog-write`, `catalog-use`,
  `catalog-lines`, `catalog-import`) and `register-media` (files catalogued where they are, never moved).
- **`approve-project`**: reads a copy of the Premiere project, the final sequence and its nested parts; what stayed
  is approved, what got a review label keeps its verdict, what was replaced is not approved.
- **GPU analysis per client** (Settings › client): when off, the inbox is taken into the library without it.
- The estimate before starting an analysis is a **range** too.
- Fixed: a client whose disk disconnects for a moment stays the active client (the app no longer switches by
  itself); agent orders with `--client` work for a client that is not the active one; `prune-uses --unplaced` keeps
  the uses that are on the timeline; early colour photos (autochromes, Prokudin-Gorsky) are no longer flagged as
  present-day photos; a file a project uses where it is is never moved by itself.

## 3.4.0 beta — a real time left, the profile in view and "Check for updates"

- **Fixed: the time left of an analysis could grow to thousands of hours** (about 20,000 h for 800 videos on an RTX
  5070 Ti). It counted the whole session, including the time spent **waiting for memory** (Premiere open) and
  **loading a model** for the first time. Now only the time spent working counts, with the speed measured on your PC,
  and the time left is a **range**. While Oriel waits for memory it says so and the number does not grow.
- **Quick search first**: in a new folder, Oriel first finds the shots and makes the visual search for every file;
  the heavy steps (speech, details, descriptions, marks) follow in the background. You see "Searchable now: 120 of
  800 · full analysis ~3 h left". Pause and Resume work as before.
- **Your profile in view**: Analyze and Settings show e.g. "Pro · RTX 5070 Ti · GPU" or "Light · CPU". If your PC
  has an NVIDIA card but Oriel runs on the CPU, a clear warning says how to fix it.
- **"Check for updates" button** in the top bar (app and panels), with a dot when a new version is out. Oriel also
  checks by itself once a day. Recent notices are now in **Settings › Notices**.
- A step whose model is not downloaded yet waits instead of downloading inside the analysis.
- The installer checks that PyTorch can use your NVIDIA card; if not, it reinstalls the GPU version and, if that is
  not enough, tells you to update the NVIDIA driver.

## 3.1.0 beta — model profiles and terms of use

- **Model profiles**: **Light** (integrated graphics or CPU only), **Standard** (NVIDIA with about 6–10 GB) and **Pro**
  (NVIDIA with 12 GB or more). The wizard finds your graphics card and recommends one; you can choose another and
  change it later in Settings › AI model profile (it downloads what is missing and can send unused models to the
  Recycle Bin).
- The **visual search model is the same in every profile**: a library analysed with one profile searches the same
  with another, without analysing again.
- What a profile cannot analyse stays **pending**, with the note "This needs the Standard or Pro profile".
- **Terms of use** in the wizard ("I agree"), in Settings (English and Spanish), in TERMS.md and in the README.

## 3.0.0 beta — the first public version

- **First-run wizard**: language (English or Spanish), your first client and its library folder, NVIDIA or CPU mode,
  and the models with their size and a progress bar.
- **Search** by what is seen and by what is said, in videos and images, with no repeats inside a project.
- **Clients and projects**, each with its own library, language and rules. Two rule profiles: *General* (rules off
  but available) and *Archive footage* (the strict rules on: sensitive material, maps, fiction, graphics, low
  quality, logos, era of the project, identity protection...).
- **Inbox folder** with duplicates, approval, and undo for every move.
- **Panels** for Premiere Pro, After Effects and DaVinci Resolve Studio.
- **CPU mode** for PCs without an NVIDIA card.
- **AI agents**: MCP and the `oriel` command line (see AGENTS.md).
- **Check for updates** from this repository's Releases.
- **Help › Send a suggestion**.
- The face model is optional and off by default (non-commercial licence).
