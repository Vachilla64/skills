## What it does

`setup-speak` is an interactive onboarding wizard that installs a local neural text-to-speech engine, plays spoken auditions of candidate voices, and configures how and when an [agent](https://www.aihero.dev/ai-coding-dictionary/agent) should speak to you.

It **auditions voices aloud before you choose**. Instead of selecting an abstract voice name from a text menu, the agent renders a sample greeting across candidate voices and plays each sample through your speakers so you hear the exact cadence and timbre before saving your choice.

## When to reach for it

You invoke this by typing `/setup-speak`; the agent won't reach for it on its own.

Run this once when setting up a new machine or configuring a repository for audible notifications. It detects your operating system, walks you through engine selection, and saves your preferences to `.speak.md` in your project root or `~/.config/speak/config.md` globally.

To modify your voice, tone, or frequency later without repeating engine installation, use [edit-speak](https://aihero.dev/skills-edit-speak). To fire speech notifications during work, see [speak](https://aihero.dev/skills-speak).

## Three local engines for different constraints

`setup-speak` supports three open-weight local speech engines:

| Engine | Ideal Scenario | Highlights |
|---|---|---|
| **Pocket-TTS** | Conversational identity | 100M parameters, CPU-first, zero-shot voice cloning from a 5-second audio clip, MIT license. |
| **Kokoro-82M** | Multilingual breadth | 82M parameters, 54+ studio voices across 8 languages, StyleTTS 2 architecture, Apache 2.0. |
| **Kitten TTS** | Minimal memory footprint | 15M to 80M parameters (under 25 MB INT8 on disk), runs in under 35 MiB RAM on pure ONNX. Set speed to 1.25 for natural cadence. |

## Shaping your agent's persona

Voice notifications are only valuable if they do not become noisy or irritating. `setup-speak` helps you calibrate three parameters:

- **Tone**: Choose `conversational` for natural updates, `formal` for neutral reporting, or `minimal` for clipped status notices under five words.
- **Frequency**: Limit speech to `completions-and-errors` so you are only notified when a task finishes or crashes, or select `all-milestones` if you want updates at task start and intermediate phases.
- **Task categories**: Toggle speech on or off for test runs, code reviews, research legwork, and background builds.

## It's working if

- Your host operating system is detected accurately without manual configuration.
- You hear spoken audio samples played through your speakers during the voice audition step.
- A clean `.speak.md` configuration file is written to your workspace.
- The [speak](https://aihero.dev/skills-speak) skill uses your chosen voice on subsequent runs.

## Where it fits

A run-once setup skill. It creates the configuration that [speak](https://aihero.dev/skills-speak) consumes on every run, and pairs with [edit-speak](https://aihero.dev/skills-edit-speak) for subsequent adjustments. Point to [ask-matt](https://aihero.dev/skills-ask-matt) to see how it fits alongside the rest of the skills.
