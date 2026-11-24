# Machine learning lab

Two interactive classroom demos of machine learning, in one site with tabs:

- **Handwriting** (`digits.html`): a small neural network learns to read handwritten digits. Students look at the examples, watch it practice step by step, then draw their own digits to test it and teach it when it's wrong.
- **Colored dots** (`dots.html`): a network learns where orange dots end and blue dots begin on a map. Students pick a puzzle and a "brain", paint their own dots, and see how each neuron draws one straight line that the network combines into curves.

`index.html` is the tab bar that holds both. Switching tabs keeps each demo running where you left it. Each demo also works on its own if you open its file directly.

Everything runs in the browser. There's no server, no install, and no data leaves the page.

## Hosting on GitHub Pages

1. Create a new public repository on GitHub.
2. Upload `index.html`, `digits.html`, `dots.html`, and this `README.md` (Add file > Upload files), then commit.
3. Go to **Settings > Pages**. Under "Build and deployment", set Source to **Deploy from a branch**, pick the `main` branch and the `/ (root)` folder, and save.
4. After a minute or two, the site is live at `https://<your-username>.github.io/<repository-name>/`.

To link straight to one tab, add `#digits` or `#dots` to the end of the address, for example `https://<your-username>.github.io/<repository-name>/#dots`.

## Adding another demo later

Put the new page in the repository as its own `.html` file. Then, in `index.html`, add a tab button and an `<iframe>` like the two that are there, and add its name to the `views` list in the script.

## How it works

- The handwriting practice digits are generated each time the page loads, from 16 handwriting-style Google Fonts with random tilts, slants, and stroke widths. If the fonts can't load (for example, on a filtered network), it falls back to built-in fonts. The network has 784 inputs (one per pixel), 64 hidden neurons, and 10 outputs.
- The dots networks take only two inputs, each dot's left-right and up-down position, and range from no hidden neurons (a single straight line) to two layers of 8.
- Both are written in plain JavaScript with no libraries and trained with the Adam optimizer.
