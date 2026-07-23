# Darkwind Public Contributions

This directory contains Darkwind content that is available for public editing
and contribution. It is maintained in the private game repository at
`codebase/public/` and published as the root of the public repository at:

https://github.com/jasona/darkwind-public

## Documentation

The `docs/` directory is Darkwind's live documentation corpus. It appears in
the game at `/public/docs/` and includes player help, guild documentation,
wizard references, LPC and driver manuals, maps, banners, and the wiki source.

Many help files intentionally have no extension and use Darkwind color tokens.
Some documentation directories also contain LPC examples or support objects;
changes to those files receive the same review and validation as game code.

## Contributing

Submit changes through a branch and pull request in the public repository.
Accepted changes are imported into the game repository during the release
process. A merged pull request is not live until it has been imported, tested,
and deployed with a Darkwind release.

Do not add player save files, credentials, deployment configuration, private
game source, or generated build artifacts to this repository.
