# Excel to Supabase Importer Configuration

This README explains the structure and usage of the configuration file for the Excel to Supabase Importer.

## Configuration File Structure

The configuration file is a JSON document with three main sections:

1. `sheet_mapping`
2. `column_mappings`
3. `primary_keys`

### Sheet Mapping

The `sheet_mapping` section defines how Excel sheet names correspond to Supabase table names.

```json
"sheet_mapping": {
  "isel": "utilizador",
  "teste": "edificio"
}
```

In this example:
- The Excel sheet named `isel` will be imported into the Supabase table `utilizador`
- The Excel sheet named `teste` will be imported into the Supabase table `edificio`

### Column Mappings

The `column_mappings` section defines how columns in the Excel sheets should be mapped to columns in the Supabase tables. It also specifies the data type for each column.
> [!NOTE]
> Excel columns (case insensitive) with the same name as the supabase tables don't need to be added to this JSON configuration file.

```json
"column_mappings": {
  "utilizador": {
    "edificio": {
      "name": "ref_edif",
      "type": "varchar"
    },
    "andar": {
      "name": "ref_andar",
      "type": "varchar"
    },
    "num_sala": {
      "name": "ref_numero",
      "type": "varchar"
    }
  }
}
```

In this example, for the `utilizador` table:
- The Excel column `edificio` will be mapped to the Supabase column `ref_edif` with type `varchar`
- The Excel column `andar` will be mapped to the Supabase column `ref_andar` with type `varchar`
- The Excel column `num_sala` will be mapped to the Supabase column `ref_numero` with type `varchar`

### Primary Keys

The `primary_keys` section defines the primary key columns for each Supabase table.

```json
"primary_keys": {
  "utilizador": ["cd_inst"],
  "edificio": ["sigla"]
}
```

In this example:
- The "utilizador" table has `cd_inst` as its primary key
- The "edificio" table has `sigla` as its primary key

## Usage

1. Save this configuration as a JSON file (e.g., `config.json`).
2. Use this configuration file when running the Excel to Supabase Importer script:

   ```
   python excel_to_supabase.py config.json [Excel files]
   ```

## Notes

- Ensure that the Supabase table names and column names in this configuration match your actual Supabase database schema.
- All Excel columns not specified in the `column_mappings` will be imported using their original names and assumed to be of type `varchar`.
- Make sure the primary keys specified here match the primary keys in your Supabase tables.


## License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE)
