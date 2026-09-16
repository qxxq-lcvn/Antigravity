# Study Timetable Planner

A pastel study planner web app for daily scheduling, monthly focus tracking, mood notes, and Pomodoro workflows.

## Features

- Daily hourly schedule with editable tasks
- Progress tracking for completed study blocks
- Monthly focus goals
- Daily summary notebook and mood tracker
- Pomodoro timer
- Ambient rain audio generator using Web Audio API
- Browser-local persistence via LocalStorage
- Print-ready layout

## GitHub Pages deployment

This project is a static site, so it works well with GitHub Pages.

### Option 1: Manual deployment
1. Push this directory to a GitHub repository.
2. In GitHub, open the repository.
3. Go to Settings > Pages.
4. Select the branch to deploy from, usually `main`.
5. Set the folder to `/` or `/root` depending on your repo structure.
6. Save and wait for the site to publish.

### Option 2: GitHub Actions deployment
This repo includes a workflow to deploy the static site automatically.

1. Push the project to GitHub.
2. In the repo, go to Settings > Pages.
3. Under Source, choose GitHub Actions if prompted.
4. The workflow in `.github/workflows/deploy-pages.yml` will publish the app.

## Dynamic data note

GitHub Pages is static hosting only, so the app keeps its dynamic data in the browser using LocalStorage. That means:

- each user keeps their own planner data on their own device
- there is no shared backend database or multi-user accounts
- the app is ideal for personal productivity use

## Run locally

```bash
cd "d:\Personal\Projects\Antigravity"
python -m http.server 8000
```

Then open http://localhost:8000
