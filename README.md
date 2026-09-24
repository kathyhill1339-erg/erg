# erg

*early energy. lasting wealth.*

erg is an interactive website that teaches young adults how the global monetary system works. Each module poses a question, asks the learner to commit to a prediction, and then lets the learner build and run a real model in the browser.

## How the site is built

The site uses a deliberately simple architecture so that it costs nothing to host and requires no maintenance of servers or build tools.

- Every page is a static HTML file written in plain JavaScript, with no framework and no build step.
- GitHub Pages serves the files directly from this repository.
- [Pyodide](https://pyodide.org) runs real Python (with NumPy) inside the learner's browser, so no installation or account is needed.
- [Plotly](https://plotly.com/javascript/) draws the interactive charts.
- One shared stylesheet, `assets/erg.css`, holds the brand colors and fonts, so a change there updates every page.

## Repository layout

```
index.html                     Home page and module list
assets/erg.css                 Shared brand stylesheet (colors, fonts, components)
assets/bee.svg                 Bee mark used in the header and browser tab
lessons/purchasing-power.html  Module 2, the first complete lesson and the template for new ones
.nojekyll                      Tells GitHub Pages to serve files as they are
```

## Adding a new module

1. Copy `lessons/purchasing-power.html` to a new file in `lessons/`, such as `lessons/what-is-money.html`.
2. Replace the lesson text in each of the four steps (predict, model, reconcile, inspect).
3. Replace the Python in the `PY_MODEL` string with the new model. The model receives its inputs as Python globals and returns a dictionary to JavaScript.
4. Update the chart and results panels to display the new outputs.
5. In `index.html`, change the module's card from a `div` with the class `planned` to a link (`a`) that points to the new file, and change its tag to "Available".

## Publishing with GitHub Pages

1. Open the repository on GitHub and select **Settings**, then **Pages**.
2. Under **Build and deployment**, set the source to **Deploy from a branch**, choose the `main` branch and the `/ (root)` folder, and save.
3. After a minute or two, GitHub displays the public address of the site on the same page.

GitHub Pages for a private repository requires a paid GitHub plan. On a free plan, the repository must be public before Pages will publish it.

## Previewing locally

Open a terminal in the repository folder and run `python3 -m http.server`, then visit `http://localhost:8000`. The pages need an internet connection to load Pyodide, Plotly, and the fonts.

## Disclaimer

erg is an educational project. Nothing on this site constitutes financial advice.
