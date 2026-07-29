# Carl Lemer — Applied Music Technology Portfolio

A static single-page portfolio site for my application to UBC's **Minor in Applied Music
Technology**. Four projects: *Consonant Rotations*, *In Four Quadrants*, the *Cinemagic*
lighting/visual work, and *Myo* gesture-controlled lighting.

Plain HTML/CSS — no build step, no dependencies.

```
index.html                # the whole site
styles.css                # styling
assets/
  audio/consonant-rotations.mp3   # stereo fold-down of the 8-channel piece
  img/cinemagic/*.jpg             # performance, build, and rigging photos
  img/myo/*.jpg                   # Myo poster frames
APPLICATION-BLURBS.md     # draft "why this is a good example" text for the form (not shown on site)
```

---

## 1. Put it on GitHub Pages

You only need to do this once. Replace `YOUR-USERNAME` with your GitHub username throughout.

### a) Create the repo and push

```bash
# from inside this folder
git init
git add .
git commit -m "Initial portfolio site"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/amt-portfolio.git
git push -u origin main
```

(Create the empty `amt-portfolio` repo on github.com first — **Public**, no README/…gitignore,
since this folder already has them.)

### b) Turn on Pages

1. On GitHub, open the repo → **Settings** → **Pages** (left sidebar).
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Branch: **main**, folder: **/ (root)**. Click **Save**.
4. Wait ~1 minute. Your site goes live at:

   ```
   https://YOUR-USERNAME.github.io/amt-portfolio/
   ```

That's the URL to put on the AMT application form.

> The included `.nojekyll` file tells Pages to serve the files as-is (no Jekyll processing).

---

## 2. Add your videos (the empty "▶ video embed slot" boxes)

Raw clips are **not** in this repo on purpose — GitHub rejects files over 100 MB and gets slow
with big video. Instead, upload each clip to **YouTube or Vimeo as _Unlisted_** (unlisted = anyone
with the link can watch, but it won't show up in search or on your channel), then paste the embed
code into the matching slot.

There are **13 Cinemagic slots** (one per clip in your `picks` folders, grouped by event) plus **1 Myo slot**, each marked in `index.html` by its id. Each Cinemagic slot names the exact source file to upload, so the mapping is 1:1:

| Slot id | Event | Source file to upload | Length |
|---|---|---|---|
| `cinemagic-halloween-2024-1` | Halloween · Oct 26, 2024 | `20241027_123720000_iOS.MOV` | 0:23 |
| `cinemagic-lumen-1` | LUMEN: Theus Mago · Feb 8, 2025 | `20250208_094840672_iOS.MP4` | 0:07 |
| `cinemagic-lumen-2` | LUMEN: Theus Mago · Feb 8, 2025 | `20250209_080415000_iOS.MOV` | 0:12 |
| `cinemagic-lumen-3` | LUMEN: Theus Mago · Feb 8, 2025 | `20250209_084849000_iOS.MOV` | 0:10 |
| `cinemagic-openair-1` | Open Air Day Party · Jul 12, 2025 | `20250713_051903000_iOS.MOV` | 0:34 |
| `cinemagic-openair-2` | Open Air Day Party · Jul 12, 2025 | `20250714_045328000_iOS.MP4` | 0:19 |
| `cinemagic-lexer-1` | MOMENT: Lexer · Sep 12, 2025 | `20250913_105720000_iOS.MOV` | 0:32 |
| `cinemagic-lexer-2` | MOMENT: Lexer · Sep 12, 2025 | `20250913_113901000_iOS.MOV` | 0:11 |
| `cinemagic-halloween-2025-1` | Halloween · Oct 31, 2025 | `20251101_115449000_iOS.MOV` | 0:37 |
| `cinemagic-halloween-2025-2` | Halloween · Oct 31, 2025 | `20251101_120556000_iOS.MOV` | 0:14 |
| `cinemagic-einmusik-1` | MOMENT: Einmusik · Nov 21, 2025 | `20251122_093958000_iOS.MOV` | 0:40 |
| `cinemagic-yulia-niko-1` | MOMENT: Yulia Niko · Feb 14, 2026 | `20260215_055934000_iOS.MOV` | 0:21 |
| `cinemagic-friends-club-1` | Friends Club Festival · Jun 28, 2026 | `20260629_063303000_iOS.MOV` | 0:20 |
| `myo-video-1` | Myo lighting | (your Myo demo clip) | — |

(In Four Quadrants uses **photos**, not video — see section 2b.)

### How to fill a slot

**YouTube:** open the video → **Share** → **Embed** → copy the `<iframe …>` code.
**Vimeo:** open the video → **Share** → copy the embed `<iframe …>` code.

In `index.html`, find the slot, e.g.:

```html
<div class="video-embed" id="cinemagic-lumen-1">
  <!-- ▼▼ PASTE YOUR YOUTUBE / VIMEO EMBED IFRAME HERE, then delete the .video-placeholder div below ▼▼ -->
  <!-- <iframe src="https://www.youtube.com/embed/VIDEO_ID" title="Cinemagic — cinemagic-lumen-1" allow="..." allowfullscreen></iframe> -->
  <div class="video-placeholder"> ... </div>
</div>
```

Each slot's placeholder already names the source file (e.g. `Upload 20250208_094840672_iOS.MP4`), so match it to the table above.

1. **Uncomment** the example `<iframe>` and replace `VIDEO_ID` with your video's id
   (the part after `watch?v=` on YouTube) — *or* paste the full iframe you copied.
2. **Delete** the whole `<div class="video-placeholder"> … </div>` block so the striped
   placeholder disappears.

The iframe automatically fills the 16:9 box. Repeat for each slot you want to use.

**Don't want all 13 Cinemagic slots?** Delete the whole
`<div class="video-embed" id="cinemagic-…"> … </div>` block for any you're not using — and if
an entire event ends up empty, delete its surrounding `<div class="reel-event"> … </div>` too,
so no empty placeholder or heading shows on the live site.

When you're done:

```bash
git add index.html
git commit -m "Add video embeds"
git push
```

Pages redeploys in about a minute.

> ⚠️ Unlisted keeps the clips off search but they're still viewable by anyone with the link, and
> the site itself is public. If any footage shouldn't be public yet, just leave that slot empty for now.

---

## 2b. Add your In Four Quadrants photos

This section uses **photos instead of video**. There are four picture slots that fill in
automatically — you don't touch the HTML, you just add correctly named image files.

1. Put your photos in the folder **`assets/img/quadrants/`**.
2. Name them exactly:

   ```
   quadrants-1.jpg
   quadrants-2.jpg
   quadrants-3.jpg
   quadrants-4.jpg
   ```

3. Any slot with a matching file shows the photo; any slot without one shows a labelled
   placeholder. Using fewer than four? Open `index.html`, find the `id="quadrants-gallery"`
   block, and delete the extra `<a class="photo-slot"> … </a>` lines so no placeholder shows.
4. Commit and push:

   ```bash
   git add .
   git commit -m "Add In Four Quadrants photos"
   git push
   ```

> Tip: phone photos are large (and HEIC won't display in browsers). Resize to ~1600&nbsp;px wide
> and save as JPG first — or just send them to me and I'll optimize and drop them in for you.

---

## 3. Editing text or swapping photos

- All copy lives in `index.html` — edit it directly.
- Photos are in `assets/img/`. To add one, drop an optimized JPG in the folder and add an
  `<a href="…"><img src="…" alt="…"></a>` inside the relevant `.gallery` block.
- Keep committed images reasonably small (these are ~1600px wide, quality-82 JPGs).

---

## 4. Run it locally (optional)

Just open `index.html` in a browser. For the audio to load reliably you can serve it:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```
