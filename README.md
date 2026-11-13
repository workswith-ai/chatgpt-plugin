# workswith.ai for ChatGPT

A ChatGPT / Codex plugin that connects ChatGPT to your organization on workswith.ai: its Types, Records
and Processes, and the Actions you may invoke. It adds one MCP server, `https://auth.workswith.ai/mcp`.

This repository is both the plugin and its marketplace (`.agents/plugins/marketplace.json`).

## Install

```
codex plugin marketplace add workswith-ai/chatgpt-plugin
codex plugin add workswith-ai@workswith-ai
```

Or in the Codex app, open **Plugins**, add the marketplace `workswith-ai/chatgpt-plugin` and install
**workswith.ai**.

The plugin signs in when you install it. Your browser opens workswith.ai, where you sign in as usual and
choose what ChatGPT may do: *read*, *act*, and *build*. You need the *Connect apps* permission in the org.
Revoke the connection at any time under Desk › Connected apps.

## How sign-in works

The plugin names only the MCP address. The client reads that host's protected-resource metadata, which
names workswith.ai's authorization server, registers itself there (dynamic client registration) and signs
in with PKCE. No client id or secret is packaged, and the token is for your org alone.

## Layout

| File | Purpose |
| --- | --- |
| `plugin.json` | Plugin manifest (Agent Plugins 1.0.0, with ChatGPT presentation under `extensions.com.openai`) |
| `mcp.json` | The workswith.ai MCP server |
| `.agents/plugins/marketplace.json` | Marketplace listing this repository as the one plugin |
| `assets/logo.svg` | Icon and logo |

## Privacy

[Privacy policy](https://workswith.ai/privacy). MIT licensed; see `LICENSE`.

## Developing

```
codex plugin marketplace add ./
codex plugin add workswith-ai@workswith-ai
```

After changing files, bump `version` in `plugin.json` and run `codex plugin marketplace upgrade workswith-ai`.
