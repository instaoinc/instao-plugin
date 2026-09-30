# Instao hosted pilot: tester guide

The pilot helps you discover and compare French public tenders from a conversation using Instao's production catalog. Start with a real business need, refine the results and ask what still needs checking. Searches, previews and available consultation files can be used without an Instao account.

Ask the assistant to inspect a consultation's files, cite numbered passages or retrieve an original document. Missing files and incomplete text extraction must remain explicit. Account linking is not needed for this pilot.

This is an early hosted pilot with a publicly installable package. It is not a published or officially recommended OpenAI directory plugin. Response preparation, saved company profiles, favorites, UI panels and proactive notifications are outside this version.

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
