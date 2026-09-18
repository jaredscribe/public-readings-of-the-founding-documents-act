# Constitution Week 2027 handbills

"Read the Constitution Aloud" — Constitution Week, September 17–23, 2027, on
the Capitol East Steps. The back asks three things: that Congress read it on
the House and Senate floor, that the reader sign the petition for an executive
action, and that a member introduce the bill and its companion.

| File | What it is | How to print |
| --- | --- | --- |
| `cards-4up-letter.pdf` | The card, **four to a letter sheet**, cut marks at the sheet edges | Letter cardstock, duplex, **flip on long edge**, 100 %, then cut on the two centre lines |
| `card-quarter-letter.pdf` | The same card alone, 4.25 × 5.5 in, page 1 front, page 2 back | Only if the shop prints that size directly; it costs about four times as much per card |
| `poster-letter.pdf` | One-sided 8.5 × 11 in poster | Letter, single-sided, 100 %. Plain paper is fine — a poster does not need cardstock |

Print at **Actual size / 100 %**, never "fit to page", which shrinks the QR
codes. Everything sits inside a white margin, so no bleed is needed.

**Why quarter-letter.** A copy shop charges by the printed side. Four cards to
a sheet cost about a quarter of a 4 × 6 card printed on its own — roughly $1 a
card rather than $3.98 at the $1.99-per-side price paid on 2026-09-17. All four
cards on a sheet are identical, so a long-edge duplex flip lines the backs up
with no mirroring. With a week of lead time, a postcard printer is cheaper
still (~$0.30–0.45 a card at 100).

The artwork carries no time of day and no year on its face beyond the
`1787 – 2027` line, so the same files serve any year the dates fall on.

## Links

Every QR code was decoded from a 300 dpi render of these PDFs:

- Site: `https://declareindependence.net/constitution-week` — printed in full, and the footer QR code points there. **That page does not exist yet**; it must be published before these are printed.
- Petition: `https://www.change.org/readconstitutionaloud`
- Model legislation: `https://github.com/jaredscribe/public-readings-of-the-founding-documents-act`

## Sources and rebuilding

`assets/` is a symlink to the Constitution Day set's assets — same fonts, same
"We the People" lettering from the National Archives scan, same QR codes. The
CSS is a copy, so this event's layout can drift without touching the other.

The bill named on the back is the repository's **Commemorative Days Observance
Act** (Track A2), the companion to the Public Readings of the Founding
Documents Act. The separate *Spring Holidays Reform Act* lives in its own
repository and is **not** named here.

Rebuild with the `print-handbills-from-html` skill's renderer:

```
sh ~/.claude/skills/print-handbills-from-html/scripts/render-pdf.sh "$PWD" \
  card-quarter-letter.html cards-4up-letter.html poster-letter.html
```

Call the chrome binary inside the snap, not `/snap/bin/chromium`. See
`../constitution-day-2026/README.md` for why.
