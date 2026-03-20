# Scripts — cài đặt OpenClaw

<!-- SPDX-License-Identifier: MIT -->
<!-- Copyright (c) 2026 DataOnline. DataOnline OpenClaw Auto-Installer. -->

Thư mục **entry** và các module Bash (`lib/`) cho DataOnline OpenClaw Auto-Installer.

**Liên kết:** [README gốc](../README.md) · [Thư mục lib/](lib/README.md)

---

## Cấu trúc

```
scripts/
├── install.sh          # Menu chính — nạp lib/
└── lib/
    ├── utils.sh        # Banner, màu, root, logging, openclaw (lệnh global)
    ├── checks.sh       # OS, RAM, cổng, mạng, Docker
    ├── install-core.sh # Docker, thư mục deploy, compose, khởi động
    ├── ufw.sh          # Firewall (22, 18789, 18790)
    ├── cli.sh          # Menu OpenClaw CLI trong container
    ├── status.sh       # Báo cáo trạng thái
    └── uninstall.sh    # Gỡ cài
```

## Cài đặt (từ repo đã clone)

```bash
cd openclaw_self_hosted_scripts
sudo ./scripts/install.sh
```

Luôn chạy từ thư mục gốc repo để `install.sh` tìm được `lib/*.sh`.

## Lệnh `openclaw`

Khi chạy `install.sh` từ bản clone có đủ `install.sh` và `lib/`, script có thể:

1. Sao chép bản cài vào **`/opt/dataonline/openclaw-installer/`**
2. Tạo symlink **`/usr/local/bin/openclaw`** → `install.sh` đã copy

Sau đó:

```bash
sudo openclaw
```

Nếu đã chạy trực tiếp từ thư mục cài trong `/opt/dataonline/openclaw-installer/`, bước copy/symlink được bỏ qua.

## Kiến trúc

- `install.sh` chỉ điều phối menu; logic nằm trong `lib/*.sh` (`source` theo thứ tự cố định).
- Biến màu, logging và đường dẫn dùng chung: **`lib/utils.sh`**.

## Ngôn ngữ giao diện

Toàn bộ prompt và thông báo trong script hiển thị bằng **tiếng Việt**.
