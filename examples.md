
# WorkoutHarmony Plan Authoring Examples

WorkoutHarmony is currently available only to testers. Anyone can try the prompts below and review the resulting Markdown.

Paste or attach the [AI chat guide](chat.md) in a regular chat, then send one of the prompts below. If you use an agent with the [WorkoutHarmony plan skill](workout-harmony-plans/SKILL.md) installed, ask it to use `workout-harmony-plans` and send the same prompt.

You can review and save the generated Markdown before importing it into the app.

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

## Create a Xing Yi Five Elements Practice

This example creates a Xing Yi Quan (形意拳) Five Elements practice. It begins with 15 minutes of San-ti Shi (三体式) standing practice per side, followed by five separate fist movements.

It demonstrates a simple martial arts routine combining timed and self-paced exercises, using Chinese exercise names.

**Prompt to copy**

```text
Create one WorkoutHarmony plan for Xing Yi Quan Five Elements (形意五行拳) practice.

Start with one 三体式 standing practice step with a 15-minute timer on the left, then a separate 15-minute timer on the right.

Then add the five element fists as separate steps in this order:

1. 劈拳
2. 钻拳
3. 崩拳
4. 横拳
5. 炮拳

Use Chinese names for the section and all exercises.

Leave repetitions and durations unspecified for the five fists so they can be practiced at an individual pace.

Return the complete sections and steps.
```

**Example output**

```markdown
##### 形意五行拳
- 三体式, x15m ea
- 劈拳
- 钻拳
- 崩拳
- 横拳
- 炮拳
```

San-ti Shi (三体式) uses **Left / Right Duration**. It runs for 15 minutes on the left, then 15 minutes on the right, for 30 minutes of standing practice. Each of the five fists is a separate, self-paced step without a predefined duration or repetition count.

WorkoutHarmony supports Chinese and English exercise names.

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
