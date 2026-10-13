# PayProof demonstration source

Editable 1920×1080, 30 fps rehearsal: **4,755 frames / 2:38.500**. It combines real app screenshots, recorded synthetic evaluation evidence, generated stock narration and timed captions. The updated Sandbox scene uses screenshots of actual observed test results: seeded excess caught, corrected controls passed, and a fresh two-case Codex run passed with independent refund readbacks. This is a local review artifact; it has not been published to YouTube or submitted.

From this directory:

```sh
npm ci
npm run lint
npm run captions
npm run dev
```

Studio is served only on `127.0.0.1:4324`. Open `http://localhost:4324/PayProof-Demo`. Each of the eight scenes also has a separate editable timeline. The captions are source-relative JSON in `public/captions/` and inline arrays on their scene's `BasicCaptions` node, so Studio can edit them.

Export the rehearsal:

```sh
npm run render
```

Output: `out/payproof-demo.mp4`. `npm run captions` validates the source timing and writes the companion SRT and timing report. Rendering downloads Chrome-for-Testing on first use; it does not call an AI model or payment provider. Chrome-for-Testing avoids a missing `icudtl.dat` helper resource observed with the macOS headless-shell distribution during this edit.

The source audio and captions are already included. To regenerate captions, work in a disposable copy, install `@remotion/whisper-webgpu@4.0.535` plus its documented auxiliary dependencies, ensure FFmpeg is installed, then run `node scripts/transcribe.mjs`. The optional transcription stack is not needed to edit or render this video. Review spelling and timing, copy the new arrays into the scene nodes, and rerun `npm run captions` after editing.

The actual Sandbox verification is documented in the source package. Preserve simulator, recorded-AI, actual-Sandbox and mock labels. Public YouTube delivery and free judging access remain unfinished. Retain all failed or inconclusive outcomes. See [asset attribution](NOTICE.md), [demo evidence](../docs/demo-script.md), and the [submission checklist](../docs/submission.md).
