# Web Scraping System

This directory contains a flexible web scraping system designed to extract data from ISEL website (or any other website) and import it into a Supabase database. The system is configurable through JSON files, allowing for easy adaptation to different web structures.

## Components

1. `scraper.py`: The main script that performs web scraping based on configuration files.
2. `scraping_to_supabase.py`: A script to import scraped data (in JSON format) into a Supabase database. 
3. `import_all_to_supabase.py`: A script to import all JSON files in a directory to the Supabase database.
4. `config_parser.py`: Parses the configuration JSON files into `ScrapeInstruction` objects.
5. `json_handler.py`: Handles writing scraped data to JSON files.
6. `scrape_instruction.py`: Defines the `ScrapeInstruction` class used to represent scraping instructions.

## Setup

1. Install the required packages:
   ```
   pip install -r requirements.txt
   ```

2. Set up a `.env` file in the project root with your Supabase credentials:
   ```
   SUPABASE_URL=your_supabase_url
   SUPABASE_KEY=your_supabase_key
   ```

3. Create JSON configuration files in the `config/web/` directory for each website or section you want to scrape.

## Usage

### Web Scraping

To run the web scraper:

```
python scraper.py <config_path>
```

Replace `<config_path>` with the path to the desired JSON configuration file.

### Importing Scraped Data to Supabase

After scraping, use the following command to import a single JSON file into Supabase:

```
python scraping_to_supabase.py <json_file> <table_name> <error_log_file> [--delete-before-import]
```

- Replace `<json_file>` with the path to the scraped data JSON file.
- Replace `<table_name>` with the name of the Supabase table to import into. 
- Replace `<error_log_file>` with the path to the error log file.
- Optionally, add the `--delete-before-import` flag to delete all existing data from the table before importing.

To import all JSON files in a directory:

```
python import_all_to_supabase.py <output_dir>
```

Replace `<output_dir>` with the path to the directory containing the JSON files to import.

## Configuration Files

Configuration files are explained [here](../config/web/readme.md).

## Features

- Configurable scraping instructions
- Support for nested data structures
- Various extraction types (item, list, custom, regex)
- Progress tracking and colorized console output
- Automatic JSON file naming with timestamps
- Data processing for specific formats (e.g., office hours)
- Batch import of all JSON files in a directory
- Detailed import logging and error handling

## Notes

- The system uses Supabase for data storage, so make sure your Supabase project is set up correctly.

## License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.