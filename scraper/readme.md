# Web Scraping System

This directory contains a flexible web scraping system designed to extract data from websites and import it into a Supabase database. The system is configurable through JSON files, allowing for easy adaptation to different web structures.

## Components

1. `scraper.py`: The main script that performs web scraping based on configuration files.
2. `scraping_to_supabase.py`: A script to import scraped data (in JSON format) into a Supabase database.
3. `config_parser.py`: Parses the configuration JSON files into `ScrapeInstruction` objects.
4. `json_handler.py`: Handles writing scraped data to JSON files.
5. `scrape_instruction.py`: Defines the `ScrapeInstruction` class used to represent scraping instructions.

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
python scraper.py
```

This will present a menu of available configuration files. Select the desired configuration to start scraping.

### Importing Scraped Data to Supabase

After scraping, use the following command to import the data into Supabase:

```
python scraping_to_supabase.py <json_file> <table_name>
```

Replace `<json_file>` with the path to the scraped data JSON file and `<table_name>` with the name of the Supabase table to import into.

## Configuration Files

Configuration files are explained [here](../main/config/web/readme.md).

## Features

- Configurable scraping instructions
- Support for nested data structures
- Various extraction types (item, list, custom, regex)
- Progress tracking and colorized console output
- Automatic JSON file naming with timestamps
- Data processing for specific formats (e.g., office hours)

## Notes

- Ensure you have permission to scrape the target websites.
- Be respectful of the websites' resources and consider implementing rate limiting.
- The system uses Supabase for data storage, so make sure your Supabase project is set up correctly.

## License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
