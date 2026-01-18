---
title: "The Tools That Stuck"
date: 2025-11-25
description: "After weeks with modern CLI tools, which ones earned permanent spots? The survivors and why they matter."
slug: "the-tools-that-stuck"
showDate: true
showReadingTime: true
---

A month into the [Framework 13](/updates/framework-13-sovereign-laptop/) experiment. Time to take stock.

Which of the modern CLI tools actually stuck? Which ones am I reaching for daily?

---

## The Survivors

These earned permanent spots in muscle memory:

**fish** for interactive shell. The autocompletions alone justify it. Tab through command history with context. Syntax highlighting as you type. Sane defaults without configuration sprawl.

**yazi** for file management. Terminal file manager that doesn't feel like punishment. Image previews. Bulk operations. Keyboard-driven but not hostile.

**ripgrep (rg)** for searching. grep, but fast. Really fast. Respects .gitignore by default. The tool I reach for many times a day.

**fd** for finding files. find, but with human syntax. `fd "\.md$"` instead of `find . -name "*.md"`. Small thing. Matters.

**bat** for viewing files. cat with syntax highlighting and git integration. See what changed at a glance.

**eza** for listing. ls, but with git status, better colors, sensible defaults. Tree view built in.

**zoxide** for navigation. cd that learns. `z node0` takes me to /home/cps/node0 because that's where I go when I type those letters.

**LazyVim** for editing. Neovim with opinions. Fast, configured, extensible. Replaced years of VSCode muscle memory in weeks.

**lazygit** for version control. TUI for git that makes complex operations visible. Interactive rebasing without fear.

---

## The Pattern

Notice something? These tools share traits:

**Speed.** Written in Rust, Go, or well-optimized C. No startup lag. No waiting.

**Defaults.** Sane out of the box. Minimal configuration needed to be useful.

**Composability.** They play well with others. Pipe ripgrep into bat. Use fd with xargs. Unix philosophy, modern execution.

**Respect for existing knowledge.** fd feels like find. rg feels like grep. They're better, not alien.

---

## What Didn't Stick

Some experiments didn't survive:

**Helix** (editor). Tried it. Interesting modal model. But LazyVim's plugin ecosystem won.

**nnn** (file manager). Fast and minimal. But yazi's previews and operations were worth the extra weight.

**broot** (file tree). Good, but zoxide + fd covered the use cases.

Not failures. Just not winners for my workflow.

---

## The Stack Now

```
Shell:     fish + fisher + fzf
Editor:    LazyVim (Neovim)
Files:     yazi + eza + fd
Search:    ripgrep + fzf
View:      bat
Navigate:  zoxide
Git:       lazygit + git-delta
Monitor:   btop
```

Everything plays together. Fish completions know about my tools. Fzf integrates with everything. LazyVim has Telescope for fuzzy finding.

It's not about individual tools. It's about the system they form.

---

## Why It Matters

This isn't tool fetishism. It's about removing friction.

Every time I don't wait for a slow tool, that's cognitive space preserved. Every time a command does what I expect, that's flow maintained. Every time I don't have to remember arcane syntax, that's energy saved for the actual work.

The tools that stuck are the ones that get out of the way.

---

## Sovereignty Connection

All of these are open source. All run locally. None phone home. None require accounts.

If any of them disappeared tomorrow, I could fork them, replace them, or adapt. No vendor lock-in. No subscription. No asking permission.

The tools serve the work. The work is sovereign.

---

*Part 3 of the Node0 build series. Next: [The Storage Foundation](/updates/the-storage-foundation/), deploying the storage layer that everything builds on.*
