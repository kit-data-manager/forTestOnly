# testPackaging
# ghcr-badge: Generate ghcr.io container's status badge

[![1] ![2] ![4]](https://github.com/VolkerHartmann/testPackaging/pkgs/container/testpackaging)



## Available paths

### `label` parameter

- `label=hello`: ![label=hello](https://ghcr-badge.egpl.dev/eggplants/ghcr-badge/tags?trim=major&label=hello)

### `ignore` parameter

Use the ignore parameter to filter returned tags, supports pattern matching and a comma separated list.

- `ignore=latest` ignores the `latest` tag (default).
- `ignore=sha256*` ignores all tags prefixed with `sha256`.
- `ignore=v0.0.1,latest,sha256*` ignores the `latest` and `v0.0.1` tags, and all tags prefixed with `sha256*`.

### `trim` parameter

- `trim=patch` trims `^v?\d+\.\d+\.\d+[^.]*$` tags.
- `trim=major` trims `^v?\d+\.\d+[^.]*$` tags.

### `color` parameter

Available color names and hex codes are listed on [here](https://github.com/jongracecox/anybadge#colors).

## Note

Generated badge will be cached for 3666 seconds in GitHub's [Camo](https://github.com/atmos/camo) server.
To update immediately, send PURGE request to the badge Camo link.

```bash
curl -X PURGE "https://camo.githubusercontent.com/..."
```

[1]: <https://ghcr-badge.egpl.dev/eggplants/ghcr-badge/tags?trim=major>
[2]: <https://ghcr-badge.egpl.dev/eggplants/ghcr-badge/latest_tag?trim=major&label=latest>
[3]: <https://ghcr-badge.egpl.dev/ptr727/plexcleaner/develop_tag>
[4]: <https://ghcr-badge.egpl.dev/eggplants/ghcr-badge/size>

## Development

1. Install [`poetry`](https://python-poetry.org/docs/#installation)
1. Run `poetry install && poetry shell && pre-commit install`
1. Launch live server with `task dev`Badges:
