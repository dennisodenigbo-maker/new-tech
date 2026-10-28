# ODB AI — Vercel-ready website

This package is arranged so Vercel can publish the frontend from one explicit output directory. The static website files are in `public/`, and `vercel.json` points directly to that directory. There is no catch-all rewrite that could accidentally mask missing static assets.

## Deploy the frontend
1. Extract this ZIP into a folder.
2. Push the folder contents to a GitHub repository.
3. In Vercel, import that repository.
4. Set **Root Directory** to `./` (the repository root).
5. Set **Framework Preset** to `Other`.
6. Set **Build Command** to empty/disabled (this frontend needs no build step).
7. Set **Output Directory** to `public`.
8. Deploy, then open the Production deployment URL shown by Vercel.

The root `vercel.json` already specifies `public` as the output directory. Make sure the Vercel Root Directory is the repository root, not `backend` or `public`.

## Check the deployed output
The published output must contain `index.html`, `styles.css`, and `app.js`. If the homepage returns 404, open the latest deployment's Build Output and verify those files are present. Confirm you are visiting the latest Production URL, not an older deployment URL.

## Run the frontend locally
Open `public/index.html` in a browser. For a local server, from the project root run:

```bash
python -m http.server 8080 --directory public
```

Then visit `http://localhost:8080`.

## Backend
The `backend/` folder is a separate FastAPI scaffold. This static deployment configuration does not deploy Python routes. Run it locally from `backend/` with:

```bash
pip install -r requirements.txt
uvicorn app.main:app --reload
```

Deploy the backend as a separate service/project and test its `/health` endpoint before connecting the frontend to it.

## Honest feature status
The dashboard, workload planner, and cost estimator are interactive demo functionality. Values and rates are illustrative. Real login, persistent user accounts, production database integration, live provider connections, current cloud pricing, and AI inference require additional backend integrations and credentials.
