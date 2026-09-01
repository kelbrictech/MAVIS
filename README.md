# MAVIS — Page Flow Generator

A mobile-first, form-based page flow design tool. Create, visualize, and export page flows for any project.

**Features:**
- 📝 **Form-based entry** — add pages with labeled fields (Page #, Name, Zone, Provisions, Notes)
- 🗺️ **Live visualizer** — fullscreen page-by-page preview with navigation
- 💾 **Built-in storage** — saves to browser (persists between sessions)
- 📥 **Import/Export** — download as CSV, re-upload to update
- 📱 **Mobile-first** — optimized for phones and tablets
- 🎨 **Zone support** — color-coded areas (YELLOW, RED, BLUE, GREEN, custom)

## Quick Start

### Web Browser
1. Download `index.html`
2. Open in any modern browser (Chrome, Safari, Firefox, Edge)
3. Start adding pages

### GitHub Pages
This repo is hosted on GitHub Pages. Visit the live demo: [kelbrictech.github.io/MAVIS](https://kelbrictech.github.io/MAVIS/)

### Android APK
See [Building the APK](#building-the-apk) below.

## Usage

### Add a Page
1. Tap **+ Add Page**
2. Fill in the form fields:
   - **Page #** — sequential number
   - **Page Name** — human-readable title
   - **Zone** — occupied area (YELLOW, RED, BLUE, GREEN, RED + BLUE)
   - **Provisions** — comma-separated UI elements
   - **Notes** — optional metadata (TODO, COMPLETE, STUB, etc.)
3. Tap **Save**

### Preview Pages
1. Tap the **Visualizer** tab
2. Navigate with **Prev/Next** buttons
3. See all pages one at a time

### Export/Import
- **Download** — exports all pages as CSV (for offline editing)
- **Upload** — re-import CSV to restore data

### Spreadsheet Schema

| Column | Purpose | Example |
|--------|---------|---------|
| `Page #` | Sequential identifier | 1, 2, 3, ... |
| `Page Name` | Page title | Splash, Login, Studio Selection |
| `Zone` | Area/constraint class | YELLOW, RED, BLUE, GREEN |
| `Orientation` | Screen orientation | Portrait, Landscape |
| `Provisions` | Comma-separated elements | tap me, username field, 6 buttons |
| `Notes` | Optional metadata | TODO, COMPLETE, STUB |

## Building the APK

### Option 1: GitHub Actions (Automatic)
Every push to `main` triggers an automated build:
1. Go to **Actions** tab → find your build
2. Download the `.apk` artifact
3. Install on your Android device

### Option 2: Build Locally

**Prerequisites:**
- Node.js 16+
- Android SDK (or Android Studio)

**Steps:**
```bash
git clone https://github.com/kelbrictech/MAVIS.git
cd MAVIS
npm install -g @capacitor/cli
npx cap init MAVIS com.mavis.pagegen
npx cap add android
npx cap build android
```

The APK will be in `android/app/build/outputs/apk/`.

## Local Storage

MAVIS stores all data in browser **localStorage**. Your pages persist between sessions.

**Clear data:**
```javascript
localStorage.removeItem('pageFlowData');
```

## File Structure

```
MAVIS/
├── index.html
├── README.md
├── LICENSE
├── capacitor.config.json
├── package.json
├── docs/
│   └── BUILDING.md
└── .github/
    └── workflows/
        └── build-apk.yml
```

## License

MIT — Use freely, modify, distribute. See [LICENSE](LICENSE) for details.

## Contributing

Pull requests welcome! For major changes, open an issue first.

## Support

- **Questions?** Open an issue on GitHub
- **Bug report?** File a GitHub issue with steps to reproduce
- **Feature request?** Describe your use case

---

**Made with ❤️ for designers and product builders.**
