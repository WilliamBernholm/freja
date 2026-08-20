# Freja

**A study tutor that quizzes you on your own course material.**

Freja does not explain topics at you and does not do your homework. It asks
you one question at a time about the lecture notes, textbook chapters, and
problems you give it, works out what you actually understand, and tells you
where the gaps are.

It runs through five stages, in order:

| Stage | What it asks |
|---|---|
| **Conceptual** | What is this, in your own words? |
| **Procedural** | What are the steps? |
| **Predictive** | What happens if...? |
| **Corrective** | Here is a formula with one error in it. Find it. |
| **Transfer** | Same technique, new situation. |

---

## This is a work in progress, and feedback is wanted

Freja is new and still being tested. It works well on individual lecture
notes, but it has not been through a full course yet, and there are rough
edges.

**The bad feedback is the useful kind.** If a question was confusing, if it
quizzed you on something your notes never actually said, if the setup did not
work, or if it simply was not helpful, please say so. Open an issue on this
repo, or tell me directly if you are on one of my courses.

What helps most is a concrete example: what you asked, what it said, and what
you expected instead. "It got the notation wrong in lecture 6" is worth ten
times more than "it was a bit off".

---

## Setup, in four steps

You need **[Claude Code](https://claude.com/claude-code)** installed. Nothing
else.

### 1. Make an empty folder

Anywhere you like. Call it something like `MyCourse`. This is where your
study material will live.

### 2. Open Claude Code in that folder

Open a terminal in the folder and run:

```bash
claude
```

### 3. Paste this in, exactly as it is

```
Set this folder up for Freja, my study tutor.
Fetch https://raw.githubusercontent.com/WilliamBernholm/freja/main/SETUP.md
and follow it exactly. Do not do anything it does not ask for.
```

Claude downloads Freja, puts it where it needs to go, and creates your
folders. It takes under a minute. If it asks permission to fetch a URL or
write files, say yes.

One of the files it creates is `.claude/settings.json`, which switches off
Claude Code's suggested-reply text. **Leave it there.** Without it, Claude
Code shows you a plausible answer in the input box before you have thought
about the question, which defeats the whole point of being quizzed.

### 4. Restart Claude Code

Close the session and open a new one in the same folder. **This step is not
optional.** Claude Code only looks for skills when a session starts, so Freja
will not exist until you restart.

---

## Adding your course material

After setup you will have three folders. Drag your files in:

```
Lectures/      lecture notes, one file per lecture
Literature/    textbook chapters, one file per chapter
Homeworks/     problem sets, exam papers, assignments
```

**Markdown (`.md`) works best. PDFs also work.** Freja reads whatever is
there, so you do not need all three folders filled. One lecture note is
enough to start.

Name files so you can recognise them. If a filename contains the lecture
number or the topic, Freja will find it when you ask by number or by name.

---

## Using it

Once you have added at least one file and restarted, just ask:

```
Freja, quiz me on lecture 6
```

Other things that work:

- `Freja, quiz me on the SVD chapter`
- `Freja, quiz me on compressed sensing`
- `Freja, run the mastery learning loop on HW1 problem 3`
- `Freja, quiz me again` for a second pass with different questions

If you do not name anything specific, it will ask you what you want to work
on.

**While a session is running:**

- Answer in your own words. Rough and half-formed is fine, that is the point.
- Stuck? Say so. It gives hints first, and only breaks things down further
  if you are still stuck.
- Small side questions are fine ("what does RAAN stand for?"). It answers
  briefly and carries on.
- Want to stop early? Say `let's stop` and you still get the summary of how
  far you got.

---

## What it will not do

Freja is a study tool, not an answer service.

- It will not write your homework, produce a full derivation, or hand you a
  solution you could submit. Ask outright and it will decline and offer a
  hint instead.
- It will not answer from general knowledge and pass it off as your course.
  If something is not in the material you gave it, it says so.
- It uses **your course's notation**, not the textbook-standard version. If
  your notes write `H` where most books write `h`, so does Freja.

If your course has its own rules about AI use, put them in your lecture notes
and Freja will follow those instead of these defaults.

---

## Prefer ChatGPT?

There is a version that works in plain web chat, in [`chatgpt/`](chatgpt/).
No installation at all: paste one file into ChatGPT, upload a lecture note,
and go. It is slightly less capable, because it cannot search your folders
the way Claude Code can, but it works on a free account.

See [`chatgpt/README.md`](chatgpt/README.md).

---

## If something goes wrong

**Grey text appears in the input box suggesting an answer.**
Then `.claude/settings.json` is missing or was deleted. Recreate it with
exactly this, and restart Claude Code:

```json
{
  "env": { "CLAUDE_CODE_ENABLE_PROMPT_SUGGESTION": "false" }
}
```

**"Workspace trust needed", but no prompt appears.**
Claude Code asks you to trust a folder the first time you open it. If the
banner appears with no dialog behind it, close the folder and open it again.
Failing that, start Claude Code from a terminal inside the folder, which asks
the same question as a plain yes/no you cannot miss.

**"Freja" does nothing / Claude does not recognise it.**
You almost certainly skipped step 4. Restart Claude Code in the same folder.
If it still does not work, check that the file
`.claude/skills/freja/SKILL.md` exists, with that exact path including the
leading dot.

**It says it cannot find my lecture.**
Check the file is actually inside `Lectures/` and not one level up. Try
naming it by filename instead of by topic.

**It starts quizzing me on the wrong thing.**
Say so. It will re-resolve. Naming the file directly is the reliable fix.

**It is quizzing me on things my notes do not cover.**
Tell it. That is a real bug, not you misunderstanding, and it is worth
reporting.

---

## Credits

Freja is descended from **MiLLy**, the Mastery Learning Loop agent by Ric
Glassey (KTH), via a course-specific adaptation that was later made
course-agnostic. See [Pedagogical Agents](https://github.com/Pedagogical-Agents).

MIT licensed. Use it, change it, share it.
