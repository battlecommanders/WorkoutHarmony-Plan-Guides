# WorkoutHarmony Plan Authoring Examples

WorkoutHarmony is currently available only to testers. Anyone can try the prompts below and review the resulting Markdown.

Send the guide link below before your workout prompt. If you have the [plan skill](workout-harmony-plans/SKILL.md) installed, ask your agent to use `workout-harmony-plans`.

You can review and save the generated Markdown before importing it into the app.

## Start with a Simple Request

You do not need to design every exercise or learn the Markdown format before starting. Ask your AI to read the guide, then describe your goal in plain language. Refine the initial plan through conversation.

**First prompt — provide the guide**

```text
Read this guide and wait for my workout request.
https://raw.githubusercontent.com/battlecommanders/WorkoutHarmony-Plan-Guides/refs/heads/main/chat.md
```

**Second prompt — describe your goal**

```text
Create a simple full-body workout for home using one 35 lb kettlebell. Use @35 for kettlebell exercises.
```

The AI can produce an initial WorkoutHarmony plan from this short request. Review its suggestions, then adjust what matters to you.

## Create a One-Dumbbell Strength Plan

This example adapts the strength circuit from Michael Boyle's one-dumbbell in-season workout. It uses three rounds of bodyweight split squats, push-ups, single-leg deadlifts, and rows, with one 20 lb dumbbell and a timed rest after each round.

[One Dumbbell In-Season Workout](https://www.strengthcoach.com/resource/62c890a11ce9f0e626093690)

**Prompt to copy**

```text
Create a strength workout plan based on Michael Boyle's One Dumbbell In-Season Workout.
Do 3 rounds of 10 bodyweight split squats each side, 10 push-ups, 10 single-leg dumbbell deadlifts each side, and 10 one-arm dumbbell rows each side.
Use 20 lb for dumbbell exercises (@20).
Add a 60-second rest after each round, including the last.
Use "Single-leg deadlift" as the short Watch name. No notes.
```

**Example output**

```markdown
##### Strength
- (round) , 3x
  - Bodyweight split squat, x10 ea
  - Push-up, x10
  - Single-leg dumbbell deadlift | Single-leg deadlift, x10@20 ea
  - One-arm dumbbell row, x10@20 ea
  - Rest, x60s
```

`ea` means **Each Side**. `@20` specifies a 20 lb dumbbell for this plan. The name after `|` is the shorter **Watch name**. The Rest step runs after the row in every round, including the last.

### Modify the Same Plan

Use a short follow-up in the same chat to adjust the plan.

**Prompt to copy**

```text
Skip the rest after the last round.
```

**Updated output**

```markdown
##### Strength
- (round) , 3x
  - Bodyweight split squat, x10 ea
  - Push-up, x10
  - Single-leg dumbbell deadlift | Single-leg deadlift, x10@20 ea
  - One-arm dumbbell row, x10@20 ea
  - Rest, x60s|x60s|
```

Rest is now a **Flexible** round step with one slot per round. The first two slots keep the 60-second rests. The trailing pipe leaves the final slot empty, so the workout ends after the last row.

[Markdown format reference](workout-harmony-plans/references/markdown.md)

## Martial Arts Practice: Xing Yi Five Element Fists

This martial arts workout starts with Three-Body Standing for 15 minutes on each side, followed by the five foundational fists. It shows how to combine a timed left/right exercise with self-paced movements in one WorkoutHarmony plan.

**Prompt to copy**

```text
Create a WorkoutHarmony plan for Xing Yi Five Element Fists.
Start with Three-Body Standing, 15 minutes on each side.
Then list these exercise names only: Splitting Fist, Drilling Fist, Crushing Fist, Crossing Fist, Cannon Fist.
No sections, no notes, no rest.
```

**Example output**

```markdown
- Three-Body Standing, x15m ea
- Splitting Fist
- Drilling Fist
- Crushing Fist
- Crossing Fist
- Cannon Fist
```

`ea` means **Each Side**. Three-Body Standing uses **Left / Right Duration** for 15 minutes per side (30 minutes total). Each fist is a separate, self-paced step.

## Import or Update a Plan

If you have tester access to WorkoutHarmony:

1. Create a new workout plan or select an existing one.
2. Paste the complete generated Markdown into the app's editor.
3. Review the workout structure and save the plan.

To update an existing plan with AI:

1. Use **Copy Markdown** in WorkoutHarmony to copy the current plan's sections and steps.
2. Provide the Markdown and requested changes to your preferred AI chat or agent.
3. Paste the complete revised Markdown back into the app, review the changes, and save.

No direct AI integration or API key is required.
