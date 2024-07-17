# Excel to Supabase Importer

This Python script imports data from Excel files into Supabase tables, supporting both insertion of new records and updating of existing ones.

## Features

- Process multiple Excel files
- Map Excel sheets to Supabase tables
- Custom column mapping
- Data type conversion
- Upsert functionality (insert or update based on primary keys)
- Progress bar for each sheet
- Colorized console output
- Summary report of imported data

## Prerequisites

- Python 3.6+
- Required Python packages: 
  - pandas
  - python-dotenv
  - supabase
  - colorama
  - tabulate

## Installation

1. Install required packages:
   ```
   pip install pandas python-dotenv supabase colorama tabulate
   ```
2. Set up a `.env` file in the same directory with your Supabase credentials:
   ```
   SUPABASE_URL=your_supabase_url
   SUPABASE_KEY=your_supabase_key
   ```

## Configuration

1. Create an import configuration JSON file (e.g., `import_config.json`) with the following structure:

```json
{
  "excel_config": "path/to/excel_config.json",
  "import_order": [
    {
      "type": "excel",
      "file": "path/to/excel_file.xlsx",
      "tables": [
        {
          "name": "table_name",
          "delete_before_import": false
        }
      ]
    }
  ]
}
```

2. Create an Excel configuration JSON file (e.g., `excel_config.json`) with the following structure:

```json
{
  "sheet_mapping": {
    "Excel Sheet Name": "Supabase Table Name"
  },
  "column_mappings": {
    "Supabase Table Name": {
      "excel_column_name": {"name": "supabase_column_name", "type": "data_type"}
    }
  },
  "primary_keys": {
    "Supabase Table Name": ["primary_key_column"]
  }
}
```

## Usage

Run the script from the command line:

```
python excel_to_supabase.py import_config.json [excel_file] [--sheet sheet_name]
```

- `import_config.json`: Path to the import configuration JSON file
- `excel_file`: Path to the Excel file to process (relative to the project root)
- `--sheet sheet_name`: (Optional) Name of the specific sheet to process

Examples:
```
python excel_to_supabase.py import_config.json database/siges/DADOS_SIGES.xlsx
python excel_to_supabase.py import_config.json database/siges/DADOS_SIGES.xlsx --sheet utilizador
```

## Output

The script provides real-time progress updates and a summary table at the end, showing the number of inserted, updated, and error rows for each processed file and table.

## Notes

- Ensure that your Supabase project has the necessary tables and columns set up before running the import.
- Ensure RLS policies are disabled.

## Additional Scripts

### `salas_to_excel.py`

This script parses a list of room names and generates an Excel file (`LS_SALAS.xlsx`) with the parsed room data. The Excel file contains columns for building, floor, room number, and additional information.

To run the script:

```
python salas_to_excel.py
```

The generated Excel file can be used as input for the `excel_to_supabase.py` script to import room data into Supabase.

## License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.