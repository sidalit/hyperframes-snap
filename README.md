# Hyperframes snap

[![hyperframes](https://snapcraft.io/hyperframes/badge.svg)](https://snapcraft.io/hyperframes)

Snap packaging for [Hyperframes](https://github.com/heygen-com/hyperframes), a framework for creating, previewing and rendering HTML video compositions.

Unofficial build, not affiliated with or endorsed by the Hyperframes project.

## Build

```bash
snapcraft pack
```

## Install and try

<a href="https://snapcraft.io/hyperframes"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install hyperframes
sudo snap connect hyperframes:password-manager-service   # desktop sign-in and API keys
hyperframes
```

On amd64, open **HyperFrames** from the application menu or run `hyperframes` to launch the desktop app. Projects default to `~/HyperFrames`.

The command-line tools remain available on both architectures:

```bash
hyperframes init my-video --example blank
cd my-video
hyperframes preview
```

Open the local URL printed by the preview. After editing your composition, stop the preview with Ctrl+C and render it:

```bash
hyperframes render --output output.mp4
sudo snap connect hyperframes:removable-media   # optional: /media, /mnt
sudo snap connect hyperframes:audio-record      # optional: microphone recording
```

## Known limitations

- Projects and media must be in a non-hidden home folder or connected removable storage.
- The desktop application is available on amd64 only; arm64 includes the command-line tools.
- Docker rendering, arbitrary host programs, Whisper compilation and AWS Lambda/GCP deployment are not supported.
- User state lives under `~/snap/hyperframes/common`. Configure agents and credentials inside the snap; existing host installations and the desktop app's host-terminal shortcuts are unavailable.

## Update to a new upstream release

Change `version` in `snap/snapcraft.yaml`, then rebuild. The desktop build is pinned separately in the `desktop` part; update its download URL and checksum together.

## Automation

Builds, publishing, and dependency updates use [snap-automation](https://github.com/sidalit/snap-automation).

## License

The packaging is MIT-licensed (see `LICENSE`). The Hyperframes CLI and framework are Apache-2.0-licensed. The desktop bundle and its dependencies retain their upstream licensing and notices.
