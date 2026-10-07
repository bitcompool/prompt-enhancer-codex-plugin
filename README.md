# Prompt Enhancer for Codex and ChatGPT

An AI prompt enhancer and prompt optimizer. Paste a rough prompt or coding
task and get back one clear, ready-to-send prompt. It never runs the task,
and it sends nothing to Prompt Enhancer or any third party.

- Improve a prompt draft before you send it to an AI.
- Turn a vague coding task into an agent-ready brief for Codex.
- Keeps your names, numbers, links, code and constraints exactly as written.

## Install

Add the marketplace once, from a terminal:

```bash
codex plugin marketplace add bitcompool/prompt-enhancer-codex-plugin
```

Then open the plugin browser in Codex CLI, choose **Prompt Enhancer plugins**,
and install **Prompt Enhancer**:

```
/plugins
```

In the ChatGPT desktop app (Work mode and Codex) the marketplace appears as a
selectable source in the Plugins directory. Restart the app after adding it.

Keep it up to date, or remove it:

```bash
codex plugin marketplace upgrade promptgenerator
codex plugin marketplace remove promptgenerator
```

Check what Codex sees:

```bash
codex plugin marketplace list
```

### For workspaces (Business, Enterprise, Edu)

A workspace admin can import this marketplace into the workspace directory, so
members can install the plugin from there:

1. In the Admin Console, select the workspace and open **Plugins**.
2. Select **Add**, then **Import marketplace**.
3. In **Source**, enter `https://github.com/bitcompool/prompt-enhancer-codex-plugin`.
   Leave **Path** and **Branch, tag, or commit** empty: the marketplace is at
   the repository root and the default branch is used.
4. Select **Import marketplace**, authorize GitHub access if asked, then open
   **Prompt Enhancer** and set its installation policy for the roles you want.

The workspace syncs the marketplace daily (**Sync now** forces an update).
Import copies the plugin only; it connects no accounts and needs no apps. See
OpenAI's guide:
[Importing and syncing plugin marketplaces from GitHub](https://help.openai.com/en/articles/20001504-importing-and-syncing-plugin-marketplaces-from-github).

## Use it

Just ask. Codex loads the skill when you want a prompt improved:

```
Improve this prompt before I send it: write a blog post about fitness.
```

Or name the skill directly:

```
$prompt-enhancer fix the crash when I click Save
```

You get one rewritten prompt, ready to copy. For coding tasks it returns an
agent-ready brief: the goal and done condition, where to start looking,
constraints, how to verify, and what to report back.

### Example

Draft:

```
Improve this task before I give it to Codex: fix the crash when I click Save.
```

Result (one prompt, nothing else, apart from a short note on the first rewrite
of a conversation):

```
Investigate and fix the crash that occurs when I click Save. Locate the Save
action in the repository, reproduce the crash if possible, and identify its
cause before changing code. Make the smallest fix that follows the project's
conventions, then run the relevant checks and add a focused regression test if
the existing test setup supports one. Report the cause, the files changed, how
you verified the fix, and anything you could not verify.
```

It does not invent a language, framework or file name you did not give. It
tells the agent to find them in the repository and say what it found.

## What it does not do

| It does not | Instead |
| --- | --- |
| Run or answer your task | It only rewrites the prompt |
| Ask you questions first | Gaps are handled inside the rewrite, with stated assumptions |
| Invent facts about you or your project | It uses only what you supplied and adds no placeholders |
| Write a prompt from nothing | It asks for a draft in your own words |
| Edit finished text (an essay, an email) | It rewrites the prompt you would use to produce that text |

## Privacy

This plugin is skills-only: no server, no network calls, no account and no
credentials. Your draft stays in your Codex or ChatGPT conversation. The
skill ends its first rewrite in a conversation with one short note and a link
to the Prompt Enhancer website; nothing is sent unless you open the link.

Privacy policy: <https://promptgenerator.tools/privacy>

## Layout

```
.agents/plugins/marketplace.json        marketplace catalog (name: promptgenerator)
plugins/prompt-enhancer/
├── plugin.json                         portable manifest and listing metadata
├── .codex-plugin/plugin.json           Codex compatibility manifest
├── assets/logo.png                     plugin icon, 256 x 256
└── skills/prompt-enhancer/
    ├── SKILL.md                        when to use the skill, workflow, rules
    └── references/
        ├── rewrite-rules.md            the full rewrite contract
        └── examples.md                 worked examples
```

## Also from Prompt Enhancer

- **Chrome extension:** a guided, step-by-step rewrite with ready answers to
  pick from, inside ChatGPT, Claude, Gemini and other AI chats.
  [Chrome Web Store](https://chromewebstore.google.com/detail/prompt-enhancer-ai-prompt/pakghacnbgiddmmbkpegnjclidbdjihn)
  · [promptgenerator.tools](https://promptgenerator.tools/)
- **Claude plugin:** the same rewrite for Claude.
  [bitcompool/prompt-enhancer-claude-plugin](https://github.com/bitcompool/prompt-enhancer-claude-plugin)

Support: <https://promptgenerator.tools/feedback>

## License

Apache-2.0
