# Web Scraping Scripts

This folder contains Python scripts for web scraping the ISEL website to populate the database.

## Files

- `scraper.py`: Main script for executing web scraping tasks.
- `config/`: Directory containing JSON configuration files for the scraper.

## Prerequisites

- Python 3.x
- requests
- BeautifulSoup4
- supabase-py

## Instructions

1. **Configure Scraper:**
    - Modify the JSON files in the `config/` directory as needed.

2. **Run Scraper:**
    ```bash
    python scraper.py
    ```

The scraper will extract data according to the configurations and insert it into the Supabase database.
