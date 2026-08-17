<div align="center">

# MarzSetup

One-shot Marzban panel installer with Nginx reverse proxy, firewall rules and credential saving.

[![Marzban](https://img.shields.io/badge/marzban-panel-1a1a2e?style=for-the-badge&logo=proxy&logoColor=white)](https://github.com/gozargah/Marzban)

</div>

---

### Install

```bash
sudo bash -c "$(curl -fsSL https://raw.githubusercontent.com/myrat-stack/MarzSetup/main/install.sh)"
```

That's it. The script handles everything else.

---

### What it does

| Step | Action |
|------|--------|
| 1 | Installs Docker if not present |
| 2 | Deploys Marzban via Docker Compose |
| 3 | Creates admin account with random credentials |
| 4 | Configures Nginx reverse proxy on port `3169` |
| 5 | Sets up 4 inbound protocols |
| 6 | Opens required ports in firewall |
| 7 | Saves credentials to `/root/marzban-credentials.txt` |

---

### Protocols

| Protocol | Port |
|----------|------|
| VLESS | 5000 |
| VMess | 5001 |
| Trojan | 5002 |
| Shadowsocks (chacha20) | 5003 |

Dashboard is served on port **3169**.

---

### After install

Credentials are printed to stdout and saved to:

```
/root/marzban-credentials.txt
```

Panel URL, username and password are stored there with `chmod 600`.

---

### Requirements

- Debian / Ubuntu based VPS
- Root or sudo access
- Clean server (no existing Nginx config on port 3169)

---

### Notes

- Dashboard path is proxied through Nginx, not exposed directly on the Marzban port.
- Admin credentials are randomly generated on every run.
- Xray core config is applied via the Marzban API after container is healthy.

---

<div align="center">

Based on [Marzban](https://github.com/gozargah/Marzban) by Gozargah

</div>
