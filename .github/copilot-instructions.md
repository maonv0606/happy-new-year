# Copilot Instructions - Happy New Year Countdown

## Project Overview

Vietnamese Lunar New Year (Tết) celebration website with a two-phase user flow. **No build tools** - pure vanilla HTML/CSS/JavaScript.

## Architecture

```
index.html → app.js (countdown) ──[redirect on zero]──→ intro.html → intro.js (celebration)
     ↓                                                        ↓
  style.css                                              intro.css
```

- [data.js](../data.js) defines personalization data (not yet wired into UI)

## Critical Configuration

### Countdown Target Date

Update **only** the date string in [app.js](../app.js#L1):

```javascript
var fut = new Date("jan 29, 2025 00:00:00").getTime(); // Lunar New Year 2025
```

The redirect to `intro.html` triggers automatically when countdown reaches zero (line 19).

### Page Titles & SEO

Update year references in:

- [index.html](../index.html#L9) - `<title>Happy New Year 2026</title>`
- [intro.html](../intro.html#L14-L25) - Open Graph meta tags for social sharing

## Animation Pattern

All celebration animations use CSS class toggling. The `.active` class triggers `@keyframes` defined in [intro.css](../intro.css):

```javascript
// intro.js - button click reveals all decorative elements
element.classList.toggle("active");
```

Key animated elements: `.flower-img`, `.circle`, `.cat`, `.mail`, `.rhombus`

## Audio

Background music auto-plays on first button click ([intro.js](../intro.js#L48-L53)):

- Audio file: `image/nhac.mp3`
- Controlled via `mySong.play()` / `mySong.paused`

## Assets

All media lives in `/image/`:

- Backgrounds: `bgr.jpg`, `background.jpg`
- Animations: `Lion-dance.gif`, `Lion-dance2.gif`
- Decorations: `flower*.png`, `lanterns*.png`, `apricot-blossom.png`
- Personalization: `tham.jpg` (recipient photo for OG image)

## Development

```bash
# Serve locally (any static server works)
python3 -m http.server 8000
# Then open http://localhost:8000
```

Or open `index.html` directly in browser (audio may require user interaction first).

## Quick Reference

| Task                            | File(s)                                                         |
| ------------------------------- | --------------------------------------------------------------- |
| Change countdown date           | [app.js](../app.js#L1)                                          |
| Update year in titles           | [index.html](../index.html#L9), [intro.html](../intro.html#L30) |
| Modify celebration animations   | [intro.css](../intro.css)                                       |
| Add click interactions          | [intro.js](../intro.js)                                         |
| Personalize greeting recipients | [data.js](../data.js) (needs UI integration)                    |
