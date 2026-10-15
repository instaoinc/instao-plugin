# Instao — French public tenders

Find and compare French public tenders, inspect available consultation documents
and retrieve their originals. The hosted service works without an Instao account
or API key. The bundled `find-public-tenders` skill guides discovery, refinement
and evidence-based qualification; it does not submit bids or contact buyers.

## Package and connection

This folder is the plugin root. It includes portable Agent Plugins manifests,
Codex, Claude and Cursor compatibility manifests, the skill and brand assets.
Remote MCP tools connect to `https://api.instao.fr/instao-mcp/mcp` using HTTP,
without authentication. No server runtime or private credentials are packaged.

For a repository-backed Claude submission, select `plugins/instao` as the plugin
path. The repository-root `.claude-plugin/marketplace.json` and
`.cursor-plugin/marketplace.json` catalogs point to the same folder; the existing
Codex `.agents/plugins/marketplace.json` catalog remains available.

In Claude Code 2.1.275 or later, install directly:

```text
/plugin install instao --marketplace instaoinc/instao-plugin
```

Alternatively, add the repository using `/plugin marketplace add
instaoinc/instao-plugin`, then install `instao@instao-remote`. A Claude connector
uses the same MCP URL; connecting only the endpoint does not load the skill.
In Codex:

```sh
codex plugin marketplace add https://github.com/instaoinc/instao-plugin.git
codex plugin add 'instao@instao-remote'
```

For a local Cursor CLI exercise after cloning, use
`cursor-agent --plugin-dir /absolute/path/to/instao-plugin/plugins/instao`.
Grok Bot's marketplace submission accepts the public repository or MCP URL.
Marketplace review and publication are separate from installing this package.

## Test complete conversations

1. Ask: “Nous nettoyons des écoles dans le Rhône. Trouve des marchés ouverts
   adaptés et compare leurs lots.” Check buyer, lot, location and deadline.
2. Refine the operating area or clarify that you supply goods without installation.
   The assistant should preserve these requirements and explain unknowns.
3. Select a consultation, list its files and ask whether a site visit is mandatory.
   Verify the answer cites a document and an observed passage or section.
4. Request an original RC or DCE archive. Open the result and verify filename and
   contents. Download URLs expire quickly and are single-use. If the host saves
   the file, it should present that file instead of a consumed download URL.
5. Try an empty search, an unavailable document and private-sector-only prospecting.
   The assistant should explain limitations without inventing results or redirecting
   unrelated work into public tenders.

Confirm actual tool calls, skill loading and file delivery in the target host.
CLI or endpoint tests alone do not prove native host installation or previews.
Available files and extraction coverage vary; a match does not certify eligibility.
Search and capacity limits apply. Saved profiles, Instao monitoring and bid
submission are outside this version.

## Publisher and policies

- [Instao](https://www.instao.fr/)
- [Documentation](https://github.com/instaoinc/instao-plugin)
- [Support](https://www.instao.fr/contact)
- [Plugin privacy policy](https://www.instao.fr/confidentialite-plugin-instao)
- [Terms](https://www.instao.fr/conditions-generales)

The square `assets/logo-plated.svg` places the original Instao mark on a white
background for listings that require a background plate. A public logo URL is
[available from the repository](https://raw.githubusercontent.com/instaoinc/instao-plugin/main/plugins/instao/assets/logo-plated.svg).

The distributed plugin files are licensed under [MIT](LICENSE). The hosted
backend and consultation documents are not included in this software license.
