# Proofsheet — PDF text editor with OCR

Edit the text inside a PDF, in the browser. Nothing is uploaded: the file is
opened, edited and re-saved entirely inside the tab.

**Live:** _(add the deploy URL here)_

## What it does

- **Line-level editing.** Runs from the PDF text layer are regrouped into visual
  lines, so a sentence is one editable field instead of three fragments.
- **No ghosting.** An edited line's box always spans the full width of the
  original line, so deleting text can never expose the old pixels behind it.
- **Background matching.** The dominant colour inside each line box is sampled
  from the rendered page and used to paint out the original, so edits on tinted
  or shaded backgrounds stay invisible.
- **OCR for scans.** Pages with no text layer can be read with Tesseract and
  become editable. Low-confidence words are reported in the activity log.
- **Add text, erase regions, find and replace, undo.**
- **Untouched text is never re-rendered.** Only edited lines are painted over
  and redrawn; everything else is copied through from the original file.

## How it is built

Single HTML file, no build step, no dependencies to install.

| Piece | Library |
|---|---|
| Rendering + text extraction | pdf.js 3.11 |
| Writing the edited file | pdf-lib 1.17 |
| OCR | tesseract.js 4.1 |

## Known limits

These are inherent to editing PDFs without the original fonts, and the UI
marks each one rather than hiding it.

- **Font substitution.** If the PDF embeds a font that is not one of the 14
  standard PDF fonts, edited lines are redrawn in the closest of
  Helvetica / Times / Courier. Those lines get an amber underline.
- **Auto-fit.** Longer replacement text is scaled down to hold the original
  line width. The save log reports how many lines were fitted.
- **Rotated text** is redrawn upright and flagged in the log.
- **Characters** outside WinAnsi are normalised (smart quotes, em dashes,
  ellipses) or replaced with `?`.

## Running it

Open `index.html` in a browser, or serve the folder with any static host.

## Licence

MIT
