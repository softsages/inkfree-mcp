<p align="center">
  <img src="assets/logo.png" alt="Inkfree" height="48">
</p>

# Inkfree MCP Server

Connect Claude, ChatGPT, Cursor, VS Code and other MCP clients to your Inkfree e-signature account.
Ask your assistant what is waiting on signatures, send an envelope from a template, chase a signer,
pull the audit trail, or download the completed document.

This is a **hosted** MCP server. There is nothing to install or run: point your client at the URL
below and sign in with your Inkfree account.

```
https://api.inkfree.app/core/inkfree/mcp/
```

| | |
| --- | --- |
| Transport | Streamable HTTP |
| Authentication | OAuth 2.1 with PKCE and dynamic client registration (sign in with Inkfree) |
| Tools | 32 ([full list](docs/tools.md)) |
| Account needed | Yes, an Inkfree account ([sign up](https://www.inkfree.app/)) |
| Registry name | `app.inkfree/mcp` |

> This repository holds documentation and the registry manifest only. The server itself is
> operated by SoftSages and is not open source.

## What you can do

- **Envelopes**: list and filter by status, see each signer's status and order, send a draft,
  send from a template, bulk-send one envelope to many recipients as separate envelopes, resend a
  reminder, and void.
- **Documents and audit**: get download links for documents and read the full audit trail (sent,
  viewed, signed, declined, voided).
- **Organizing**: folders for envelopes and templates, plus move, rename and delete.
- **Sharing**: give a colleague view-only access to an envelope, list who has access, and revoke it.
- **Webforms**: list webforms and see which templates they are linked to.
- **Reports**: dashboard counts, status and funnel counts by date, per-recipient, per-template and
  per-user activity.

### Example prompts

- "What's still waiting on someone else's signature, and since when?"
- "Send the NDA template to jane@example.com and remind me if she hasn't signed by Friday."
- "Who viewed the Acme MSA envelope and when?"
- "How many envelopes did we send and complete last month, by template?"

## Connect your client

### Claude (claude.ai, desktop and mobile)

Settings > Connectors > **Add custom connector**, paste `https://api.inkfree.app/core/inkfree/mcp/`,
then **Connect** and sign in.

### Claude Code

```bash
claude mcp add --transport http inkfree https://api.inkfree.app/core/inkfree/mcp/
```

Then run `/mcp` inside Claude Code and choose **Authenticate**.

### ChatGPT

Settings > Apps and Connectors > Advanced > turn on **Developer mode**, then **Create** a connector
with the URL `https://api.inkfree.app/core/inkfree/mcp/` and authentication **OAuth**.

### Cursor

`~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "inkfree": {
      "url": "https://api.inkfree.app/core/inkfree/mcp/"
    }
  }
}
```

### VS Code (GitHub Copilot agent mode)

`.vscode/mcp.json`:

```json
{
  "servers": {
    "inkfree": {
      "type": "http",
      "url": "https://api.inkfree.app/core/inkfree/mcp/"
    }
  }
}
```

### Any other MCP client

Use the URL with Streamable HTTP transport. The server answers unauthenticated requests with
`401` and a `WWW-Authenticate` header pointing at its
[protected resource metadata](https://api.inkfree.app/core/.well-known/oauth-protected-resource/inkfree/mcp),
so any client that follows the MCP authorization spec can discover the authorization server and
register itself.

## Authentication and permissions

- You sign in on Inkfree's own login page. Your password is never shared with the AI client.
- The client receives a short-lived access token scoped to your account. Every tool call acts as
  you and only sees envelopes and templates you can see in Inkfree.
- Scopes advertised: `mcp:read`, `mcp:write`, `mcp:send`.
- Every tool carries MCP annotations. Read tools are marked read-only. Sending and voiding envelopes
  are marked destructive, so well-behaved clients ask you to confirm before running them.
- To disconnect, remove the connector in your client.

## Privacy and security

- Privacy policy: https://www.inkfree.app/privacy-policy/
- Terms: https://www.inkfree.app/terms/
- Report a vulnerability: see [SECURITY.md](SECURITY.md)

## Support

- Email: support@inkfree.app
- Contact page: https://www.inkfree.app/contact-us/
- Documentation issues with this repository: open a GitHub issue.

---

Inkfree is a product of [SoftSages](https://www.softsages.com/).
