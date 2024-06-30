# Database Management

This directory contains scripts and configuration files for managing the Supabase database used by the ISEL APP.

## Subdirectories

- **siges/**: Scripts for extracting and importing data from the SIGES system.
- **supabase/**: SQL files for managing the Supabase database.
- **web/**: Web scraper scripts for populating the database.

## Tables

### Inserted by Web Scraping

- `conteudo` (news, information, events)
- `curso` (course)
- `departamento` (department)

### Inserted by Excel

- `inscricao` (enrollment)
- `ruc` (RUC)
- `sala` (room)
- `utilizador` (user)

### Inserted Manually

- `edificio` (building) - Suggestion to use an Excel file

### Inserted by User (Frontend)

- `horario` (schedule)

### Inserted by Backend

- `notificacao` (notification)

## Libraries

- **Pandas**
- **Supabase**
- **openpyxl**
