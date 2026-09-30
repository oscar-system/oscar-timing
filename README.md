# OSCAR Timing Dashboard

This repository provides a web dashboard which collects,
visualizes, and compares timing information from the OSCAR benchmark
infrastructure.

## Live Dashboard

Visit: **https://speed.oscar-system.org**

## How to run locally

From the repository root, execute

```bash
python3 -m http.server
```

and open the link shown in the terminal.

## Data Pipeline

A dedicated server (`build-bench`) periodically (approximately every
three hours) fetches the latest changes from the OSCAR repository. If
new commits are available, it benchmarks them one at a time in
chronological order.

The benchmarking process produces timing data, which are committed to
this repository. Since the dashboard is hosted as a GitHub Pages site,
pushing the updated data automatically updates the website.

## License

MIT
