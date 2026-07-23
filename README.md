# PDF Editor

Edit a PDF directly on the page, in the browser. Nothing is uploaded — the file
is opened, edited and re-saved entirely inside the tab.

**Live:** https://amankhan321.github.io/PDF-Editor/

## What it does

- **Edit existing text in place.** Double-click any text. It stays in position at
  its own size and colour: the original is covered with the exact background
  colour sampled from the page, and the replacement is drawn over it. No visible
  input boxes.
- **Add anything.** Text boxes, images, stamps, signatures, links, form fields
  (text, multiline, dropdown, radio, checkbox, signature), shapes, freehand ink,
  highlights, underlines and strikeouts.
- **Direct manipulation.** Everything placed can be dragged, resized from any
  corner and rotated, with alignment guides that snap to other elements and to
  the page centre.
- **Whiteout** samples the paper colour, so it disappears into tinted pages.
- **Page operations.** Delete a page, insert a blank one, rotate, zoom, fit
  width, thumbnail navigation.
- **Find and replace** and **OCR for scanned pages** live in a collapsible panel.
  A scanned page shows a quiet inline prompt instead of a technical sidebar.
- **Full undo/redo history.**

Untouched content is never re-rendered — it is copied straight through from the
original file. Only edited lines are painted over and redrawn.

## How it is built

Single HTML file, no build step, nothing to install.

| Piece | Library |
|---|---|
| Rendering + text extraction | pdf.js 3.11 |
| Writing the edited file | pdf-lib 1.17 |
| OCR | tesseract.js 4.1 |

## Known limits

These come from editing a PDF without its original font files. The app reports
each one in the summary after saving rather than hiding it.

- **Font substitution.** If the PDF embeds a font outside the 14 standard PDF
  fonts, edited text is redrawn in the closest of Helvetica / Times / Courier.
- **Auto-fit.** Longer replacement text is scaled down to hold the original line
  width; the save summary says how many lines that affected.
- **Characters** outside WinAnsi are normalised (smart quotes, dashes) or
  replaced.
- Scanned pages need OCR before their text can be edited, and every OCR word is
  a guess.

## Keyboard

| | |
|---|---|
| `V` / `T` | Select tool / Text tool |
| `Ctrl+Z` / `Ctrl+Shift+Z` | Undo / Redo |
| `Ctrl+F` | Find and replace |
| `Ctrl+S` | Apply changes and download |
| `Delete` | Remove the selected element |
| `Esc` | Finish editing, back to Select |

## Running it

Open `index.html`, or serve the folder with any static host.

## Licence

MIT
