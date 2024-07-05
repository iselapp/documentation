# Web Scraping Configuration Guide

This README provides a comprehensive guide to configuring the web scraper for extracting information from various sections of the Lisbon School of Engineering's website (https://www.isel.pt/).

## Table of Contents

- [Configuration Structure](#configuration-structure)
- [Scrape Instruction](#scrape-instruction)
- [Actions](#actions)
- [Types](#types)
- [Examples](#examples)
- [Usage](#usage)

## Configuration Structure

The scraper configuration is a JSON file that defines a list of scraping instructions. Each instruction represents a step in the scraping process, such as navigating to a URL, selecting elements, or extracting data.

## Scrape Instruction

A `ScrapeInstruction` object represents a single step in the scraping process. It has the following properties:

- `action`: The type of action to perform (e.g., "entry", "select", "extract")
- `type`: The type of data to extract (e.g., "item", "list", "custom", "regex")
- `url`: The URL to scrape (only for "entry" action)
- `selector`: The CSS selector to use for finding elements
- `attribute`: The attribute to extract from the selected elements
- `pagination`: Pagination information (if applicable)
- `key`: The key to use for the extracted data in the output
- `formatting_begin`: The beginning of a formatting string (for custom extraction)
- `formatting_end`: The end of a formatting string (for custom extraction)
- `regex`: A regular expression pattern (for regex extraction)
- `add`: A string to add to the extracted data
- `output_name`: The name of the output file
- `output_dir`: The directory to save the output file
- `children`: A list of child instructions

## Actions

- `entry`: The starting point of the scraping process, typically a URL
- `select`: Select elements on the page using a CSS selector
- `extract`: Extract data from the selected elements
- `navigate`: Follow a link and perform more tasks on the new page

## Types

- `item`: Extract a single piece of information
- `list`: Extract multiple pieces of information as a list
- `custom`: Use custom formatting to extract information
- `regex`: Use a regular expression to extract information
- `regex-add-beg`: Use a regular expression and add a prefix to the extracted information
- `add-beg`: Add a prefix to the extracted information

## Examples

Here's an example configuration for extracting news article titles and URLs:

```json
[
  {
    "action": "entry",
    "url": "https://www.isel.pt/noticias",
    "output_dir": "output",
    "output_name": "news",
    "children": [
      {
        "action": "select",
        "selector": ".item-columns",
        "children": [
          {
            "action": "extract",
            "type": "item",
            "selector": ".views-field-title a",
            "attribute": "text",
            "key": "title"
          },
          {
            "action": "extract",
            "type": "item",
            "selector": ".views-field-title a",
            "attribute": "href",
            "key": "url"
          }
        ]
      }
    ]
  }
]
```

This configuration will:
1. Start at the news page
2. Select all news items
3. For each item, extract the title and URL
4. Save the results in a JSON file in the "output" directory

## Usage

1. Create a JSON configuration file based on the structure described above.
2. Run the scraper script with the configuration file as an argument:

   ```
   python scraper.py
   ```

3. The script will show all the configuration files available.
4. After choosing the configuration file the script will execute the scraping instructions and save the results in the specified output directory.

Remember to adjust the selectors and structure based on the specific website you're scraping.

## License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE)
