# ISEL APP

The ISEL APP is a mobile application designed to streamline access to critical information for the Lisbon School of Engineering (ISEL) university community. This repository contains all the resources needed to understand and set up the project.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [GitHub Actions](#github-actions)
- [Contributing](#contributing)
- [License](#license)

## Introduction

The ISEL APP simplifies the process of accessing essential academic information. It offers a user-friendly and efficient interface to improve the student experience at ISEL.

## Features

- Access to academic records
- Grade simulations
- Virtual student card
- Course schedules
- Campus news and events
- Department and faculty information

## Technologies Used

- **React Native**: For building the cross-platform mobile application
- **Python**: For web scraping, data extraction, and processing
- **Supabase**: For the backend database and authentication
- **PostgreSQL**: Database management system
- **Pandas, openpyxl**: For handling Excel data
- **BeautifulSoup**: For web scraping


## Getting Started

### Prerequisites

- Node.js (v14 or later)
- Python 3.12 (only version tested)
- Supabase account
- Android Studio (for Android Virtual Device) or Android w/ USB cable
- IDE for Development (e.g., VSCode)

### Configuration

1. Fill in your Supabase credentials and other configuration details in your `.env` file.

2. Configure Supabase:
   - Follow the instructions in the [database/supabase/readme.md](database/supabase/readme.md) file to set up your Supabase account, project, and tables.

3. Configure web scraping:
   - Modify the JSON files in `config/web/` to match the structure of the web pages you want to scrape. See the [config/web/readme.md](config/web/readme.md) file for a detailed guide on configuring the web scraper.

4. Configure Excel import:
   - Update the `config/siges/config.json` file to map your Excel sheets and columns to the corresponding Supabase tables and columns. Refer to the [config/siges/readme.md](config/siges/readme.md) file for instructions on configuring the Excel to Supabase importer.

5. Run `run_scrapers.py`:
   - Finally run `run_scrapers.py` locally to test the cronjob system manually.

## GitHub Actions

The project includes a GitHub Actions workflow (`scraper.yml`) that automates the process of running the web scrapers and updating the scraped data in the repository. The workflow is triggered on a schedule (every hour) or can be run manually.

Make sure to set the `SUPABASE_URL` and `SUPABASE_KEY` secrets in your repository settings for the workflow to access your Supabase instance.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.