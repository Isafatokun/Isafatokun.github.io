# isafatokun.github.io

Personal site — [isafatokun.github.io](https://isafatokun.github.io/)

Static HTML and CSS. No build step, no dependencies. GitHub Pages serves
`master` at the root, so pushing to `master` deploys.

```
index.html              the whole page
css/site.css            tokens, layout, sections, motion
fonts/*.woff2           Geist + Geist Mono, latin subset, self-hosted
images/isaac.jpg        hero portrait (320x380 crop)
cv.pdf                  linked from the hero
og-image.png            1200x630 link preview
favicon.ico             16/32/48
apple-touch-icon.png    180
.nojekyll               serve files as-is, skip Jekyll
```

## Working on it

```bash
python3 -m http.server 8899   # then open http://127.0.0.1:8899
```

Design tokens live at the top of `css/site.css`. Geometry, type scale and the
two easing curves were transcribed from a v0 portfolio template, so px values
are kept as px to stay diffable against it.

## Notes

- Fonts are self-hosted; the page makes no third-party requests.
- All entrance animation is progressive enhancement, gated on a `.js` class.
  Without JavaScript nothing is ever left invisible.
- `prefers-reduced-motion` stops everything, including the marquee — an
  infinitely scrolling band is a vestibular trigger. The marquee also has a
  pause button (WCAG 2.2 SC 2.2.2), since hover alone excludes keyboard and
  touch users.
- The marquee sits inside `.marquee-band`, which clips it. A `rotate(-2deg)`
  full-width bar overflows the viewport and leaves white wedges at the corners;
  the band is 108% wide and offset to fix both.
- Writing cards link to real Medium articles. Update them by hand when you
  publish — there is no feed fetch at runtime.

## Replacing the portrait

Drop a portrait-orientation image at `images/isaac.jpg` (640x760 or larger).
It is cropped to 320x380, `object-position: center top`, and carries a 20%
grayscale that clears on hover. While the file is missing, a placeholder box
shows in its place.
