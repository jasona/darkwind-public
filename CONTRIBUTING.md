# Contributing

1. Create a branch from `main`.
2. Make changes only to content already published in this repository.
3. Open a pull request describing the player-facing effect of the change.
4. Address review feedback before the change is merged.

Most player help lives under `docs/helpdir/`, grouped by section. Guild-specific
help lives under `docs/guild/`. Preserve existing filenames, Darkwind color
tokens, metadata footers, and extensionless help-file formatting unless the
change specifically requires altering them.

Files ending in `.c` or `.h` are LPC source even when they live below `docs/`.
Treat changes to them as game-code changes and describe their runtime impact in
the pull request.

Contributions must not include player data, secrets, private game source, or
generated files. A change merged here is not live until it is imported into a
Darkwind release and deployed.
