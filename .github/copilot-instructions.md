# Copilot Instructions - Happy New Year Countdown

## Project Overview

A Vietnamese Lunar New Year (Tết) celebration website with two-phase flow:

1. **Countdown phase** (`index.html` → `app.js`) - Timer counting down to a target date
2. **Celebration phase** (`intro.html` → `intro.js`) - Interactive greeting page with animations

**No build tools required** - Pure vanilla HTML/CSS/JavaScript served as static files.

## Architecture & File Relationships

```
index.html ─── style.css ─── app.js (countdown timer)
     │                            │
     └──────── redirects to ──────┘
                    ↓
intro.html ─── intro.css ─── intro.js (interactive celebration)
     │
data.js (personalization config - currently unused)
```

### Critical Flow Pattern

- `app.js` redirects to `intro.html` when countdown reaches zero (`window.location.href="intro.html"`)
- Target date is hardcoded in `app.js` line 1: `new Date("jan 21, 2023 23:59:00")`

## Key Conventions

### Date Configuration

Update the countdown target in [app.js](app.js#L1):

```javascript
var fut = new Date("jan 21, 2023 23:59:00").getTime();
```

### CSS Animation Pattern

Animations use CSS `@keyframes` + JavaScript class toggling via `classList.toggle("active")`:

```javascript
// intro.js pattern - toggle multiple elements simultaneously
boxFlower.classList.toggle("active");
circleActive.classList.toggle("active");
```

### Personalization Data Structure

[data.js](data.js) defines user greeting cards (not yet integrated):

```javascript
{ ma_ten: "id", name: "Display Name", message: "...", img: "url" }
```

## UI Structure

- **Vietnamese language** - All UI text is in Vietnamese (Ngày/Giờ/Phút/Giây)
- **External dependencies**: Font Awesome 6.2.1 (CDN), Google Fonts (Lobster, Caramel, Fredoka One, etc.)
- **Assets** in `/image/` - Background images, decorative elements (flowers, lanterns, lion dance GIFs)

## Development

**Run locally**: Open `index.html` directly in browser or use any static file server

```bash
# Example using Python
python3 -m http.server 8000
```

## Common Tasks

| Task                        | Location                              |
| --------------------------- | ------------------------------------- |
| Change countdown date       | `app.js` line 1                       |
| Modify countdown UI         | `index.html` + `style.css`            |
| Edit celebration animations | `intro.css` (2130 lines of keyframes) |
| Add interactive behaviors   | `intro.js`                            |
| Add new greeting recipients | `data.js` array                       |
