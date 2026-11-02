# Oriel for AI agents

Any AI agent can use Oriel to find shots in the user's footage, log what it uses and look up where a video came
from. There are two ways in, with the same tools and the same rules:

- **MCP** (Model Context Protocol): for Claude Code, Claude Desktop, Codex, Cursor and any MCP client.
- **The `oriel` command line**: JSON in, JSON out, for any agent that can run a program.

Oriel's server only answers on this PC (`127.0.0.1`, port 6789). It starts by itself when the PC starts (Settings ›
Background server), and the command line starts it when it is off.

## Connect

### MCP, the easy way

In Oriel: **Settings › AI assistants**. Oriel finds Claude Code, Claude Desktop and Codex on this PC and installs
the connection with one click (it backs up their config file first). It also installs Oriel's skills for Claude Code
(how to search, B-roll, paper cuts, timeline review...).

### MCP, by hand (any other client)

Oriel speaks MCP over stdio through a small bridge. Use this command in your client's MCP settings (replace the
folder if you installed Oriel elsewhere):

```json
{
  "mcpServers": {
    "oriel": {
      "command": "%LOCALAPPDATA%\\Programs\\Oriel\\.venv\\Scripts\\python.exe",
      "args": ["-m", "reeldex.mcp.stdio"],
      "env": { "PYTHONPATH": "%LOCALAPPDATA%\\Programs\\Oriel\\backend", "REELDEX_PORT": "6789" }
    }
  }
}
```

(Expand `%LOCALAPPDATA%` to the real path if your client does not.) The bridge reads the access token from
`%USERPROFILE%\.reeldex\agent_token` by itself.

### Command line

```
"%LOCALAPPDATA%\Programs\Oriel\oriel.cmd" ping
"%LOCALAPPDATA%\Programs\Oriel\oriel.cmd" capabilities
```

`ping` says whether Oriel is running and lists the clients. `capabilities` lists every command with its arguments.
Every command except `ping` and `capabilities` needs `--client <slug or name>`.

## How to work with Oriel

1. **Name the client in every order.** Each client is isolated (its own library, rules, uses and searches).
2. **Read the client's profile first**: MCP `get_client_profile`, CLI `oriel --client <c> profile`. Follow its
   `agent_instructions`. The rules are enforced by Oriel itself; a refused request says why.
3. **Choose the project** being edited: MCP `set_project`, CLI `oriel --client <c> project "<name>"`. What was used
   in the project is never suggested again.
4. **Search**:
   - what is seen: MCP `search_visual`, CLI `oriel --client <c> search "soldiers marching in the snow"`;
   - what is said: MCP `search_speech`, CLI `oriel --client <c> search --speech "we never gave up"`.
   Prefer `exact` results; use each result's `suggested_in` / `suggested_out` (clips) and `suggested_duration`
   (images).
5. **Log every use before placing a clip**: MCP `register_use`, CLI
   `oriel --client <c> register-use --item S2824 --in 30 --out 33`. A repeated or excluded clip is refused with
   alternatives; after several refusals in a row, stop and ask the user. `check_use` / `check-use` is the dry run.
6. **Before importing a library file**, check its final name: MCP `final_name`, CLI `oriel --client <c> final-name S2824`.
7. **Sources**: before proposing or downloading a video, ask whether it is (or was) already in Oriel: MCP
   `source_check`, CLI `oriel --client <c> source-check "<URL, YouTube ID or title>"`. `source_cards` /
   `source-cards` shows where each video came from and what was used of it.
8. **New downloads** go through the client's inbox or `ingest_media` / `register_download`: they wait for the user's
   approval before they can be searched or used.

Other useful tools: `get_transcript`, `get_frame` (look at a result), `find_similar`, `build_timeline` (an
FCPXML / EDL / OTIO timeline from clips, logged as uses), `read_timeline` / `review-timeline` (what the editor
placed or rejected), `coverage` (how much usable material there is for a script), `list_people` and
`propose_person_name` (names stay *proposed* until the user confirms them).

## Rules every agent must keep

- Never move, rename or delete the user's files. Oriel files the inbox and renames only what the user approves.
- Faces never decide identities: a proposed name is not a verified identity.
- Heavy analysis (`start_analysis`, `start_gpu_batch`) is only started when the user asks for it.
- Report what you used and anything uncertain (for example a *probable* person).
