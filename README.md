# Designelier MCP Server

Generate coordinated icon sets, spot illustrations and transparent design assets for websites and apps from any MCP client. Plan a pack from a short brief or your page, review the exact quote, and generate only after you confirm.

- **Endpoint:** `https://mcp.designelier.com/mcp` (Streamable HTTP)
- **Auth:** OAuth, sign in with your Designelier account
- **Website:** https://designelier.com/mcp
- **Official MCP Registry:** `com.designelier/mcp`

## What you can do

- Plan a matching icon set or spot illustrations (1 to 6 assets in one shared style and palette) from a short brief.
- Plan a full artwork pack for a website from its public URL.
- See the planned subjects, the style and the exact credit quote first. Planning is free.
- Generate only after you confirm the quote. Download a ZIP with SVG files and full-canvas and cropped transparent WebP files.

The SVG files embed raster artwork. They are not editable vector paths.

## Connect

The server uses OAuth. Your client opens a browser window, you sign in with your Designelier account and approve access. You do not copy an API key.

### Claude (claude.ai and Claude Desktop)

Open **Settings → Connectors → Add custom connector**, enter `https://mcp.designelier.com/mcp` and select **Connect**.

### Claude Code

```bash
claude mcp add --transport http designelier https://mcp.designelier.com/mcp
```

Then run `/mcp` in Claude Code and authenticate `designelier`.

### Codex CLI

```bash
codex mcp add designelier --url https://mcp.designelier.com/mcp
codex mcp login designelier
```

### Cursor

Add this to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "designelier": { "url": "https://mcp.designelier.com/mcp" }
  }
}
```

### VS Code

```bash
code --add-mcp '{"name":"designelier","type":"http","url":"https://mcp.designelier.com/mcp"}'
```

### Gemini CLI

```bash
gemini mcp add --transport http designelier https://mcp.designelier.com/mcp
```

### ChatGPT and other clients

Add a custom connector (in ChatGPT, developer mode) with the URL `https://mcp.designelier.com/mcp`. Any client that supports Streamable HTTP and MCP OAuth works.

## Tools

Your client always gets the current list and schemas from `tools/list`.

| Tool | What it does |
| --- | --- |
| `designelier_get_account` | Read total, reserved and available credits. Never spends credits. |
| `designelier_plan_assets` | Plan a matching icon set or spot illustrations with transparent backgrounds. |
| `designelier_plan_pack` | Analyze one public website URL and create a pack plan with an immutable quote. Free. |
| `designelier_get_pack` | Read a pack, its planned subjects, style, quote, previews and download. |
| `designelier_confirm_pack` | Confirm the exact quote and generate the pack. Spends credits on success. |

## Authentication and account

OAuth 2.1 with dynamic client registration. Sign in with your Designelier account in the browser. Scopes: `designelier:read`, `designelier:generate`.

You need a Designelier account. Generation uses credits from your account.

## Links

- Website: https://designelier.com
- MCP setup page: https://designelier.com/mcp
- Privacy policy: https://designelier.com/privacy

## About this repository

This repository is the public home of the hosted Designelier MCP server. It holds this setup guide and the registry metadata (`server.json` for the official MCP Registry, `glama.json` for Glama). The server runs as a hosted service at `https://mcp.designelier.com/mcp`. Its source code is not in this repository.

Found a problem or have a question? Open an issue.

## License

The contents of this repository are available under the [MIT License](LICENSE).
