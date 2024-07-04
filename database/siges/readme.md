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

Create a JSON configuration file (e.g., `config.json`) with the following structure:
> [!NOTE]
> Excel columns (case insensitive) with the same name as the supabase tables don't need to be added to this JSON configuration file.

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
python excel_to_supabase.py config.json [file_names]
```

- `config.json`: Path to the configuration JSON file
- `[file_names]`: Excel files to process. Use 'all' to process all Excel files in the current directory, or specify individual file names.

Examples:
```
python excel_to_supabase.py config.json all
python excel_to_supabase.py config.json file1.xlsx file2.xlsx
```

## Output

The script provides real-time progress updates and a summary table at the end, showing the number of inserted, updated, and error rows for each processed file and table, as shown in the following example

![image](https://github.com/rhgui/public_iselapp/assets/29288168/f342ecba-f347-4edf-8fac-f5eaf9c29a07)

## Notes

- Ensure that your Supabase project has the necessary tables and columns set up before running the import.
- The script uses the service role key, which bypasses RLS policies. Ensure proper security measures are in place.
- Adjust RLS policies or temporarily disable them if you encounter permission issues during import.

## Troubleshooting

- If you encounter RLS policy violations, you may need to temporarily disable RLS or adjust the policies for the import process.
- Ensure that the Supabase key used has the necessary permissions for the operations being performed.

## License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE)
