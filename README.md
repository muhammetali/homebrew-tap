# homebrew-tap

Homebrew packages for [MixTerm](https://github.com/muhammetali/mixterm), an
SSH/SFTP client with multi-tab terminals, a visual file browser and
AES-256 encrypted credential storage.

```sh
brew trust muhammetali/tap
brew tap muhammetali/tap
brew install --cask mixterm
```

The first line is not optional on Homebrew 6 and later, which refuses to
load casks from a third-party tap until you say you trust it. Without it
`brew tap` stops with "Refusing to load cask … from untrusted tap".

Upgrading follows the usual route:

```sh
brew upgrade --cask mixterm
```

## Why a tap rather than homebrew-cask

Homebrew's [package acceptance
policy](https://github.com/Homebrew/brew/blob/master/docs/Package-Acceptance-Policy.md)
asks a repository owner submitting their own project for at least 90 forks,
90 watchers or 225 stars. MixTerm is below that, so a tap is the supported
route until it is not. The cask here is written to homebrew-cask's rules and
can move across unchanged.

## What gets installed

The macOS build published on the MixTerm releases page: a universal binary
(x86_64 and arm64), signed with a Developer ID certificate, notarized by
Apple and stapled, so it opens without a Gatekeeper warning and without
`xattr` incantations.

`brew uninstall --zap --cask mixterm` also removes the sandbox container the
app stores its data in — the encrypted server list, settings and any Google
Drive session. Plain `brew uninstall` leaves that in place.
