# Lojong Mind Training

Beautiful web pages displaying the 59 traditional Lojong slogans from the Atisha tradition of Buddhist mind training.

## About

The Lojong teachings, also known as "The Seven Points of Training the Mind," are a series of 59 contemplative slogans developed in Tibet. These teachings help practitioners transform difficulties into opportunities for spiritual growth and cultivate compassion and wisdom.

## Features

The site is a single-page app with smooth view transitions between a home
screen, a daily slogan, and a randomly drawn teaching.

### 📅 Daily Practice
- Displays the same slogan each day of the year
- Rotates through all 59 slogans sequentially
- Perfect for consistent daily contemplation

### 🎲 Draw a Teaching
- Shows a different random slogan, with a "Draw New Teaching" button
- Great for spontaneous insight
- Each draw avoids immediately repeating the previous slogan

### ✨ Design: "Sacred Scroll"
Inspired by Tibetan thangka painting and illuminated manuscripts:
- **Palette:** lapis lazuli background, antique gold, deep crimson, ivory parchment
- **Typography:** Cinzel for titles, EB Garamond for the slogans
- **Ornamentation:** layered gold/crimson borders, corner flourishes, and a
  shimmer sweep across the frame
- **Animation:** a counter-rotating dharma wheel, a scroll-unfurl reveal on each
  view, roll transitions between slogans, and a mouse-tracking glow on the draw button
- Each slogan is labelled with its traditional Point (One through Seven)
- Fully responsive
- Slogan numbers are shown out of 59

## The Seven Points Structure

The 59 slogans are organized into seven traditional points:

1. **The Preliminaries** (1 slogan)
2. **Training in Bodhicitta** (9 slogans)
   - Absolute Bodhicitta
   - Relative Bodhicitta
3. **Transforming Bad Circumstances** (6 slogans)
4. **Condensed Practice for One Lifetime** (2 slogans)
5. **Measure of Having Trained the Mind** (4 slogans)
6. **Commitments of Mind Training** (16 slogans)
7. **Guidelines of Mind Training** (21 slogans)

## Usage

Simply open `index.html` in a web browser. The app handles all views internally
via URL hash routing:

- `index.html` - Home screen
- `index.html#daily` - Daily rotating slogan (deep-linkable)
- `index.html#random` - Randomly drawn teaching (deep-linkable)

The legacy `daily-lojong.html` and `random-lojong.html` URLs still work — they
redirect to `index.html#daily` and `index.html#random` respectively, so any
existing bookmarks or links remain valid.

## Publishing

These pages are pure HTML/CSS/JavaScript with no dependencies, making them easy to publish on any static web host.

### Live Site

The site is hosted at [lojong.tributaryrss.com](https://lojong.tributaryrss.com) on a VPS running Caddy.

### Deploying to the Server

**Automated (recommended):** Pushing to the default branch triggers the
`.github/workflows/deploy.yml` GitHub Action, which rsyncs the site to the VPS
over SSH. You can also run it manually from the repo's **Actions** tab via
**Run workflow**.

This requires the following repository secrets to be configured under
**Settings → Secrets and variables → Actions**:

| Secret | Description |
| --- | --- |
| `DEPLOY_SSH_KEY` | Private SSH key authorized on the server (full key contents) |
| `DEPLOY_HOST` | Server hostname or IP (e.g. `tributaryrss.com`) |
| `DEPLOY_USER` | SSH username on the server |
| `DEPLOY_PATH` | Target directory, e.g. `/var/www/lojong/` (trailing slash) |
| `DEPLOY_PORT` | *(optional)* SSH port, defaults to `22` |

**Manual fallback:** from a local checkout with SSH access to the server:

```bash
rsync -avz --exclude='.git' claude-projects/ tributary:/var/www/lojong/
```

### Caddy Configuration

```
lojong.tributaryrss.com {
    encode gzip
    root * /var/www/lojong
    file_server
}
```

## Credits

Traditional Lojong slogans from the Atisha tradition of Tibetan Buddhism. These are ancient public domain teachings that have been passed down through generations of practitioners.

## License

The traditional Lojong slogans are ancient Buddhist teachings and part of our shared spiritual heritage. The web implementation is provided freely for anyone to use, modify, and share.

---

*May these teachings benefit all beings.*
