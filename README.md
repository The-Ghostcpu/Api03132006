# Student Management API 
A RESTful API built with Laravel for managing student records. 
## Features 
- Create, read, update, and delete student records 
- Validation for all input data 
- Proper HTTP status codes 
- JSON responses 
- Laravel Eloquent ORM for database operations 
## Project Structure 
- `app/Models/Student.php` - Eloquent model for students 
- `app/Http/Controllers/Api/studentController.php` - API controller handling student operations 
- `routes/api.php` - API route definitions 
- `database/migrations/2026_03_14_050759_create_student_table.php` - Migration for student table 
## Installation 
1. Clone the repository 
2. Install dependencies: 
   ```bash 
    composer install 
    npm install 
    ``` 
3. Copy `.env.example` to `.env` and configure your environment: 
   ```bash 
    cp .env.example .env 
    ``` 
4. Generate application key: 
   ```bash 
    php artisan key:generate 
    ``` 
5. Run migrations: 
   ```bash 
    php artisan migrate 
    ``` 
6. Start the development server: 
   ```bash 
    php artisan serve 
    ``` 
## API Endpoints 
All endpoints return JSON responses. 
### Get All Students 
- **URL:** `/api/students` 
- **Method:** `GET` 
- **Success Response:** 
    ```json 
      { 
        "students": [...], 
        "status": 200 
      } 
    ``` 
### Get Single Student 
- **URL:** `/api/students/{id}` 
- **Method:** `GET` 
- **Success Response:** 
    ```json 
      { 
        "student": {...}, 
        "status": 200 
      } 
    ``` 
- **Error Response (404):** 
    ```json 
      { 
### Create Student 
- **URL:** `/api/students` 
- **Method:** `POST` 
- **Required Fields:** Nombre, Ap_paterno, Ap_materno, Sexo, email, Carrera 
- **Success Response:** 
    ```json 
      { 
        "student": {...}, 
        "status": 201 
      } 
    ``` 
### Update Student 
- **URL:** `/api/students/{id}` 
- **Method:** `PUT` 
- **Required Fields:** Nombre, Ap_paterno, Ap_materno, Sexo, email, Carrera 
- **Success Response:** 
    ```json 
      { 
        "message": "Estudiante actualizado", 
        "student": {...}, 
        "status": 200 
      } 
    ``` 
### Partial Update Student 
- **URL:** `/api/students/{id}` 
- **Method:** `PATCH` 
- **Fields:** Any subset of Nombre, Ap_paterno, Ap_materno, Sexo, email, Carrera 
- **Success Response:** 
    ```json 
        "message": "Estudiante actualizado", 
        "student": {...}, 
        "status": 200 
      } 
    ``` 
### Delete Student 
- **URL:** `/api/students/{id}` 
- **Method:** `DELETE` 
- **Success Response:** 
    ```json 
      { 
        "message": "Estudiante eliminado", 
        "status": 200 
      } 
    ``` 
- **Error Response (404):** 
    ```json 
      { 
        "message": "Estudiante no encontrado", 
        "status": 404 
      } 
    ``` 
## Database Schema 
The `students` table contains: 
- `id` (primary key, auto-increment) 
- `Nombre` (string) 
- `Ap_paterno` (string) 
- `Ap_materno` (string) 
- `Sexo` (string) 
- `email` (string, unique) 
- `Carrera` (string) 
- `created_at` (timestamp) 
- `updated_at` (timestamp) 
## Validation Rules 
All endpoints validate input data: 
- Nombre, Ap_paterno, Ap_materno, Sexo, Carrera: required, max 255 characters 
- email: required, valid email format, unique in students table 
- For updates: email must be unique except for the current record 
## Technology Stack 
- **Backend:** Laravel 10.x 
- **Database:** SQLite (default, configurable in .env) 
- **PHP:** 8.1+ 
- **Composer:** Dependency management 
## Contributing 
1. work the repository 
2. Create a feature branch 
3. Commit your changes 
4. Push to the branch 
5. Open a pull request 
## License 
This project is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT). 
