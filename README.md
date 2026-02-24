# Yet Another Web Scraping Tool (YAWST)

Yet Another Web Scraping Tool (YAWST) is a terminal-based web scraping utility written in **Bash** with an interactive **dialog UI**.

Instead of passing complex command-line arguments, the tool provides a simple text-based interface that guides the user step‑by‑step through the scraping process.

It supports scraping:

- Text content from HTML using CSS selectors
- Tables (or any 2D structured data) using customizable selectors

## Overview

YAWST is designed for users who want a lightweight, dependency-minimal scraping tool that runs entirely in the terminal.

The application:

- Fetches HTML using `curl`
- Parses content using `pup` (CSS selector parser)
- Uses `dialog` to provide an interactive terminal UI
- Outputs results to a selected file
- Supports configurable behavior via a `.yawstrc` config file

No complex CLI arguments are required — everything is handled through the interactive menu.

## Features

- Interactive terminal UI powered by `dialog`
- Scrape text via CSS selector
- Scrape tables with separate selectors for:
  - Table container
  - Header cells
  - Data cells
- Configurable output formatting
- Automatic config file generation

## Requirements

Make sure the following tools are installed:

- `bash`
- `curl`
- `dialog`
- `pup`
- `awk`

Example (Debian/Ubuntu):

```bash
sudo apt install curl dialog
go install github.com/ericchiang/pup@latest
```

## Installation

```bash
git clone https://github.com/arosicki/yet-another-web-scaping-tool.git
cd yet-another-web-scaping-tool
chmod +x yawst.sh
```

Run:

```bash
./yawst.sh
```

## How It Works

After launching, you will see a main menu:

1. **Scrape Text**
2. **Scrape Table**
3. Exit

The UI will guide you through:

- Entering a URL
- Providing CSS selector queries
- Selecting an output file
- Saving the scraped results

If enabled in config, the application will automatically close after a successful scrape.

## Configuration

YAWST uses a configuration file located at:

```
~/.yawstrc
```

If the file does not exist, it is automatically generated with default values.

### Available Configuration Options

```env
FILE_INPUT_DEFAULT=~/          # Default directory for file selection
TABLE_SEPARATOR=';'            # Separator used in table output
OMIT_TABLE_HEADERS=false       # Skip header row in table output
AUTOCLOSE=true                 # Exit automatically after scraping
WHOLE_ELEMENTS=false           # Return full HTML elements instead of text only
```

You can modify these values to customize behavior.

## Table Scraping Output

When scraping tables:

- Headers and rows are parsed using CSS selectors
- Output is formatted using the configured separator
- Results are saved in a CSV‑like format

Example output:

```
Name;Price;Location
House A;500000;Warsaw
House B;450000;Krakow
```

## Command Line Options

The tool itself is interactive, but supports two utility flags:

```bash
./yawst.sh -v   # Show version
./yawst.sh -h   # Show help
```

All scraping functionality is handled via the dialog interface.

## Project Structure

```
yet-another-web-scaping-tool/
├─ yawst.sh        # Main application script
├─ yawst-EN-us.1   # English manual
├─ yawst-PL-pl.1   # Polish manual
├─ LICENSE
└─ README.md
```
