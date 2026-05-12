# LDF Comparator

A browser-based tool that compares two LDF (LIN Description File) files and visually highlights the differences between them.

## How to Use

1. Open `LDF_COMPARATOR.html` in your browser.
2. Drag and drop (or select) the **old** LDF file on the left, and the **new** LDF file on the right.
3. Click the **Compare** button.
4. Differences are listed section by section.

No installation required, and no internet connection is needed (CDN dependencies load on first launch).

---

## What It Shows

| Color / Label | Meaning |
|---|---|
| Red — **Deleted** | Existed in the old file, not in the new one |
| Green — **Added** | Exists in the new file, not in the old one |
| Yellow — **Changed** | Line exists in both, but its content has changed |

### Smart Comparison

The tool understands the LDF format and presents certain changes in a more meaningful way:

- **Master / Slaves:** If a node name has changed, it is marked as "changed" instead of "deleted + added".
- **Signal publisher ECU:** If the publishing ECU has changed, it is shown as "publisher changed".
- **Signal subscriber ECU:** If the subscriber list has changed, it is shown as "subscribers changed".
- **Frame publisher:** If the ECU publishing a frame has changed, it is highlighted separately.
- **Schedule delay:** If the delay duration has changed, the difference is shown as `+X ms` / `−X ms`.

---

## Sections and Filters

Comparison results are grouped into separate **tabs** based on LDF blocks:
`Nodes`, `Signals`, `Frames`, `Schedule_tables`, `Signal_encoding_types`, `Node_attributes`, etc.

You can click on the header of each tab to expand or collapse that section.
Inside the `Frames` section, each frame is displayed under its own sub-header; clicking the sub-header hides that frame's changes as well.

The **filter chips** at the top of the page let you show or hide the following categories:

| Filter | Description |
|---|---|
| Delay | Schedule delay changes |
| Publisher | Signal / frame publishing ECU changes |
| Subscriber | Signal subscribing ECU changes |
| Deleted | Lines that were completely removed |
| Added | Lines that were completely added |

---

## Language Option

Using the **TR / EN** button in the top-right corner, you can switch the interface language between Turkish and English.

---

## Technical Notes

- Single-file application: `LDF_COMPARATOR.html`
- No external libraries required; Tailwind CSS and Material Symbols are loaded via CDN.
- The diff algorithm is based on LCS (Longest Common Subsequence).
- Pure JavaScript — no framework is used.
