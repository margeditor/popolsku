# Polish sounds — a pronunciation guide

A single-file interactive pronunciation guide for English speakers learning Polish. Six clickable cards cover the main sound groups, with example words, English meanings, phonetic breakdowns, and a speaker button on every word.

## What's in it

- **Six sound categories:** simple vowels, nasal vowels, surprise letters (ł/w/j), hissing sounds (sz/cz/ż/szcz), soft sounds (ś/ć/ź/ń), and the ts family (c/dz/dż)
- **Phonetic guide on every word** — syllables split by ·, stressed syllable in capitals (e.g. `SHKOH · wah`)
- **Speaker button** on every word — click to hear it pronounced
- **Light and dark mode** — respects the system preference automatically
- **No build step, no dependencies** — one HTML file, open in any browser

## Usage

Download `polish-sounds.html` and open it in a browser. No server, no install.

```
open polish-sounds.html
```

## Speaker button

The speaker icon next to each word uses the browser's built-in **Web Speech API** (`speechSynthesis`) with the language set to `pl-PL`. It plays the Polish word using whatever voices are installed on the user's operating system. There are no audio files to host or maintain.

### Best browsers

| Browser | Platform | Polish voice support |
|---------|----------|----------------------|
| Chrome | Windows, macOS, Android | Excellent |
| Edge | Windows | Excellent |
| Safari | macOS, iOS | Good |
| Chrome | iOS | Good (uses iOS voices) |

### Where it may not work

**Firefox** does not bundle its own TTS voices and relies entirely on the OS. On Windows it may work; on Linux it typically produces no audio at all. There is no reliable fix for this without switching to pre-generated audio files.

### Fallback option

If Web Speech API quality is not acceptable on your target platform, the next step is to pre-generate `.mp3` files using a TTS service (Google Cloud TTS, ElevenLabs, or AWS Polly all support Polish) and swap the `speechSynthesis` calls for `new Audio('path/to/word.mp3').play()`.

## Fonts

The file loads **Lora** from Google Fonts, which requires an internet connection on first load (browsers will cache it after that). For fully offline use, remove the two `<link>` tags in the `<head>` and the `--serif` variable will fall back to Georgia.

## File structure

```
polish-sounds.html   # the whole project — HTML, CSS, and JS in one file
README.md
```

## Extending it

All content lives in the `C` array near the top of the `<script>` block. Each entry is either a `"table"` type (used for simple vowels) or a `"groups"` type (used for everything else). Adding a new card means adding a new object to that array; the renderer handles the rest.

The phonetic notation convention is: syllables separated by ` · `, stressed syllable in ALL CAPS. The `ph()` function reads this and highlights the stressed syllable automatically.
