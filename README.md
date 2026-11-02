# Oriel

**Oriel finds the right shot in your own footage library.** You describe what you need ("a crowd waving flags in the
rain", "someone saying *we never gave up*") and Oriel shows the shots and lines that match, in your videos and images.
It runs on your PC: your footage, your catalogue and your searches never leave it.

> **Beta.** This is a beta version of Oriel (3.1.0 beta). Things may change between versions. Please send
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
| Disk | 10 GB free (Light profile) to 21 GB (Pro) for the app and the models, plus your footage | an SSD |
| Graphics | none: integrated graphics work (**Light** profile, analysis on the CPU) | NVIDIA card with 6 GB or more (Standard) or 12 GB or more (Pro) |
| Internet | to install, to download the models and for updates | |

The installer also installs, if they are missing and you agree: **Python 3.12** and **ffmpeg** (both through
Windows' own `winget`).

## Model profiles

Oriel works on any PC; what it analyses depends on the **model profile**. The first-run wizard finds your graphics
card and **recommends** one; you can choose another, and change it later in **Settings › AI model profile** (Oriel
downloads what is missing and can send the models you no longer use to the Recycle Bin).

| Profile | For | Analyses | Download |
|---|---|---|---|
| **Light** | integrated graphics or CPU only | shots, clean range, visual search, speech (Qwen3-ASR 0.6B). Attributes, logos / text on screen and descriptions stay **pending** | about 6.5 GB |
| **Standard** | NVIDIA with about 6–10 GB (e.g. RTX 3060 / 4060) | everything; attributes, logos and descriptions with Qwen3-VL 2B | about 13.6 GB |
| **Pro** | NVIDIA with 12 GB or more (e.g. RTX 4070 Ti / 5070 Ti) | everything, with Qwen3-VL 4B (best quality) | about 18.2 GB |

The **visual search model (SigLIP2) is the same in every profile**: a library analysed on a Pro PC searches exactly the
same on a Light one, without analysing again. What a profile cannot analyse stays *pending* (never an error) with the
note "This needs the Standard or Pro profile".

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
2. **Terms of use**: read them and tick *I agree* (see below).
3. **Your first client**: a name, and its library folder (a new empty folder, or an existing folder with your
   footage: Oriel never moves or renames the files of an existing folder). Choose **General** (rules off, like a
   plain search app) or **Archive footage** (the strict rules on).
4. **Model profile**: Light, Standard or Pro (the recommended one is marked).
5. **Models** of that profile: the search model (SigLIP2, about 4.6 GB) is required; the others are optional. Each
   shows its size and a progress bar. The face model is optional and **off by default** (see *Licences*).

Then open **Analyze**, add the batch and press **Start**. When it ends, search in **Search**.

## Updates

**Settings › Version and updates › Check for updates** looks for a newer version on this repository's Releases page.
Updating replaces only Oriel's code: your clients, catalogues, settings and models stay as they are, and the previous
version is kept beside it until the next update.

## Privacy

Everything is local. Oriel only goes online to download the models, to check for updates and to send a suggestion
when you press *Send*. No accounts, no analytics. Full details: [PRIVACY.md](PRIVACY.md).

## Terms of use

The full text is in [TERMS.md](TERMS.md) and in the app (Settings › Terms of use, in English and Spanish). In short:

- Oriel is **free** and in **beta**. It is provided **"as is"**, without warranties of any kind.
- The author is not responsible for any loss of data or files, or any damage, caused by its use. **Keep backups.**
- Everything runs locally. Oriel only goes online to download models, check for updates and send suggestions (when
  you ask it to). No usage data is collected.
- You are responsible for the material you analyse and for respecting its copyright.
- You may use Oriel for free. You may not resell it, redistribute it modified, or present its name or logo as your
  own.
- The AI models have their own licences ([TERMS.md](TERMS.md), [LICENSES.md](LICENSES.md)). The face model
  (insightface) is for non-commercial use only: it is off by default and you must accept its licence to turn it on.
- Oriel is not affiliated with Adobe, Blackmagic Design or any other manufacturer; their trademarks belong to their
  owners.
- These terms may change in future versions.

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
