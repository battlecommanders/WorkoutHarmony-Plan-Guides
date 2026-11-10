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

This example adapts the strength circuit from Michael Boyle's one-dumbbell in-season workout. It uses a bodyweight split squat, a push-up, a single-leg deadlift, and a row. The example uses three rounds and adds a timed rest.

[One Dumbbell In-Season Workout](https://www.strengthcoach.com/resource/62c890a11ce9f0e626093690)

**Prompt to copy**

```text
Create one WorkoutHarmony plan based on the strength circuit in Michael Boyle's One Dumbbell In-Season Workout.
Use three rounds. In each round, do 10 bodyweight split squats per side, 10 push-ups, 10 single-leg dumbbell deadlifts per side, and 10 one-arm dumbbell rows per side.

Give each exercise its own step. Use "Single-leg deadlift" as the deadlift's Watch name.

Add a 60-second Rest after every round, including the last. Leave the dumbbell weight unspecified.

Return the complete sections and steps.
```

**Example output**

```markdown
##### Strength
- (round) One-dumbbell circuit, 3x
  - Bodyweight split squat, x10 ea
  - Push-up, x10
  - Single-leg dumbbell deadlift | Single-leg deadlift, x10 ea
  - One-arm dumbbell row, x10 ea
  - Rest, x60s
```

`ea` means **Each Side**. The name after `|` is the shorter **Watch name**. The ordinary Rest step runs after the row in every round.

## Modify the Same Plan

Give the chat or skill the complete Markdown above and the change you want.

If you have already edited the plan in WorkoutHarmony, use **Copy Markdown** to start from the current version.

**Prompt to copy**

```text
Revise the supplied WorkoutHarmony plan.

Keep all three rounds and the four exercises exactly as written.

Rest for 60 seconds after round 1, rest for 90 seconds after round 2, and finish after the row in round 3.

Change only the Rest step and return the complete revised contents.
```

**Example output**

```markdown
##### Strength
- (round) One-dumbbell circuit, 3x
  - Bodyweight split squat, x10 ea
  - Push-up, x10
  - Single-leg dumbbell deadlift | Single-leg deadlift, x10 ea
  - One-arm dumbbell row, x10 ea
  - Rest, x60s|x90s|
```

Rest is now a **Flexible** round step. The three slots specify 60 seconds, 90 seconds, and skip. The trailing pipe leaves the third slot empty.
**Flexible** round steps allow each named step to be included or skipped in individual rounds, with different repetitions, weights, or durations when included.

[Markdown format reference](workout-harmony-plans/references/markdown.md)

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
