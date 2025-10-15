# SassyShell (sassysh)

Your sassy, command-line tutor that remembers the commands you keep forgetting.

---



### Why I Built This

Like a lot of developers, I found myself constantly switching contexts to ask an LLM for the same simple shell commands over and over. `tar` flags, `find` syntax, `awk` one-liners... I wasn't *learning* them, I was just outsourcing my memory. It felt like a bad habit.

Instead of just trying to memorize everything, I thought: what if a tool could track my bad habits and help me internalize the patterns?

So, I built **SassyShell**. It's not just another "GPT in the terminal." It's a CLI sidekick that:
1.  Uses a local TF-IDF search to find similar commands you've asked for in the past.
2.  Feeds that history to an LLM to provide context-aware answers.
3.  Gives you the command you need, along with a bit of sarcastic feedback based on how often you forget it.

It's a project born from turning my own laziness into data. It's designed to mock you into getting better.

### Features

* **Personalized Memory:** Remembers the *types* of commands you struggle with and uses that history to inform its responses.
* **Sassy Feedback:** The more you ask for the same thing, the more it will gently (or not so gently) remind you.
* **Platform Aware:** Automatically detects if you're on Linux, macOS, or Windows and asks the LLM for the correct shell syntax (`bash`/`zsh` vs. PowerShell).
* **Lightweight & Fast:** Uses a fast local similarity search before ever calling an LLM.

<img src="assets/render1760508770224.gif" alt="Sassyshell Demo" width="800" />

### Installation

The recommended way to install SassyShell is with `pipx` or `uvx`. This installs it in an isolated environment so it doesn't clutter your global packages.

```bash
pipx install sassyshell
```

You can install `pipx` using:
```bash
pip install --user pipx
```

Or, if you use `uvx`:

```bash
uvx sassyshell
```

### Quickstart

#### 1. One-Time Setup

Before you can use the tool, you need to run the setup wizard to configure your LLM provider and API key. Your credentials are saved locally in `~/.config/sassyshell/.env`.

```bash
sassysh setup
```

You'll be guided through selecting a provider (OpenAI, Google, etc.) and entering your API key.

#### 2. Ask a Question

Use the `ask` command to ask for help.

```bash
sassysh ask "how to find all files modified in the last 24 hours"
```

**Example Interaction:**

```
$ sassysh ask "how to add changes to my last git commit without a new one"

Looks like you're having trouble with your Git commits again! You can add your new changes using:

git commit --amend --no-edit
```

### License

This project is licensed under the MIT License.