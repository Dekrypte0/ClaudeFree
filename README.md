```text
  █▀▀ █   ▄▀█ █ █ █▀▄ █▀▀ █▀▀ █▀█ █▀▀ █▀▀
  █▄▄ █▄▄ █▀█ █▄█ █▄▀ ██▄ █▀  █▀▄ ██▄ ██▄
```

# ClaudeFree

ClaudeFree is an automated tool for generating and adding API trial keys to a local Free Claude Code (FCC) installation using alternate accounts.

## Features

| Feature | Description |
| --- | --- |
| **Browser automation** | Uses Playwright and ChromeDriver for browser interaction. |
| **Email management** | Reads configured email information from `assets.txt`. |
| **Gmail verification bridge** | Receives verification codes through a local HTTP server and Tampermonkey. |
| **API key management** | Saves API keys locally in `keys.txt`. |
| **Provider integration** | Adds keys to the existing trial provider in Free Claude Code (FCC). |

## Requirements

- Windows 10 or Windows 11
- Python 3.10+
- Google Chrome
- Playwright and Chromium
- ChromeDriver
- Free Claude Code (FCC) running locally
- Tampermonkey browser extension
- A Gmail account
- A Nonecap API key

## Setup

### 1. Download the project

Clone the repository or download its source files, then open PowerShell in the project directory.

### 2. Configure `assets.txt`

Create or open `assets.txt` in the project folder. This file stores the local configuration used by ClaudeFree.

- Use a Gmail address (longer aliases work better if your base address is short).
- Enter your email in `assets.txt`.
- Enter your Nonecap API key in `assets.txt` as `nonecap=` or `nonecapapi=`.
- Account generation is limited (typically 10 per IP per hour).

### 3. Set up Tampermonkey

1. Install the Tampermonkey extension from the official browser extension store.
2. Open the Tampermonkey dashboard.
3. Select **Create a new script**.
4. Paste the project's Gmail bridge userscript from `tampermonkey.user.js` into the editor.
5. Save the script.
6. Open Gmail in Chrome.
7. If the script does not load initially, press `Ctrl+Shift+R` (hard refresh).
8. Keep this Gmail tab running in the background.

The userscript communicates with the local verification bridge. Only install scripts you trust and review their permissions before enabling them.

### 4. Configure NoneCap

1. Open https://nonecap.com.
2. Create an account.
3. Complete account setup.
4. Generate an API key from your dashboard.
5. Add it to `assets.txt`.

### 5. Start Free Claude Code (FCC)

Make sure Free Claude Code is running locally and that its admin panel is accessible. If it is not installed, ClaudeFree can guide you through the install/start steps.

Default admin address:

```text
http://localhost:8082/admin
```

### 6. Run ClaudeFree

```powershell
python api-gen-headless.py
```

ClaudeFree checks dependencies, starts local services, and opens the FCC admin panel.

## Local Files

| File / Folder | Description |
| --- | --- |
| `api-gen-headless.py` | ClaudeFree headless runner |
| `api-gen-headful-old.py` | Legacy headed runner |
| `assets.txt` | Local configuration |
| `keys.txt` | Locally stored API keys |
| `accounts.txt` | Recent account history |
| `drivers/` | Browser driver files |

## Ports

| Port | Purpose |
| --- | --- |
| `8080` | Local Gmail verification bridge |
| `8082` | Free Claude Code (FCC) admin panel |

## Credits

- **NoneCap** — CAPTCHA service
- **Playwright** — Browser automation
- **Tampermonkey** — Browser userscript support
- **Free Claude Code** — Local application integration target

## Support

For help or issues, contact **in_d7fferent** on Discord.
