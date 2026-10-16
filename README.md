# Space Exploration Quiz

A ten-question, multiple-choice quiz about space exploration and the solar system.
Get instant answer feedback, track your progress, and see your final score.
Your best score is saved in your browser's local storage when available.
The interface supports light and dark color schemes.

## Play online

Visit [Space Exploration Quiz](https://zihyeon08.github.io/space-quiz/).

## Run locally

Clone this repository and open `index.html` in a modern web browser.
No installation, build step, or server is required: all HTML, CSS, and JavaScript
are contained in that file.

To check changes, reload the page, answer the questions, and use **Try Again**
on the results screen.

## Deployment

GitHub Pages uses **GitHub Actions** as its publishing source.
The workflow in `.github/workflows/pages.yml` prepares and uploads a site artifact
containing only `index.html`; no compilation is needed.
Pull requests targeting `main` run the preparation job without deploying.
Pushes to `main` deploy the site automatically, and the workflow can also be
run manually from the Actions tab on `main`.

Deployment status and logs are available in the repository's
[Actions tab](https://github.com/zihyeon08/space-quiz/actions/workflows/pages.yml).
