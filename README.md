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
hyperframes init my-video --example blank
cd my-video
hyperframes preview
```

Open the local URL printed by the preview. After editing your composition, stop the preview with Ctrl+C and render it:

```bash
hyperframes render --output output.mp4
sudo snap connect hyperframes:removable-media   # optional: /media, /mnt
```

## Known limitations

- Projects and media must be in a non-hidden home folder or connected removable storage.
- Docker rendering, arbitrary host programs, Whisper compilation and AWS Lambda/GCP deployment are not supported.
- User state lives under `~/snap/hyperframes/common`. The application and bundled browser update through snapd.
- Automatic integration with host AI agents is unavailable. Only open compositions you trust.

## Update to a new upstream release

Change `version` in `snap/snapcraft.yaml`, then rebuild.

## Automation

Builds, publishing, and dependency updates use [snap-automation](https://github.com/sidalit/snap-automation).

## License

The packaging is MIT-licensed (see `LICENSE`). Hyperframes is Apache-2.0-licensed; its dependencies carry their own licenses.
