# Adding Audio to Posts

## 1. Place Your Audio File

Put your MP3 file in:
```
static/audio/
```

**Naming convention:** Match the post filename for easy reference.
- Post: `content/updates/20260114-website-live.md`
- Audio: `static/audio/20260114-website-live.mp3`

## 2. Add the Shortcode to Your Post

In your markdown file, add this line where you want the player to appear (usually right after the front matter):

```markdown
---
title: "Your Post Title"
date: 2026-01-14T09:00:00-07:00
description: "Your description"
draft: false
---

{{< audio file="your-filename.mp3" >}}

Your post content starts here...
```

## 3. That's It!

The player will display with:
- Play/pause controls
- Progress bar
- Speed controls (0.75x, 1x, 1.25x, 1.5x, 2x)
- Download link

## Example

For a post called `20260115-new-update.md`:

1. Save audio to: `static/audio/20260115-new-update.mp3`
2. Add to post:
   ```markdown
   {{< audio file="20260115-new-update.mp3" >}}
   ```

## Notes

- Audio files are served from `/audio/` on the live site
- Supported format: MP3 (`.mp3`)
- The shortcode file is located at: `layouts/shortcodes/audio.html`
- Styling is in: `assets/css/custom.css` (search for "AUDIO PLAYER")

---

# External Links

For external links that open in a new tab, use the `extlink` shortcode:

```markdown
{{< extlink url="https://worthchoosing.org" text="Worth Choosing" >}}
```

This renders as a link that opens in a new tab with proper `rel="noopener"` for security.

**Example usage in a post:**
```markdown
Check out {{< extlink url="https://chrisplough.com" text="Christoph's site" >}} for more.
```
