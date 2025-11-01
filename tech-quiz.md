# Tech Vocabulary Quiz

**Description:** Interactive quiz to learn technical terminology in plain English

**Usage:**
- `/tech-quiz` - Start a quiz session
- `/tech-quiz stats` - View your progress
- `/tech-quiz [topic]` - Quiz on specific topic (git, nextjs, terminal, react, general)

---

## Instructions

When the user invokes this skill:

1. **Load terms database** from `~/.claude/skills/quiz-terms.json`

2. **Load progress** from `~/.claude/quiz-progress.json` (create if doesn't exist)

3. **Select quiz mode:**
   - If user said `/tech-quiz stats` → Show statistics
   - If user said `/tech-quiz [topic]` → Quiz on that topic only
   - Otherwise → Quiz on random terms from all topics

4. **Quiz format:**

   **IMPORTANT: Randomize answer positions!**
   - Shuffle the 4 choices before displaying
   - Track which letter (A-D) has the correct answer after shuffling
   - Don't always put correct answer in same position

   ```
   ==========================================
   📚 Tech Vocabulary Quiz
   ==========================================

   Question X of 5

   Term: [TERM]

   What does this mean?

     A) [choice 1] (shuffled)
     B) [choice 2] (shuffled)
     C) [choice 3] (shuffled)
     D) [choice 4] (shuffled)

   Your answer (A-D or 'skip'): (make this line bold with \033[1m)
   ```

5. **After answer - Use color codes:**

   **Correct answer:**
   ```
   ✓ Correct! 🎉 (in green)

   [TERM] = [short definition] (in cyan/blue)

   📖 Full explanation: (in yellow)
   [Full definition text]
   [Analogy]

   💡 Real example: (in yellow)
   [Example text]
   ```

   **Wrong answer:**
   ```
   ✗ Not quite (in red)

   Correct answer: [LETTER]) [correct choice] (in green)

   📖 Full explanation: (in yellow)
   [Full definition, analogy, example]
   ```

   **Color codes to use:**
   - Green: \033[92m (correct answers)
   - Red: \033[91m (incorrect)
   - Yellow: \033[93m (explanations/examples)
   - Cyan: \033[96m (term definitions)
   - Reset: \033[0m (end color)

6. **Update progress:**
   - Track correct/incorrect for each term
   - Update mastery level (0-5 scale)
   - Save to `~/.claude/quiz-progress.json`

7. **Quiz length:** 5 questions per session (quick and frequent)

8. **Progress tracking:**
   ```json
   {
     "terms": {
       "Branch": {
         "correct": 5,
         "incorrect": 1,
         "mastery": 4,
         "lastSeen": "2025-11-01",
         "category": "git"
       }
     },
     "stats": {
       "totalQuestions": 50,
       "totalCorrect": 42,
       "streak": 3,
       "lastQuiz": "2025-11-01"
     }
   }
   ```

9. **Mastery levels:**
   - 0: Never seen
   - 1-2: Learning (needs review)
   - 3-4: Familiar (occasional review)
   - 5: Mastered (rare review)

10. **Smart selection:**
    - Prioritize terms with low mastery
    - Mix in occasional mastered terms for reinforcement
    - Avoid recently quizzed terms (unless explicitly requested)

## Stats Display

When showing stats:
```
==========================================
📊 Your Quiz Statistics
==========================================

Overall Progress:
  Total Questions: 50
  Correct: 42 (84%)
  Current Streak: 3 sessions

Mastery by Category:
  Git:      ████████░░ 8/10 mastered
  Next.js:  ██████░░░░ 3/5 mastered
  Terminal: ██████████ 6/6 mastered
  React:    ████░░░░░░ 2/4 mastered
  General:  ███████░░░ 3/4 mastered

Terms to Review (mastery < 3):
  - API Route (mastery: 1)
  - useEffect (mastery: 2)
  - Rebase (mastery: 2)

Keep going! 🎯
```

## Notes

- Keep quizzes SHORT (5 questions max)
- Use PLAIN ENGLISH in all explanations
- Always show the ANALOGY after answering
- Make it FUN and encouraging
- Track progress automatically

---

**Created:** 2025-11-01
**Location:** Global skill (works in all projects)
**Progress File:** `~/.claude/quiz-progress.json`
**Terms File:** `~/.claude/skills/quiz-terms.json`
