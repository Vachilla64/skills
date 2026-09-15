## What it does

`speak` gives an [agent](https://www.aihero.dev/ai-coding-dictionary/agent) a voice to notify you audibly of progress, completions, findings, or errors. It synthesizes audio through a local neural text-to-speech engine and plays it in the background without needing cloud API keys.

It is strictly **fire-and-forget**. An agent must never block execution waiting for spoken audio to finish playing. It launches playback as an asynchronous background task and immediately proceeds to its next tool call.

## When to reach for it

Type `/speak`, or the agent reaches for it automatically when a task fits.

Reach for it whenever you want ambient audio notifications while working on other things. The agent speaks at natural milestones: starting a major task, completing a build or test suite, reporting an error, or surfacing a critical diagnostic finding.

For configuring your audio engine, auditioning voices, or setting up triggers, use [setup-speak](https://aihero.dev/skills-setup-speak) first. To tweak your active settings later, use [edit-speak](https://aihero.dev/skills-edit-speak).

## Prerequisites

A running local text-to-speech engine (Pocket-TTS, Kokoro-FastAPI, or Kitten TTS). Run [setup-speak](https://aihero.dev/skills-setup-speak) once to install an engine and write your initial configuration.

## Audio without stalling the workflow

Spoken audio takes seconds to play aloud. If an agent pauses its loop while audio plays, multi-step workflows grind to a halt.

`speak` treats voice as an ambient side channel. The audio generation and output process runs detached in the background. The agent reports its message to the TTS engine and moves on without waiting for playback to conclude.

## Concurrency in multi-agent swarms

When multiple subagents operate concurrently, they often finish their respective tasks at nearly the same moment. Without coordination, multiple voices speak over one another.

`speak` relies on a lightweight file lock. Each speaking process acquires a lease with a timestamp. If another agent is actively speaking, incoming notifications queue or defer until the lock clears, preventing overlapping speech.

## It's working if

- You hear natural audible updates when long tasks or builds finish without touching the terminal.
- The agent continues editing files or executing commands while its previous status message is still playing.
- When an error occurs during a background run, you are alerted immediately by voice.
- The agent fails silently without interrupting its work if the local TTS server is stopped.

## Where it fits

A reach-for-it-anytime standalone notification capability. It pairs with [setup-speak](https://aihero.dev/skills-setup-speak) for initial installation and [edit-speak](https://aihero.dev/skills-edit-speak) for preference updates. Point to [ask-matt](https://aihero.dev/skills-ask-matt) to see how it fits alongside the rest of the skills.
