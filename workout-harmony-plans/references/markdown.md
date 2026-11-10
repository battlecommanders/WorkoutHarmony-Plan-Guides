#### WorkoutHarmony single-workout Markdown

Format originally designed by George (commanders.ca). This reference documents its syntax and behavior.

This is the contents format for pasting into one workout. Supply no workout title/header, metadata table, IDs or scheduling fields. The app manages workout details. A user can keep a named Markdown file for later personal updates, with the name outside the importable contents.

Output the complete intended contents, not a patch or an insertion fragment. A Markdown fence is useful for copying; the content inside it must contain only sections/list items (and optional blank lines). Use spaces, not tabs, with two spaces per nesting level.

That is the canonical indentation for generated output. Input edited elsewhere may use another consistent indentation width or tabs; the intended list hierarchy must stay clear. Do not infer nesting from visual alignment alone or flatten child steps when revising externally edited Markdown.

#### Phone paste replaces contents

Return the complete desired sections and exercise list. Pasting on iPhone replaces that whole list; repeated names are independent and omitted old exercises/settings are not retained by matching. Plan Details (name, exercise type, activity, and schedule) and completed records stay intact. Keep all wanted exercises, notes, Watch/Spoken names and non-default properties in the output, including those outside the requested change. Leave unspecified values absent; do not invent values from phone input suggestions.

Omitted properties use normal defaults: direct tap for Next is true, timeout inherits personal Settings, naming overrides and notes are empty, and a round has one set. Removing a property from the complete output is enough to restore its default; no reset token is required. Review the replaced contents in the editor before saving. The separate Mac full-catalog Expert import is outside this selected-plan contents workflow; do not infer its retention rules from phone paste.

#### App terminology

Use the iPhone’s names when explaining a plan: **Exercise**, **Volume** and **Options** are the editor sections; combined groups use **Exercises** instead. The Volume **Type** labels are **Reps / Weight**, **Duration**, **Variable Sets** for standalone flexible work, and **Flexible** for round children. **Ramp-up Exercise** is the optional `(ramp)` exercise before repeated round work.

**Different Left / Right Volume** means asymmetric resistance; **Left / Right Duration** means timed Left then Right. The panels **Switch Interval** and **Set Interval** describe the timed transitions; the latter’s add/remove action is **Rest Between Sets**. **Announce Switch Side** and **Announce Set Numbers** control those interval cues.

**Name**, **Spoken name**, **Note**, **Watch name** and **Watch note** are separate fields. Spoken name changes pronunciation on both devices; Watch name changes only the Watch label. Use **Volume** when explaining values after an exercise’s comma; Markdown markers remain unchanged.

Within Flexible, **Empty Slot** means skip and **Restore Slot** includes the exercise again using its shared volume type. The type selector’s **–** means blank volume, written `-` in a populated Markdown slot; its normal capsule differs from an empty gray skipped slot. Ordinary no-volume work omits the comma/value instead.

#### Simple workout without sections

```markdown
- March in place, x2m
- Squat, x10
  - Move slowly and keep your balance.
- Rest, x30sc
- Wall push-up, x8
- Easy walk, x2m
```

#### Workout with sections

```markdown
##### Warm-up
- Easy walk, x2m

##### Strength
- Squat, 3x8@20
  - Keep the movement controlled.
- Rest, x1m
- Push-up, x10
```

A section uses exactly `##### `. Sections are optional for a short plan. Each step needs a nonempty name; its comma and value are optional. Additional sections should have names.

#### Name, Spoken name and Watch text

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

#### Volume

Volume is the value after the step name and comma. The following table describes ordinary steps. Flexible round slots and standalone flexible slots have the narrower restrictions in their dedicated sections below. Combined members are restricted to ordinary reps/weight values with optional side suffixes, or no value; do not apply the timer or asymmetric forms to them.

| Value | Meaning |
| --- | --- |
| `x10` | Ten reps |
| `3x10` | Three sets of ten reps within this step |
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
| `x1m30s` | Ninety-second timer |
| `2x30s` | Two timed sets within this step |
| `x30sc` | Thirty-second timer with countdown enabled |
| `x10 L` | Ten reps on the left side |
| `x10 ea` | Each-side reps |

Sets, reps and weight are independently optional. A set count does not require reps: it can repeat weight-only work or timed work, as in `3x@20` or `3x30s`. Omitted fields remain unspecified; zero reps or weight is an explicit value, not an omission. If there is no volume, omit the comma/value entirely. Phone input suggestions such as 2 sets, 10 reps or weight 10 are conveniences, not plan data or authoring defaults.

For left/right resistance pairs, omitted reps, set counts or weights on one side inherit the supplied value from the other side. Explicit values on both sides stay independent. Thus `x12@17 L @10 R` means twelve reps for both sides, whereas `5x5@18 L 4x2@13 R` retains different sets, reps and weights. If neither side supplies a field, it remains unspecified; `@22 L @18 R` does not imply a rep count. Suffixes are `L` left, `R` right, `ea` each side and `ea_dir` each direction. Use `ea_dir` for direction-based exercises such as clockwise/counterclockwise rotations; it does not mean Left/Right.

The app calls intentionally different left/right values **Different Left / Right Volume** (asymmetric resistance). Preserve those requested differences; this form belongs in an ordinary step, not a combined member or flexible slot. Its `L` and `R` already define the sides; do not append an additional `ea`, `ea_dir` or single-side suffix to the pair.

Choose options by volume:

| Volume | Supported options |
| --- | --- |
| Ordinary reps/weight | Independently optional sets, reps and weight; optional `L`, `R`, `ea` or `ea_dir` |
| Different Left / Right Volume | Left/right sets, reps and weight, with inheritance as above; no extra side suffix |
| Duration | Positive work duration; optional sets and countdown; no side, `L` or `R`; optional rest between repeated timed sets |
| Left / Right Duration | Positive duration per side with `ea`; optional sets, countdown, side-switch interval and rest between repeated pairs |

Timers do not support `ea_dir`. Countdown and timer interval modifiers do not apply to reps/weight values. A combined member remains limited to ordinary resistance or no volume, even when another volume form would otherwise be valid.

Use the app's weight convention and the user's intended units; the grammar stores a numeric weight, not a `kg`/`lb` suffix. Do not infer a unit conversion.

Weights must be whole numbers or whole numbers plus `.5`. Write `@5`, not `@5.0`; `@5.5` is valid, but `@5.25` is not allowed for plan authoring. Do not silently round an incompatible requested weight; clarify it with the user. Do not change unrelated existing values during a scoped update.

Reps and weights must be nonnegative; explicit set counts must be positive. Use positive timer durations for actual timed work. Avoid ordinary prose such as `30 seconds` where a real timer is intended: unrecognized values can become custom text without implementing timer behavior.

Write Rest as an ordinary named step. Give each occurrence its own duration or settings when needed.

#### Ordinary rounds

```markdown
##### Circuit
- (round) Superset A, 3x
  - Squat, x10
  - Push-up, x8
  - Rest, x45s
- Easy walk, x2m
```

Use `(round) Superset A, 3x` for a named round with three repetitions, with a positive count followed by `x`. The round name may be empty: `(round) , 3x` is also valid. Every ordinary child repeats each time; the final Rest repeats on the final round too. `3x10` inside a three-round block means three sets per repetition, not ten reps once per round. Return to zero indentation for the next standalone step, or start a new section. Blank lines do not close a round. Nested rounds are not supported.

Always include the `x` when writing an explicit round count: `3x`, not bare `3`. The default count of one can be omitted, including when updating a round. `1x` is accepted but is not needed to clear a previous round count during phone paste.

#### Flexible (round children)

**Flexible** is the app’s name for a round child that defines whether it is used in each set and which reps, weight, duration or side values it uses in that set. Together, flexible child steps let one round vary both its exercise combination and each exercise's workload without duplicating the whole round for every set.

Each pass through a round's child steps is one set of that round. Separate the flexible step's slots with `|` after its comma: slot 1 belongs to set 1, slot 2 to set 2, and so on.

- **Exercise selection:** an empty slot omits that named step from the set. Selecting different named children in different sets changes the exercise combination.
- **Step workload:** a populated slot includes that step with its specified reps, weight, duration or side values. A main exercise can remain present in every set while these values change.
- **Valid empty workload:** a slot containing only `-` includes the exercise without reps, weight or duration. It is performed; an unpopulated slot is skipped. Do not add a side suffix to `-`.

Apply these rules to planned Rest steps too, preserving the intended order of the included children in each set.

Choose **one volume type for the whole flexible child**, not a different type per slot:

| Shared type | Allowed populated slots |
| --- | --- |
| `–` (blank, written `-` in Markdown) | Only `-`: perform without volume; tap Next to continue |
| Reps / Weight | Reps and/or weight, with an optional `L`, `R`, `ea` or `ea_dir` suffix; no nested sets count or asymmetric pair |
| Duration | A positive duration such as `x15s`, with optional countdown `c` per slot; no sets count, side suffix, alternating timer or switch/set interval modifiers |

Any slot may instead be empty to skip the exercise in that round set. Never mix `-`, resistance and duration values in one flexible child: `-|x10|x15s` is invalid. Choose separate ordinary round children when richer volume types or different types are needed. For example, asymmetric resistance and repeated/alternating timers belong in ordinary children, not flexible slots.

The parent round determines the slot count: write **exactly one slot per round set**, including every leading, middle and trailing omission. When revising the round count, update every flexible child's slots too. Decreasing the count removes trailing slots. Increasing it appends copies of the last slot, including an empty/skipped slot, unless the requested workout explicitly supplies different values. A source empty slot still means skip; it never inherits a preceding value. A ramp-up exercise is outside this repeated slot list and keeps its independent value count.

```markdown
##### Strength
- (round) Squat sets, 3x
  - Squat, x12@20|x10@25|x8@30
  - Rest, x10sc|x10sc|
- Easy walk, x2m
```

Squat is a flexible step used in all three sets with different reps and weight. Rest is a flexible step used for ten seconds with countdown in sets 1 and 2, and omitted in set 3. The trailing pipe preserves its empty third slot.

```markdown
- (round) , 3x
  - Squat, x10
  - Rest, |x10sc|
```

Here the flexible Rest step is used only in set 2 of the round. The leading and trailing slots are empty, so sets 1 and 3 omit it. A middle omission can be written `x10||x8`.

To include an exercise without a workload only in the second set:

```markdown
- (round) Practice, 3x
  - March in place, x30s
  - Balance practice, |-|
```

The Balance practice slots mean skip / perform without a value / skip. If it should run without a value in every repetition, use a plain simple child `  - Balance practice`; `-|-|-` is redundant. Do not confuse the slot marker after the comma with the list bullet before the exercise name. This valid-empty marker is only for flexible children of a round, not ordinary standalone or ramp volumes.

Flexible steps can change the exercise combination in each set of a superset, as well as change the main exercise's weights or reps:

```markdown
- (round) Superset A, 3x
  - Squat, x10@20|x8@25|x6@30
  - Push-up, x10||
  - Row, |x10@10|
  - Lunge, ||x8
  - Rest, x45sc|x45sc|
```

Set 1 uses Squat and Push-up; set 2 uses Squat and Row; set 3 uses Squat and Lunge. The main Squat step remains in every set with different reps and weight, while the other named flexible steps are selected by their populated slots. Rest follows only sets 1 and 2. Each different exercise is a separate named child; a slot supplies that child's volume value, not a replacement exercise name.

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

#### Variable Sets (standalone flexible steps)

**Variable Sets** is the app’s name for a standalone flexible step: one actionable exercise containing successive reps/weight sets, completed with one Next action after the whole list. Each slot represents exactly one set. Reps and weight are independently optional, but each slot must supply at least one of them. Do not add a nested sets count, side suffix, duration, asymmetric pair or custom-text volume. Every slot must be populated: no leading, middle or trailing omissions and no `-` slots.

Do not describe standalone and in-round flexible steps as identical execution structures. Round slots define each repetition's exercise workload and resolve into separate ordinary actionable steps during execution.

Choose **Variable Sets** (a standalone flexible step) for a simple progression of one exercise, usually changing reps or weight, when the person wants to perform the whole list without pressing Next between sets. Prefer a round for more complex sequences, individual confirmation/skipping of working sets, separate Rest steps or other exercises between sets. Each round child has its own step controls.

A `(ramp)` child has a separate role before the repeated working steps, as described below; changing ordinary flexible values or naming a round “ramp-up” does not make it a ramp child.

The optional property `f:N` records the flexible slot count. Preserve it when needed for an existing valid one-slot representation with no pipe identifying the flexible form, and keep it equal to the actual slot count. Prefer an ordinary simple step when no variation is needed. Do not create zero-slot/`f:0` placeholders or use a representation property to bypass the standalone-slot restrictions.

```markdown
- Squat, x10@10|x10@12|x10@15
```

Multiple pipe-separated slots already identify a flexible step; do not add a redundant `f:3` to this example.

#### Multiple Exercises (combined steps)

`(+)` joins a member to the immediately preceding ordinary/combined step at the same indentation. It does not mean a repeated round. Members form one actionable combined step rather than separate Next actions.

```markdown
- Neck mobility, x5
- (+) 6 point rocks, x8
```

These simple steps are merged into one combined step, each retaining its own reps. Add further `(+)` lines at the same indentation to include more members. Without `(+)`, the lines represent separate steps.

Every member, including the first, must have a name and either no volume or **one ordinary reps/weight value** with an optional `L`, `R`, `ea` or `ea_dir` suffix. This may include a sets count such as `3x10`: one volume definition is not a requirement for exactly one set. Do not combine timed/alternating-timer values, asymmetric left/right pairs, custom text or flexible slot lists. For example, `- (+) Plank, x30s` is not an allowed combined member; put timed exercises on separate ordinary lines.

Combined groups are allowed inside rounds. Indent all their member lines by two spaces and detail lines by four. Do not attach `(+)` to a flexible step or ramp. Do not put flexible pipes in combined **volume values**; Watch/spoken-name separators before the comma are still allowed. Place any existing/requested group description and Next/timeout properties after the final member. The group has one Next action, not one for each exercise. This grammar does not provide reliable independent notes/property lines for every combined member; use separate ordinary steps when independent instructions or controls are required.

#### Ramp-up Exercise inside a round

A round can have one optional ramp-up exercise, identified by `- (ramp)`. It is mainly intended for strength warm-ups and accepts a simple Reps / Weight step or standalone reps/weight Variable Sets; do not author a no-volume, duration or combined ramp.

The complete ramp is performed once before the repeated working exercises. The `(ramp)` marker, rather than the round's name, defines this behavior. A round still needs at least one regular exercise; a ramp alone does not form a round.

```markdown
- (round) Squat work, 3x
  - (ramp) Warm-up squat, x8@10
  - Squat, x8@20
  - Rest, x1m
```

Put `(ramp)` first, indented by two spaces like other round children, with a space after the bullet. Descriptions and `(p)` properties beneath it use four spaces.

For a progression of warm-up reps or weights, use a standalone flexible ramp:

```markdown
- (round) Squat work, 3x
  - (ramp) Warm-up squat, x8@10|x5@15
  - Squat, x5@20
  - Rest, x1m
```

All ramp values belong to one actionable warm-up exercise: finish them, then press Next once to enter the repeated work. No automatic rests are inserted between those values. The ramp’s value count is independent of the round’s working-set count; do not resize it when changing that round count. Apply the standalone flexible rules: reps and weight are individually optional but each value needs at least one; no empty or `-` slots, nested set counts, side suffixes, timers or asymmetric values. Do not generate combined ramps. Ordinary flexible round children retain their different role: each slot defines inclusion and workload in one working repetition.

#### Note, Watch note and Options

**Allow Direct Tap for Next Exercise** is normally on (`next = true`), allowing direct step-screen tap-to-next/complete on Watch. Turn it off only if the Watch screen may touch the person's body during this exercise and cause accidental advancement. It applies to that exercise, not the other exercises in the workout. `(p) n` sets next false (off); `(p) y` sets it true (on). Omit the default true value from generated Markdown, including updates: removing `(p) n` restores normal direct tapping when the complete list is pasted on phone. Explicit Next/Complete in Watch Controls and iPhone Next remain available.

Add a step description/note as a plain bullet one indentation level below the step. Reserve `(p)` for property definitions. Both use two spaces below a standalone step and four spaces below a round child. Use one description line per step; multiple plain detail lines can replace the preceding description rather than append to it.

```markdown
- Plank, x30sc
  - Keep a steady position.
  - (p) t:no
- Untimed practice
  - Finish at your own pace.
  - (p) t:8,15
- Hold, x20sc
  - (p) n
- (round) Superset A, 3x
  - Squat, x10
    - Move slowly and keep your balance.
```

A property detail line starts `- (p) `. Separate its property tokens with ` | `. A single plain description is the shared/Watch cue; `note | Watch note` separates its text as described above. Neither creates an additional exercise. Descriptions/notes are content, not property definitions: always generate them as plain indented bullets, never as `(p) c:Text`.

Omit default options such as `y`, `t:default` and an empty `s:` override, and omit the entire `(p)` line when no options remain. Phone paste replaces all contents with newly parsed values: no name/occurrence matching restores old settings. Omitting `n` gives normal direct tapping; omitting timeout inherits the personal Settings default; omitting a symbol gives no override. Explicit default tokens remain accepted but are unnecessary in generated contents.

| Token | Behavior |
| --- | --- |
| `n` | Set next false: turn **Allow Direct Tap for Next Exercise** off for this exercise; explicit Watch Controls and iPhone Next remain available |
| `y` | Set next true: turn **Allow Direct Tap for Next Exercise** on, enabling direct Watch step-screen tap-to-next/complete |
| `t:default` | Use the app's default inactivity timeout |
| `t:no` | Disable the step's inactivity timeout |
| `t:8,15` | Custom pause/end inactivity thresholds of 8 and 15 minutes, measured from the same activity baseline |
| `s:` | No explicit symbol override |
| `s:VALUE` | A supported app symbol raw value; use only values supplied by the app/user, not arbitrary SF Symbol names |
| `f:N` | Flexible representation/slot count; match the actual list and do not generate zero-slot placeholders |

The direct-tap setting does not change automatic timer completion. Inactivity timeout is separate from work duration and planned Rest. Timed steps are exempt from the inactivity scheduler. Custom timeout values are nonnegative integers; ordinarily choose end greater than pause when both events are wanted. Zero is not an alternative spelling of `t:no`.

Countdown is the trailing `c` on a duration, such as `x30sc`; it is separate from description text. Unknown property keys are unsupported. Property lines apply to actionable steps, not a round header or a section.

#### Duration sets and Left / Right Duration

A duration can repeat in sets. Add `tN` in parentheses for N seconds of rest between sets with an announcement of the upcoming set number; `-tN` keeps the same rest silent. The rest applies before Set 2 onward, never before Set 1 or after the final set. With no sets count or a count of one, there is no between-set rest or set announcement.

```markdown
- Plank, 3x30sc(t10)
- Side plank, 3x30sc(s5,-t10) ea
```

The first example performs three 30-second holds with countdown and ten seconds of rest between holds, announcing Set 2 and Set 3 during those rests. The second performs three Left/Right pairs: 30 seconds Left, a five-second side-switch interval with a voice cue, then 30 seconds Right. Its ten-second rests between pairs are silent.

Use **Left / Right Duration**, written with `ea`, for timed work on both sides. `x20sc ea` gives twenty seconds per side with countdown. `s5` inserts a five-second interval between Left and Right and announces the side switch; `-s5` keeps that interval silent. Side-switch settings require alternating-side work with `ea`; set-rest settings also work on normal durations, including a single explicit `L` or `R` side. Each alternating set is a complete Left/Right pair.

Author intervals as positive whole seconds. Zero means blank in the plan: omit the modifier rather than generating `s0`, `-s0`, `t0` or `-t0`. Omit parentheses when there are no modifiers. Generate set-rest modifiers only when the timed set count exceeds one; side-switch modifiers require alternating Left/Right work with `ea`. Preserve unrelated existing settings during a scoped update.

Voice flags control the announcement, not whether a supplied interval occurs. The set cue says the upcoming set number and the switch cue says to change sides; neither cue speaks the interval length. Omit unrequested intervals. These intervals belong to the timed step; use a separate named Rest step when an independent planned rest is wanted.

#### Text escaping and existing custom values

In literal names and descriptions, escape `&` first as `&amp;`, then comma as `&#44;`, full-width comma as `&#65292;`, pipe as `&#124;`, and `#` as `&#35;`. Use `&#32;` for significant spaces, `&#9;` for tabs, `&#13;` for carriage returns and `&#10;` for newlines when needed. Keep structural commas/pipes unescaped and never split a literal field over physical lines.

Do not create custom-text volumes. For an untimed exercise with no numeric target, omit its comma/value and put any requested instruction in the plain note. Existing supplied custom display values may be retained unchanged when outside the requested edit, but they do not implement timers or structured workload. Do not reinterpret an unknown text value as timed work.

#### Compatibility limits

Use top-level rounds and put properties on their individual steps. Keep plan metadata in Plan Details. Set workload and inclusion with Flexible slots, put countdown in each relevant duration slot, and set timeout on the step. Use separate steps or sections when you need independent controls.

Examples illustrate workout authoring syntax; they do not imply app/runtime validation.
