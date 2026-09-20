# Pet Arena

Open `dist/index.html` in a modern browser. No install or server required.

Choose one of eight pets and collect the most tokens in a three-minute round. Maps change every 30 seconds. Clover Canopy has normal gravity, Moon Mochi has low gravity, and Sunset Speedway increases movement speed.

- A/D or arrow keys: move
- Space/W/Up: jump (release early for a shorter keyboard jump)
- J: dash into rivals
- K: use Star Burst when charged
- Escape: pause
- Touch: use the on-screen buttons

Tokens increase score and size, up to 3× at 150 tokens. Land on rivals or dash into them to spill tokens. Larger pets can knock aside smaller pets. Invulnerability briefly protects a pet after a hit. Shield, magnet, and speed boosts last nine seconds. Spring pads launch pets toward higher routes. Glowing ground patches spill tokens and bounce pets away. Token storms arrive every 20 seconds.

The eight original pets use an ImageGen sprite atlas and procedural idle, running, airborne, dash, and hit motion. The requested hatch-pet skill was not available. Music and sound effects are synthesized locally after play begins.

Art: built-in ImageGen. Prompt: “Create a game sprite atlas on transparent background, exactly 4 columns by 2 rows of equal sized cells. Eight original cute rounded pets, one centered fully contained in each cell with generous transparent padding. Row 1: mint green leaf-eared bunny; peach orange round fox; lavender tiny horned dragon; sky blue axolotl. Row 2: pink round cat with star forehead; yellow fluffy chick with sprout; turquoise tiny turtle; purple moth kitten. Consistent delightful polished 3D clay toy style, big expressive dark eyes, full bodies facing slightly right, tiny feet, soft shading. No text, no grid lines, no shadows outside characters, no props.”

Artwork: `dist/pets.png`. Game source: `dist/game.js`, `dist/style.css`, and `dist/index.html`.

## Project structure

```text
codex-pet-arena/
  dist/
    index.html       Game interface and entry point
    style.css        Responsive desktop and touch interface
    game.js          Canvas rendering, physics, AI, audio, and gameplay
    pets.png         Eight original pet sprites
  .github/workflows/pages.yml
  README.md
```

## Run locally

Extract the ZIP and open `dist/index.html` in a current Chrome, Edge, Firefox, or Safari browser. The game has no package dependencies, build step, API keys, or external asset requests. Audio starts after you press Play.

For a local HTTP preview, if Python is installed:

```sh
python -m http.server 8080 --directory dist
```

Then open http://localhost:8080 in your browser.

## Upload to GitHub

1. Create a new GitHub repository.
2. Extract this archive and upload the contents of `codex-pet-arena/` into the repository root. Include the hidden `.github` directory if you want the deployment workflow.
3. Keep all four files inside `dist/` together so the artwork and scripts load correctly.

Alternatively, from the extracted project folder:

```sh
git init -b main
git add .
git commit -m "Add Codex Pet Arena"
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
git push -u origin main
```

## Publish with GitHub Pages

A deployment workflow is included. It uploads `dist/` directly; no compilation is required.

1. In your repository, open **Settings → Pages** and choose **GitHub Actions** as the build source.
2. Open **Actions → Deploy game to GitHub Pages → Run workflow**, or push a change to `main`.
3. When the deployment completes, open the URL shown in the deployment result.

Your GitHub account and repository must support GitHub Pages. The workflow publishes only the game files in `dist/`.

## Verification

The delivered build was checked in desktop and emulated mobile Edge with keyboard movement, jumping, touch movement, pause/resume, combat spills, the 3× growth cap, and five map transitions. No browser errors occurred in those checks. The measured mobile-emulation frame time was approximately 16.6 ms; performance varies by device. Physical mobile devices and other browser engines have not been tested.

## Implementation notes

- Single-player only: all seven rivals run locally in the browser.
- Canvas 2D rendering with a generated sprite atlas and procedural animation.
- Three-minute rounds; maps rotate every 30 seconds.
- No server, analytics, account system, or saved progress.
- This archive contains source and artwork, not Git history or private hosting configuration.
