# Create or update a WorkoutHarmony workout in an AI chat

Anyone can use this guide to generate a readable Markdown plan, review it, and keep a copy for later changes. The guide is part of the MIT-licensed authoring package.

Paste or attach this file in your preferred AI chat, then describe the workout you want: exercises, reps or durations, rest and any rounds, including flexible steps that can be used or skipped in each set with different reps, weights or other volume values. To update a workout, also supply its existing Markdown and the requested changes. No installed skill is needed. Work on one workout at a time.

See the [worked examples](examples.md) for copyable prompts and complete Markdown output.

If you have access to WorkoutHarmony, create or select the destination plan. Set its name, exercise type, activity, and schedule in the app. Paste the AI's Markdown into that plan, review it, and save. Countdown, timeout and other small step-property adjustments can be handled in the phone editor.

## Phone paste replaces contents

Return the complete desired sections and exercise list. Pasting on iPhone replaces that whole list; repeated names are independent and omitted old exercises/settings are not retained by matching. Plan Details (name, exercise type, activity, and schedule) and completed records stay intact. Keep all wanted exercises, notes, Watch/Spoken names and non-default properties in the output, including those outside the requested change. Leave unspecified values absent; do not invent values from phone input suggestions.

Omitted properties use normal defaults: direct tap for Next is true, timeout inherits personal Settings, naming overrides and notes are empty, and a round has one set. Removing a property from the complete output is enough to restore its default; no reset token is required. Review the replaced contents in the editor before saving. The separate Mac full-catalog Expert import is outside this selected-plan contents workflow; do not infer its retention rules from phone paste.

## Format terminology

The following terms have specific meanings in this Markdown workout format, originally designed by George (commanders.ca). Use the current iPhone labels below when describing or generating a workout. Markdown markers remain syntax, not alternative app labels.

| Term | Meaning in the app and this format |
| --- | --- |
| Workout | The single ordered workout described by the Markdown contents. |
| Section | A named group of steps and rounds, introduced by `##### Section name`. |
| Exercise | The name and note of a step; a simple step is one exercise or planned rest. |
| Multiple Exercises (combined step) | The app’s **Change to Multiple Exercises** action groups named exercises into one Next action. Markdown uses `(+)`; each member has no volume or one ordinary Reps / Weight value, optionally with a Side. Timers, asymmetric volumes, custom text and flexible lists are not allowed. |
| Round | A group repeated for a number of Sets, such as `(round) Superset A, 3x`. Its name may be empty. |
| Volume | The value after a step’s comma, such as `3x10@5` for three sets of ten reps at weight 5. |
| Volume Type | The kind of Volume used by a step. Options include **Reps / Weight**, **Duration**, **Variable Sets** outside a round, and **Flexible** for a round child. Ordinary no-volume work uses the app’s `–` option and omits the Markdown comma/value. |
| Variable Sets | A standalone flexible step: successive populated reps/weight values of one exercise, completed with one Next action. The same form can be a Ramp-up Exercise. |
| Flexible | A round flexible child: one slot per parent round Set, with one shared volume type across all populated slots. |
| Slot | One position in a Flexible child’s pipe-separated volumes, corresponding to the same numbered round Set. |
| Empty Slot / Restore Slot | Omit or restore an exercise for one round Set. An empty Markdown slot is skipped, shown as an empty gray capsule; it never inherits the preceding value. |
| `–` (blank volume) | Inside Flexible, the selector’s `–` type uses Markdown `-` in populated slots. The exercise runs without volume, shown as `-` in a normal capsule; this differs from Empty Slot. |
| Reps / Weight | Resistance volume with independently optional Sets, Reps and Weight in ordinary steps; flexible slots have no nested Sets count. |
| Side | **Left**, **Right**, **Each Side** or **Each Direction**, written `L`, `R`, `ea` or `ea_dir` where supported. No Side means no suffix. |
| Different Left / Right Volume | The app’s term for asymmetric resistance in an ordinary step, such as `x12@17 L @10 R`; not allowed in combined members or flexible slots. **Same Left / Right Volume** returns to ordinary volume using the Left values. |
| Left/right inheritance | In Markdown asymmetric pairs, a field omitted on one side uses the other side’s supplied value; explicit differences remain independent. This does not apply to empty Flexible slots. |
| Duration | Timed work, such as `x30s`; optional Sets in ordinary steps. Flexible duration slots allow only time and their own Countdown. |
| Left / Right Duration | The app’s term for alternating-side duration: `ea` times Left then Right. Available for ordinary steps, not Flexible duration slots. |
| Switch Interval | Seconds between Left and Right in Left / Right Duration. **Announce Switch Side** determines whether its cue is spoken (`sN` versus `-sN`). |
| Set Interval / Rest Between Sets | Seconds before timed Set 2 onward, never before Set 1 or after the final set. **Announce Set Numbers** determines whether the upcoming set is spoken (`tN` versus `-tN`). The app uses **Set Interval** as the panel title and **Rest Between Sets** for the add/remove action. |
| Countdown | The optional trailing `c` in a duration, such as `x20sc`. |
| Name / Watch name / Spoken name | `Name` is required; the optional Watch name changes the Watch label, while Spoken name supplies pronunciation on both iPhone and Watch. Markdown: `Name \| Watch name \| Spoken name`. |
| Note / Watch note | A plain indented detail bullet; `note \| Watch note` separates phone/Mac text from its Watch note. A single description remains the shared/Watch cue. |
| Options | Behavior settings such as **Allow Direct Tap for Next Exercise** and **Inactivity timeout**; their Markdown definitions go on an indented `(p)` line. They are not Volume types. |
| Ramp-up Exercise | One optional `(ramp)` exercise before a round’s repeated work. Use a simple Reps / Weight step or Variable Sets; its value count is independent of round Sets. |

## Instructions for the AI

Create the contents of one WorkoutHarmony workout from the user's request. When designing a new workout, use reasonable assumptions where necessary and state them outside the output block. When revising an existing workout, preserve all unrelated content and leave unspecified values unchanged. Ask a brief question only when missing information materially affects the result.

Return the complete contents in one fenced `markdown` block, with no explanations inside it.

Use the following format:

- A step is `- Step name` or `- Step name, value`.
- To group named simple exercises into one combined step, prefix each additional member with `(+)` at the same indentation as the first. Each member may have no volume or one normal reps/weight value with an optional side; no timers, asymmetric resistance, custom text or flexible volume lists. Group properties, or an existing/requested group note, go below the final member.
- Reps use `x10` for ten reps, or `3x10` for three sets of ten.
- Durations use `x30s`, `x2m` or `x1m30s`. Keep the `x`; bare `30s` is not the timer syntax.
- A trailing `c` enables countdown, for example `x30sc`. Omit it unless wanted; it can also be adjusted in the app.
- Add a step description/note as an indented plain bullet below its step, for example `  - Keep your movement controlled.` Use one description line per step. Inside a round, indent descriptions by four spaces. Descriptions are content, not properties; do not write them as `(p) c:Text`.
- A detail line starting with `(p)` defines properties, for example `  - (p) t:no`. It is separate from the description/note. Countdown and timeout can also be adjusted in the phone editor.
- Give each rest its own ordinary line, such as `- Rest, x45s`. Do not use `[rest]` or invent a kind property. A visible Rest label alone does not assign the app's internal Rest kind.
- Use `##### Section name` for sections. Section headings have exactly five `#` characters. A short plan can omit sections altogether.
- An ordinary repeated round is `- (round) Superset A, 3x`, followed by steps indented by two spaces in generated output. The round name is optional: `- (round) , 3x` is also valid. This repeats the child steps three times. Use `x10` in a round when ten reps are wanted each time, rather than accidentally multiplying with `3x10`.
- Explicit round counts end in `x`: write `3x`, not bare `3`. The default count of one can be omitted when creating a round.
- A top-level step or a new section after a round ends that round. Blank lines do not end it.
- Keep repeated names when appropriate; two Rest lines are separate occurrences and can have different durations.
- Use plain exercise names. If literal text needs a comma, pipe or `#`, encode it as `&#44;`, `&#124;` or `&#35;` respectively. Keep grammar delimiters unescaped.

Return only sections and steps inside the output block. Do not add a plan title/header, metadata table, numbered list, checkbox, IDs or scheduling fields. Nested rounds are not supported. Use a flexible step as described below when its presence or volume value differs between sets of a round.

Treat rests as planned steps. Add a rest after every set or round only if requested or if you state it as an assumption for a new workout. An ordinary round repeats every child, including a final Rest, on its final repetition too.

Generate consistent two-space nesting. Markdown edited elsewhere may use other consistent indentation widths or tabs; preserve the intended hierarchy rather than relying on a particular editor's visual spacing.

## Name, Spoken name and Watch text

Every exercise needs a nonempty name. Before the comma, use `name | Watch name | Spoken name` for optional display and pronunciation overrides. The Watch name changes only the Watch label. The **Spoken name** is pronounced on both iPhone and Watch instead of spelling out an abbreviation; it does not change either display label. If absent or empty, speech uses the regular name.

```markdown
- Standing calf raise | Calf raise, x10
- TK || Full name to pronounce
- TK | Short Watch label | Full name to pronounce, x10
```

Use `name || Spoken name` when no Watch override is needed. Existing one-part and two-part names remain valid. Phone contents paste replaces the whole exercise list with newly parsed values. Omitted Watch/Spoken name components are empty, so the regular name is used; old names are not recovered by matching. To remove an override, omit it from the returned contents. Keep an empty middle component only when a Spoken name follows, as in `name || Spoken name`. A trailing empty third component is accepted but unnecessary: `name | Watch name` already has no Spoken name. Escape literal pipes as `&#124;`. Name separators are before the comma; flexible volume slot separators are after it.

Descriptions keep their separate two-part rule: a plain detail bullet `note | Watch note` separates the phone/Mac note from the Watch note.

```markdown
- Standing calf raise | Calf raise, x10
  - Keep a steady pace. | Steady pace.
```

A single description without a pipe remains the shared/Watch cue. Use `note |` for a phone/Mac-only note with no Watch note. Do not add a spoken-name field to description bullets. Preserve supplied Watch/spoken text unless asked to change it. Combined members may each have their own Watch and spoken names; any supported description after their final member belongs to the group, not each exercise. The same name syntax applies to simple and flexible exercises, including round children and ramp-up exercises.

## Volume

Volume is the value after the step name and comma, for example `- Squat, 3x10`. The table describes ordinary steps. Flexible round slots and standalone flexible slots have the narrower restrictions in their dedicated sections below. Combined members allow only its ordinary reps/weight forms and side suffixes, or no value; timer and asymmetric forms are for separate steps.

| Value | Meaning |
| --- | --- |
| `x10` | Ten reps |
| `3x10` | Three sets of ten reps |
| `3x` | Three sets, with reps and weight unspecified |
| `@20` | Weight 20, with reps and sets unspecified |
| `3x@20` | Three sets with weight 20, for example repeated farmer's walks; reps are unspecified |
| `x9@5` | Nine reps with weight 5 |
| `x10 R` | Ten reps on the right side |
| `x10s` | Ten-second timer, not ten reps |
| `@22 L @18 R` | Left weight 22 and right weight 18; reps are unspecified |
| `x12@17 L @10 R` | Twelve reps on each side, with left weight 17 and right weight 10 |
| `5x5@18 L 4x2@13 R` | Left: five sets of five reps at weight 18; right: four sets of two reps at weight 13 |
| `x8 ea_dir` | Eight reps in each direction |
| `x20sc ea` | Twenty seconds on each side, with countdown |
| `x30sc(s3) ea` | Thirty seconds on each side with countdown, plus a three-second side-switch interval with a voice cue |
| `3x30s(t10)` | Three 30-second holds with ten seconds of rest between holds, announcing Set 2 and Set 3 |
| `3x30s(-t10)` | The same timed holds with silent between-set rest |

Sets, reps and weight are independently optional. Sets can repeat reps, durations or weight-only work; they do not require reps. Leave missing fields unspecified, and omit the comma/value when there is no volume. Zero reps or weight is an explicit value, not an omission. Phone input suggestions are conveniences, not plan data; do not insert them as authoring defaults.

Use `L` for left, `R` for right, `ea` for each side and `ea_dir` for each direction, such as clockwise/counterclockwise rather than Left/Right. In left/right resistance pairs, omitted reps, set count or weight on one side inherits the supplied value from the other; explicitly supplied values on both sides remain different. If neither side supplies a field, leave it unspecified. Do not assume missing reps from a weight-only value.

The app calls intentionally different left/right values **Different Left / Right Volume** (asymmetric resistance), supported in ordinary steps, but not combined members or flexible slots. Preserve requested differences rather than making the sides equal. The pair already specifies `L` and `R`; do not add an extra side suffix.

Use numeric weights in the app's weight convention without appending unit labels. Durations can also use minutes, such as `x2m` or `x1m30s`. Keep the `ea` suffix when using the side-switch timer modifier. Set-rest modifiers `tN` (with a set-number cue) and `-tN` (silent) work on normal and alternating durations. Rest occurs before Set 2 onward, with no initial or final rest. For alternating duration, one set is a complete Left/Right pair. For example, `3x30s(s5,t10) ea` adds a five-second switch interval within each pair and ten seconds of rest between pairs. Intervals are seconds; voice settings do not change their length.

Normal durations support no side, `L` or `R`; use `ea` for **Left / Right Duration**. Timers do not support `ea_dir`. Countdown and interval modifiers belong only to durations, not reps/weight. Generate set-rest modifiers only when there is more than one timed set. A side-switch interval requires Left/Right duration with `ea`.

Author intervals as positive whole seconds. Zero means blank: omit the modifier instead of writing `s0`, `-s0`, `t0` or `-t0`, and omit empty parentheses. Preserve unrelated existing settings during a scoped update. An enabled interval announcement says the switch cue or upcoming set number, not the interval length.

Weights must be nonnegative whole numbers or whole numbers plus `.5`: write `@5` or `@5.5`, not `@5.0` or `@5.25`. Clarify incompatible requested weights instead of silently rounding them; preserve unrelated existing values during a scoped update. Reps must be nonnegative integers, explicit set counts must be positive integers, and timed work must have a positive duration.

Do not create custom-text volumes. For an untimed exercise with no numeric target, omit the comma/value and put any requested instruction in its note. Existing supplied custom text can be retained when outside the requested change; it does not create a timer or structured workload.

## Options (Markdown properties)

**Allow Direct Tap for Next Exercise** is normally on (`next = true`), allowing direct step-screen tap-to-next/complete on Watch. Turn it off only if the Watch screen may touch the person's body during this exercise and cause accidental advancement. It applies to that exercise, not the other exercises in the workout. `(p) n` sets next false (off); `(p) y` sets it true (on). Omit the default true value from generated Markdown, including updates: removing `(p) n` restores normal direct tapping when the complete list is pasted on phone. Explicit Next/Complete in Watch Controls and iPhone Next remain available.

Put properties on a nested `- (p)` line below the step. Inside a round, indent that line by four spaces instead of two.

Omit default options and empty property lines in generated contents, including updates. Phone paste reconstructs all sections and exercises from the complete Markdown; omitted options use normal defaults rather than old settings. Omitting `n` allows direct tapping, omitting timeout inherits personal Settings defaults, and omitting the round count gives one set. Explicit `y`, `t:default` or `1x` remain accepted but are not needed as resets.

| Property definition | Meaning |
| --- | --- |
| `(p) t:8,15` | Pause/end inactivity thresholds of 8 and 15 minutes, both measured from the same activity baseline |
| `(p) t:no` | Disable inactivity timeout for this step |
| `(p) n` | Set next false: turn **Allow Direct Tap for Next Exercise** off for this exercise; explicit Watch Controls and iPhone Next remain available |
| `(p) y` | Set next true: turn **Allow Direct Tap for Next Exercise** on, restoring direct Watch step-screen tap-to-next/complete |

```markdown
- Practice, x10
  - Keep the movement controlled.
  - (p) t:8,15
- Balance, x10 R
  - (p) t:no
- Hold, x20sc
  - (p) n
```

Timeout is an inactivity rule, not the step duration; timed steps are exempt from inactivity timeout. Countdown uses the `c` in the duration. Properties can share a line using ` | `, for example `- (p) t:8,15 | n`.

## Multiple Exercises (combined steps)

```markdown
- Neck mobility, x5
- (+) 6 point rocks, x8
```

These two named exercises are performed together with one Next action. Additional `(+)` lines can add more members; without `(+)`, they remain separate steps. Every member needs a name and either no volume or one ordinary reps/weight value, optionally with `L`, `R`, `ea` or `ea_dir`. A sets count such as `3x10` remains one ordinary volume value; “single volume” does not mean exactly one set.

Do not combine timers, alternating timers, asymmetric left/right pairs, custom text, flexible steps or ramps. In particular, `- (+) Plank, x30s` is not an allowed combined member: write Plank as its own step. Combined groups can be children of a round; indent every member equally. Do not put flexible pipes in their volume values; Watch/spoken-name separators before the comma are still allowed. Group Next/timeout properties go below the final member. Use separate steps when independent notes or controls are needed.

## Flexible (round children)

**Flexible** is the app’s name for a round child whose use and volume value can differ in each set of that round. This lets one round vary both its exercise combination and each exercise's workload, without duplicating the whole round for every set.

Use `|` to separate the step's slots: the first slot is for set 1 of the round, the second for set 2, and so on. The slots control:

- **Exercise selection:** an empty slot omits that named step from that set. Selecting different named steps in different sets changes the exercise combination.
- **Step workload:** a populated slot includes the step with its specified reps, weight, duration or side values. The same main exercise can therefore stay present with different workloads.
- **Valid empty workload:** `-` includes the exercise for that set without reps, weight or duration. It is performed; an empty slot is skipped.

These rules apply to planned Rest steps too.

Choose **one volume type for the whole flexible child**, not a different type per slot:

| Shared type | Allowed populated slots |
| --- | --- |
| `–` (blank, written `-` in Markdown) | Only `-`: perform without volume; tap Next to continue |
| Reps / Weight | Reps and/or weight, with an optional `L`, `R`, `ea` or `ea_dir` suffix; no nested sets count or asymmetric pair |
| Duration | A positive duration such as `x15s`, with optional countdown `c` per slot; no sets count, side suffix, alternating timer or switch/set interval modifiers |

Any slot may instead be empty to skip the exercise in that round set. Never mix `-`, resistance and duration values in one flexible child: `-|x10|x15s` is invalid. Choose separate ordinary round children when richer volume types or different types are needed. For example, asymmetric resistance and repeated/alternating timers belong in ordinary children, not flexible slots.

The parent round determines the slot count: write **exactly one slot per round set**, including every leading, middle and trailing omission. When revising the round count, update every flexible child's slots too. Decreasing the count removes trailing slots. Increasing it appends copies of the last slot, including an empty/skipped slot, unless the requested workout explicitly supplies different values. A source empty slot still means skip; it never inherits a preceding value. A ramp-up exercise is outside this repeated slot list and keeps its independent value count.

```markdown
- (round) Superset A, 3x
  - Squat, x12@17|x10@18|x8@20
  - Rest, x10sc|x10sc|
```

Squat is a flexible step with different reps and weight in each set of the round. Rest is another flexible step: it runs for ten seconds with countdown in sets 1 and 2, and is ignored in set 3.

```markdown
- (round) Superset A, 3x
  - Squat, x10
  - Rest, |x10sc|
```

Here the flexible Rest step is used only in set 2 of the round. Similarly, `x10||x8` uses a step for ten reps in set 1, omits it in set 2, and uses it for eight reps in set 3. Write exactly one slot per set of the round, leaving intentional omissions empty. Keep properties and descriptions below the step; the slots contain volume values, not separate property definitions. Do not attach `(+)` members to a flexible step.

```markdown
- (round) Practice, 3x
  - March in place, x30s
  - Balance practice, |-|
```

Balance practice runs only in set 2 with no workload value; sets 1 and 3 skip it. Write `-` only as that slot's complete value, without a side suffix. If an exercise runs without a value in every round set, use an ordinary child such as `  - Balance practice`, not `-|-|-`. Empty and `-` slots are allowed only in flexible children of a round, never in standalone flexible steps or ramp volumes.

Flexible steps can also change which exercises make up each set of a superset. A main exercise can stay present with different weights, while other exercises are used in selected sets:

```markdown
- (round) Superset A, 3x
  - Squat, x10@20|x8@25|x6@30
  - Push-up, x10||
  - Row, |x10@10|
  - Lunge, ||x8
  - Rest, x45sc|x45sc|
```

Set 1 uses Squat and Push-up; set 2 uses Squat and Row; set 3 uses Squat and Lunge. Squat uses different reps and weight in each set, and Rest follows only the first two sets. Each different exercise has its own named flexible step, with empty slots controlling where it is omitted. The slots contain that exercise's volume values, not different exercise names.

Timed and untimed Rest use the same slot rules, in separate flexible definitions:

```markdown
- (round) Timed rests, 3x
  - Squat, x10
  - Rest, x15sc|x10sc|
- (round) Untimed rests, 3x
  - Squat, x10
  - Rest, -|-|
```

The timed Rest lasts 15 seconds, then 10 seconds, each with countdown; set 3 omits it. The untimed Rest requires Next in sets 1 and 2 and is omitted in set 3. `-` has no side suffix or duration. If a child runs without volume in every set, use an ordinary no-volume child instead of a redundant all-`-` flexible list.

## Variable Sets (standalone flexible steps)

Outside a round, **Variable Sets** is a standalone flexible step. A list such as `- Squat, x12@17|x10@18|x8@20` represents one exercise with successive reps/weight sets, completed with one Next action after the whole list. Each slot represents exactly one set. Reps and weight are independently optional, but each slot must supply at least one. Do not add nested sets counts, side suffixes, durations, asymmetric pairs or custom-text volumes. Every slot must be populated: no leading, middle or trailing omissions and no `-`. Do not create zero-slot placeholders.

Inside a round, each flexible slot instead determines whether that child exercise is used and its volume for the corresponding repetition; it resolves into a separate ordinary actionable step.

Choose **Variable Sets** (a standalone flexible step) for a simple reps/weight progression of one exercise when the person wants to perform all sets without pressing Next between them. Prefer a round for more complex sequences, individual confirmation/skipping of working sets, separate Rest steps or other exercises between sets. Each round child has its own step controls.

## Ramp-up Exercise inside a round

A round can have one optional ramp-up exercise marked with `(ramp)`. It accepts a simple Reps / Weight step or standalone reps/weight Variable Sets and runs once before the repeated working steps. Do not author a no-volume, duration or combined ramp. The marker defines the ramp; the round's name is just a label. The round still requires a regular exercise in addition to any ramp.

```markdown
- (round) Squat work, 3x
  - (ramp) Warm-up squat, x8@10
  - Squat, x5@20
  - Rest, x1m
```

The ramp child is performed once before the three working repetitions. Keep it first. Write `- (ramp)` with a space after the bullet, and indent it by two spaces like other round children.

A flexible ramp such as `  - (ramp) Warm-up squat, x8@10|x5@15` runs all its values as one warm-up exercise, followed by one Next action to enter the working repetitions. No automatic rests are inserted between those values. The ramp’s value count is independent of the round’s working-set count; do not resize it when changing that round count. Follow the standalone flexible rules: each value has reps and/or weight, without empty or `-` slots, nested set counts, side suffixes, timers or asymmetric values. Do not generate combined ramps. This differs from a flexible round child, whose slots define inclusion and workload during each working repetition.

## Simple workout without sections

These examples demonstrate formatting; they are not personalized training recommendations.

```markdown
- March in place, x2m
- Squat, x10
  - Move slowly and keep your balance.
- Rest, x30sc
- Wall push-up, x8
- Easy walk, x2m
```

## Workout with sections and an ordinary round

```markdown
##### Warm-up
- March in place, x2m
- Shoulder circles, x10

##### Main
- (round) Superset A, 3x
  - Squat, x10
    - Move slowly and keep your balance.
  - Wall push-up, x8
  - Rest, x45s

##### Cool-down
- Easy walk, x2m
```

The app treats the pasted contents as the selected workout's complete structure, not an insertion fragment. Review all sections and steps before saving. When updating existing Markdown, retain exercises, order, descriptions and settings outside the requested changes, and return the complete revised contents.
