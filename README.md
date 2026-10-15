# Instao — French public tenders

Instao helps your AI assistant find and compare French public tenders, understand
requirements and retrieve available consultation documents to help you prepare a
bid. Describe your business and where you work, then refine the results through
conversation.

No Instao account or API key is needed.

## Install

### Codex

With Git and a recent Codex CLI with plugin support installed, run in your terminal:

```sh
codex plugin marketplace add https://github.com/instaoinc/instao-plugin.git
codex plugin add 'instao@instao-remote'
```

Start a new Codex task to use Instao.

### Claude Code

Run these commands inside Claude Code:

```text
/plugin marketplace add instaoinc/instao-plugin
/plugin install instao@instao-remote
```

Start a new session to use Instao.

### Other MCP clients

If your assistant supports remote MCP servers, connect to
`https://api.instao.fr/instao-mcp/mcp` with no authentication. This gives it access
to Instao's tools; installing the plugin also includes guidance for finding and
comparing tenders.

## Try it

Tell your assistant what you offer and where you operate. For example:

- “Nous nettoyons des bureaux et des écoles dans le Rhône. Trouve des marchés
  ouverts adaptés et compare les lots.”
- “Compare ces deux consultations et indique les points à vérifier avant de
  répondre.”
- “Retrouve le règlement de consultation, vérifie si une visite est obligatoire
  et télécharge le document original.”

Document availability varies. Ask for sources when checking requirements and
confirm deadlines before responding to a tender.

## Learn more

[Instao](https://www.instao.fr/) · [Support](https://www.instao.fr/contact) ·
[Privacy](https://www.instao.fr/confidentialite-plugin-instao) ·
[Terms](https://www.instao.fr/conditions-generales)

The plugin files are licensed under [MIT](LICENSE). The hosted service and
consultation documents are not covered by this license.
