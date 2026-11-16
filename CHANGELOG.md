# What's new in Oriel

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
