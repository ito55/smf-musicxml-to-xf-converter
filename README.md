# 🎼 xf-tools

## Overview

`xf-tools` is a Python command-line utility designed to synthesize **XF files** (YAMAHA's extended format) by combining two essential inputs: a **MusicXML** file (containing lyrics and chord data) and a **Standard MIDI File (SMF)** (containing performance data like melody and timing).

This tool allows musicians and developers to utilize standard notation software like MuseScore to input detailed musical information (chords and lyrics) and integrate it with existing, high-quality performance data, resulting in a single XF file ready for display and playback on YAMAHA keyboards and modules.

## ✨ Key Features

* **MusicXML Parsing:** Extracts structural information, specifically lyrics (`<lyric>`) and chord harmony (`<harmony>`) from MusicXML.
* **SMF/MIDI Handling:** Reads the base SMF, preserves all existing performance events (Note On/Off, Pitch Bend, CC data), and inserts new XF events at precise timings.
* **XF Encoding:** Converts the parsed MusicXML chord and lyric data into the specific **YAMAHA System Exclusive (SysEx) and Meta Events** required by the XF standard.
* **Modular Design:** Built with future extensibility in mind (e.g., support for other input formats or XF analysis).

## ⚙️ Requirements

* Python 3.8+
* Dependencies (Install via `requirements.txt`):
    * `mido` (For robust MIDI/SMF handling)
    * `lxml` (Recommended for efficient MusicXML parsing)

## 🚀 Usage

The tool accepts two input files and outputs one combined XF file.

### 1. Preparing Input Files

1.  **Base SMF (`base.mid`):**
    * The MIDI file containing the core musical performance data (melody, instrument tracks, volume/expression events).
2.  **MusicXML (`score.musicxml`):**
    * The MusicXML file exported from notation software (e.g., MuseScore) which has been explicitly edited to include the desired **Lyrics** and **Chords**.

### 2. Execution Command

Run the tool from your terminal, specifying the paths to the input and output files:

```bash
python3 cli.py --base-mid <path/to/base.mid> --score-xml <path/to/score.musicxml> --output <output_file_name.mid>
```

Example:
```bash
python3 cli.py --base-mid data/performance.mid --score-xml data/song_with_lyrics.musicxml --output out/my_song_xf.mid
```
## 💻 Project Structure

The project uses a modular design to separate concerns and facilitate future development of additional XF utilities (e.g., XF analysis, alternative format support).

```
xf-tools/
├── cli.py             # Handles Command Line Interface (CLI) arguments and main control flow.
├── converter.py       # xf to MusicXML converter.
├── merger.py          # Core logic for data transformation (MusicXML to XF Data structures).
├── midi_handler.py    # Manages SMF reading, writing, and event insertion using the mido library.
├── xml_parser.py      # Contains functions dedicated to parsing the MusicXML structure.
└── requirements.txt   # Lists all required Python packages.
```
## 🗺️ Roadmap & Future Plans

* **XF Analyzer:** Implement a function to reverse-engineer and display chord/lyric information from existing XF files.
* **Alternative Input:** Investigate support for simpler, non-MusicXML lyric/chord input formats (e.g., YAML, CSV).
* **Target Device Optimization:** Add configuration options for specific YAMAHA devices (e.g., Genos, PSR-S/SX series) to ensure optimal playback settings (Program Change, Sysex headers).

## ⚖️ License

This project is licensed under the **MIT License**.

This means you are free to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the software, provided you include the original copyright and permission notice.

## 🤝 Contributing

Bug reports, feature suggestions, and code contributions are highly welcome. Please open an Issue or submit a Pull Request on GitHub.