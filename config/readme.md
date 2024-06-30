# Configurations

This folder contains JSON configuration files for web scraping various sections of the ISEL website.

## Files

- `news.json`: Configuration for scraping news articles.
- `events.json`: Configuration for scraping event information.
- `courses.json`: Configuration for scraping course details.

## Structure

Each JSON file contains structured configurations that instruct a web scraper on how to fetch and organize data from the ISEL website. The main components include:

- **Entries**: Starting points for scraping.
- **Selectors**: CSS selectors to locate elements.
- **Actions**: Define tasks for the scraper (e.g., `navigate`, `select`, `extract`).
- **Attributes**: Specify the data to be extracted (e.g., `text`, `href`).

For detailed examples and explanations, refer to the main [README.md](../README.md).
