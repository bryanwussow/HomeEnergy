# How I Can Use Claude in This VS Code Context

Reference notes on Claude Code's session model inside the VS Code extension — written 2026-10-05 after this came up mid-conversation in a long-running session originally titled "geothermal-loop-design-prompt." Sourced from the official docs at `code.claude.com/docs/en/vs-code.md` and `.../sessions.md`.

## The core unit: session, tied to a project folder

The **project folder** (the directory open in VS Code) is the container. It determines which `CLAUDE.md`, git repo, and memory apply. Within one project folder, you can run any number of independent **sessions** — each a separate saved conversation with its own history and context. So the relationship is: one folder → many possible sessions, not one folder → one chat.

## Why a session's tab/pane gets named after an early topic

New sessions get an **AI-generated title based on your first message** in that session — not the file that happened to be open, and not anything you set manually (unless you rename it yourself). That title is static for the life of the session; it does not update as the conversation's topic drifts. This is why a long conversation that started on one topic (e.g., a specific file) keeps that name even after moving on to cover unrelated things.

## Multiple concurrent sessions: yes, no fixed limit

You can have several independent sessions open at once in the same project. Each keeps its own transcript, saved locally and tied to the project directory.

## Opening the project and starting or resuming a session

1. Open the project folder in VS Code.
2. Open the Claude Code panel — the spark icon (top-right of the editor, bottom-right status bar, or the Activity Bar on the left).
3. Clicking the Activity Bar spark icon opens the **sessions list** — but note: a brand-new, empty session won't appear there until it has at least one message sent and its transcript is persisted to disk. The list only shows sessions that already have content.
4. **To resume** an existing session: click it in that sessions list — full message history restores.
5. **To start a brand-new session** (the list itself doesn't have a visible "+ New session" button for this):
   - Press **`Ctrl+Shift+Esc`** (Windows/Linux) or **`Cmd+Shift+Esc`** (Mac) — opens a fresh conversation as a new tab in your preferred location.
   - Or, Command Palette (`Ctrl+Shift+P`) → type **"Claude Code: Open in New Tab"** (or "Open in New Window" for a separate window) → Enter.
   - `Ctrl+N`/`Cmd+N` also works as "New Conversation," but it's disabled by default — requires setting `claudeCode.enableNewConversationShortcut: true` in VS Code settings.

Once you send the first message in a new session, it gets its own AI-generated title and shows up in the sessions list from then on.

## Open gap in the official docs

The docs confirm you can "start a new one" from the sessions list, but don't document a specific visible button/icon for it inside that view — the keyboard shortcut or Command Palette route above are the documented ways.
