# warpussy

warpussy is an experimental fork of Warp focused on local bring-your-own-key AI provider setup.

The app is intentionally branded as **warpussy** in OSS builds. It is not an official Warp release.

## What Changed

- The OSS app name, installer name, URL scheme, log name, and config directory are branded as `warpussy`.
- Provider Setup stores API keys locally through secure storage.
- Signed-out users can configure and use local BYOK providers.
- OpenRouter is prioritized for signed-out BYOK agent requests when an OpenRouter key is configured.
- Warp-hosted model defaults are avoided when local BYOK keys are available.
- The model picker shows configured BYOK provider models and lets users hide models from the selector.

## OpenRouter Testing

1. Open `Settings > AI > Provider Setup`.
2. Enable Warp Agent if needed.
3. Add an OpenRouter API key.
4. Choose an OpenRouter model from `Default BYOK Model`, or leave it unset to use the first enabled OpenRouter model.
5. Use `/model` to verify only enabled BYOK models appear alongside any locally available choices.

## Current Limitations

- Requesty and arbitrary custom OpenAI-compatible endpoints are not fully routed through the current Warp multi-agent backend because the request protobuf only supports specific BYOK fields.
- Codex OAuth should be handled by the Codex CLI itself with `codex login`; warpussy can detect and support `codex` as a third-party CLI agent.
- Some upstream source comments and internal identifiers still use `warp` because they refer to crate names, protocols, or inherited implementation details.

## Building

```bash
./script/bootstrap
./script/run
```

For Windows installer testing, use the GitHub Actions workflow `Build Windows Test Installer` with `channel=oss`.

## Upstream

This fork is based on the open-source Warp repository from `warpdotdev/warp` and keeps the upstream AGPL/MIT licensing structure.
