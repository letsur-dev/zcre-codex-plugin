# Desktop connection verification — 2026-09-24

## Observed boundary

The public plugin installs and authenticates successfully through the Codex CLI.
The owner reported that the existing desktop conversation still exposed only
its development connection and could not use the production plugin.
A fresh, separate Codex runtime reported OAuth plus six tools; that was not
verification of the existing desktop conversation.

The current desktop conversation subsequently called production
`zcre-plugin.query_zcre` with `query.action=models` and received 26 models,
including `gpt-image-2`. The owner explicitly confirmed that the app had been
fully closed and reopened before that success. Record this as **post-restart**
evidence only. No upload, generation, or provider charge was performed.

## Restart-free path is not yet verified

The installed app's source invokes `config/mcpServer/reload` after its own OAuth
completion flow. Official Codex source implements that operation by refreshing
loaded threads:
https://github.com/openai/codex/blob/main/codex-rs/app-server/src/mcp_refresh.rs

The CLI proxy cannot reach this running desktop host: its default control socket
is absent. No exposed tool in this task provides an equivalent refresh action.
No undocumented socket or denied UI automation may be used to work around this.
Plugin manifests in this package do not expose an OAuth-completion callback that
can force the host to reload its current conversation.

App-managed installation/login is a candidate for further testing, not a
verified customer instruction. Before advertising restart-free setup, observe
installation and OAuth in the running app, keep the same conversation and app
process, and successfully query production models through that conversation's
native tool surface. A separate CLI/app-server readback does not satisfy this.

## Documentation patch

Remove blanket restart instructions and distinguish login from tool readiness.
Installation agents must inspect fresh tool availability and use a read-only
model query before announcing success. These changes prevent misleading guidance;
they do not patch Codex's desktop runtime or establish restart-free support.
