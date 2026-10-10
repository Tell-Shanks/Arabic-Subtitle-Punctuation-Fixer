# 🎬 Arabic Subtitle BiDi & Punctuation Fixer (MKV, MP4, SRT, VTT)

A modern, 100% client-side web application that repairs broken bidirectional text layout (BiDi), leading inverted punctuation, and neutral ASCII quotes in Arabic subtitles embedded inside video containers (`.mkv`, `.mp4`) or standalone subtitle files (`.srt`, `.vtt`).

Runs **100% in the browser** using WebAssembly (FFmpeg WASM single-thread). **Zero backend. Zero server dependencies. Zero data uploaded.**

---

## 🌟 Key Features

- **MKV Video Container Support**: Drop your `.mkv` file directly. It extracts the Arabic subtitle stream, fixes all BiDi and punctuation anomalies, and remuxes the repaired subtitle back into the video container.
- **Ultra-Fast Stream Copy (`-c copy`)**: Video and audio streams are copied verbatim without re-encoding, preserving 100% original video/audio quality in just a few seconds.
- **Standalone Subtitle Support**: Also accepts direct `.srt` and `.vtt` subtitle files.
- **BiDi & Punctuation Engine**:
  - **Leading Punctuation Reordering**: Repositions leading inverted punctuation clusters (`!`, `؟`, `...`, `،`, `?`, `.`) to their natural logical end.
  - **Quotation Normalization**: Converts ASCII double quotes (`"..."`) to typographically stable Arabic quotes (`«...»`).
  - **RTL Embedding**: Injects Unicode Right-to-Left Embedding (`\u202B` - RLE) and Pop Directional Format (`\u202C` - PDF) markers.
  - **Stale Control Character Cleanup**: Strips orphaned control characters (`\u200E`, `\u200F`, `\u202A`–`\u202E`).
- **Live Side-by-Side Preview**: Visual comparison of Before (broken) vs After (repaired) lines with difference highlighting.
- **1-Click Export**: Download the repaired `.mkv` container, or download the standalone repaired `.srt` file.

---

## 🚀 How to Host on GitHub Pages

### Option A: Using the Automated GitHub Action (Recommended)

1. Create a new repository on [GitHub](https://github.com/new) (e.g. `arabic-subtitle-fixer`).
2. Push this repository to GitHub:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/<your-username>/arabic-subtitle-fixer.git
   git push -u origin main
   ```
3. In your GitHub repository:
   - Go to **Settings** &rarr; **Pages**.
   - Under **Build and deployment** &rarr; **Source**, select **GitHub Actions**.
4. The workflow in `.github/workflows/deploy.yml` will automatically build and publish your site!
   Your site will be live at:
   `https://<your-username>.github.io/arabic-subtitle-fixer/`

---

### Option B: Deploying directly from the `main` branch

1. Push your repository to GitHub (same as Step 2 above).
2. Go to your repository **Settings** &rarr; **Pages**.
3. Under **Build and deployment** &rarr; **Source**, choose **Deploy from a branch**.
4. Select the **main** branch and root folder (`/`), then click **Save**.
5. Your site will be published at `https://<your-username>.github.io/arabic-subtitle-fixer/`.

*(The included `.nojekyll` file ensures that all files and WebAssembly assets are served untouched without Jekyll interference).*

---

## 💻 Running Locally

You can preview the app locally using any static web server:

```bash
# Using Python
python -m http.server 8080

# Or using Node.js
npx serve .
```

Then open `http://localhost:8080` in your web browser.

---

## 🔒 Privacy & Security

This application processes all files entirely on the client side using browser WebAssembly. Your videos and subtitles never leave your device.
