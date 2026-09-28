# Needle Drop

Needle Drop is a private, browser-based music flashcard app for learning to identify songs and artists by ear. Choose a folder of MP3 files, listen to a short excerpt, reveal the answer, and rate how well you remembered it.

**Your music stays on your device.** The app runs entirely in the browser and does not upload audio files to a server.

## Features

- Select a local folder of MP3 files or drag MP3s into the app
- Start excerpts at the beginning, at a random point 20–60 seconds in, or use a mix of both
- Choose an excerpt length from 5–10 seconds
- Practice the song title, artist, or both
- Optionally continue playback after revealing the answer
- Rate each answer as **Missed**, **Almost**, or **Know**
- See missed songs more often using lightweight spaced repetition
- Keep review history and corrected metadata in browser storage
- Use the responsive interface on desktop or mobile browsers

## Using the app

1. Open the [hosted app](https://nosejam.github.io/music_flashcards/) or open `index.html` locally in a modern browser.
2. Choose a folder containing MP3 files. Browsers do not remember file access, so you will select the folder again when returning to the app.
3. Listen to the excerpt and try to name the requested song information.
4. Select **Reveal answer**.
5. Correct the inferred title or artist if necessary, then choose **Missed**, **Almost**, or **Know**.

Review history is stored locally in the browser. **Reset review history** clears scores and any title or artist corrections.

## MP3 filenames

Needle Drop infers metadata from filenames because the app has no external dependencies and does not read ID3 tags. For the best results, name files like this:

```text
Artist - Song Title.mp3
```

A leading track number is ignored:

```text
01 - Artist - Song Title.mp3
```

If a filename does not contain ` - `, the full filename is treated as the song title and the artist is shown as unknown. You can correct either field after revealing a card; that correction will be remembered in the current browser.

## Spaced repetition

New and missed songs receive more selection weight. A missed song becomes due again after roughly 3 minutes, an almost-correct song after roughly 15 minutes, and known songs receive progressively longer intervals. If nothing is currently due, the app still chooses from the full library so a session can continue.

## Run locally

There is no build step or package installation. Either open `index.html` directly or serve the directory with any static web server:

```bash
python3 -m http.server 8000
```

Then visit <http://localhost:8000>.

## Browser support and privacy

The directory picker works best in current Chromium-based browsers. Drag-and-drop can be used where directory selection is not supported. Audio files are accessed through temporary browser object URLs and are never transmitted by this app. Only review scores, scheduling data, and metadata corrections are saved in `localStorage`.

## Project structure

```text
index.html  Application, styles, and JavaScript
README.md   Project documentation
```

## License

This project is available under the [MIT License](LICENSE).
