# OSCAR Timing Dashboard

A focused static dashboard for visualizing OSCAR benchmark timings.

## Live dashboard

<https://speed.oscar-system.org>

## Run locally

From the repository root, run:

```bash
python3 -m http.server
```

Open the URL shown in the terminal. Opening `index.html` directly does not work
because browsers block its JSON request from a `file:` URL.

On a first visit, individual jobs are selected by default; the aggregate
`test 1.12 short` and `test 1.12 long` jobs start unchecked. Saved or shared
selections override this default, including an explicitly empty selection.

The job counter shows selected and available jobs in the current time range,
search, and Julia version. Its total includes every series in the data file,
including historical and aggregate jobs, so these counts can differ.

## Data pipeline

A dedicated benchmark server periodically checks OSCAR for new commits and
benchmarks them in chronological order. It writes `data/timing_summary.json`
and commits that file here; this repository does not fetch benchmark data.

Each data update adds its source CSV under `data/raw/` and regenerates
`data/timing_summary.json`. The raw files are retained as producer inputs and
as the reproducible archive behind the generated summary.

Pushing to `main` deploys only the dashboard, favicon, domain configuration,
and summary JSON to GitHub Pages. The raw benchmark exports remain in Git but
are intentionally excluded from the public Pages artifact.

## License

[MIT](LICENSE)
