<div align="center">

<img src="snap/gui/hyperframes.png" alt="HyperFrames logo" width="128" />

# HyperFrames

**Create, preview and render HTML video compositions.**

[![hyperframes](https://snapcraft.io/hyperframes/badge.svg)](https://snapcraft.io/hyperframes)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64 and arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [HyperFrames](https://github.com/heygen-com/hyperframes), with a native desktop on amd64 and command-line tools on both architectures.

</div>

---

## Getting Started

<a href="https://snapcraft.io/hyperframes"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install hyperframes
```

On amd64, launch **HyperFrames** from the application menu or run `hyperframes`. The CLI works on both architectures:

```bash
hyperframes init my-video --example blank
cd my-video
hyperframes preview
```

Open the URL printed by the preview. Stop it with **Ctrl+C**, then render with `hyperframes render --output output.mp4`.

## Configure

This snap has no `snap set` options. The desktop launcher accepts this environment variable:

| Variable | Accepted values | Default |
| --- | --- | --- |
| `HYPERFRAMES_PROJECTS_ROOT` | A directory accessible to the snap; empty or unset uses the default. | `~/HyperFrames` |

```bash
HYPERFRAMES_PROJECTS_ROOT="$HOME/Videos" hyperframes
```

Connect permissions as needed:

```bash
sudo snap connect hyperframes:password-manager-service   # sign-in and API keys
sudo snap connect hyperframes:removable-media            # /media, /mnt
sudo snap connect hyperframes:audio-record               # microphone
```

User state lives in `~/snap/hyperframes/common`; desktop settings are under `.config/HyperFrames` there.

## Limitations

- The native desktop is available on amd64 only. Both architectures include the CLI and browser preview.
- Projects and media must be in a non-hidden home folder or connected removable storage.
- Host-installed agents and programs are unavailable. Configure agents and credentials inside the snap; host-terminal shortcuts are unsupported.
- Docker rendering, Whisper compilation and AWS Lambda/GCP deployment are unsupported.

## Build

```bash
git clone https://github.com/sidalit/hyperframes-snap.git
cd hyperframes-snap
sudo snap install snapcraft --classic
snapcraft pack
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/hyperframes-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/heygen-com/hyperframes/issues).

## License

Snap packaging: [MIT](https://github.com/sidalit/hyperframes-snap/blob/main/LICENSE).
