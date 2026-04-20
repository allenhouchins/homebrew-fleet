# homebrew-fleet

A [Homebrew tap](https://docs.brew.sh/Taps) for Fleet-maintained macOS apps
that aren't in [homebrew-cask](https://github.com/Homebrew/homebrew-cask).

## Install

```sh
brew tap allenhouchins/fleet
brew install --cask <cask-name>
```

Or in one shot:

```sh
brew install --cask allenhouchins/fleet/<cask-name>
```

## Available casks

| Cask | Description |
| ---- | ----------- |
| [`fleet-desktop`](Casks/fleet-desktop.rb) | End-user client for Fleet device management |
| [`druva-insync`](Casks/druva-insync.rb) | Endpoint data backup and recovery client |

## Contributing

- One cask change per PR.
- Keep diffs minimal.
- Every PR runs `brew style` and `brew audit --cask --online` via CI.
- Verify locally before opening a PR:
  ```sh
  brew style Casks/<cask>.rb
  brew audit --cask --online --tap allenhouchins/fleet <cask>
  ```

## Machine-readable API

For each cask, a formulae.brew.sh-shaped JSON file is published at:

```
https://raw.githubusercontent.com/allenhouchins/homebrew-fleet/main/api/cask/<cask>.json
```

These files are regenerated automatically by the
[`publish-cask-json`](.github/workflows/publish-cask-json.yml) workflow on
every push to `main` that touches `Casks/`, so they always reflect the
current cask definitions. Consumers (e.g. the Fleet-maintained apps
ingester) can fetch these directly.

## Updating a cask

```sh
brew bump-cask-pr --tap allenhouchins/fleet <cask>
```

Or manually edit `Casks/<cask>.rb` to bump `version` and `sha256`.

## License

MIT
