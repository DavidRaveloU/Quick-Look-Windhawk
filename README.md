<div align="center">

# Quick Look For Windhawk

A native Quick Look preview for Windows File Explorer, packed as a [Windhawk](https://windhawk.net) mod.

Select a file or a folder and press **Space**. That is the whole idea.

<br>

<a href="https://github.com/DavidRaveloU/Quick-Look-Windhawk/blob/main/LICENSE">
  <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License: MIT">
</a>
<a href="https://github.com/DavidRaveloU/Quick-Look-Windhawk/blob/main/version.json">
  <img src="https://img.shields.io/badge/dynamic/json?url=https://raw.githubusercontent.com/DavidRaveloU/Quick-Look-Windhawk/main/version.json&query=%24.version&label=version&prefix=v&color=informational&cacheSeconds=300" alt="Version">
</a>
<a href="https://www.microsoft.com/windows">
  <img src="https://img.shields.io/badge/platform-Windows%2010%20%7C%2011-0078D6" alt="Platform: Windows 10/11">
</a>
<a href="https://windhawk.net">
  <img src="https://img.shields.io/badge/Windhawk-mod-orange" alt="Windhawk mod">
</a>

</div>

Quick Look docks a real panel **inside the File Explorer window**, next to the file list, and previews
whatever is selected. It is not a floating window: it is a child of the Explorer tab, so it moves with
it, is clipped to it and, if you want, shrinks the Details columns to reserve its own space, the way
File Pilot's inspector does.

Folders open with **Explorer's own file list**, not a copy: the same icons, columns, sorting, view modes
and scrollbars. Text, images, video, audio, PDF, Word, Excel, PowerPoint, archives and everything else
have their own preview or a proper fallback. Nothing runs on a timer in the background, and nothing that
touches the disk ever blocks Explorer.

## Screenshots

<p align="left">
  <img width="760" alt="Quick Look panel docked in File Explorer" src="https://github.com/user-attachments/assets/2dc374a1-185a-4a94-a060-3624ca6b6a92" />
</p>


A few of the things it previews:

<table>
  <tr>
    <td align="center"><img width="230" alt="Aurora Amber" src="https://github.com/user-attachments/assets/7c6b57dc-7d5a-4b93-ab37-919f8af1e0d5" /><br><b>Winrar/Zip</b> &middot; Support</td>
    <td align="center"><img width="230" alt="Aurora Emerald" src="https://github.com/user-attachments/assets/7b7b3a98-c824-4374-9754-8305b3a5f340" /><br><b>Plain Text</b> &middot; Support</td>
    <td align="center"><img width="230" alt="Aurora Violet" src="https://github.com/user-attachments/assets/cf05e7a1-96d4-4b8b-9ffd-907cd0327446" /><br><b>Images</b> &middot; Support</td>
  </tr>
  <tr>
    <td align="center"><img width="230" alt="Aurora Violet" src="https://github.com/user-attachments/assets/08cd3401-0be9-482e-a361-ff6c9325d9ae" /><br><b>PDF</b> &middot; Support</td>
    <td align="center"><img width="230" alt="Aurora Violet" src="https://github.com/user-attachments/assets/5366aae3-ceba-4e45-a517-198c47ddf542" /><br><b>Office Files</b> &middot; Support (Only text)</td>
    <td align="center"><img width="230" alt="Aurora Violet" src="https://github.com/user-attachments/assets/2dc374a1-185a-4a94-a060-3624ca6b6a92" /><br><b>Folder</b> &middot; Support</td>

  </tr>
</table>

## Highlights

- **A panel, not a window.** Space opens it, Space or Esc closes it, the header has a close button for the
  mouse. It docks on the right, or at the bottom when the window is too narrow; drag its edge to change
  its width and the width is remembered.
- **Folders, with Explorer's own list.** The preview hosts a real Explorer browser, so icons, columns,
  sorting, grouping and the Details / List / Icons view modes are Explorer's. A view dropdown in the
  header switches between Details, List, Small, Medium, Large and Extra Large icons.
- **A real filter, at the same level.** Typing in the filter box shows only the matching direct children
  of the previewed folder, with their original columns, and clearing it brings the folder back. No
  subfolder is ever searched.
- **Text and code, detected by content.** No extension list: a file is text when its bytes say so, so
  `.ahk`, `.psd1`, `.config`, extensionless files and anything else just work. UTF-8, UTF-16 LE/BE and the
  ANSI code page are decoded, and the footer reports which one was used, the size and the line count.
- **An editor-style toolbar.** Word wrap, line numbers (a wrapped continuation keeps its number once), a
  whitespace inspector that draws spaces as dim dots, and alternating row colors. The four toggles are
  remembered if you want them remembered, and the defaults are settings.
- **Search inside the file.** The same filter box keeps only the matching lines, each with its original
  line number, and highlights every match with your Windows accent color.
- **Documents without Office.** Word, Excel, PowerPoint, RTF and OpenDocument files are opened as a zip
  of XML parts and reduced to their text, so they preview instantly even when Office is not installed.
  Old binary `.doc`, `.xls` and `.ppt` files use the Windows preview handler when one is registered.
- **Images, video and audio.** Images are decoded at full resolution, videos show a frame and audio shows
  its album art, both through the same still-image providers Windows uses.
- **PDF.** Rendered by the Windows PDF preview handler, the same component Explorer's preview pane uses,
  hosted inside the panel. Zoom and scroll belong to the handler.
- **Archives.** A `.zip` (and any format the shell exposes as a folder) lists its contents in the native
  list. Formats with no shell namespace fall back to the properties view.
- **A fallback that still helps.** Anything else shows the real file icon plus its type, size, modified
  date and full path.
- **Colors that follow Windows.** The panel samples Explorer's actual pixels for the background and the
  text, and takes the accent from Windows itself, so light, dark and custom accents look native.
- **Explorer never freezes.** Listing a folder, reading a file, decoding an image, building a thumbnail or
  checking a cloud placeholder all run on worker threads. The panel opens at once with a loading state,
  a new selection cancels the previous load, and a file that is only a cloud placeholder is never
  downloaded just to be previewed.

## Install

1. Install [Windhawk](https://windhawk.net) (Windows 10 or 11).
2. In Windhawk open **Mods** → **Create a new mod**, paste the contents of
   [`quick-look.wh.cpp`](quick-look.wh.cpp) in place of the editor contents and save.
3. Select a file or folder in File Explorer and press **Space**.

Quick Look is an **injected** mod: it runs inside `explorer.exe`, which is what lets the panel be a real
child of the window instead of a window that follows it.

## Keys

| Key | Action |
| --- | --- |
| **Space** | Open or close the preview |
| **Esc** | Close the preview |
| **Click the close button** | Close the preview with the mouse |
| **Shift + wheel** | Scroll a text preview sideways when word wrap is off |
| **Mouse wheel / drag the bars** | Scroll the preview |

## Settings

| Setting | Default | What it does |
| --- | --- | --- |
| Shrink columns to fit the panel | On | Shrinks the file view and scales the Details columns to the space left by the panel. Turn it off to overlay the panel instead. |
| Remember the text preview options | On | Keeps wrap, line numbers, whitespace dots and alternating rows as you left them for the next window or session. |
| Line numbers by default | Off | The gutter used when the options are not remembered. |
| Alternating rows by default | Off | The alternating row color used when the options are not remembered. |
| Write a diagnostic log file | Off | Appends diagnostics to `%TEMP%\quick-look.log`. Off because every line is a disk write. |

## What each file shows

| Selection | Preview |
| --- | --- |
| Folder | Explorer's native list, with a view dropdown, a name filter and file/folder counts |
| Text, code, config, logs | Text with wrap, line numbers, whitespace dots, alternating rows and in-file search |
| Word, Excel, PowerPoint, RTF, OpenDocument | The document text, read directly without Office |
| Old `.doc`, `.xls`, `.ppt` | The Windows preview handler when one is installed, otherwise the properties view |
| Images (`png`, `jpg`, `gif`, `bmp`, `tif`, `ico`, `webp`…) | The decoded image, fitted to the panel |
| Video and audio | A frame or the album art, as Windows produces it |
| PDF | The Windows PDF preview handler, hosted in the panel |
| Archives (`.zip`, and formats with a shell namespace) | The archive contents in the native list |
| Anything else | The real file icon with type, size, modified date and path |

## How it behaves

- **The panel never navigates.** Double-clicking a folder inside the preview opens its **Properties**;
  it does not enter it. Quick Look is a preview, not a file manager.
- **Single click selects.** A double click on empty space does nothing.
- **Cloud files are left alone.** A file that is only a placeholder is not downloaded to be previewed.
- **Text is capped.** A text preview reads the first 200 KB and says so in the footer.

## Troubleshooting

- **Space does nothing.** Press **Ctrl + Alt + Shift + L**: it forces the panel toggle and bypasses the
  focus check. If that opens the panel, the mod is loaded and the focus detection is the blocker.
- **Something looks wrong.** Enable **Write a diagnostic log file** in the mod settings, reproduce it,
  and attach `%TEMP%\quick-look.log` to the issue. **F8** dumps the Explorer window tree to the Windhawk
  log and **Ctrl + Alt + Shift + D** dumps the foreground tree even while the panel is hidden.
- **A document shows only text.** That is by design: modern Office and OpenDocument files are read as
  text, so layout, images and colors are not part of the preview.

## Contributing

Bug reports, fixes and new features are welcome. Open an
[issue](https://github.com/DavidRaveloU/Quick-Look-Windhawk/issues) with your Windows build, the mod
version, the steps to reproduce it and, when it is visual, a screenshot or a short clip.

For a pull request: fork, branch from `main`, change `quick-look.wh.cpp`, confirm it compiles and open
the PR describing **what** changed and **why**. One bug or feature per PR is much easier to review.

Leave `@version` in the mod header and `version.json` alone: the maintainer sets both when a release is
published, so they always agree with what the mod shows.

## License

Released under the **MIT License**. See [`LICENSE`](LICENSE).

Copyright (c) 2026-present David Ravelo.
