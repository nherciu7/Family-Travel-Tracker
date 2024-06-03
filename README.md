
# Visited Countries and Family Members App

This is a simple web application built with Node.js, Express, and PostgreSQL that allows users to track visited countries and add family members.

## Features

- View a list of visited countries.
- Add new countries to the visited list.
- View a list of family members.
- Add new family members.

## Prerequisites

- Node.js (version 12.x or higher)
- PostgreSQL

## Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/your-username/visited-countries-app.git
   cd visited-countries-app
   ```

2. **Install dependencies:**

   ```bash
   npm install
   ```

3. **Set up PostgreSQL:**

   - Create a PostgreSQL database named `world`.
   - Create the necessary tables:

     ```sql
     CREATE TABLE countries (
         country_code VARCHAR(3) PRIMARY KEY,
         country_name VARCHAR(100) NOT NULL
     );

     CREATE TABLE visited_countries (
         country_code VARCHAR(3) REFERENCES countries(country_code)
     );
     ```

   - Insert sample data into the `countries` table:

     ```sql
     INSERT INTO countries (country_code, country_name) VALUES ('USA', 'United States');
     INSERT INTO countries (country_code, country_name) VALUES ('CAN', 'Canada');
     ```

4. **Configure database connection:**

   Update the database connection details in `index.js`:

   ```javascript
   const db = new pg.Client({
     user: "your-postgres-user",
     host: "localhost",
     database: "world",
     password: "your-postgres-password",
     port: 5432,
   });
   ```

## Running the Application

1. **Start the server:**

   ```bash
   npm start
   ```

2. **Open your browser and visit:**

   ```
   http://localhost:3000
   ```

## Project Structure

- `index.js`: Main server file.
- `views/index.ejs`: Template for the main page.
- `views/new.ejs`: Template for adding a new user.
- `public/`: Directory for static files (CSS, JavaScript, images).

## Usage

- **Home Page:**
  - Displays the list of visited countries and family members.
  - Provides forms to add new countries and a link to add new family members.

- **Add Family Member:**
  - Clicking "Add Family Member" will navigate to a form where you can input the name and favorite color of the new family member.
  - After submitting, you will be redirected back to the home page with the updated list of family members.


## Acknowledgements

- Built with [Express](https://expressjs.com/)
- Database managed with [PostgreSQL](https://www.postgresql.org/)
