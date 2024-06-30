# ISEL APP

The ISEL APP is a mobile application designed to streamline access to critical information for the Lisbon School of Engineering (ISEL) university community. This repository contains all the resources and documentation needed to understand and contribute to the project.

## Table of Contents

- [Introduction](#introduction)
- [Technologies Used](#technologies-used)
- [Folder Structure](#folder-structure)
- [Getting Started](#getting-started)
- [License](#license)

## Introduction

The ISEL APP simplifies the process of accessing essential academic information. It offers features such as personalized notifications, access to academic records, grade simulations, and a virtual student card. This project aims to improve the student experience by providing a user-friendly and efficient interface.

## Technologies Used

- **React Native**: For building the mobile application.
- **Python**: For web scraping and data extraction.
- **Supabase**: For the backend database.
- **PostgreSQL**: Database management.
- **Pandas, openpyxl**: For handling Excel data.

## Folder Structure

public_iselapp/
├── config/
│ └── [web scraping JSON configurations]
├── database/
│ ├── siges/
│ │ └── [Excel extraction and importing scripts]
│ ├── supabase/
│ │ └── [SQL files for database management]
│ └── web/
│ └── [Web scraper scripts]
└── mobile/
└── [React Native mobile application]


## Getting Started

### Prerequisites

- Node.js
- Python 3.x
- Supabase account

2. **Set up the mobile application:**
    ```bash
    cd mobile
    npm install
    npm start
    ```

3. **Set up the Python environment:**
    ```bash
    pip install -r requirements.txt
    ```

4. **Configure Supabase:**
    - Follow the instructions in the `database/supabase/readme.md` file.

### Running the Application

1. **Start the mobile application:**
    ```bash
    npm run android # or npm run ios
    ```

2. **Run the web scrapers and data import scripts:**
    ```bash
    python database/web/scraper.py
    python database/siges/excel_importer.py
    ```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
