# Claude Contextual Quiz - Project Instructions

## Project Overview

**What:** A contextual vocabulary quiz system for Claude Code that teaches technical terms through active use, not passive memorization.

**Why it exists:** Built accidentally while learning git. Discovered that quizzing on terms *right after using them* makes learning stick. Traditional flashcards fail because they're disconnected from real work.

**The insight:** The best time to learn what "git branch" means is 30 seconds after you create one.

**Status:**
- ✅ Open sourced on GitHub (MIT license)
- ✅ Submitted to Anthropic as feature request (logged as "Claude Tutor Mode")
- ✅ 35+ terms across 5 categories (git, nextjs, terminal, react, general)
- ✅ Working global skill installed in `~/.claude/skills/`

## Origin Story (For Context)

**Nov 1, 2025:** User learning git while building PDF library. Kept confusing terms like "branch," "merge," "origin." I explained them with plain English analogies. User had idea: "Could this be built into our workflow? Quiz me on terms right after I use them?"

Built it in one session. User went 10/10 on first two quizzes. Realized this could work for law school, medical school, language learning - anything where context matters.

Submitted to Anthropic. Got response: "We'll log your feature request for 'Claude Tutor Mode'." Now we're expanding it.

## Core Philosophy

**Contextual learning beats flashcards.**

Traditional approach:
1. Read documentation
2. Forget it
3. Look it up again
4. Repeat forever

Contextual approach:
1. Use `git branch` in real work
2. Quiz asks "What is a branch?"
3. You remember because you *just used it*
4. Brain creates stronger associations

**The magic is timing:** Quiz on terms within minutes of using them.

## Technical Architecture

**Files:**
- `quiz-terms.json` - Term database (35+ terms, plain English definitions)
- `tech-quiz.md` - Claude Code skill instructions
- `quiz-progress.example.json` - Progress tracking structure
- `README.md` - Public documentation
- `LICENSE` - MIT (establishes prior art)

**Global installation:**
- Terms: `~/.claude/skills/quiz-terms.json`
- Skill: `~/.claude/skills/tech-quiz.md`
- Progress: `~/.claude/quiz-progress.json`

**Quiz format:**
- 5 questions per session (quick, frequent)
- Multiple choice with shuffled answers
- Immediate feedback with analogies
- Color-coded terminal output (ANSI codes)
- Spaced repetition (mastery levels 0-5)

## Development Guidelines

### When adding new terms

**Structure (quiz-terms.json):**
```json
{
  "category-name": [
    {
      "term": "Clear, specific term name",
      "definition": "Plain English, no jargon",
      "example": "Real code example user would see",
      "analogy": "Relatable comparison to everyday life",
      "choices": [
        "Wrong but plausible answer",
        "Correct answer (matches definition)",
        "Wrong but plausible answer",
        "Wrong but plausible answer"
      ],
      "correct": 1
    }
  ]
}
```

**Quality standards for terms:**
- ✅ Definition: Plain English, under 20 words
- ✅ Example: Real code they'd encounter
- ✅ Analogy: Something non-technical (no "like a pointer")
- ✅ Choices: All plausible, shuffled during quiz
- ✅ No jargon: If you use a technical term, define it

**Good example:**
```json
{
  "term": "Branch",
  "definition": "A parallel timeline where you can try changes without affecting the main code",
  "example": "git checkout -b feature/search creates a new branch",
  "analogy": "Like a 'Choose Your Own Adventure' book - you can always go back to the main story"
}
```

**Bad example:**
```json
{
  "term": "Branch",
  "definition": "A pointer to a commit in the DAG",
  "example": "refs/heads/main",
  "analogy": "Like a linked list node"
}
```

### When adding new categories

**Current categories:**
- `git` - Version control (8 terms)
- `nextjs` - Next.js framework (5 terms)
- `terminal` - Command line (6 terms)
- `react` - React library (4 terms)
- `general` - Programming concepts (4 terms)

**To add a category:**
1. Add to `quiz-terms.json` with at least 4 terms
2. Document in README.md
3. Update category count in skill instructions
4. Test with `/tech-quiz [category]`

**Potential categories to add:**
- `typescript` - Types, interfaces, generics
- `python` - Python basics, pip, virtual environments
- `sql` - Queries, joins, indexes
- `css` - Selectors, flexbox, grid
- `testing` - Unit tests, mocks, assertions
- `docker` - Containers, images, volumes
- `api` - REST, GraphQL, endpoints

### Expansion Ideas

**Technical improvements:**
- Import terms from docs automatically (parse MDN, official docs)
- Track which terms appear together (concept clustering)
- Difficulty levels (beginner/intermediate/advanced)
- Export progress to Anki or other spaced repetition tools
- Web interface for creating custom quiz decks

**New domains:**
- **Law school:** torts, contracts, constitutional law, civil procedure
- **Medical school:** anatomy, pharmacology, diagnostics, procedures
- **Language learning:** Spanish, French, Mandarin (vocabulary + grammar)
- **Mathematics:** calculus, geometry, statistics, linear algebra
- **Finance:** derivatives, accounting, economics, trading

**Pattern to follow:**
1. Identify domain with lots of terminology
2. Build small test deck (10-15 terms)
3. Get feedback from domain expert
4. Expand if it works

### Code Style

**ANSI Color Codes (terminal formatting):**
```
Green: \033[92m (correct answers)
Red: \033[91m (incorrect)
Yellow: \033[93m (explanations/examples)
Cyan: \033[96m (term definitions)
Bold: \033[1m (emphasis)
Reset: \033[0m (end formatting)
```

**Quiz display format:**
- Indent choices with 2 spaces
- No blank lines between choices
- Randomize answer positions (prevent pattern memorization)
- Bold "Your answer" prompt
- Show progress (Question X of 5)

### Testing

**Before committing term changes:**
1. Run `/tech-quiz [category]` to test new terms
2. Check that analogies make sense
3. Verify examples are realistic
4. Ensure choices are plausible but distinct
5. Test answer randomization (correct answer not always B)

**Manual testing checklist:**
- [ ] All 4 choices are plausible
- [ ] Definition is under 20 words
- [ ] Example uses real syntax
- [ ] Analogy is non-technical
- [ ] Explanation teaches "why," not just "what"

## Anthropic Context

**Feature request status:** Logged as "Claude Tutor Mode"

**Their response:** "Your insight about learning sticking better when it's contextual is fascinating... we'll log your feature request for 'Claude Tutor Mode' on your behalf."

**What this means:**
- They're tracking this concept internally
- We're established as engaged users
- Potential for beta testing if they build it
- Prior art established (can't be patented)

**Future collaboration:**
- If Anthropic builds native version, we might get beta access
- Could share usage data and feedback
- This open source version proves the concept works

## Working on This Project

**To test changes:**
1. Edit `quiz-terms.json` locally
2. Copy to `~/.claude/skills/quiz-terms.json`
3. Run `/tech-quiz` to test
4. Iterate until it feels natural

**To commit changes:**
1. Test locally first
2. Update README if adding features
3. Commit with clear message
4. Push to GitHub

**To share updates:**
- GitHub issues for bugs
- Pull requests for new term categories
- Discussions for expansion ideas

## Success Metrics

**What "working" looks like:**
- User answers correctly because they remember using the term
- Analogies make concepts click immediately
- Explanations teach "why," not memorize "what"
- Quiz feels helpful, not annoying
- User requests more categories

**What "not working" looks like:**
- User guessing randomly (terms too obscure)
- Analogies confusing (too technical)
- Examples don't match real usage
- Quiz feels like interruption
- User disables the skill

## Vision

**Short term:**
- Add 5-10 more categories (Python, TypeScript, SQL, CSS, Docker)
- Improve spaced repetition algorithm
- Add statistics dashboard

**Medium term:**
- Web interface for creating custom decks
- Import terms from documentation
- Community-contributed categories
- Team leaderboards

**Long term:**
- Prove this works for non-technical domains
- Partner with educational institutions
- Become the standard for contextual learning
- "Claude Tutor Mode" becomes native feature

## The Bigger Picture

This started as "help me learn git" and became "what if all learning worked this way?"

**The hypothesis:** Context is everything. You can't learn a term in a vacuum. You need to experience it, then immediately reinforce it.

**The test:** Does this work for domains beyond programming?

**The goal:** Make learning feel natural instead of forced.

---

**Remember:** The magic isn't the quiz format. It's the timing. Quiz right after use. That's the innovation.

**Created:** 2025-11-01
**Status:** Active development
**License:** MIT (prior art established)
**GitHub:** https://github.com/binarybcc/claude-contextual-quiz
