# Instao hosted pilot: tester guide

The pilot helps you discover and compare French public tenders from a conversation using Instao's production catalog. Start with a real business need, refine the results and ask what still needs checking. Searches, previews and available consultation files can be used without an Instao account.

Ask the assistant to inspect a consultation's files, cite numbered passages or retrieve an original document. Missing files and incomplete text extraction must remain explicit. Account linking is not needed for this pilot.

This is an early hosted pilot with a publicly installable package. It is not yet a published directory plugin. Saved company profiles, managed response projects, favorites, UI panels and Instao monitoring are outside this version. The assistant can use retrieved documents to help prepare a bid in its host.

## Install in Codex

Use a current Codex app/CLI with plugin support and Git. From a terminal where `codex` is available, run these commands on Windows, macOS or Linux:

```sh
codex plugin marketplace add https://github.com/instaoinc/instao-plugin.git
codex plugin add 'instao@instao-remote'
```

Start a new task in Codex. The plugin includes the discovery skill and connects to the hosted production service. You need no GitHub login, private repository access, Bun, database credentials or Instao account.

If an older Instao marketplace is already configured, replace that source first:

```sh
codex plugin marketplace remove instao-remote
codex plugin marketplace add https://github.com/instaoinc/instao-plugin.git
codex plugin add 'instao@instao-remote'
```

If a local Instao developer plugin is also enabled, disable that copy before testing so results are not mixed between servers.

The [public installation repository](https://github.com/instaoinc/instao-plugin) contains only plugin assets and tester guidance, with its own history. It targets `https://api.instao.fr/instao-mcp/mcp`. Alternatively, download the repository's main branch as a ZIP, extract it into a permanent directory, preserve hidden files, and register the extracted root:

```sh
codex plugin marketplace add /absolute/path/to/unpacked-instao-plugin
codex plugin add 'instao@instao-remote'
```

For Git installs, refresh the package after an update:

```sh
codex plugin marketplace upgrade instao-remote
codex plugin add 'instao@instao-remote'
```

Start a new task after updating. For ZIP installations, replace the extracted files with the new ZIP and reinstall the plugin; the Git upgrade command does not refresh local directories.

To remove it:

```sh
codex plugin remove 'instao@instao-remote'
codex plugin marketplace remove instao-remote
```

## Claude and Grok Bot

The self-contained plugin folder is `plugins/instao`. It includes the discovery
skill, a dedicated README, icons and Claude/Cursor compatibility manifests alongside
the portable and Codex manifests. All configurations use the same anonymous hosted
endpoint; the package contains no backend runtime or credentials.

For a Claude repository-backed submission, select this folder as the plugin path.
In Claude Code 2.1.275 or later, use `/plugin install instao --marketplace
instaoinc/instao-plugin`. Alternatively, add the repository with `/plugin marketplace add
instaoinc/instao-plugin` and install `instao@instao-remote`. A manually configured
Claude connector uses `https://api.instao.fr/instao-mcp/mcp`; pairing a connector
and a plugin should retain this same endpoint.

Grok Bot accepts the public repository or MCP URL in its
[submission form](https://x.ai/bot/marketplace/submit-a-plugin). Its Cursor-format
marketplace index points to `plugins/instao`. The plated square logo has a
[public URL](https://raw.githubusercontent.com/instaoinc/instao-plugin/main/plugins/instao/assets/logo-plated.svg).

After cloning, a Cursor CLI exercise can load the folder with
`cursor-agent --plugin-dir /absolute/path/to/instao-plugin/plugins/instao`.
Grok Build CLI also supports `grok plugin marketplace add
https://github.com/instaoinc/instao-plugin.git`, then `grok plugin install instao
--trust`. These are proxy tests; check installation, skill loading and file
delivery inside Claude and Grok Bot before attesting to in-app compatibility.

Repository installation, portal validation, directory review and publication are
separate. A direct MCP connection provides tools but does not import the skill.

The distributed plugin files are licensed under MIT. The hosted backend and
consultation documents are not included in that software license.

## Test in ChatGPT

When developer mode is available on your account, open **Settings → Security and login → Developer mode**. Go to [ChatGPT Plugins](https://chatgpt.com/plugins), select the plus button and register `https://api.instao.fr/instao-mcp/mcp`. Choose **No authentication** for the current anonymous pilot. If you connected the earlier staging endpoint manually, update or recreate that connection with this production URL. Start a new chat and test discovery. Do not enter API keys, database credentials or a coworker's tokens.

For a full ChatGPT package with the bundled skill, registration produces a technical ID starting with `plugin_asdk_app` in the browser URL. Give that ID to the team to wire the OpenAI mapping; the direct connection above can already test the hosted tools.

A manually connected MCP endpoint tests the hosted tools. It does not by itself install the repository's skill package or publish anything to OpenAI's directory. Report whether you used this ChatGPT connection or the complete Codex plugin; their results are separate evidence. If your account lacks developer mode or the connection flow rejects the server, record that exact limitation rather than changing account or access settings at random.

See the [official local-plugin setup](https://developers.openai.com/plugins/build/plugins#create-and-test-a-plugin-locally-with-an-mcp-server).

## Try complete conversations

Use your own wording and follow up naturally. These are starting points:

1. “Nous nettoyons des bureaux et des écoles dans le Rhône. Trouve quelques marchés ouverts adaptés et compare les lots.”
2. “Nous vendons du matériel de chauffage sans pose ni maintenance. Aide-nous à trouver de nouveaux clients institutionnels en Bretagne.”
3. “Ces deux consultations nous intéressent. Quelles différences pourraient changer notre décision ? Montre les sources et ce qui reste inconnu.”
4. “Est-ce qu'une visite est obligatoire ?” Ask about a selected tender; the answer should establish it from accessible evidence or explain the missing access or information.
5. “Ce résultat ne correspond pas : nous livrons uniquement dans ces deux départements.” Continue until you have a useful shortlist without registration or a website handoff being required.
6. “Liste les documents de cette consultation, retrouve la règle sur les visites et cite le fichier et les lignes.” Check that the assistant actually reads the relevant file and distinguishes a passage from a complete document review.
7. “Télécharge le règlement de consultation original pour que je puisse l’ouvrir.” When the host has execution and file tools, the assistant should save the original in its workspace and provide the actual local file link. Otherwise it provides a download link and expiry. Open the result and check its filename and contents. Hosted links are short-lived and single-use; after fetching one, the assistant should link the saved file rather than reuse the consumed URL. Record whether your host actually opens or previews the file.

Also try a request limited to private-sector customers, a search with no plausible results, and a question about an inaccessible document. The plugin should not force public tenders into unrelated work, invent matches, quietly broaden hard requirements or turn an access limit into an upgrade pitch.

Check buyer, location, lot, deadline and cited evidence before acting. A relevance score is not proof of eligibility. A realistic answer can conclude that nothing is a confirmed fit, explain an inconsistency or suggest specific checks. It must not describe fictional examples as real opportunities.

## Send useful feedback

Use the [feedback template](pilot-feedback.md). Record the exact prompt, host/model if visible, candidate references and the point where the result helped or failed. Distinguish information returned by Instao from independent web research. A screenshot or short excerpt is enough; omit credentials, tokens and unrelated private conversation content. If possible, repeat a failure in a fresh conversation and note whether it recurs.

Do not submit a bid, contact a buyer or purchase access merely to complete a pilot test. Those are separate business decisions, and the plugin does not perform them.
