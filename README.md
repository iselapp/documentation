# ISEL APP

The ISEL APP is a mobile application designed to streamline access to critical information for the Lisbon School of Engineering (ISEL) university community. This repository contains all the resources needed to understand and set up the project.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Folder Structure](#folder-structure)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [Data Management](#data-management)
- [Contributing](#contributing)
- [License](#license)

## Introduction

The ISEL APP simplifies the process of accessing essential academic information. It offers a user-friendly and efficient interface to improve the student experience at ISEL.

## Features

- Personalized notifications
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

## Folder Structure

```
public_iselapp/
├── app/                      # React Native mobile app
├── config/
│   ├── siges/              # Configuration file for SIGES excel files
│   ├── web/               # Configuration files for web scraping
├── database/
│   ├── siges/             # SIGES data extraction and processing
│   ├── supabase/      # Supabase configuration and scripts
├── .env                     # Environment variables
├── requirements.txt     # Python dependencies
└── README.md            # This file
```

## Getting Started

### Prerequisites

- Node.js (v14 or later)
- Python 3.12 (only version tested)
- Supabase account
- Android Studio (for Android Virtual Device) or Android w/ USB cable
- IDE for Development (e.g. VSCode)

### Configuration

1. Fill in your Supabase credentials and other configuration details in your `.env` file.

2. Configure Supabase:
   - Follow the instructions in the [here](../main/database/supabase/readme.md) file to set up your Supabase account, project and tables.

## Running the Application

1. Start the mobile application:

   ```bash
   cd mobile
   npm run android  # or npm run ios
   ```

2. Run the web scrapers and data import scripts:
   ```bash
   python scraper/scraper.py
   python scraper/scraping_to_supabase.py
   python database/siges/excel_to_supabase.py
   ```

## Data Management

- Web scraping configurations are located in `config/web/`.
- Excel data import configurations are in `config/siges/`.
- To update the database schema, modify the SQL files in `database/supabase/` and apply them to your Supabase project.

For detailed instructions on data management, refer to the README files in each subdirectory of this project.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
