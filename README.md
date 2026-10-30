# Watchly keep-awake

A scheduled GitHub Action that opens https://watchly.azurewebsites.net/health every 10 minutes.

Watchly runs on Azure's free tier, which puts the site to sleep after about 20 minutes without visitors. While it's asleep, its background jobs (checking for new episodes, refreshing which services titles are on, and the 6pm notification round-up) don't run. This ping keeps it awake.

- It only sends a plain request to a public page; there are no secrets here.
- It's in its own public repo because GitHub Actions are free and unlimited on public repos, but limited to 2,000 minutes a month across all private repos.
- The app itself is in the private repo `GSymes/Watchly` (see `docs/KEEP-AWAKE.md` there).
- To stop it: Actions > Keep Watchly awake > ⋯ > Disable workflow, or delete this repo.
- GitHub may run scheduled jobs a few minutes late. It also turns off schedules in public repos after 60 days with no commits, so on the 1st of each month the workflow makes an empty "keep-alive" commit. If the round-up notifications ever stop, check the Actions tab here.
