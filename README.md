# Po polsku — an interactive guide to Polish

An interactive language learning project for English speakers. Built as a set of standalone HTML modules, each covering a different aspect of Polish. No framework, no build step, no dependencies.

Live site: [margeditor.github.io/popolsku](https://margeditor.github.io/popolsku/)

## Modules

### Polish sounds (`polish-sounds.html`)
A pronunciation guide covering the six main sound groups in Polish — simple vowels, nasal vowels, surprise letters (ł/w/j), hissing sounds (sz/cz/ż/szcz), soft sounds (ś/ć/ź/ń), and the ts family (c/dz/dż). Each group has example words with full phonetic breakdowns.

### Polish basics (`vocabulary.html`)
Essential vocabulary for a week in Poland — 49 words across seven everyday categories (greetings, numbers, getting around, food and drink, shopping, hotel, and emergencies). Built around the 7±2 rule: seven words per card, seven cards total.

Both modules share:
- **Phonetic guide on every word** — syllables split by ·, stressed syllable in capitals (e.g. `SHKOH · wah`)
- **Speaker button** on every word — click to hear it pronounced
- **Light and dark mode** — respects the system preference automatically

## Usage

Open `index.html` in a browser to reach the menu, then navigate to either module. No server, no install required.

```
open index.html
```

Each module also links back to the menu in the footer.

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

All files load **Lora** from Google Fonts, which requires an internet connection on first load (browsers will cache it after that). For fully offline use, remove the two `<link>` tags in the `<head>` of each file and the `--serif` variable will fall back to Georgia.

## File structure

```
index.html           # menu page — links to all modules
polish-sounds.html   # pronunciation guide
vocabulary.html      # vocabulary for travellers
README.md
```

## Adding a new module

1. Create a new HTML file using the same CSS variable structure as the existing modules
2. Add a `← menu` link in the footer pointing to `index.html`
3. Add a card for it in `index.html` following the same `.module-card` pattern
4. Upload both files to the main branch — GitHub Pages will pick them up automatically

## Phonetic notation

Syllables are separated by ` · ` and the stressed syllable is written in ALL CAPS. The `ph()` function in each module reads this format and highlights the stressed syllable automatically. When writing phonetics, favour spellings an English speaker will attempt over spellings that are technically accurate but visually daunting.
