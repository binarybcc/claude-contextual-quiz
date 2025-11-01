# Claude Contextual Quiz

**Learn technical vocabulary naturally while you code.**

## The Problem

Traditional flashcards don't work for learning technical terminology because they're disconnected from real work. You memorize a term, then forget it immediately because you've never used it in context.

## The Solution

**Contextual learning** - Quiz yourself on technical terms *right after using them in real work*.

When you finish using `git branch` in your project, Claude pauses and asks: "What does 'branch' mean?" You answer, get immediate feedback with analogies and examples, and the term sticks because you just experienced it.

## How It Works

This is a **global skill for Claude Code** that integrates vocabulary quizzes into your natural workflow:

1. **Work on your project** - Use git, write React code, run terminal commands
2. **Natural pause** - Between tasks, Claude asks: "Quick quiz?"
3. **Answer 5 questions** - About terms you just used or will use soon
4. **Learn through context** - Definitions, analogies, and real examples
5. **Track progress** - Spaced repetition ensures you master terms over time

### Example Quiz Session

```
==========================================
📚 Tech Vocabulary Quiz
==========================================

Question 1 of 5

Term: Branch

What does this mean?

  A) The main version of your code
  B) A parallel timeline for trying changes safely
  C) A way to delete code
  D) A save point in your code

Your answer (A-D or 'skip'): B

✓ Correct! 🎉

Branch = A parallel timeline where you can try changes without affecting the main code

📖 Full explanation:
A branch lets you experiment with code changes in a separate timeline. If things go wrong,
you can simply switch back to the main branch. Think of it like a "Choose Your Own Adventure"
book - you can always go back to the main story.

💡 Real example:
git checkout -b feature/search creates a new branch called "feature/search"
```

## Installation

1. Copy `quiz-terms.json` to `~/.claude/skills/quiz-terms.json`
2. Copy `tech-quiz.md` to `~/.claude/skills/tech-quiz.md`
3. Create progress tracker: `touch ~/.claude/quiz-progress.json`

## Usage

**In any Claude Code session:**

```bash
/tech-quiz              # Random 5-question quiz from all categories
/tech-quiz git          # Quiz specifically on git terms
/tech-quiz nextjs       # Quiz on Next.js concepts
/tech-quiz terminal     # Quiz on terminal commands
/tech-quiz react        # Quiz on React concepts
/tech-quiz general      # General programming terms
/tech-quiz stats        # View your progress and mastery levels
```

**Or let Claude integrate it naturally:**
When there's a natural pause in your work, Claude will offer a quick quiz on relevant terms.

## What's Included

**35+ technical terms across 5 categories:**

- **Git** (8 terms): Branch, Commit, Merge, Pull, Push, Origin, Rebase, Clone
- **Next.js** (5 terms): Server Component, Client Component, Route, API Route, Middleware
- **Terminal** (6 terms): ls, cd, pwd, mkdir, rm, grep
- **React** (4 terms): useState, useEffect, Props, Component
- **General** (4 terms): API, JSON, Environment Variable, Cache

Each term includes:
- ✅ Plain-English definition
- ✅ Real code example
- ✅ Relatable analogy
- ✅ Multiple choice question with shuffled answers

## Features

- 🎯 **Smart selection** - Prioritizes terms you struggle with
- 📊 **Progress tracking** - Mastery levels 0-5 with spaced repetition
- 🎨 **Beautiful formatting** - Color-coded terminal output
- 🔄 **Randomized answers** - Prevents pattern memorization
- 📚 **Comprehensive explanations** - Learn why, not just what
- 🌍 **Global across all projects** - One quiz system for all your work

## Why This Works

**Traditional approach:**
1. Read documentation → 2. Forget it → 3. Look it up again → 4. Repeat

**Contextual learning:**
1. Use `git branch` in your project → 2. Quiz asks "What is a branch?" → 3. You remember because you *just used it*

The difference is context. When you learn a term immediately after using it, your brain creates stronger associations.

## Expanding the System

**Want to add your own terms?** Edit `quiz-terms.json`:

```json
{
  "your-category": [
    {
      "term": "Your Term",
      "definition": "Plain English explanation",
      "example": "Real code example",
      "analogy": "Relatable comparison",
      "choices": [
        "Wrong answer 1",
        "Correct answer",
        "Wrong answer 2",
        "Wrong answer 3"
      ],
      "correct": 1
    }
  ]
}
```

**Works for any subject:**
- Law school (torts, contracts, constitutional law)
- Mathematics (calculus, geometry, statistics)
- Languages (Spanish, French, Mandarin)
- Medicine (anatomy, pharmacology, diagnostics)
- Finance (derivatives, accounting, economics)

## The Bigger Vision

This started as a way to learn git commands while building a PDF library. But the pattern is universal:

**What if every learning tool worked this way?**

Imagine medical students quizzed on anatomy terms *while examining a patient simulation*. Law students quizzed on precedents *while writing a brief*. Spanish learners quizzed on vocabulary *while having a conversation*.

Context is everything. This is a proof of concept that it works.

## Prior Art Notice

This project is open sourced under MIT license to establish prior art and prevent patent trolling by educational technology companies. The concept of "contextual vocabulary quizzing during workflow pauses" is hereby released to the public domain for anyone to implement.

## Contributing

Want to add more terms? Improve the quiz format? Add new categories? Pull requests welcome!

**Ideas for expansion:**
- Import terms from documentation automatically
- Track which terms are used together (concept clustering)
- Difficulty levels (beginner, intermediate, advanced)
- Team leaderboards for collaborative learning
- Export progress to Anki or other spaced repetition tools

## License

MIT License - See LICENSE file for details.

## Credits

Built accidentally while learning to code with Claude Code. Turned out to be too useful not to share.

**Created:** November 1, 2025
**Built with:** Claude Code (Anthropic)
**Powered by:** The realization that flashcards suck and context matters

---

*"The best time to learn what a git branch is... is right after you create one."*
