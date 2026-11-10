# The mark (schema 1)

A repository becomes a piece of the observatory's picture with two things:

1. `oco.toml` at its root;
2. the GitHub topic `oco-project`, so the harvest can find it.

```toml
schema = 1                      # this mark's version

[project]
id = "owner/repo"               # the repository
name = "What it is, in a few words"
kind = "device-lab"             # picture | conveyor | device-lab | tool | research
parent = "linux-phone-oco"      # the larger project it belongs to

[exports]                       # tad tables others may read: name = path in this repository
backlog = "data/backlog.json"
```

## The tables a project may export

Standard names, so the pieces join up across projects; each is a tad table (one JSON object per
line) with at least these columns:

| table | columns | what it says |
|---|---|---|
| `backlog` | id, title, status, note, date | the work ahead and done |
| `session_log` | id, entry_date, title, done, considered, rejected | how the work went |
| `test_runs` | id, device_id, run_at, kernel, shell, passed, failed, skipped | what was measured |
| `support_status` | device_id, component_id, status | what works on which device |
| `feature_support` | feature_id, platform_id, status | features against platforms |
| `landscape` | id, name, project, what, for_us, link, checked | the projects around ours |

A project exports only what it keeps; more columns are welcome. The harvest tags every row with the
project it came from.
