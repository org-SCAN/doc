# Documentation for Types Import Zip Folder Format

This document explains the format you must follow to prepare a zip folder containing the types required by the application. Please follow these instructions to ensure proper functionality.

## Zip Folder Structure

The zip folder must include a `types.json` file structured as follows:

```
/types
    types.json
```

## types.json Format

The `types.json` file must contain an array of any size with type labels:

```json
[
    "Case.Type1",
    "Case.Type2",
    "Case.Type3",
    "Case.Type4",
    "Case.Type5",
    "Case.Type6"
]
```

## Formatting Rules

- Each label should be a **string**.
- The system automatically converts labels into a structured format `{ label, value }`. The label is the field shown in the app, while the value is the field present in the JSON output.
- **Value Formatting:**
  - Converted to lowercase.
  - Spaces replaced with underscores (`_`).
  - Special characters (e.g., `é, ü, ñ, العربية, 中文`) are preserved.
  - Symbols and punctuation are removed.

### Example of Processed Output

If the input is:

```json
["Café", "مرحبا", "Français & English"]
```

The system generates:

```json
[
    { "label": "Café", "value": "café" },
    { "label": "مرحبا", "value": "مرحبا" },
    { "label": "Français & English", "value": "français_english" }
]
```

### Final Steps

1. Ensure the `types.json` file is correctly formatted.
2. Compress the folder into a zip file.
3. Share the zip file via a URL or upload it to the application.

