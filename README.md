# TwinSyncScroll

An offline JS web app that lets you scroll two text fields in sync for side-by-side reading and review.

It is designed for documents that are mostly similar but occasionally drift out of alignment. Scroll either pane independently when needed, then use the center gutter to move both documents by the same number of logical lines.

**Live app:** https://inventwithpython.com/twinsyncscroll

## Features

- Two editable, line-numbered text panes.
- Independent mouse-wheel scrolling in either pane.
- Synchronized scrolling when the mouse wheel is used over the center gutter.
- Center buttons for synchronized scrolling by 1 or 10 logical lines.
- **Sync Cursors to Top** places each pane's remembered cursor line at the top of that pane.
- Draggable center divider for resizing the panes.
- Responsive stacked layout on narrow screens.
- Word wrap can be enabled or disabled independently for each pane; enabled by default.
- Syntax highlighting with automatic detection or manual selection.
- Open any plaintext file with the file picker or drag-and-drop.
- Download either pane using its editable filename field.
- Per-pane search and replace, undo, redo, and select all.
- Per-pane line, column, line count, character count, and selection statistics.
- Autosaves editor state to `localStorage` and restores it on the next visit.
- Automatic light/dark appearance based on the browser or operating-system preference.
- 500 ms delayed button tooltips.
- Accessible labels, keyboard operation, focus indication, and high-contrast light/dark themes.
- 40 interface languages, including right-to-left layout support.
- Share button that copies a description and app link to the clipboard.
- No network connection required after the HTML file has been saved locally.

## Quick Start

1. Download `TwinSyncScroll.html`.
2. Open it in a modern web browser.
3. Open or drag a plaintext file into either pane, or paste/type text directly.
4. Scroll inside a pane to move it independently.
5. Hover over the center gutter and use the mouse wheel to scroll both panes together.
6. Use the gutter chevrons to move both panes by 1 or 10 logical lines.
7. Place the caret where you want in each document and click **Sync Cursors to Top** to put each caret line at the top of its pane.
8. Use the download button on either pane to save that pane's current text.

Everything needed to run the editor—including CSS, JavaScript, icons, translations, favicon data, and PrismJS—is embedded in the HTML file.

## Synchronized Scrolling

TwinSyncScroll does not perform diffing or content matching.

The center gutter moves both documents by the same number of **logical lines**, meaning newline-delimited lines. This makes it possible to manually compensate when one document gains or loses a block of text:

- Scroll over the left or right editor to adjust only that side.
- Scroll over the center gutter to move both sides together.
- Use the single-chevron buttons to move both sides by 1 line.
- Use the double-chevron buttons to move both sides by 10 lines.
- Use **Sync Cursors to Top** to independently move each pane so its last remembered caret line becomes its top visible line.

Word wrapping does not change logical line numbering.

## Keyboard Shortcuts

Shortcuts act on the pane that has focus.

| Action | Windows/Linux | macOS |
| --- | --- | --- |
| Open file | `Ctrl+O` | `Cmd+O` |
| Download file | `Ctrl+S` | `Cmd+S` |
| Find | `Ctrl+F` | `Cmd+F` |
| Find and replace | `Ctrl+H` | `Cmd+H` |
| Undo | `Ctrl+Z` | `Cmd+Z` |
| Redo | `Ctrl+Y` or `Ctrl+Shift+Z` | `Cmd+Shift+Z` |

## Syntax Highlighting

TwinSyncScroll embeds a compact PrismJS bundle and can automatically detect highlighting from common filename extensions. Highlighting can also be selected manually for each pane.

Supported modes:

- Plain text
- HTML
- XML
- CSS
- JavaScript
- JSON
- Markdown
- Python
- YAML
- Bash/shell
- SQL
- C
- C++
- Java
- Go

Syntax highlighting is presentation-only: editing and text selection use the browser's native `<textarea>` behavior.

For very large documents, live syntax highlighting is automatically paused after 750,000 characters to keep editing responsive.

## Supported Interface Languages

The interface automatically uses the browser's preferred language when supported and falls back to English otherwise. A language selector is also available in the app.

- English
- Simplified Chinese
- Spanish
- Arabic
- Indonesian
- Portuguese
- French
- Japanese
- Russian
- German
- Hindi
- Bengali
- Urdu
- Korean
- Vietnamese
- Turkish
- Italian
- Dutch
- Polish
- Thai
- Persian
- Ukrainian
- Czech
- Malay
- Romanian
- Greek
- Hebrew
- Swedish
- Filipino
- Tamil
- Hungarian
- Danish
- Finnish
- Norwegian Bokmål
- Slovak
- Bulgarian
- Serbian
- Croatian
- Slovenian
- Catalan

Arabic, Urdu, Persian, and Hebrew use right-to-left interface direction.

## Files and Persistence

Opening a file reads it locally in the browser. The file is not uploaded anywhere.

Each pane has an editable filename field. When a local file is opened, its filename is loaded into that field; the field is then used as the filename when downloading edited text.

Editor state is autosaved with `localStorage`. Browser storage limits vary, so extremely large documents may exceed the available storage quota even though they can still be edited in the current session.

## Privacy and Offline Use

TwinSyncScroll has no ads, registration, subscriptions, analytics, or trackers. It does not require a server to edit files and does not send document contents over the network.

To keep a permanent offline copy, save `TwinSyncScroll.html` locally and open it directly in a browser.

## Repository Files

```text
TwinSyncScroll.html             Complete offline application
TwinSyncScroll-og-preview.png   Social/Open Graph preview image
README.md                       Project documentation
```

## Development

TwinSyncScroll deliberately has no build step. The application source is readable directly inside `TwinSyncScroll.html`.

The file contains:

- HTML structure and metadata.
- Responsive light/dark CSS.
- Embedded SVG/data-URI assets.
- An embedded minified PrismJS library and selected language grammars.
- Readable, commented application JavaScript.
- Localization data for all supported interface languages.

The application version is defined by the single `APP_VERSION` constant in the source. The current release is **v0.2.0**.

When editing translations, keep the source comments surrounding the translation table intact. The language dropdown is generated from the translation entries that remain in the source.

No package manager, bundler, web server, or third-party CDN is required to develop or run the app.

## Browser Support

TwinSyncScroll targets current desktop and mobile browsers with standard support for JavaScript, `localStorage`, the File API, Blob downloads, and modern CSS.

Clipboard access can depend on browser security rules. If direct clipboard access is unavailable, the app falls back where possible and provides the app URL for manual copying.

## Credits

Generated and human-reviewed by [Al Sweigart](https://inventwithpython.com/).

This app works offline and you own it forever. No ads. No registration. No subscriptions. No trackers. Just right-click and save the `.html` page.

Syntax highlighting is provided by [PrismJS](https://prismjs.com/), embedded directly in the HTML for offline use.
