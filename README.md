# ZLATYN — personal clip desk

Paste a YouTube link or drop a video. Zlatyn transcribes it, picks the strongest spoken
hooks, snaps each cut to real sentence boundaries, and exports a clean 9:16 / 1:1 / 16:9 clip
(with audio, no captions, no watermark). Everything except speech-to-text and clip scoring
runs in your browser; projects live in IndexedDB.

## Run

    npm install
    XAI_API_KEY=... npm run dev      # http://localhost:8080

Without `XAI_API_KEY` the app still works: paste a transcript and a local heuristic picks clips.

## Deploy (Vercel)

Set `XAI_API_KEY` in the project's environment variables. The API routes are unauthenticated and
spend that key, so add a Vercel Firewall rate limit (the in-app limiter is per-instance only) or
turn on sign-in before sharing the URL.

## Known limits

- Files over ~700 MB can't be decoded in the browser; paste a transcript instead.
- Export records in real time in the foreground tab (a 30 s clip takes 30 s). Keep the tab visible.
- YouTube caption scraping is unofficial and often blocked from datacenter IPs; uploading the file is the reliable path.
- Pasted transcripts have no timestamps, so cuts are estimated.
