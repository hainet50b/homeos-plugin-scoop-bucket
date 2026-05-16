# homeos-plugin-scoop-bucket

![License](https://img.shields.io/badge/license-MIT%20OR%20Apache--2.0-blue)

A [homeos](https://github.com/hainet50b/homeos) plugin that adds a [Scoop bucket](https://github.com/ScoopInstaller/Scoop/wiki/Buckets) on Windows. Use it as a dependency of packages installed via the [scoop plugin](https://github.com/hainet50b/homeos-plugin-scoop) when those apps live in an additional bucket.

## Usage

Add the plugin to your homeos repository:

```sh
homeos plugin add scoop-bucket
```

Define a setup package that adds the bucket, and have the actual package depend on it:

```sh
$ homeos package add scoop-bucket-extras --plugin scoop-bucket --param name=extras
$ homeos package add vscode --plugin scoop --param app=vscode --depends-on scoop-bucket-extras
```

## Parameters

| Parameter | Description |
|-----------|-------------|
| `name` | Bucket name (e.g., `extras`) |

## Actions

| Action | Command |
|--------|---------|
| install | `scoop bucket add {{name}}` |
| update | None — buckets refresh via `scoop update` (skipped automatically) |
| uninstall | `scoop bucket rm {{name}}` |

## License

Licensed under either of

 * Apache License, Version 2.0
   ([LICENSE-APACHE](LICENSE-APACHE) or <http://www.apache.org/licenses/LICENSE-2.0>)
 * MIT license
   ([LICENSE-MIT](LICENSE-MIT) or <http://opensource.org/licenses/MIT>)

at your option.

## Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.
