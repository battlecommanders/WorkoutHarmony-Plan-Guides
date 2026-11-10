# WorkoutHarmony — Workout Design Tips

Practical tips for designing workout plans that are easy to follow **during actual training**. The goal is to keep prompts, steps, and interactions simple while supporting the workout as it is performed.

These are **authoring suggestions**, not additional Markdown format rules. Use them when they fit the workout; don't add complexity just to use a feature. This file can grow as practical lessons emerge.

## 1. Design steps around the real workout

A good plan is more than a list of exercises. Consider what the person is doing between movements: changing position, switching sides, handling equipment, or preparing for the next exercise.

- Keep steps distinct when they need their own timer, control, or completion point.
- Avoid unnecessary Next actions during a continuous sequence.
- Prefer a straightforward execution flow over a technically elaborate structure.

## 2. Combine simple steps when it reduces interaction

When simple movements naturally belong together and do not require separate controls, use **Multiple Exercises** to present them as one actionable step. This keeps the movement cues while reducing repeated taps on iPhone or Apple Watch.

Do not combine movements that need independent timers or other unsupported combined-step behavior. Use separate steps when that makes the workout easier to follow.

## 3. Use Rest as a practical transition

Use an ordinary step named for the transition, such as **Rest** or **Shake out**. It can give the person time to recover, set down equipment, change position, or prepare for the next movement.

- Add a timer where a predictable pause helps the next action.
- Choose the duration based on the actual transition or recovery need.
- In a round, decide which sets need a pause and whether to include one after the final set.

## 4. Use countdowns as clear cues

For timed steps, a countdown can help signal that a transition is approaching, so the person does not need to keep checking the screen. For example:

```markdown
- Shake out, x30sc
```

Here `c` enables countdown for the 30-second step. Use countdowns when they make the next action easier to anticipate, not on every timer by default.

## 5. Keep Watch labels and spoken cues short

During a workout, the user needs to recognize or hear **what comes next**, not a full exercise description.

- **Name:** Use a clear, complete exercise name for editing and review.
- **Watch name:** Use a shorter label that's easy to recognize at a glance.
- **Spoken name:** Use concise, natural, unambiguous words for speech on iPhone and Watch; they need not match the Watch label.
- Put detailed technique explanations in **notes**, rather than making names or spoken cues long.

For example:

```markdown
- Single-leg dumbbell deadlift | Single-leg deadlift | Single leg deadlift, x10 ea
```

The full name remains descriptive, the Watch label is compact, and the spoken name is straightforward to pronounce.

## Guiding principle

**Make the workout easy to perform, not merely easy to describe.** Use the simplest step structure and cues that reliably support the intended movements.
