# localctx — Releases & Issue Tracker

`localctx` is a local codebase search CLI and optional MCP server for Apple Silicon Macs (`macOS 14 Sonoma` or newer, `M1` or newer, `16 GB+` unified memory). Coding agents such as Claude Code, Cursor, Codex, and Antigravity call `localctx search` to locate relevant files and line spans locally before reading files into cloud context, and call `localctx ask` when a local Metal-accelerated explanation with `path:Lstart-Lend` citations is needed.

This public repository hosts signed macOS release archives on GitHub Releases and the public issue tracker. `localctx` is proprietary commercial software; the source code is not public.

## Benchmark Summary (Held-Out Set 6)

- First-try file match on 90 held-out merged PRs across 9 unseen repository-disjoint repositories in Held-Out Set 6 (freeze SHA 3a702e269c0b0d83): 56.7% for zero-GPU localctx search (95% CI 46.7–66.7%) and 56.7% for localctx ask E4B vs 31.1% for ripgrep (95% CI 22.2–41.1%, +25.6 pp, McNemar p = 0.0002); top-3 file match 73.3% vs 52.2% (+21.1 pp, p = 0.0005); cutting median estimated cloud input tokens per query by −84.9% (1,040 vs 6,900; mean 1,017 vs 17,294 is skewed by pocketbase/pocketbase).
- On `vitejs/vite` within Set 6, `ripgrep` achieved higher line-hunk overlap at top 3 (16.19% vs 13.33% for `localctx search`). Full per-repository results and loss disclosures are published at https://localctx.apolloswave.com/research.

## Install

```bash
brew install apolloswave/tap/localctx
cd ~/code/your-repo && localctx init . --configure-agents
```

Signed release tarballs and `.sha256` checksums are published under https://github.com/ApollosWave/localctx/releases and verified by `localctx update` against the embedded Ed25519 release signing key (`97c5774ed01d4fbda2ed7c3a776723848266a25af209ba9625bf508383f7d275`).

## Documentation

Full CLI, coding-agent setup, MCP configuration, and troubleshooting reference: https://localctx.apolloswave.com/docs

## Privacy

- Zero source code, prompts, or file contents leave your Mac (0 outbound network calls on Free tier after the one-time huggingface.co model download on init; paid license lease checks and explicit opt-in --share / update / feedback commands send only metadata, verified across 5 CLI source modules).
- Privacy policy: https://localctx.apolloswave.com/privacy

## License & Terms

`localctx` is proprietary software licensed by ApollosWave LLC (with a local Free tier and paid Pro, Founding, and Team seats). Source code is not public. Full license terms: https://localctx.apolloswave.com/terms

## Reporting Issues

Issues and bug reports are welcome:

- Public issue tracker: https://github.com/ApollosWave/localctx/issues
- Sanitized CLI diagnostics (for active license holders, interactive preview before sending): `localctx feedback "Short description" --attach-diagnostics`
- Email support and security disclosures: `localctx@apolloswave.com`
