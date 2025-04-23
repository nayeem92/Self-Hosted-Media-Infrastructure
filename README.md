
# 🧠 Self-Hosted Media Infrastructure (Docker Stack)

A fully automated, modular home media server stack deployed on Ubuntu 24.04 using Docker Compose. Features include torrent and Usenet automation, IPTV streaming with EPG, secure remote access via Tailscale, and containerized service orchestration using best DevOps practices.

---

## 📦 Stack Overview

| Service         | Purpose                                          |
|-----------------|--------------------------------------------------|
| **Jellyfin**    | Media playback & streaming platform              |
| **Sonarr**      | TV series automation (torrent & Usenet)          |
| **Radarr**      | Movie automation (torrent & Usenet)              |
| **qBittorrent** | Torrent client with automation integration       |
| **NZBGet**      | Usenet downloader for high-speed automation      |
| **Prowlarr**    | Indexer manager for Sonarr/Radarr                |
| **Jellyseerr**  | User request interface for Jellyfin              |
| **Cabernet**    | IPTV integration proxy with XMLTV EPG support    |
| **AdGuard Home**| DNS-level ad blocker (network-wide filtering)    |
| **Homarr**      | Elegant dashboard UI to manage all services      |
| **Portainer**   | Docker container manager with GUI                |
| **FlareSolverr**| Cloudflare bypass support for indexers           |

---

## 🔐 Access & Networking

- **Tailscale Mesh VPN**: Secures remote access without port forwarding.
- **Services exposed**:
  - Jellyfin: `8096`
  - Sonarr: `8989`
  - Radarr: `7878`
  - qBittorrent: `8080`
  - NZBGet: `6789`
  - Prowlarr: `9696`
  - Jellyseerr: `5055`
  - AdGuard: `3000`
  - Homarr: `7575`
  - Cabernet: `6077`
  - Portainer: `9000`

---

## 🔁 Automation Flow

```
Jellyseerr
   │
   ├──► Radarr / Sonarr ───► qBittorrent / NZBGet
   │                             │
   └─────────────────────────────┘
        Hardlink import to Jellyfin
```

- All media automation (TV/movies) is triggered via **Jellyseerr**.
- **Sonarr/Radarr** handle retrieval via torrent or Usenet (qBittorrent/NZBGet).
- Files are hardlinked (not copied) into `/data/media`, optimizing space.
- Metadata + posters are fetched automatically for Jellyfin display.
- **Cabernet** feeds IPTV into Jellyfin with EPG from custom `xmltv.xml`.

---

## ⚙️ Deployment Highlights

- Built with **Docker Compose** (no host pollution)
- Media and config paths are shared under `/data`
- Secure and remote-friendly via **Tailscale**
- Transcoding optimized with **VAAPI hardware acceleration**
- Clean, UI-first access using **Homarr**
- DNS filtering across network via **AdGuard Home**

---

## 📁 Directory Layout

```
/data/
├── configs/
│   └── jellyfin, radarr, sonarr, etc.
├── media/
│   ├── movies/
│   └── tv/
├── torrents/
│   ├── movies/
│   └── tv/
├── nzbs/
│   ├── movies/
│   └── tv/
```

---

## 🚀 Coming Soon

- Discord bot for live request notifications
- Auto-backup system for config and media state
- DVR support for IPTV via Jellyfin Live TV

---

## 🧠 Skills Demonstrated

- Docker Compose orchestration and volume management
- Infrastructure automation and systemd integration
- Media ingestion pipelines using torrent + Usenet
- Networking with Tailscale, firewall-less remote control
- IPTV proxying with Cabernet and custom EPG parsing
- System performance tuning (transcoding, DNS ad-blocking)

---

## 📸 Screenshots
![Alt Text](screenshots/Capture1.PNG)
![Alt Text](screenshots/Capture2.PNG)
![Alt Text](screenshots/Capture3.PNG)
![Alt Text](screenshots/Capture4.PNG)
![Alt Text](screenshots/Capture5.PNG)
![Alt Text](screenshots/Capture6.PNG)
![Alt Text](screenshots/Capture7.PNG)
![Alt Text](screenshots/Capture8.PNG)
---

## 🧾 License

MIT License — free to fork and modify.
