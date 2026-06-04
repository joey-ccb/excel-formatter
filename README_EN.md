# Excel Formatter

[中文版](README.md)

A pure frontend Excel formatting tool that solves inconsistent formatting issues in Excel files, including fonts, margins, paper size, and layout structure.

![Excel 格式统一工具](./Excel%20格式统一工具.png)

## Features

- **Paper Settings**: Unified A4 paper size with smart portrait/landscape auto-switching (auto landscape when content width > 19cm)
- **Page Margins**: Unified top, bottom, left, and right margin configuration
- **Unified Fonts**: Separate font size and style settings for headers, data, and note rows
- **Layout**: Unmerge cells (fill with previous row values), auto column width, borders, alignment, text wrapping
- **Freeze Header**: Auto-freeze the header row for easy scrolling
- **Print Scaling**: Auto-scale to 1 page width for consistent printing
- **Multi-Sheet Support**: Select different sheets in Excel files
- **Column Management**: Show/hide specific columns when there are too many columns
- **Format Presets**: 4 built-in presets (Standard Report, Wide Table, Compact, Formal Document)
- **Custom Config**: Support YAML configuration files for custom format rules
- **Export Excel**: Export formatted Excel files with page settings preserved
- **Print Preview**: Browser print preview support

## Quick Start

### Option 1: Direct Open

Double-click `excel-formatter.html` to open in your browser.

### Option 2: Local Server (Recommended)

```bash
# Using Python
cd Excel统一格式工具
python -m http.server 8080

# Then visit http://localhost:8080/excel-formatter.html
```

## Usage

1. **Upload File**: Click the upload area or drag & drop an Excel file (.xlsx/.xls)
2. **Select Sheet**: Choose the sheet to process for multi-sheet files
3. **Choose Format**: Select a preset format from the dropdown or upload a custom YAML config
4. **Column Management**: Column selector appears automatically when columns > 8, check columns to display
5. **Format**: Click the "Format" button to process data
6. **Export/Print**: Export Excel or print preview after formatting

## Configuration

Configuration file is located at `config/formatter-config.yaml`:

```yaml
paper:
  size: A4                    # Paper size
  orientation: auto           # auto/portrait/landscape
  landscape_threshold: 19     # Auto landscape threshold (cm)

margins:
  top: 1.5                    # Top margin (cm)
  bottom: 1.5                 # Bottom margin (cm)
  left: 1.8                   # Left margin (cm)
  right: 1.8                  # Right margin (cm)

font:
  header:
    size: 12
    bold: true
  data:
    size: 10
  note:
    size: 9
    italic: true

layout:
  unmerge:
    enable: true
    fill_mode: previous_row
  column_width:
    mode: auto
  border:
    style: thin
  alignment:
    horizontal: auto
  wrap_text: true

freeze:
  enable: true
  pane: "A2"

print:
  enable: true
  fit_to_width: 1
```

## Built-in Presets

| Preset Name     | Description                                            |
| --------------- | ------------------------------------------------------ |
| Standard Report | Default config, A4 smart orientation, standard margins |
| Wide Table      | Landscape layout, narrow margins, for wide tables      |
| Compact         | Small margins, small fonts, space-saving               |
| Formal Document | Portrait layout, wide margins, large fonts             |

## Tech Stack

- **HTML/CSS/JavaScript**: Pure frontend, no backend required
- **SheetJS (xlsx)**: Excel file parsing and generation
- **js-yaml**: YAML configuration file parsing

## Browser Compatibility

Supports modern browsers: Chrome, Edge, Firefox, Safari

## License

MIT License

## Author

[joey-ccb](https://github.com/joey-ccb)
