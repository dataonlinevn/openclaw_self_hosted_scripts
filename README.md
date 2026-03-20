# DataOnline OpenClaw Auto-Installer

<!-- SPDX-License-Identifier: MIT -->
<!-- Copyright (c) 2026 DataOnline. DataOnline OpenClaw Auto-Installer. -->

Script cài đặt tự động trợ lý AI **OpenClaw** trên Ubuntu — **DataOnline** (VPS, hosting, server tại Việt Nam).

**Repo:** [github.com/dataonlinevn/openclaw_self_hosted_scripts](https://github.com/dataonlinevn/openclaw_self_hosted_scripts)

**Tài liệu theo thư mục:** [scripts/](scripts/README.md) · [scripts/lib/](scripts/lib/README.md)

---

## Tổng quan

| | |
|---|---|
| **Mục tiêu** | Đơn giản hóa triển khai OpenClaw trên VPS Ubuntu |
| **Đối tượng** | Người dùng VPS / AI tại Việt Nam |
| **Triết lý** | Rõ ràng, thân thiện, ít bước thủ công |

## Yêu cầu hệ thống

- **OS:** Ubuntu 22.04 hoặc 24.04 LTS (x86_64)
- **RAM:** Khuyến nghị ≥ 2GB; dưới 2GB script cảnh báo nhưng vẫn cho phép tiếp tục
- **Quyền:** Root (`sudo`)

## Cài đặt

**Cách dùng khuyến nghị:** clone repo (đủ `scripts/lib/`, menu và Docker/CLI ổn định hơn so với chạy qua pipe).

```bash
git clone https://github.com/dataonlinevn/openclaw_self_hosted_scripts.git
cd openclaw_self_hosted_scripts
sudo ./scripts/install.sh
```

Sau lần chạy đầu, script có thể cài lệnh **`openclaw`** (bản trong `/opt/dataonline/openclaw-installer/`, symlink tại `/usr/local/bin/`). Có thể ghi đè tên lệnh qua biến môi trường `OPENCLAW_GLOBAL_CMD`. Chi tiết: [scripts/README.md](scripts/README.md).

## Tính năng

- Cài OpenClaw qua Docker (image có sẵn)
- Cấu hình qua menu CLI (onboard, models, pairing, config…)
- UFW: cổng 22, 18789, 18790
- Kiểm tra trạng thái (Docker, cổng, RAM, UFW, health)
- Gỡ bỏ stack và kênh hỗ trợ

## Cấu trúc repo

```
├── README.md              # Tổng quan dự án (file này)
├── LICENSE
├── scripts/               # Entry + lib — xem scripts/README.md
│   ├── README.md
│   ├── install.sh
│   └── lib/
│       ├── README.md
│       └── *.sh
```

Trên máy đã cài, cấu hình và compose thật nằm trong **`/opt/dataonline/openclaw/`** (gồm `.env`, `docker-compose.yml`, thư mục `config/` dành cho OpenClaw — không liên quan tới cấu trúc repo này).

## Port và truy cập

Sau khi cài:

| Dịch vụ | Cổng |
|--------|------|
| Gateway (WebSocket API) | **18789** |
| Bridge (nội bộ) | **18790** |

**Cấu hình sau cài:** trong menu chính chọn **3) Cấu hình OpenClaw (CLI)** (`onboard`, `models`, `config`, `pairing`, `devices`…).

### VPS & mạng

- **Cloud:** Mở **18789** và **18790** trên Security Group / firewall nhà cung cấp (AWS, GCP, DigitalOcean…).
- **NAT / gia đình:** Cần port forward hai cổng trên router nếu truy cập từ ngoài.
- **Upstream:** [docs.openclaw.ai](https://docs.openclaw.ai)

## Hỗ trợ

- **Facebook:** [DataOnline VN](https://www.facebook.com/groups/openclawselfhosted)
- **Telegram:** [@DataOnlineVN](https://t.me/DataOnlineVN)
- **Zalo:** [dataonline](https://zalo.me/dataonline)
- **Hotline:** 0356958688

## License

MIT — xem [LICENSE](LICENSE).

Copyright (c) 2026 DataOnline. DataOnline OpenClaw Auto-Installer.
