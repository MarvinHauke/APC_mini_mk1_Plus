# APC_mini_mk1_Plus

A MIDI Remote Script for the **Akai APC mini mk1** in Ableton Live 12.4, built on Live's
`ableton.v3` framework and tested with Live 12.4.16. Its first mode is a drum step sequencer; more functions for the
same controller will follow.

Not affiliated with Akai Professional or Ableton. "APC" is Akai's trademark, named here only to
say which controller the script is for.

## What it does

Select a MIDI track with a Drum Rack. The sequencer edits the clip in the selected scene's slot.

- **Top four rows:** 32 steps of the selected drum pad. A press sets or clears a note. On an
  empty slot the first press creates a 2-bar clip. Green: a note. Yellow: the playhead. Red:
  beyond the clip's loop end.
- **Bottom four rows, left half:** a 4x4 bank of the Drum Rack's pads. A press plays the pad and
  selects it for the steps. Scene buttons 5-6 scroll the bank by a row.
- **Bottom four rows, right half, top row:** the steps' resolution (1/32, 1/16, 1/8, 1/4); the
  active one is yellow. Scene buttons 1-2 step it finer or coarser.
- **Track buttons 1-8:** pages of 32 steps. While the clip plays, the steps follow the
  playhead's page.
- **Scene buttons 3-4:** previous and next scene. **7-8:** previous and next track.
- **Faders 1-8:** the volumes of tracks 1-8. **Fader 9:** the master volume.

The selected MIDI track is armed for the pads (Live's auto-arm). A Drum Rack inside an
Instrument Rack counts too; on a track without a Drum Rack the grid stays dark. The full description is the docstring of
`APC_mini_mk1_Plus/__init__.py`.

## Install

Copy the folder `APC_mini_mk1_Plus` into `Remote Scripts` in your User Library
(`~/Music/Ableton/User Library/Remote Scripts/` on macOS), restart Live, and in
Settings → Link, Tempo & MIDI choose **APC_mini_mk1_Plus** as a Control Surface, with the
APC mini as its input and output.

With [ableton-remote-script-mcp](https://github.com/MarvinHauke/ableton-remote-script-mcp)
installed, `ableton-remote-script-mcp install APC_mini_mk1_Plus` checks the script against your
Live build and copies it.

## Develop

This repo is written with ableton-remote-script-mcp and is its real-world test field; that repo
holds it as a submodule. Plan and decision numbers in comments (such as "plan 0003 Decision 32")
refer to the plans in that repo's `docs/feature-plans/`.

- **Editor completion:** in your clone of ableton-remote-script-mcp, after
  `uv run ableton-remote-script-mcp build-index`, run
  `uv run ableton-remote-script-mcp build-stubs --build 12.4.16 --project path/to/APC_mini_mk1_Plus`
  (this repo's root). It writes type stubs of your Live build into `stubs/` and keeps the
  existing `pyrightconfig.json` and ignore line. The stubs are made from Ableton's code, so they
  are git-ignored and stay on your machine.
  [Editor setup](https://marvinhauke.github.io/ableton-remote-script-mcp/editor-setup/) has the
  editor configuration.
- **Test rig:** `APC_mini_mk1_Plus/checks.yaml` and `device.yaml` are for the tool's test rig
  (in the clone: `uv run ableton-remote-script-mcp rig run path/to/APC_mini_mk1_Plus/APC_mini_mk1_Plus/checks.yaml`).
  Live ignores both files.

## Licence

MIT, see `LICENSE`.
