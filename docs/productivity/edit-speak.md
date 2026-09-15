## What it does

`edit-speak` lets you adjust your agent speech settings without re-running engine installation or setup questionnaires. It reads your existing configuration, displays current values, and updates voice, tone, frequency, or volume in place.

It is **configuration-only**. It touches neither the installed TTS binary nor system daemon processes. It updates your local `.speak.md` or global `~/.config/speak/config.md` and confirms the change with a single audio test sentence.

## When to reach for it

You invoke this by typing `/edit-speak`; the [agent](https://www.aihero.dev/ai-coding-dictionary/agent) won't reach for it on its own.

Reach for it whenever you want to switch your agent's voice, change notification frequency before starting a noisy test suite, boost volume for background audio, or silence speech entirely.

For the initial engine installation and full voice auditions, use [setup-speak](https://aihero.dev/skills-setup-speak). For the runtime skill that fires speech notifications, see [speak](https://aihero.dev/skills-speak).

## Prerequisites

An existing `.speak.md` in the current project or `~/.config/speak/config.md` in your user profile. If neither exists, `edit-speak` prompts you to run [setup-speak](https://aihero.dev/skills-setup-speak) first.

## Quick settings adjustments

`edit-speak` presents a fast menu to change:

- **Voice**: Switch to another voice supported by your active engine (for instance, switching from `eponine` to `michael` for focus mode).
- **Tone**: Adjust verbosity between `conversational`, `formal`, and `minimal`.
- **Frequency**: Change notification frequency or switch to `silent` mode to mute audio without uninstalling anything.
- **Volume**: Adjust volume multipliers from standard (1.0) to amplified (1.5 to 4.0) to cut through background noise.
- **Task filters**: Enable or disable audible notifications for specific tasks like builds, tests, or code reviews.

## It's working if

- Your current speech settings are printed accurately upon invocation.
- Updates are saved directly into `.speak.md` without damaging custom comments.
- You hear a short one-sentence confirmation in the newly selected voice or tone.
- Subsequent calls to [speak](https://aihero.dev/skills-speak) immediately reflect the updated preferences.

## Where it fits

A reach-for-it-anytime standalone adjustment tool. It modifies the configuration created by [setup-speak](https://aihero.dev/skills-setup-speak) and read by [speak](https://aihero.dev/skills-speak). Point to [ask-matt](https://aihero.dev/skills-ask-matt) to see how it fits alongside the rest of the skills.
