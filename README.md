# AI News Updator Work3

[![Website](https://img.shields.io/badge/Website-Live-0A7A5A)](https://giao-123-sun.github.io/AI_news_updator_work3/)
[![Digest](https://img.shields.io/badge/Digest-AI--Style-1f6feb)](https://giao-123-sun.github.io/AI_news_updator_work3/web/index.html)
[![Python](https://img.shields.io/badge/Python-3.10%2B-3776ab)](#quick-start)
[![License](https://img.shields.io/badge/License-MIT-lightgrey)](./LICENSE)

An end-to-end X intelligence pipeline that crawls posts, filters low-signal content, classifies insights, and generates readable web outputs for daily decision-making.

## Table of Contents

- [Live Website](#live-website)
- [What You Get](#what-you-get)
- [Architecture](#architecture)
- [Project Structure](#project-structure)
- [Quick Start](#quick-start)
- [Deployment](#deployment)
- [Roadmap](#roadmap)

## Live Website

- Home: https://giao-123-sun.github.io/AI_news_updator_work3/
- Digest (replica): https://giao-123-sun.github.io/AI_news_updator_work3/web/index.html
- Archive: https://giao-123-sun.github.io/AI_news_updator_work3/web/archive.html
- Search: https://giao-123-sun.github.io/AI_news_updator_work3/web/search.html

## What You Get

- Source crawling from configured X accounts.
- Reply/original mixed stream parsing with image capture.
- Dedup + precision filtering to remove noisy/marketing-only posts.
- Category outputs:
  - tool sharing (+ links + images)
  - usage experience (+ images)
  - news/paper tracking (+ paper links + title context)
- Readable pages:
  - daily digest
  - searchable archive
  - methodology and source mapping

## Architecture

```text
data/X.txt + cookies
        |
        v
x_user_crawler.py
        |
        v
structured csv/json outputs
        |
        +--> build_insight_hub_v1.py
        +--> build_longreads_v1.py
        +--> build_ai_digest_clone.py
        |
        v
report/* (local generated)
        |
        v
web/* (deployable static site)
```

## Project Structure

- `x_user_crawler.py`: crawl + classify + quality scoring.
- `build_insight_hub_v1.py`: feed/hub/brief/idea-compare pages.
- `build_longreads_v1.py`: reading-friendly long-form pages.
- `build_ai_digest_clone.py`: AI-digest style static pages.
- `run_daily_pipeline_v1.py`: one-command build runner.
- `qa_capture_*.py`: visual QA screenshot scripts.
- `web/`: static site files deployed by GitHub Pages.
- `docs/`: architecture, design, functions, progress docs.
- `config/`: model/prompt settings (secrets ignored).

## Quick Start

1. Prepare source and auth:
- put account list in `data/X.txt`
- put X cookie in `human_comment/cookies.txt`

2. Run crawl:
```bash
python x_user_crawler.py
```

3. Build all outputs:
```bash
python run_daily_pipeline_v1.py
```

4. Sync deployable site:
```powershell
Copy-Item report\ai_digest_clone\* web -Recurse -Force
```

5. Optional visual QA:
```bash
python qa_capture_hub_v1.py
python qa_capture_longreads_v1.py
python qa_capture_ai_digest_clone.py
```

## Deployment

This repo uses GitHub Pages from `main` branch root.  
Site entry is [index.html](./index.html), and digest assets are served from `web/`.

If pages are not enabled yet:
- Repository Settings -> Pages
- Source: `Deploy from a branch`
- Branch: `main` / `root`

## Roadmap

- Better ad/PR filtering before long-form generation.
- Stronger conversation thread capture (replies/comments).
- Per-topic trend cards and change-over-time visualizations.
- Fully automated daily publish workflow.

