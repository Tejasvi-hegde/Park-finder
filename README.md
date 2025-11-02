# Park-finder

A  web application to find and display park locations and work with polygon generation scripts. It helps to find the parking spaces by using the already installed CCTV.

 The project combines a Node.js + Express backend with EJS views and client-side assets, and includes several Python utilities for polygon creation and geoprocessing located in the `programs/` folder.

This README explains how to set up and run the project locally, what each folder contains, and helpful notes for development and contribution.

## Table of contents

- [Quick start](#quick-start)
- [Prerequisites](#prerequisites)
- [Install](#install)
- [Run the app](#run-the-app)
- [Python utilities](#python-utilities)
- [Project structure](#project-structure)
- [Development notes](#development-notes)
- [Troubleshooting](#troubleshooting)
- [Next steps & suggestions](#next-steps--suggestions)
- [License](#license)

## Quick start

1. Install Node.js dependencies

```bash
npm install
```

2. Run the server (development)

```bash
npm start
# or
node app.js
```

3. Open a browser and navigate to:

```
http://localhost:3000
```

If your app uses a different port, set the `PORT` environment variable before starting.

## Prerequisites

- Node.js (v14+ recommended)
- npm (comes with Node.js)
- Python 3.8+ (for the scripts in `programs/`) and pip

Optional tools for development:

- nodemon (for auto-restart during development): `npm install -g nodemon`

## Install

1. Clone the repository and change into the project directory

```bash
git clone <repo-url>
cd Park-finder
```

2. Install dependencies

```bash
npm install
```

3. (Optional) Install Python dependencies used by the scripts in `programs/`.

If a `programs/requirements.txt` file exists, run:

```bash
python -m pip install -r programs/requirements.txt
```

If not, install packages as needed (e.g. OpenCV, Shapely) depending on which scripts you use.

## Run the app

Start the server:

```bash
npm start
# or
node app.js
```

Common environment variables:

- `PORT` — port to run the Express server on (default in code is often 3000)
- any DB or API keys used by your app if added later

## Python utilities

The `programs/` folder contains Python scripts used for polygon generation and other utilities. Example files:

- `create_polygons.py` — generate polygon geometries (usage depends on script arguments)
- `create.py`, `hi.py`, `main.py`, `main_with_Trackbars.py` — helper scripts for processing and experiments

To run a script:

```bash
python programs/create_polygons.py [args]
```

Read the top of each Python file for usage instructions or open the script to inspect CLI arguments.

## Project structure

Top-level files and folders (key ones shown):

- `app.js` — main Express application entrypoint
- `package.json` — Node project manifest and scripts
- `public/` — client-side assets (JS/CSS)
  - `index.js` — client-side JS
  - `css/` — stylesheets (`main.css`, `style.css`)
- `views/` — EJS templates for server-side rendering
  - `home.ejs`, `login.ejs`, `map.ejs`, `register.ejs`
  - `partials/header.ejs`
- `programs/` — Python utilities and experiments
  - `create_polygons.py`, `create.py`, etc.

This repository uses EJS for server-side templating and serves static assets from `public/`.

## Development notes

- If you want live reloading while editing server code, install `nodemon` and run `nodemon app.js`.
- Add a `.env` file for environment variables (and use `dotenv` in `app.js` if desired).
- Add a `programs/requirements.txt` file listing required Python packages for easier setup.

Edge cases & suggestions

- Ensure port collisions are avoided by setting `PORT` if 3000 is in use.
- If pages rely on external APIs, confirm API keys are present in environment variables.

## Troubleshooting

- Server doesn't start: check that required Node packages are installed and no other process is using the configured port.
- Python scripts fail: verify Python version and that required Python packages are installed.
- View errors in browser: open developer console and server logs for stack traces.


