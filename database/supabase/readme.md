# ISEL APP Supabase Configuration

This file contains the Supabase configuration for the ISEL APP project.

## SQL Files

1. `tables.sql`: Defines the database schema and table structures.
2. `dummy_pop.sql`: Contains SQL statements to populate the database with dummy data for testing.
3. `full_truncate.sql`: Includes SQL commands to truncate all tables, useful for resetting the database.

## Database Schema

The database schema consists of the following tables:

- `servico`: Represents services with their acronym, name, location, and URL.
- `edificio`: Stores information about buildings, including their acronym, latitude, longitude, icon, and description.
- `acesso_rapido`: Contains quick access links with an icon, title, translation, and URL.
- `conteudo`: Stores content details such as date, URL, image, alt text, title, text, type, and location.
- `contacto`: Represents contact information for services, including address and contact type.
- `departamento`: Stores department details with their acronym, name, and associated building.
- `curso`: Represents courses with their acronym, name, code, and associated department.
- `sala`: Stores information about rooms, including the building, floor, number, latitude, longitude, acronym, and description.
- `atendimento`: Contains attendance information with an ID, acronym, day of the week, and hours.
- `disciplina`: Represents disciplines with their code, name, and acronym.
- `utilizador`: Stores user information, including their institutional code, user type, email, name, gender, identification number, associated course, department, building, floor, and room.
- `conversa`: Represents conversations with an ID, conversation ID, name, type, and associated user.
- `mensagem`: Stores messages with an ID, creation date, conversation reference, text, editable flag, and the user who sent it.
- `evento`: Represents events with an ID, title, description, date, time, duration, type, associated user, and discipline.
- `aula`: Stores class information, including the ID, day of the week, start time, duration, associated discipline, professor, and user.
- `plano_curricular`: Represents the curricular plan with discipline code, course acronym, branch code, ECTS credits, period, area, translation, optional flag, option group, year, and ID.
- `inscricao`: Stores enrollment information with an ID, academic year, enrollment date, status, associated discipline, final grade, and user.
- `ruc`: Represents the "Responsável da UC" with the academic year, period, course acronym, discipline code, ID, and the "regente".
- `notificacao`: Stores notifications with an ID, type, date and time, message, recipient user, and image.

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

### 4. Functions

To create serverless functions:

1. Go to the Functions section.
2. Click "Create a new function" and follow the prompts.
3. Deploy your function using the Supabase CLI.

### 5. Triggers

To set up database triggers:

1. Use the SQL Editor to create triggers or go to the Triggers section (next to the Functions section).
2. Define the trigger function in your SQL.

## Additional Resources

- [Supabase Documentation](https://supabase.com/docs)
- [Supabase CLI](https://supabase.com/docs/reference/cli)
- [Supabase Python Client](https://supabase.com/docs/reference/python)

## License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.