# hypr-paths

Fail-closed XDG config, data, and runtime paths for the hypr suite.

- config: `$XDG_CONFIG_HOME` if set and absolute, else `$HOME/.config`
- data: `$XDG_DATA_HOME` if set and absolute, else `$HOME/.local/share`
- runtime: `$XDG_RUNTIME_DIR` must be set and absolute

There is no `/run/user/<uid>` fallback, no `/tmp` fallback, and no `~`
expansion. Relative or empty XDG values are errors.

`ConfigDirs` is enough for tools that only need config/data.
`BaseDirs` also requires runtime.

This public repo exists so packaged tools can git-depend on the crate.
hypr-commons is private. crates.io publish waits on a registry token.

```toml
hypr-paths = { git = "https://github.com/MasonRhodesDev/hypr-paths", rev = "<sha>" }
```
