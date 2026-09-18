# Constitution Day 2026 handbills

A reading of the Constitution on the steps of the U.S. Capitol, Thursday,
September 17, 2026, 11 a.m. — with the asks: write your Representative and
Senators, sign the change.org petition, and read the bill.

| File | What it is | How to print |
| --- | --- | --- |
| `card-4x6.pdf` | Two-sided 4 × 6 in card, page 1 front, page 2 back | Duplex, **flip on long edge**, on 4 × 6 cardstock (FedEx "postcards"), or: |
| `cards-2up-letter.pdf` | Same card, two per letter sheet, with crop marks | Letter cardstock, duplex, flip on long edge, **Actual size / 100 %**, then cut on the marks |
| `poster-letter.pdf` | One-sided 8.5 × 11 in poster for bulletin boards | Letter, single-sided, **Actual size / 100 %** |

Everything sits inside a white margin of at least 0.2 in, so nothing needs to
print to the edge and no bleed is required. Turn off "fit to page", which
would shrink the QR codes.

## Where they're published

- **HTML, on the site:** `/print/constitution-day-2026/card-4x6`, `cards-2up-letter`
  and `poster-letter`, linked from the Constitution Day page. `public/print/constitution-day-2026/`
  holds **symlinks** to the HTML, `handbill.css` and `assets/` here. The build copies
  them as real files, and this directory stays the only source. The PDFs and this
  README are deliberately not linked there.
- **PDFs, in the public repository:**
  [`handbills/`](https://github.com/jaredscribe/public-readings-of-the-founding-documents-act/tree/main/handbills),
  renamed with a `2026-09-17-constitution-day-` prefix and released under CC0.
  After re-rendering a PDF, copy it there too.

`assets/OFL-*.txt` ship beside the fonts, because the site serves the font files
and the Open Font License requires its text to travel with them.

## Links

Every QR code was decoded from a 300 dpi render of the PDFs and checked
against these URLs:

- Site: `https://declareindependence.net/legislation-advocacy` (printed as `declareindependence.net`)
- Model legislation: `https://github.com/jaredscribe/public-readings-of-the-founding-documents-act`
- Petition: `https://www.change.org/readconstitutionaloud` (short link; redirects to the petition, and is printed in full)

## Sources and rebuilding

- `assets/we-the-people.png` and `assets/preamble-texture.png` were extracted
  from the National Archives scan of page 1 of the Constitution (public domain),
  via [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Constitution_of_the_United_States_-_DPLA_-_9ca804144bd5965e992ae3528bc3c6a3_(page_1).jpg),
  recoloured to the site's navy.
- Fonts: EB Garamond (static instances of the variable font; a variable font
  embeds as Type 3, which some print processors render soft) and IM Fell
  English SC. Both SIL Open Font License.
- The PDFs are rendered with headless Chromium from the HTML files beside them:

  ```
  /snap/chromium/current/usr/lib/chromium-browser/chrome --headless=new --disable-gpu \
    --no-pdf-header-footer --print-to-pdf=card-4x6.pdf "file://$PWD/card-4x6.html"
  ```

  Call the binary inside the snap, not `/snap/bin/chromium`: the snap launcher
  cannot read this hidden `.claude/worktrees` path and intermittently hangs for
  two minutes waiting on the desktop document portal.
