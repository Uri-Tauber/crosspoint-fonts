# CrossPoint Fonts

Pre-built `.cpfont` font files for [CrossPoint Reader](https://github.com/crosspoint-reader/crosspoint-reader), an open-source e-reader firmware for the Xteink X4 (ESP32-C3).

This repo hosts only release assets — the build tooling and font configuration live in the [main firmware repository](https://github.com/crosspoint-reader/crosspoint-reader/tree/main/lib/EpdFont/scripts).

## Installing fonts on your device

### From the device (recommended)

1. Go to **Settings > System > Download Fonts**
2. Connect to WiFi when prompted
3. Browse available fonts and select one to download
4. The font appears immediately in **Settings > Reader > Font Family**

### From a web browser

1. Connect your CrossPoint reader to WiFi
2. Open the device's web interface in your browser
3. Go to the **Fonts** tab
4. Upload `.cpfont` files from a [release](https://github.com/crosspoint-reader/crosspoint-fonts/releases)

### Manual SD card copy

1. Download `.cpfont` files from the latest [release](https://github.com/crosspoint-reader/crosspoint-fonts/releases)
2. Create a font family folder on the SD card and copy the files:

       SD Card Root/
       └── fonts/
           └── Literata/
               ├── Literata_12.cpfont
               ├── Literata_14.cpfont
               ├── Literata_16.cpfont
               └── Literata_18.cpfont

3. Insert the SD card and restart the device

## Available fonts

### Serif

| Font | Description |
|------|-------------|
| Literata | Screen-optimized serif (Latin, Greek, Cyrillic) |
| SourceSerif4 | Adobe transitional serif (Latin, Greek, Cyrillic) |
| NotoSerifExtended | Serif (Latin, Greek, Cyrillic) |
| Merriweather | Warm serif for long-form reading (Latin, Cyrillic) |
| Lora | Calligraphic serif for literary reading (Latin, Cyrillic) |
| GentiumBookPlus | Scholarly serif with wide Unicode coverage (Latin, Greek, Cyrillic, IPA) |
| IBMPlexSerif | Professional serif (Latin, Greek, Cyrillic) |
| Bitter | Slab serif designed for e-ink (Latin, Cyrillic) |
| Alegreya | Calligraphic serif/display (Latin, Greek, Cyrillic) |

### Sans-serif

| Font | Description |
|------|-------------|
| NotoSansExtended | Sans-serif (Latin, Greek, Cyrillic, Georgian, Armenian, Ethiopic) |
| Inter | Modern sans-serif (Latin, Greek, Cyrillic) |
| SourceSans3 | Adobe humanist sans-serif (Latin, Greek, Cyrillic) |
| IBMPlexSans | IBM corporate sans-serif (Latin, Greek, Cyrillic) |

### Monospace

| Font | Description |
|------|-------------|
| IBMPlexMono | Monospace for code and technical reading (Latin, Greek, Cyrillic) |
| SourceCodePro | Adobe monospace with excellent hinting (Latin) |

### Accessibility

| Font | Description |
|------|-------------|
| AtkinsonHyperlegibleNext | Accessibility font for low vision (Latin) |
| LexicaUltralegible | Accessibility font for low vision / dyslexia (Latin) |

All fonts include regular, bold, italic, and bold-italic styles at 12, 14, 16, and 18pt.

## Converting custom fonts

See the [SD Card Fonts documentation](https://github.com/crosspoint-reader/crosspoint-reader/blob/main/docs/sd-card-fonts.md) in the main repo for instructions on converting your own TrueType/OpenType fonts to `.cpfont` format.

## How releases are built

Releases are published automatically by a [CI workflow](https://github.com/crosspoint-reader/crosspoint-reader/blob/main/.github/workflows/release-fonts.yml) in the main firmware repo. The pipeline:

1. Reads font families from a [declarative YAML config](https://github.com/crosspoint-reader/crosspoint-reader/blob/main/lib/EpdFont/scripts/sd-fonts.yaml)
2. Downloads source TTF/OTF files from upstream font repositories
3. Converts them to `.cpfont` binary format using `fontconvert_sdcard.py`
4. Generates a `fonts.json` manifest for the device's download UI
5. Publishes everything as a GitHub Release on this repo

## License

The `.cpfont` files distributed here are converted from open-source fonts under their original licenses (primarily [SIL Open Font License](https://openfontlicense.org/) and [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0)). See each font's upstream repository for specific license terms.

This repository and its automation are part of the [CrossPoint Reader](https://github.com/crosspoint-reader/crosspoint-reader) project, licensed under the [MIT License](https://github.com/crosspoint-reader/crosspoint-reader/blob/main/LICENSE).
