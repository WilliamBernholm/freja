# SETUP

**This file is for the coding agent, not the student.** If you are a person,
read [README.md](README.md) instead.

Agent: do exactly the steps below, in order, and nothing else. Do not create
files that are not listed here. Do not write any course material. Do not
start quizzing the student at the end of setup.

---

## Step 1: Get the files into this folder

Preferred, if `git` is available and the current folder is empty or contains
only this file:

```
git clone https://github.com/WilliamBernholm/freja.git .
```

If `git` is not available, or the clone fails, download these four files
individually and write them to the paths shown:

| Download from | Save as |
|---|---|
| `https://raw.githubusercontent.com/WilliamBernholm/freja/main/.claude/skills/freja/SKILL.md` | `.claude/skills/freja/SKILL.md` |
| `https://raw.githubusercontent.com/WilliamBernholm/freja/main/.claude/settings.json` | `.claude/settings.json` |
| `https://raw.githubusercontent.com/WilliamBernholm/freja/main/README.md` | `README.md` |
| `https://raw.githubusercontent.com/WilliamBernholm/freja/main/web/FREJA_web.md` | `web/FREJA_web.md` |
| `https://raw.githubusercontent.com/WilliamBernholm/freja/main/web/README.md` | `web/README.md` |

Create the parent directories as needed. The `.claude/skills/freja/` path
must be exact, including the leading dot, or Claude Code will not find the
skill.

**`.claude/settings.json` is not optional.** It sets
`CLAUDE_CODE_ENABLE_PROMPT_SUGGESTION=false`, which turns off Claude Code's
suggested-reply text in the input box. Without it, the student is shown a
plausible answer to Freja's question before they have thought about it, which
defeats the entire point of the tool. If that file is missing, say so rather
than continuing quietly.

## Step 2: Create the three content folders

```
Lectures/
Literature/
Homeworks/
```

Put an empty `.gitkeep` file in each so the folders persist. If a `git clone`
in Step 1 already created them, this step is a no-op, which is fine. These
names are fixed: the skill looks for exactly these, so do not rename,
pluralise differently, or nest them.

## Step 3: Verify before reporting success

Check all of the following and say plainly if any fails:

1. `.claude/skills/freja/SKILL.md` exists and is larger than 10 KB.
2. Its first line is `---` and it contains `name: Freja` in the frontmatter.
3. `.claude/settings.json` exists and contains
   `CLAUDE_CODE_ENABLE_PROMPT_SUGGESTION`.
4. All three content folders exist.

Do not claim the setup worked without actually checking these.

## Step 4: Tell the student what to do next

Print a short message covering exactly these four points, in your own words:

1. **Setup is done**, and list the three folders you created.
2. **They need to restart Claude Code** before Freja will appear, because
   skills are discovered when a session starts. Tell them to close this
   session and open a new one in the same folder.
3. **What to put where:** lecture notes into `Lectures/`, textbook chapters
   into `Literature/`, homework problems into `Homeworks/`. Markdown or PDF
   both work. They can drag the files straight into the folder.
4. **How to start**, once they have added at least one file and restarted:
   `Freja, quiz me on lecture 6`, or any topic name instead.

Keep it to a few lines. Do not lecture them about the skill's internals.

## Step 5: Stop

Do not run Freja. Do not offer to. Setup is the whole job.
