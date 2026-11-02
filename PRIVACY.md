# Privacy

**Everything is local.** Oriel runs on your PC. Your footage, your catalogue (what Oriel learns about each file),
your searches, your clients, your projects and what you used in them stay on your PC. There are no accounts, no
analytics and no tracking.

## When Oriel goes online

Only in these cases:

| When | Where it connects | What is sent |
|---|---|---|
| Installing | `winget` (Python, ffmpeg), the Python package index and `download.pytorch.org` | the usual download requests of those tools |
| Downloading a model (wizard or Settings) | Hugging Face (`huggingface.co`) | the request for that model's files |
| Checking for updates (Settings › Version and updates) | GitHub (`api.github.com`, this repository's Releases) | the request for the latest release; no data about you or your library |
| Sending a suggestion (Help › Send a suggestion), only when you press *Send* | Google Forms | the name and e-mail you type, the type of message, your text, Oriel's version and, only if you tick it, a short log **without file paths** |

A suggestion written without internet waits on your PC and is sent the next time Oriel is online.

## AI agents

If you connect an AI agent (Claude, Codex, Cursor...) to Oriel, the agent reads Oriel's answers (file names,
transcripts, descriptions, frames you ask for). Where that information goes then depends on that agent and its
provider, not on Oriel. Oriel itself only answers on your own PC (`127.0.0.1`), protected by a token that only your
Windows user can read.

## Where your data is

- `%USERPROFILE%\.reeldex`: settings, the client list, catalogues of clients without a library, models, backups.
- `_CATALOG` inside each library folder: that library's catalogue.
- Oriel never moves, renames or deletes your footage, except the files you download into a client's `_INBOX`
  folder, which it files by type (every move is logged and can be undone). When you choose to delete a duplicate,
  it goes to the Windows Recycle Bin.
