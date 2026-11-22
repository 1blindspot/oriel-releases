# What's new in Oriel

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
