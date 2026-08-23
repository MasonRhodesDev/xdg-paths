# xdg-paths

Fail-closed XDG config, data, cache, and runtime paths.

XDG Base Directory is the current Wayland/freedesktop path contract
(`$XDG_RUNTIME_DIR/$WAYLAND_DISPLAY` is the compositor socket). It is not
an X11 leftover. `XDG_STATE_HOME` is the only later sibling; this crate
does not need it until a consumer stores non-essential state.

- config: `$XDG_CONFIG_HOME` if set and absolute, else `$HOME/.config`
- data: `$XDG_DATA_HOME` if set and absolute, else `$HOME/.local/share`
- cache: `$XDG_CACHE_HOME` if set and absolute, else `$HOME/.cache`
- runtime: `$XDG_RUNTIME_DIR` must be set and absolute

There is no `/run/user/<uid>` fallback, no `/tmp` fallback, and no `~`
expansion. Relative or empty XDG values are errors.

`ConfigDirs` is enough for tools that only need config/data.
`BaseDirs` also requires runtime.

Published from CI on a `v*` tag (`CARGO_REGISTRY_TOKEN` org secret). Do not
`cargo publish` from a laptop.

```toml
xdg-paths = "0.2.0"
```
