# Database Management

This directory contains scripts and configuration files for managing the Supabase database used by the ISEL APP.

## Directory Structure

```
├── siges/
├── supabase/
└── readme.md (this file)
```

## Subdirectories

- **siges/**: Scripts for extracting and importing data from the SIGES system. This includes Excel files with data extracted from SIGES and a Python script to insert data into the database.
- **supabase/**: SQL files for managing the Supabase database structure.

## Data Import Methods

### Web Scraping

- Tables: 
  - `atendimento` (office hours)
  - `contacto_email` (email contacts)
  - `contacto_telefone` (phone contacts)
  - `conteudo_evento` (event content)
  - `conteudo_informacao` (information content)
  - `conteudo_noticia` (news content)
  - `curso_licenciatura` (bachelor's degree courses)
  - `curso_mestrado` (master's degree courses)
  - `departamento` (department)
  - `distribuicao_ects` (ECTS distribution)
  - `plano_curricular_licenciaturas` (bachelor's degree curriculum)
- Tool: Web scraper script
- Configuration: JSON files for web scraping configurations

### Excel Import

- Tables: 
  - `inscricao` (enrollment)
  - `ruc` (RUC)
  - `sala` (room)
  - `utilizador` (user)
  - `disciplina` (subject)
  - `edificio` (building)
- Tool: Excel to Supabase Importer script
- Configuration: JSON file with custom mapping configuration (e.g., `config.json`)

### User Input (Frontend)

- Tables: `horario` (schedule)

### Backend Processing

- Tables: `notificacao` (notification)

## Excel to Supabase Importer

This Python script imports data from Excel files into Supabase tables, supporting both insertion of new records and updating of existing ones. The script is located in the parent directory.

### Features

- Process multiple Excel files
- Map Excel sheets to Supabase tables
- Custom column mapping
- Data type conversion
- Upsert functionality (insert or update based on primary keys)
- Progress tracking and colorized console output
- Summary report of imported data

### Usage

```
python excel_to_supabase.py <config file path> <excel files>
```

For detailed usage instructions use:

```
python excel_to_supabase.py --help
```

## Setup and Configuration

1. Install required packages:
   ```
   pip install -r requirements.txt
   ```
2. Set up a `.env` file in the parent directory with your Supabase credentials:
   ```
   SUPABASE_URL=your_supabase_url
   SUPABASE_KEY=your_supabase_key
   ```
3. Create necessary configuration files (JSON) for web scraping and Excel imports.

## Notes and Troubleshooting

- Ensure that your Supabase project has the necessary tables and columns set up before running imports.
- The scripts use the service role key, which bypasses RLS policies. Ensure proper security measures are in place.
- If you encounter RLS policy violations, you may need to temporarily disable RLS or adjust the policies for the import process.

## License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
