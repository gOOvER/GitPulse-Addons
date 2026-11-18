# GitPulse Addons

Official AddOn & Plugin catalog for **[GitPulse](https://github.com/gOOvER/GitPulse)**.

Each addon lives in its own directory under `addons/<addon-id>/` using a standardized structure:

```text
addons/<addon-id>/
├── manifest.json     # Required: id, name, version, description, author, icon, runtime, entry, settingsSchema
├── README.md         # Addon documentation (English)
├── CHANGELOG.md      # Version history (Keep a Changelog)
└── assets/           # Optional: icons or banners
```

## Available Addons

| ID | Name | Version | Directory |
|---|---|---|---|
| `wow-l10n` | **WoW Addon Translator** | `1.0.0` | [addons/wow-l10n](addons/wow-l10n) |

---

## How to Create a GitPulse Plugin

Anyone can extend **GitPulse** with custom plugins:

### 1. Create the Addon Directory
Create `addons/<your-addon-id>/manifest.json` (or host `manifest.json` in your own GitHub repository):

```json
{
  "id": "my-plugin",
  "name": "My Custom Plugin",
  "version": "1.0.0",
  "description": "Short description of what your plugin does.",
  "author": "your-github-handle",
  "icon": "puzzle",
  "runtime": "iframe",
  "entry": "https://your-plugin-host.example.com/",
  "requiredRole": "STAFF",
  "settingsSchema": [
    {
      "key": "API_TOKEN",
      "label": "API Token",
      "description": "Encrypted in GitPulse PostgreSQL storage.",
      "type": "password",
      "secret": true
    }
  ]
}
```

### 2. Choose a Runtime
- **`iframe` (External Web UI — Zero Rebuild Required):** Set `"runtime": "iframe"` and `"entry": "https://..."`. GitPulse renders your plugin directly inside `/plugins/<id>` for authorized users (`STAFF` or `ADMIN`).
- **`builtin` (Native Next.js Module):** Contribute a React module under `src/plugins/<id>/` in GitPulse and set `"runtime": "builtin"` and `"entry": "<id>"`.

### 3. Install in GitPulse
1. Open **Settings → Plugins** (`/plugins`) in GitPulse.
2. Paste your GitHub repository (`owner/repo`, GitHub URL, or direct `manifest.json` raw URL) and click **Plugin installieren**.
3. Configure any `settingsSchema` fields and open your plugin from the top navigation bar.

### 4. Submit to the Official Catalog
Open a Pull Request in this repository adding your `addons/<your-addon-id>/` folder and an entry in `catalog.json`. The CI workflow automatically validates `manifest.json` and packages `<addon-id>-v<version>.zip`.
