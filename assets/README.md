# Assets

Shared, static resources used across the repo (and safe to reference from individual skills): datasets, schemas, config templates, fonts, and other reference files.

- One subdirectory per category or resource bundle, kebab-case.
- Keep files static — no scripts here (those belong inside a skill's `scripts/`).
- Large binary files are fine, but note that the Vercel Skills CLI caps installs at 10 MiB download / 25 MiB extracted / 1000 files, so anything referenced by a skill must stay under those limits.
