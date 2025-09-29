# POSIX Timezone Database Generator

A simple Python tool that generates POSIX timezone strings from system timezone data.

## Overview

This tool reads binary timezone files from `/usr/share/zoneinfo/` and extracts POSIX timezone strings, outputting them in either CSV or JSON format. It covers 469 timezone identifiers including all major regions worldwide.

## Usage

```bash
# Generate CSV output
python gen-tz.py --csv

# Generate JSON output
python gen-tz.py --json

# Save to files
python gen-tz.py --csv > zones.csv
python gen-tz.py --json > zones.json
```

## Output Format

### CSV Format
```csv
"America/New_York","EST5EDT,M3.2.0,M11.1.0"
"Europe/London","GMT0BST,M3.5.0/1,M10.5.0"
"Asia/Tokyo","JST-9"
```

### JSON Format
```json
{
  "America/New_York": "EST5EDT,M3.2.0,M11.1.0",
  "Europe/London": "GMT0BST,M3.5.0/1,M10.5.0",
  "Asia/Tokyo": "JST-9"
}
```

## POSIX Timezone String Format

The POSIX strings encode timezone rules including:
- Standard time abbreviation and UTC offset
- Daylight saving time rules (if applicable)
- DST transition dates using the format `M<month>.<week>.<day>`

Examples:
- `GMT0` - Greenwich Mean Time, no DST
- `EST5EDT,M3.2.0,M11.1.0` - Eastern Time with DST transitions
- `JST-9` - Japan Standard Time, UTC+9, no DST

## Requirements

- Python 3 (standard library only)
- System timezone data (`/usr/share/zoneinfo/`)
- No external dependencies

## License

MIT License - See LICENSE file for details