# VideoGen agent plugin

The official [VideoGen](https://videogen.io/videogen-mcp) plugin for Cursor,
Gemini CLI, and Codex-compatible hosts. Create product ads, narrated videos,
and individual media, then caption, edit, and export an MP4.

## Install

### Cursor

Once approved, install VideoGen from the Cursor Marketplace. The Cursor
manifest is `.cursor-plugin/plugin.json`; `mcp.json` connects the hosted MCP.

### Gemini CLI

```sh
gemini extensions install https://github.com/video-gen/videogen-plugins
```

### Agent skills

```sh
npx skills add video-gen/videogen-plugins --skill videogen
```

The standalone skill requires a VideoGen MCP connection configured in your
agent host. This command installs guidance, not the MCP connection itself.
Use `https://mcp.videogen.io/mcp` in the host's MCP settings and sign in.

### Codex-compatible hosts

The `.codex-plugin/plugin.json` manifest bundles `skills/` and `.mcp.json`.
For the independent Codex Plugin Marketplace, use its plugin installer after
listing approval. This repository is not an OpenAI endorsement.

## Authentication and usage

Complete the host-managed OAuth flow with your VideoGen account. No API key,
password, or token is bundled. Try:

- "Use VideoGen to create a 15-second vertical product ad, add captions, and export an MP4."
- "Use VideoGen to turn this script into a narrated landscape explainer."
- "Use VideoGen to animate this product image and return a download link."

Generation and exports may consume account credits. Connected-account access
controls project and media permissions. Respect the user's requested scope,
budget, and existing project choices.

## Network and components

One hosted HTTP MCP connection and one workflow skill. No scripts, lifecycle
hooks, local executables, dependency installation, or local secret reads.

- `https://mcp.videogen.io/mcp`: tools, guidance, and OAuth discovery/endpoints.
  The `vg_client` query parameter identifies the host in VideoGen integration
  attribution; it contains no user identifier or credential.
- `https://app.videogen.io`: account sign-in and project deep links.
- Operation-specific upload/download URLs returned by tools: transfer requested
  media only.

The manifests and endpoint discovery are checked statically. Installation,
OAuth, and generation in each host still require host-specific verification;
no successful host test is claimed by this package.

## Ownership and license

Maintained by [VideoGen](https://github.com/video-gen). Contact:
support@videogen.io. Plugin files are MIT licensed. The hosted service is
subject to [VideoGen's terms](https://videogen.io/terms-of-service) and
[privacy policy](https://videogen.io/privacy-policy).
