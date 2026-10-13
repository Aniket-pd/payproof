# PayProof demonstration source

Editable 1920×1080, 30 fps rehearsal: **4,739 frames / 2:37.967**. It combines real app screenshots, recorded synthetic evaluation evidence, generated stock narration and timed captions. Actual PayPal Sandbox execution remains unverified and is explicitly disclosed. This is a local review artifact; it has not been published to YouTube or submitted.

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

Before a final submission recording, complete actual Sandbox verification, replace the conditional integration segment with captured evidence, and update the closing. Preserve simulator, recorded-AI and mock labels. Retain all failed or inconclusive outcomes. See [asset attribution](NOTICE.md), [demo evidence](../docs/demo-script.md), and the [submission checklist](../docs/submission.md).
