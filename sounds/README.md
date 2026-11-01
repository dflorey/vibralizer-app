# Example recordings

Recordings played from the recordings slider, analysed like a note played into the microphone.
Each is listed in `src/examples.ts` in its slot (of five), with the player's name shown in the
readout; a slot without one shows "No recording" until a note you play is kept there.

| Slot | File             | Violin              |
| ---- | ---------------- | ------------------- |
| 1    |                  | (empty)             |
| 2    | `heifetz.wav`    | Jascha Heifetz      |
| 3    | `ostrakh.wav`    | David Oistrakh      |
| 4    | `horschhorn.wav` | Philippe Hirschhorn |
| 5    | `vengerov.wav`   | Maxim Vengerov      |

Viola, cello, flute and trumpet have none yet.

## Making a sample

`npm run sample -- <recording.mp3|.wav> <instrument> <position>` finds the longest held notes in a
recording (one pitch, give or take the vibrato, for over 2 s) and writes the best one here as
`<instrument>-<position>.wav`, normalised; add it to `src/examples.ts` (or rename it). `--list`
only lists the candidates, `--pick N` or `--at SECONDS` takes another. A transfer running fast or
slow (common with 78s: every note off by the same amount) is put back to speed. Convert other
formats (M4A, FLAC) to WAV first.

Tips for good results:

- One held note: a note is recorded for at most 5 s, until its level drops.
- Solo, without accompaniment, so the pitch can be read.
- Normalised to about −3 dBFS peak: a note is only recorded above −42 dBFS (RMS) and ends 30 dB
  below its loudest point (never below −52 dBFS).
- Small files: they are downloaded when played, and the installed app keeps them for offline use
  once played.
- Make sure the recordings may be used: most commercial recordings are under copyright.
