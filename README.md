# Oriel

**Oriel finds the right shot in your own footage library.** You describe what you need ("a crowd waving flags in the
rain", "someone saying *we never gave up*") and Oriel shows the shots and lines that match, in your videos and images.
It runs on your PC: your footage, your catalogue and your searches never leave it.

> **Beta.** This is the first public version of Oriel (3.0.0 beta). Things may change between versions. Please send
> what you find through **Help › Send a suggestion** inside the app.

## What it does

- **Search by what is seen** (visual search) and **by what is said** (speech, in 50+ languages).
- **Clients and projects**: each client has its own library, language and rules. Libraries never mix.
- **No repeats**: Oriel remembers what you already used in a project, so the same clip is not suggested twice.
- **Rules per client** (optional switches): hide sensitive material, maps, graphics, low quality, logos in the
  centre, footage outside the project's era, and more. The app enforces them; an AI agent cannot skip them.
- **Inbox folder**: download straight into the client's `_INBOX`; Oriel takes each finished file, spots duplicates
  and files it by type. Every move is logged and can be undone.
- **Panels for Premiere Pro, After Effects and DaVinci Resolve Studio**: search and place clips without leaving
  the editor.
- **AI agents** (Claude, Codex, Cursor and others) can search, log uses and look up sources through MCP or the
  `oriel` command line. See [AGENTS.md](AGENTS.md).

## Requirements

| | Minimum | Recommended |
|---|---|---|
| System | Windows 10 or 11, 64-bit | Windows 11 |
| Memory | 16 GB RAM | 32 GB RAM |
| Disk | 15 GB free for the app and the models (plus your footage) | an SSD |
| Graphics | none: Oriel works in **CPU mode** (slower analysis) | NVIDIA card with 8 GB or more (CUDA) |
| Internet | to install, to download the models and for updates | |

The installer also installs, if they are missing and you agree: **Python 3.12** and **ffmpeg** (both through
Windows' own `winget`).

Without an NVIDIA card, Oriel analyses shots, visual search, the clean range and speech on the CPU. The steps that
need a large vision model (attributes, logos and text on screen, descriptions) wait until the library is opened on
a PC with an NVIDIA card.

## Install

1. Download `Oriel-Setup-<version>-beta.zip` from the [Releases](../../releases) page.
2. Right-click the zip › **Extract All…** (do not run it from inside the zip).
3. Double-click **`Install Oriel.cmd`**.
   - Windows may show *"Windows protected your PC"* (SmartScreen) because the beta is not signed yet: click
     **More info › Run anyway**.
4. Follow the window: it checks Python and ffmpeg, detects your graphics card, installs the Python packages
   (about 1 GB in CPU mode, about 3 GB with an NVIDIA card) and creates the **Oriel** shortcuts.

By default Oriel is installed in `%LOCALAPPDATA%\Programs\Oriel`. Your data lives in `%USERPROFILE%\.reeldex`
and in a `_CATALOG` folder inside each library.

## First use

The first time Oriel opens, a short wizard asks for:

1. **Language**: English (default) or Spanish.
2. **Your first client**: a name, and its library folder (a new empty folder, or an existing folder with your
   footage: Oriel never moves or renames the files of an existing folder). Choose **General** (rules off, like a
   plain search app) or **Archive footage** (the strict rules on).
3. **Graphics**: Oriel tells you whether it found an NVIDIA card or will use CPU mode.
4. **Models**: the search model (SigLIP2, about 4.6 GB) is required; speech, the search translator and (with an
   NVIDIA card) the vision model are optional. Each shows its size and a progress bar. The face model is optional
   and **off by default** (see *Licences*).

Then open **Analyze**, add the batch and press **Start**. When it ends, search in **Search**.

## Updates

**Settings › Version and updates › Check for updates** looks for a newer version on this repository's Releases page.
Updating replaces only Oriel's code: your clients, catalogues, settings and models stay as they are, and the previous
version is kept beside it until the next update.

## Privacy

Everything is local. Oriel only goes online to download the models, to check for updates and to send a suggestion
when you press *Send*. No accounts, no analytics. Full details: [PRIVACY.md](PRIVACY.md).

## Licences

Oriel uses open-source libraries and AI models; each keeps its own licence. The full list is in
[LICENSES.md](LICENSES.md). In short:

- All the models Oriel needs for search, speech, shots and descriptions allow **commercial use** (Apache-2.0, MIT,
  CC-BY-4.0).
- The optional **face model (insightface buffalo_l)** is for **non-commercial research only**. It is off by default;
  download it and turn faces on only if your use fits its licence.

## Uninstall

Delete the Oriel shortcuts and the install folder (`%LOCALAPPDATA%\Programs\Oriel`). Your data stays in
`%USERPROFILE%\.reeldex` and in each library's `_CATALOG` folder; delete them too if you no longer want them.
Your footage is never touched.

## Feedback

Inside the app: **Help › Send a suggestion** (suggestions, errors, anything else).
