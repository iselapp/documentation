# ISEL APP Supabase Backend

This file contains the Supabase configuration for the ISEL APP project.

## SQL Files

1. `tables.sql`: Defines the database schema and table structures.
2. `dummy_pop.sql`: Contains SQL statements to populate the database with dummy data for testing.
3. `full_truncate.sql`: Includes SQL commands to truncate all tables, useful for resetting the database.

## Supabase Setup

### 1. Project Creation

1. Go to [Supabase](https://supabase.com/) and sign in or create an account.
2. Click "New Project" and follow the prompts to set up your project.

### 2. Database Setup

1. Navigate to the SQL Editor in your Supabase dashboard.
2. Execute the SQL files in the following order:
   <ol type="a">
    <li>`tables.sql`</li>
    <li>`dummy_pop.sql` (optional, for testing)</li>
  </ol>

To reset the database:
   - Execute `full_truncate.sql`

![image](https://github.com/rhgui/public_iselapp/assets/29288168/6dc38da4-0387-43de-9639-730c61b66570)

### 3. API Configuration

Supabase automatically generates API endpoints for your tables. To use them:

1. Go to the API Docs section in your Supabase dashboard.
2. Find your table and copy the generated API code snippets for various operations.

![image](https://github.com/rhgui/public_iselapp/assets/29288168/476792b8-5ad1-4dbf-9f4f-d422781c8390)


[comment]: <> (### 4. Authentication)

[comment]: <> (1. Navigate to the Authentication section in your Supabase dashboard.)
[comment]: <> (2. Configure authentication providers as needed \(e.g., email, social logins\).)
[comment]: <> (3. Set up email templates for verification, password resets, etc.)

### 4. Functions

To create serverless functions:

1. Go to the Functions section.
2. Click "Create a new function" and follow the prompts.
3. Deploy your function using the Supabase CLI.

### 6. Triggers

To set up database triggers:

1. Use the SQL Editor to create triggers or go to the Triggers section (next to the Functions section).
2. Define the trigger function in your SQL.

## Additional Resources

- [Supabase Documentation](https://supabase.com/docs)
- [Supabase CLI](https://supabase.com/docs/reference/cli)
- [Supabase Python Client](https://supabase.com/docs/reference/python)

## Troubleshooting

- If you encounter issues with RLS (Row Level Security), review your policy configurations in the Auth Policies section of your Supabase dashboard.
- For API-related problems, check your API keys and ensure you're using the correct project URL.

## License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE)
