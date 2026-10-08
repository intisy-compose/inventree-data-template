# inventree-data-template

Public default data folder for inventree-compose.

Default `data/` folder for
[inventree-compose](https://github.com/intisy-compose/inventree-compose), so a fresh
`git clone --recursive` runs out of the box.

It is mounted at `data/`: the db-backup sidecar writes its hourly database dumps to `backups/`, the
Tailscale sidecar keeps its node identity (a secret) in `tailscale/`, and `catalog labels` writes
its sheets to `labels/`. All three are runtime state and gitignored. The database and InvenTree's
uploaded files live in Docker volumes; `backups/` is how the database gets back.

## Use your own data

Fork or replace this repo, then point the folder at it from the inventree-compose checkout:

```powershell
.\docker-compose.ps1 data use <owner/repo[@ref]>   # your own data repo, optionally a branch
.\docker-compose.ps1 data use                      # back to this template
```

Commit configuration, not runtime state.

`catalog.toml` is a starter taxonomy for the catalog tool (see the inventree-compose README); replace
it with your own categories, fields, locations and models.

## License

[![MIT License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
