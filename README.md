# Jurabibliotek

Review, draft and edit Danish legal documents against current Danish legislation from
[Jurabibliotek](https://www.jurabibliotek.dk), in Claude for Word, claude.ai, Cowork and Claude Code.

## What it contains

- **Jurabibliotek connector** (`.mcp.json`): the remote MCP server at `https://mcp.jurabibliotek.dk/mcp`, which gives
  Claude search and retrieval tools for current Danish legislation.
- **`jurabibliotek-legal-documents` skill**: tells Claude to check legal documents against the statute through the
  connector whenever you review, draft or edit a contract or other legal document, even when you don't mention
  Jurabibliotek. It also makes Claude follow Jurabibliotek's privacy rules and end every answer with linked sources.

## Use it

1. Add the plugin from **Customize > Plugins**.
2. Open the plugin's **Connectors** tab and connect Jurabibliotek. You sign in on jurabibliotek.dk, and only accounts
   with a valid Jurabibliotek subscription get access.
3. In Claude for Word, open a document and ask, for example, "Gennemgå denne ansættelseskontrakt" or "Is the notice
   period in clause 7 lawful?". Claude searches the legislation, reads the relevant sections, and ends its answer with
   a list of the law sections it relied on, linked to jurabibliotek.dk.

You can also invoke the skill directly by typing `/jurabibliotek-legal-documents` in the chat.

## Data

The plugin sends only generic legal questions in Danish to Jurabibliotek, such as "Kan en arbejdsgiver opsige en
funktionær uden varsel?". The skill instructs Claude never to include names, CPR or CVR numbers, addresses, company
names, amounts, dates or excerpts from your documents in a query. Your document stays in your Claude conversation, and
Claude applies the retrieved legislation to it there. The plugin stores nothing itself.

Claude's answers are not legal advice. Have a qualified professional review anything you sign or file.

## Packaging for OpenAI

`plugin.json` and `mcp.json` are the OpenAI package manifests. `.claude-plugin/plugin.json` and `.mcp.json` are the
Claude ones. Build the ZIP for the OpenAI plugin submission portal with:

```sh
zip -r jurabibliotek-openai.zip plugin.json mcp.json skills assets -x '*.DS_Store'
```
