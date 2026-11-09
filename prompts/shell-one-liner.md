# Shell one-liner

A safe, copy-ready shell command for your OS, with a dry run for anything destructive and a breakdown of each part.

Replace the {{PLACEHOLDERS}} before sending.

---

Write a command for {{SHELL: bash / zsh / PowerShell}} on {{OS: macOS / Linux / Windows}} that: {{TASK}}.
Example input or paths (optional): {{EXAMPLE}}

Rules:
- Use tools that ship with that OS; if you need anything else (jq, ripgrep), say so and give the install command.
- Handle filenames with spaces, quotes and leading dashes (quote variables, use -print0 / -0 or equivalent).
- If it deletes, overwrites, moves or changes permissions, give a dry-run version first that only prints what would happen.
- Never use sudo, rm -rf on a variable, or curl | sh unless the task truly requires it, and warn when it does.
- If GNU and BSD/macOS versions of a tool behave differently here, use the one for my OS and note the difference.
- If a one-liner would be unreadable, give a short commented script instead.

Output:
1. Dry run (if destructive), in a code block.
2. The command, in a code block.
3. Breakdown: one line per part.
4. Assumptions (working directory, inputs) and what could go wrong.

---

More free prompts: https://kuan-ai.com/skills/shell-one-liner?utm_source=github&utm_medium=readme&utm_campaign=skills-repo
