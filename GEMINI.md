# MultiScore

A high-performance, mobile-first web application for keeping track of scores for up to 8 players.

## Core Mandates

- **Touch Responsiveness**: The app uses `touch-action: none` on score cards and surgical DOM updates in `renderGame()` to ensure zero-latency feedback and prevent "lost" taps during rapid scoring.
- **Visuals**: Modern, high-contrast UI using Tailwind CSS and Lucide icons.
- **Persistence**: Screen Wake Lock API is used to prevent the device from sleeping during active games.

## Development & Deployment

### Local Development
The project is a single-file application. To test changes:
1. Open `index.html` in any modern web browser.
2. Use Mobile Emulation in DevTools to test touch interactions and orientation changes.

### Deployment Workflow
Since this is a single-file app, deployment consists of pushing the updated `index.html` to the GitHub repository:

```bash
# To deploy changes:
git add index.html
git commit -m "Your description of changes"
git push origin main
```

*Note: If GitHub Pages is enabled for the repository, the app will automatically update at the corresponding URL after pushing.*

## Technical Architecture

- **State Management**: A simple `state` object tracks player count, scores, names, and colors.
- **Rendering**: The `renderGame` function performs a full grid rebuild only on orientation changes or player count updates. For score updates, it performs surgical DOM updates using element IDs (`player-score-X`) to maintain performance and event listener integrity.
