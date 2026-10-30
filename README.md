# sim_notify Web (HW5 web app, v2.0)

Static single-page app. Everything runs in the browser; no log content leaves your machine.

- Section 0: live notifications. The page subscribes to the same ntfy topic that `sim_notify.py` posts to (`/topic/json?poll=1&since=48h` for history, `/topic/sse` for live). The topic name is typed in by the user and kept in that browser only (localStorage); it is never in the page source or the repo. Optional browser (OS) notification via the Notification API. Test from the server with `python3 sim_notify.py test`.

- Section 1: load `runs.csv` (from `sim_notify.py --runs`) or `synth_logs/index.csv` (archive index from `pull_synth_logs.sh`) -> history table, KPIs, NEW/known bar chart, built-in `verify` (archive mode: flags check=MISMATCH only). A file without timestamp/status/errors columns is rejected with a message.
- Section 2: load a simulator/synthesis log -> same rules as `sim_notify.py` v2.6 (profiles vcs / xcelium / dc, `--new-only`).
- Section 3: edit the human-approved `known_errors.txt` (saved in this browser only; download to use on the server).
- Section 4: triage excerpt (first N errors, +/- context, path masking) to paste into an AI for cause candidates.

Run locally: open `index.html` in a browser, or `python3 -m http.server 8080` in this folder and visit http://localhost:8080
Deploy (optional): push this folder to GitHub -> Vercel "Import" -> Framework "Other", no build step.
