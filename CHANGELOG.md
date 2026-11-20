# Changelog

All notable changes to **Quick Look** are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

> Releases are listed **newest first**. Sections are only ever added: a new version gets a
> new entry on top and the previous ones are kept exactly as they were.

## [1.1.0] - 2026-11-20

### Added

- **Glass effects are supported.** With ExplorerBlurMica, DWMBlurGlass or similar, the panel follows
  the effect like the rest of the window, in dark and in light mode. Its text is drawn solid instead of
  being added to the blur, and an image preview is never tinted by what is behind Explorer. Without an
  effect the panel is drawn exactly as before.
- **Zoom and pan for images.** Double click an image to switch between fit and 100%, drag a zoomed
  image to pan it, and use the wheel (Shift for sideways) to scroll it.

### Changed

- **Colors follow the Windows app mode.** The text color now depends only on whether Windows is light
  or dark, so it no longer turns gray or white from one preview to the next. The background stays
  Explorer's own surface. The accent still comes from Windows.
- **Archives show the shell's own view without a name filter.** A results folder cannot resolve the
  name of an item inside an archive, so the filter box is hidden there. Folders keep the filter.

### Fixed

- **Typing in the filter no longer opens an Explorer window.** The panel's own results view is no
  longer treated as a navigation, and a navigation outside the previewed folder is cancelled silently.
- **The filter shows the right items.** Only the matching direct children of the previewed folder are
  listed, with no duplicates and no stray file.
- **The icon in the properties view** is taken from a frame the shell did not pad, so it fills its box
  instead of sitting tiny in the corner.
- **A folder inside an archive** shows an empty date instead of the 1601 epoch.
- **Opaque images scale sharply.** Only an image with real transparency is blended; a photo or a
  screenshot is scaled with a crisp filter.

## [1.0.0] - 2026-11-09

The first release: a preview panel that lives inside File Explorer.

### Added

- **The panel.** **Space** opens the preview of the selected file or folder and **Space** or **Esc**
  closes it, with a close button for the mouse. It is a real child window of the Explorer tab, so it
  moves and clips with the window instead of following it. It docks on the right, or at the bottom when
  the window is too narrow, the edge can be dragged to change its width, and the width is remembered.
- **Shrink columns to fit the panel.** In Details view the file view and its columns are scaled to the
  space the panel takes, the way File Pilot's inspector does. It can be turned off to overlay the panel
  instead.
- **Folders previewed with Explorer's own list.** The panel hosts a real Explorer browser: the same
  icons, columns, sorting, grouping, scrollbars and Details / List / Icons view modes. A view dropdown in
  the header switches between Details, List, Small, Medium, Large and Extra Large icons.
- **A name filter at the same level.** The filter box shows only the matching direct children of the
  previewed folder, with their original columns, and clearing it brings the folder back. No subfolder is
  ever searched.
- **Text and code, detected by content.** No extension list: a file is text when its bytes say so, so
  `.ahk`, `.psd1`, `.config`, extensionless files and anything else work. UTF-8, UTF-16 LE/BE (with or
  without a BOM) and the ANSI code page are decoded, and the footer reports the encoding, the size and
  the line count.
- **An editor-style toolbar.** Word wrap, line numbers with a dimmer gutter, a whitespace inspector that
  draws spaces as dim dots, and alternating row colors. A wrapped continuation keeps the color of its
  source line and is numbered only once.
- **Search inside the file.** The same filter box keeps only the matching lines, each with its original
  line number, and highlights every match with the Windows accent color.
- **Documents without Office.** Word, Excel, PowerPoint, RTF and OpenDocument files are read directly as
  text from their zip of XML parts, so they preview instantly and do not need Office installed. Old
  binary `.doc`, `.xls` and `.ppt` files use the Windows preview handler when one is registered.
- **Images, video and audio.** Images are decoded with WIC at full resolution and fitted to the panel.
  Videos show a frame and audio its album art. When Windows has no thumbnail provider for the extension,
  the first video frame is decoded with Media Foundation instead, so containers such as `.mpg4` preview
  too.
- **PDF.** Rendered by the Windows PDF preview handler, the same component Explorer's preview pane uses,
  hosted inside the panel.
- **Archives.** A `.zip` — and any format the shell exposes as a folder — lists its contents in the
  native list. Formats with no shell namespace fall back to the properties view.
- **A properties fallback.** Anything else shows the real file icon plus its type, size, modified date
  and full path, with no command hints in the footer.
- **Colors that follow Windows.** The panel samples Explorer's actual pixels for the background and the
  text, and takes the accent from Windows through `UISettings` (including the dark and light focus
  shades), so light, dark and custom accents look native.
- **Explorer never freezes.** Listing a folder, reading a file, decoding an image, building a thumbnail
  or checking a cloud placeholder run on worker threads. The panel opens at once with a loading state, a
  new selection cancels the previous load, and a file that is only a cloud placeholder is never
  downloaded just to be previewed.
- **Settings.** Shrink columns to fit the panel, remember the text preview options (or start from the
  defaults: line numbers and alternating rows).
