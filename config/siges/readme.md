# Excel to Supabase Importer Configuration

This README explains the structure and usage of the configuration file (`config.json`) for the Excel to Supabase Importer.

## Configuration File Structure

The configuration file is a JSON document with three main sections:

1. `sheet_mapping`
2. `column_mappings`
3. `primary_keys`

### Sheet Mapping

The `sheet_mapping` section defines how Excel sheet names correspond to Supabase table names.

```json
"sheet_mapping": {
  "Sheet1": "sala",
  "edificio": "edificio",
  "utilizador": "utilizador",
  "inscricao": "inscricao",
  "ruc": "ruc",
  "Cursos": "curso",
  "UCs": "disciplina",
  "PEs": "plano_curricular"
}
```

In this example:
- The Excel sheet named `Sheet1` will be imported into the Supabase table `sala`
- The Excel sheet named `edificio` will be imported into the Supabase table `edificio`
- The Excel sheet named `utilizador` will be imported into the Supabase table `utilizador`
- And so on...

### Column Mappings

The `column_mappings` section defines how columns in the Excel sheets should be mapped to columns in the Supabase tables. It also specifies the data type for each column.
> [!NOTE]
> Excel columns need to be added to this JSON configuration file in order to be imported.

```json
"column_mappings": {
  "utilizador": {
    "cd_inst": {
      "name": "cd_inst",
      "type": "varchar"
    },
    "email": {
      "name": "email",
      "type": "varchar"
    },
    ...
  },
  "inscricao": {
    "ano_letivo": {
      "name": "ano_letivo",
      "type": "varchar"
    },
    "periodo": {
      "name": "periodo",
      "type": "varchar"
    },
    ...
  },
  ...
}
```

In this example, for the `utilizador` table:
- The Excel column `cd_inst` will be mapped to the Supabase column `cd_inst` with type `varchar`
- The Excel column `email` will be mapped to the Supabase column `email` with type `varchar`
- And so on for other columns and tables...

### Primary Keys

The `primary_keys` section defines the primary key columns for each Supabase table.

```json
"primary_keys": {
  "edificio": [
    "sigla"
  ],
  "sala": [
    "sg_edif",
    "andar",
    "numero"
  ],
  "utilizador": [
    "cd_inst"
  ],
  "curso": [
    "codigo"
  ],
  "disciplina": [
    "codigo"
  ]
}
```

In this example:
- The `edificio` table has `sigla` as its primary key
- The `sala` table has a composite primary key of `sg_edif`, `andar`, and `numero`
- The `utilizador` table has `cd_inst` as its primary key
- And so on...

## Usage

1. Save this configuration as a JSON file (`config.json`).
2. Use this configuration file when running the Excel to Supabase Importer script:

## Notes

- Ensure that the Supabase table names and column names in this configuration match your actual Supabase database schema.
- All Excel columns not specified in the `column_mappings` will not be imported.
- Make sure the primary keys specified here match the primary keys in your Supabase tables.

## License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.