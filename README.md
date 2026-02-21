# rank-problem-solutions

A vector function that ranks candidate solutions to a problem from best to worst.

## Purpose

When faced with a problem that has multiple proposed solutions, choosing the best path forward requires structured, consistent evaluation. This function formalizes that judgment — it accepts a problem and a set of candidate solutions, then produces a relative ranking by evaluating each solution across six core qualities.

## Input

The function accepts an object with two required fields:

- **`problem`** (string): The problem statement to solve. This can be any kind of challenge — a business problem, a technical question, a logistical puzzle, a strategic decision, or a personal dilemma. The problem anchors all evaluation; every solution is assessed in light of it.
- **`solutions`** (array of strings, minimum 2): The candidate solutions to rank. Each solution is a text description of a proposed answer, strategy, or approach to the problem.

### Example Input

```json
{
  "problem": "Our web application's page load time has increased from 2 seconds to 8 seconds over the past month, causing user drop-off.",
  "solutions": [
    "Implement lazy loading for images and defer non-critical JavaScript to reduce initial page weight.",
    "Rewrite the entire application in a faster programming language.",
    "Add a CDN for static assets and enable server-side caching for API responses.",
    "Tell users to upgrade their internet connection."
  ]
}
```

## Output

An array of numbers, one per solution, that sum to 1. Each number represents the relative ranking weight of the corresponding solution — higher values indicate better solutions. The output order matches the input order of the solutions array.

## What It Evaluates

The function evaluates solutions across six interrelated qualities, each implemented as a dedicated sub-task:

### 1. Correctness (vector ranking)
Does the solution actually solve the stated problem? This is the most fundamental criterion. A solution that does not address the root cause, rests on flawed logic, or targets a tangential concern is ranked lower regardless of its other qualities.

### 2. Completeness (vector ranking)
Does the solution address the full scope of the problem? Many problems are multifaceted. Solutions that grapple with every dimension of the challenge are ranked above those that handle only the most obvious aspect while leaving other parts unaddressed.

### 3. Feasibility (vector ranking)
Is the solution practical and achievable under realistic constraints? Solutions that are grounded, actionable, and do not depend on unreasonable assumptions are ranked above those that are theoretically appealing but speculative or impractical.

### 4. Clarity (per-solution scoring)
Is the solution specific, well-structured, and easy to follow? Each solution is individually scored on whether it communicates a concrete, understandable course of action. Vague or muddled solutions that leave the reader guessing score lower than those that are immediately actionable.

### 5. Efficiency (vector ranking)
Is the solution appropriately proportioned to the problem? Solutions that accomplish the goal without unnecessary complexity or waste are ranked above those that are bloated or disproportionate. Equally, trivially simple responses to deeply complex problems are ranked lower.

### 6. Robustness (per-solution scoring)
Does the solution hold up under real-world variation? Each solution is individually scored on whether it accounts for edge cases, anticipates complications, and demonstrates resilience. Brittle solutions that work only under ideal conditions score lower than those that are adaptable and defensive.

## How Evaluation Works

The six qualities are assessed through two complementary methods:

- **Vector sub-tasks** (correctness, completeness, feasibility, efficiency) rank all solutions against each other comparatively, producing a relative ordering for each quality.
- **Mapped scalar sub-tasks** (clarity, robustness) score each solution individually, then normalize the scores into a relative distribution.

All sub-task outputs are combined via weighted average into the final ranking. The qualities are interdependent: correctness is foundational, feasibility gates practical value, and clarity supports the assessment of every other quality.

## Use Cases

- **Product teams**: Prioritize competing feature ideas against a known user pain point.
- **Engineering**: Compare architectural approaches or technical strategies for a system design challenge.
- **Business**: Rank vendor proposals, strategic options, or operational improvement plans.
- **Research**: Evaluate different directions for a thesis, experiment design, or methodology.
- **Decision-making**: Any scenario where multiple candidate solutions need to be ordered from most to least promising relative to a clearly stated problem.
