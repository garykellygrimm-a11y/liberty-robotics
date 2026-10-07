# Liberty Robotics — FIRST Team 1764

A rebuild of the Team 1764 website, in progress.

**Design preview:** https://garykellygrimm-a11y.github.io/liberty-robotics/

The preview is not the team's live website. The current site is at
[first1764.com](http://www.first1764.com).

## Status

Design exploration. Four home page directions are mocked up for the team to
choose from:

| Direction     | Folder                   | In short                                         |
| ------------- | ------------------------ | ------------------------------------------------ |
| Archive       | `mockups/archive/`       | Dark and data-dense, led by the season record    |
| Institutional | `mockups/institutional/` | Light and photo-led, for parents and sponsors    |
| Editorial     | `mockups/editorial/`     | Type-led, built around student voices            |
| Bumper        | `mockups/bumper/`        | Built for recruiting, with video and a countdown |

All content in the mockups is placeholder until the items in
[docs/open-questions.md](docs/open-questions.md) are answered.

## How the site gets published

GitHub Pages hosts the design preview only. It publishes from the `main`
branch automatically after every merge.

Once a direction is chosen, the site will be rebuilt in React and TypeScript
with Vite. The approved site will deploy from this repository to the team's
existing web server, so every change goes through the repo. Nobody edits
files directly on the server.

Planned: every pull request will get its own preview link on GitHub Pages, so
you can see a change working before it is merged.

## Project layout

```
liberty-robotics/
├── index.html              Preview landing page, links to each direction
├── mockups/
│   ├── archive/index.html
│   ├── institutional/index.html
│   ├── editorial/index.html
│   └── bumper/index.html
├── docs/
│   └── open-questions.md   What we still need answered
├── .editorconfig           Shared editor settings
└── .gitignore
```

Each direction lives in its own folder as `index.html`, so its address ends
in the folder name, like `/mockups/bumper/`.

## Previewing on your computer

Double-clicking `index.html` opens it, but links to folders will show a file
listing instead of the page. Run a small local web server from the repo's
top folder instead:

```bash
python3 -m http.server 8000
```

On Windows, use `py -m http.server 8000`. Then open http://localhost:8000.
Press Ctrl+C in the terminal to stop the server.

## Making a change

Nothing is pushed directly to `main`. Work happens on a branch and merges
through a pull request.

```bash
git switch main
git pull
git switch -c type/short-slug

# make changes

git add -A
git commit -m "type: what changed"
git push -u origin type/short-slug
```

Then open a pull request on GitHub.

Branch and commit prefixes: `feat/` for something new, `fix/` for something
broken, `docs/` for documentation, `style/` for visual-only changes, and
`chore/` for housekeeping.

### Before you open a pull request

- Preview it locally and click every link on every page you touched.
- Run `git diff --stat main` and check that it lists only the files you
  meant to change.

### Before you merge

- Read the **Files changed** tab, including any renamed files and their new
  paths.
- After merging, give Pages a minute or two, then click through the preview
  site.

## Open questions

See [docs/open-questions.md](docs/open-questions.md). If you answer one,
update that file in the same pull request as the change it unblocks.
