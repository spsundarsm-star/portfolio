# Sundaramoorthi S: Portfolio

A single-page portfolio built with plain HTML, CSS and JavaScript. There is no build step and nothing to install, so it works on GitHub Pages as is.

## What's in this folder

| Item | Purpose |
|---|---|
| `index.html` | The whole website (markup, styles, scripts and the list of works) |
| `resume.pdf` | Your resume, used by the "Download resume" link on the page inside the book |
| `assets/` | Your 95 original works, untouched |
| `assets/doodle.svg`, `assets/doodle.png` | Your full-length standing doodle as standalone art (the site uses its own interactive copy inside `index.html`) |
| `assets/portrait.jpg` | Your profile photo (welcome screen and sidebar) |
| `assets/thumbs/` | 82 small copies (about 900 px) that the page loads, so it stays fast |
| `README.md` | This file |

The page never loads the big originals unless a visitor clicks a design to open it full size. Animated GIF ads are used straight from `assets/` so they keep moving.

## How your works appear on the site

| Group | Designs | Where it shows |
|---|---|---|
| Social media ads | 35 | Project card + gallery |
| Web banners and display ads | 24 | Project card + gallery |
| Email design | 15 | Project card + gallery |
| Logo and identity | 8 | Project card + gallery |
| Print media | 7 | Project card + gallery |
| Photo editing | 4 | Project card + gallery |
| Figma interfaces | 2 | Project card + gallery |

- **Gallery:** the "View all N designs" button on each project card opens every design in that group. Click a design to open the full-size original in a new tab. Close with the X, Esc, or a click outside.

## Your profile photo

Your profile photo is `assets/portrait.jpg`. It shows in a circle on the welcome screen and in the sidebar. To change it, replace that file with a new photo of the same name. A portrait with your face in the upper half works best, because the circle crops the photo.

## Add a new work later

1. Put the original image in `assets/`.
2. Make a smaller copy about 900 px on the long side and save it as a JPG in `assets/thumbs/`. GIFs don't need a copy.
3. Open `index.html` and search for `works-data`. This is the list of works. Add one entry to the right group:

```json
{"n":"Short name","o":"assets/My%20Original.jpg","t":"assets/thumbs/my-copy.jpg","w":900,"h":900}
```

- `n` is the description (alt text).
- `o` is the original. Replace spaces in the file name with `%20`.
- `t` is the small copy. For a GIF, use the same path as `o`.
- `w` and `h` are the width and height of the small copy in pixels.

4. Update the number in the card's "View all N designs" button.

To remove a work, delete its entry.

## Publish on GitHub Pages

The `assets/` folder has about 180 files (97 MB), so use one of these:

- **GitHub Desktop** (easiest): add this folder as a repository, commit, then click Publish.
- **Git command line:** `git add . && git commit -m "Portfolio" && git push`.
- **Browser upload:** GitHub allows only 100 files per drag-and-drop, so upload in batches (for example `assets/` first, then `assets/thumbs/`, then the rest).

Then:

1. Create a repository (for example `your-username.github.io`).
2. Go to **Settings > Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
4. Choose branch **main** and folder **/ (root)**, then click **Save**.
5. Wait about a minute. Your site will be live at `https://your-username.github.io/`.

To preview locally, open `index.html` in a browser.

## Customize

- **Open to work pill:** in the `<script>` near the bottom, find the `CONFIG` block. Set `showOpenToWork: false` to hide it. `timeZone` and `place` control the sidebar clock.
- **Name, role, summary:** search for `Sundaramoorthi` and `Senior Executive Designer`. The "about me" summary now lives in one place only: the paragraph right under the headline at the top of the page (search for `class="about-line"`). The "Currently: ..." line above it is the `class="now"` element.
- **Headline:** edit the three `h-line` lines at the top of the page.
- **Contact and social links:** they live in one place only, the cards in the Contact overlay (open it with Contact in the sidebar): Email, Phone, LinkedIn, Instagram, Twitter and Facebook. To change a link, edit that card's `href`. The hero no longer repeats them.
- **Project cards:** each card is one `<article class="proj">`. Edit its text and the `--tint` and `--tint-bg` colors in its `style` attribute.
- **Experience:** edit the `<ul class="jobs">` list in the "The story so far" section (the nav link is still called About).
- **Tools:** edit the `<ul class="sk">` list.
- **Skills and tools strip:** edit the words inside the `<div class="strip">` block.
- **"That's a wrap on the work" section:** the shapes, grid and headline react to the cursor. Edit the words in the `<h2 id="wrap-title">` block (keep the text in both the `aria-label` and the inner `span`). Each shape is a `<g class="shape">` with its center (`data-cx`, `data-cy`) and how far it drifts (`data-depth`; a negative number drifts the other way).
- **Standing doodle (hero, right side):** a full-length figure in the pose of your illustration: blue suit, white open-collar shirt, hands in the pockets, head straight and centered over the neck, standing all the way down to the shoes, with your doodle face on top (traced and measured from your photo). The body is a vector trace of your illustration, so the folds, lapels and shadows follow it. The legs continue the trousers down to the ankles and the shoes are drawn. It is an SVG inside `index.html` (search for `id="doodle"`). At rest the suit and shirt are dimmed, while the skin of your face, neck and chest is always one and the same color. Near the cursor it lights up: the suit turns blue, the outline draws itself around the whole figure and the hair strands appear. The eyes follow the cursor, it blinks, and clicking makes it wink and throw sparks. On phones, tap it to light it up. To change the colors, edit the `.d-l0` to `.d-l11` rules (the suit and shirt shades, each with a dim and a lit color) in the style block; the face uses the `.d-hair` and `.d-beard` rules. The caption under it shows your local time.
- **Three design games, side by side (in the "That's a wrap on the work" section):** on wide screens they sit in a row of three, and on smaller screens they stack one under the other. Every game saves the visitor's best score in their own browser.
  - **Match the color** (5 rounds): match a target swatch with hue, saturation and lightness sliders. Scored by perceptual color difference. Search `colorGame` in `index.html`.
  - **Kern it** (3 short words: AVA, WAVE, LATTE): the letters start a little out of place, and you drag them sideways (or use the arrow keys, Shift for bigger steps) until the spacing looks even. A gentle magnet clicks a letter into place and turns it yellow when it gets close, and a message tells you when everything has clicked. The first letter stays put. The answer key is the font's own kerning, measured in the browser, so it follows whatever font the page is using. After you lock in, an outline shows where you left the letters and they slide to the correct positions. To change the words, edit the `WORDS` list in the script (search `kernGame`), and to change how strong the magnet is, edit `SNAP`.
  - **Hit the ratio** (5 rounds): resize a rectangle to a target proportion, such as the golden ratio, 16:9, 4:3, 3:2, 2:1 or A4 paper. The target number (for example 1.78 : 1) is shown, along with a live readout of your number as you slide, and the box glows when you are within 2%. After you lock in, a dashed outline shows the target. Scoring is forgiving for small misses. To change the ratios, edit the `GOALS` list (search `ratioGame`).
  - Clicks and drags inside the games don't trigger the shape-tossing effect of the section around them.
- **Contact card doodles:** each of the six cards in the Contact overlay has its own doodle of you with three reactions. Email: love-mail, surprised notification, laughing. Phone: talking, laughing, surprised. LinkedIn: thumbs-up, verified badge, wink and thumbs-up. Instagram: wink with hearts, heart eyes, sunglasses. Twitter: chatting (speech bubble), heart in a bubble, laughing. Facebook: thumbs-up, wow, laughing with hearts. They switch every 1.2 seconds while you hover over (or tab to) a card, and return to the first reaction when you leave. Each reaction is a group with the class `rx0`, `rx1` or `rx2` inside the card's `<svg class="cdoodle">`.
- **Colors and fonts:** change the variables in `:root` at the top of the `<style>` block.
- **Resume:** replace `resume.pdf` with a new file of the same name. The resume appears in one place only: the page inside the book in "The story so far" (its Download resume link).
- **Resume book (in "The story so far"):** a single-page book. The cover shows your doodle cartoon in a yellow circle, and inside is the resume page with the Download link. There is no tap to open and no close button: the cover opens and closes by itself. It waits closed for a moment, the cover swings open, it rests on the resume page for about seven seconds, then closes, and the loop repeats. Hover over the book and it pauses. Drag it sideways to open or close it by hand (drag left to open, right to close), or focus it with the keyboard and use the left and right arrow keys, Home and End. Tabbing into the book opens it so the Download link is reachable. While the book is closed, the cartoon on the cover blinks, hops now and then, follows the cursor with its eyes and winks when you hover over it. Behind the book, a living grid drifts and bends toward the cursor, with eight floating doodle shapes that shift with the mouse and pop whenever the cover opens or closes. On touch screens the lean is switched off, and visitors whose devices ask for reduced motion see a still book already open on the resume page. To change the timing, edit the numbers in the `advance` function (search `resume flipbook`).

## Good to know

- **Contact:** the site uses email and phone links. GitHub Pages can't process forms. Use a service such as Formspree if you want a contact form.
- **Phone number and location:** both are visible on the page. Remove them from the contact overlay and footer if you prefer.
- **Client work:** your designs show real brand names and campaigns. Check that you are allowed to show them publicly.
- **Fonts:** they load from Google Fonts (Inter Tight, Inter, IBM Plex Mono and Caveat), so the site needs an internet connection to show them. Without it, it falls back to system fonts.
