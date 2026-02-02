# Face Tracker Avatar Demo

MediaPipe + Three.js face-tracking avatar. Works in the browser on desktop and phone.

**This repo uses a GLB avatar** (same format as the raccoon model): your 2D image is converted into a `.glb` file with full MediaPipe face blendshapes (mouth, eyes, brows, etc.). Black background, floating head only.

## Build your GLB from your 2D image

1. Start a local server (`npx serve .` or `python -m http.server 8000`), then open **`build-watchdog-glb.html`** in your browser.
2. Click **Choose File** and select your face/head image (`watchdog image.png` or any PNG/JPG).
3. Click **Build watchdog.glb** — the file will download.
4. Place `watchdog.glb` in this folder, next to `index.html` and `main.js`.
5. Run the demo (see below).

---

## Test on your phone (GitHub Pages)

1. **Push this folder to a GitHub repo** (if you haven’t already):
   ```bash
   git init
   git add index.html main.js build-watchdog-glb.html .nojekyll README.md watchdog.glb
   git commit -m "Face tracker avatar web app"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
   git push -u origin main
   ```

2. **Turn on GitHub Pages**  
   On GitHub: **Settings → Pages → Build and deployment**  
   - Source: **Deploy from a branch**  
   - Branch: **main** (or **master**)  
   - Folder: **/ (root)**  
   - Save.

3. **Open the site on your phone**  
   After a minute or two, the site will be at:
   ```text
   https://YOUR_USERNAME.github.io/YOUR_REPO/
   ```
   Open that URL on your phone, allow camera access when asked, and use the front camera to drive the avatar.

**Note:** Camera only works over **HTTPS**. GitHub Pages gives you HTTPS, so it works on mobile.

---

## Run locally (desktop)

1. **Start a local server** (needed for camera and ES modules):
   ```bash
   npx serve .
   ```
   Or: `python -m http.server 8000`

2. **Open in a browser**  
   - With `npx serve .`: **http://localhost:3000**  
   - With Python: **http://localhost:8000**

3. **Allow camera access** when prompted.

---

## Files

| File | Purpose |
|------|--------|
| **index.html** | Page with hidden `<video>`, import map for Three.js, mobile-friendly layout |
| **main.js** | Demo logic: Avatar (GLB loader), MediaPipe face blendshapes, retarget gains |
| **build-watchdog-glb.html** | Build tool: converts your 2D image → `watchdog.glb` (raccoon-style format) |
| **watchdog.glb** | Your face as a 3D model (build from your image via build-watchdog-glb.html) |
| **.nojekyll** | Tells GitHub Pages not to use Jekyll |

## Change the avatar image

1. Open `build-watchdog-glb.html` in your browser.
2. Select your new face/head image.
3. Click **Build watchdog.glb** and replace the existing file.
