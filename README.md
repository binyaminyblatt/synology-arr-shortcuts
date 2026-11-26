# Arr Shortcuts for Synology DSM

Put your self-hosted apps in the **DSM main menu**, each with its own icon, just like a regular Synology app.

DSM only shows shortcuts for installed packages, so apps that run in Docker (Container Manager), such as Sonarr or Radarr, never show up there. This small package fixes that. It adds a shortcut for each app you choose, and opens it in a new browser tab.

![Screenshot](docs/screenshot.png)

![Screenshot](docs/screenshot-2.png)

## Supported apps

| App | Default port |
|---|---|
| Audiobookshelf | 13378 |
| Home Assistant | 8123 |
| Music Assistant | 8095 |
| Pocket ID | 1411 |
| Portainer | 9000 |
| Sonarr | 8989 |
| Radarr | 7878 |
| Prowlarr | 9696 |
| Bazarr | 6767 |
| Tdarr | 8265 |
| Bookshelf / Readarr | 8787 |
| Calibre | 8080 |
| Calibre-Web | 8083 |
| Spotweb | 8085 |
| Homarr | 7575 |
| WUD (What's Up Docker) | 3000 |

## How it works

- During installation you **tick the apps you run** and **enter their ports**.
- Each shortcut opens `http://<your NAS address>:<port>`. It uses the same address you use to open DSM, so it works at home and remotely (for example through Tailscale or a VPN).
- For apps served over HTTPS, prefix the port with `https:`, for example `https:8091`.
- The package itself runs nothing in the background. It only adds menu entries.

## Installation

1. Download the latest `ArrLinks-x.x.x.spk` from [Releases](../../releases).
2. Open **Package Center** → **Manual Install** and select the file.
3. DSM warns that the package has no digital signature. This is normal for community packages. Click **Yes** to continue.
4. Choose your apps and ports in the wizard.
5. Refresh DSM in your browser. The shortcuts are now in the **main menu**. Drag them to your desktop if you like.

To change your apps or ports later, install the same version again through **Manual Install**. The wizard will appear again.

## Requirements

- DSM 7.0 or newer
- Any model (the package is architecture-independent)

## Building from source

```sh
./build.sh
```

This creates `ArrLinks-<version>.spk` from the files in `src/`.

To add an app:

1. Add a line to `src/package/apps.list`: `id|Title|default port`
2. Add icons `src/package/ui/images/<id>_{16,24,32,48,64,72,256}.png`
3. Add the app to both files in `src/WIZARD_UIFILES/`

## Credits

The app icons are the logos of the respective projects and belong to their owners. They are used here only to link to those apps. Spotweb uses the classic Spotnet logo.

## License

MIT
