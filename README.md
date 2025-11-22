# Task Manager - Laravel Edition

A comprehensive task management application built with Laravel and MySQL. This is a conversion of the original Node.js/Express application to Laravel framework.

## Features

- ✨ Create, read, update, and delete tasks
- 🎯 Priority levels (Low, Medium, High)
- 📁 Task categorization
- ✅ Mark tasks as completed/pending
- 🔍 Filter tasks by category and status
- 📊 Task statistics dashboard
- 🎨 Beautiful, responsive UI with gradient design
- 🚀 RESTful API architecture

## Technology Stack

- **Backend:** PHP 8.1+, Laravel 10
- **Database:** MySQL
- **Frontend:** Blade Templates, Vanilla JavaScript
- **CSS:** Custom CSS with modern design
- **Icons:** Font Awesome 6

## Prerequisites

Before you begin, ensure you have the following installed:

- PHP >= 8.1
- Composer
- MySQL >= 5.7 or MariaDB >= 10.3
- Node.js and NPM (optional, for asset compilation)

## Installation

### 1. Clone the Repository

```bash
cd task-manager-main/task-manager/task-manager
```

### 2. Install PHP Dependencies

```bash
composer install
```

### 3. Environment Configuration

Copy the example environment file and generate application key:

```bash
copy .env.example .env
php artisan key:generate
```

### 4. Configure Database

Edit the `.env` file and update the database credentials:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=task_manager
DB_USERNAME=root
DB_PASSWORD=
```

### 5. Create Database

Create a new MySQL database named `task_manager`:

```sql
CREATE DATABASE task_manager;
```

Or use the command line:

```bash
mysql -u root -p -e "CREATE DATABASE task_manager;"
```

### 6. Run Migrations

Run the database migrations to create the tasks table:

```bash
php artisan migrate
```

### 7. Seed Database (Optional)

To populate the database with sample tasks:

```bash
php artisan db:seed --class=TaskSeeder
```

### 8. Start the Development Server

```bash
php artisan serve
```

The application will be available at: `http://localhost:8000`

## API Endpoints

The application provides a RESTful API for task management:

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/tasks` | Get all tasks (with optional filters) |
| GET | `/api/tasks/{id}` | Get a specific task |
| POST | `/api/tasks` | Create a new task |
| PUT | `/api/tasks/{id}` | Update a task |
| DELETE | `/api/tasks/{id}` | Delete a task |

### Query Parameters

- `category` - Filter tasks by category
- `status` - Filter tasks by status (pending/completed)

### Example API Requests

**Get all tasks:**
```bash
curl http://localhost:8000/api/tasks
```

**Filter by category:**
```bash
curl http://localhost:8000/api/tasks?category=Work
```

**Create a task:**
```bash
curl -X POST http://localhost:8000/api/tasks \
  -H "Content-Type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "title": "New Task",
    "description": "Task description",
    "priority": "high",
    "category": "Work",
    "due_date": "2024-12-31"
  }'
```

## Project Structure

```
task-manager/
├── app/
│   ├── Http/
│   │   └── Controllers/
│   │       └── TaskController.php    # Task CRUD operations
│   └── Models/
│       └── Task.php                  # Task model
├── config/
│   ├── app.php                       # Application configuration
│   ├── database.php                  # Database configuration
│   └── cors.php                      # CORS configuration
├── database/
│   ├── migrations/
│   │   └── 2024_01_01_000000_create_tasks_table.php
│   └── seeders/
│       ├── DatabaseSeeder.php
│       └── TaskSeeder.php            # Sample task data
├── resources/
│   └── views/
│       ├── layouts/
│       │   └── app.blade.php         # Main layout template
│       └── tasks/
│           └── index.blade.php       # Task manager interface
├── routes/
│   ├── api.php                       # API routes
│   └── web.php                       # Web routes
├── .env.example                      # Environment variables template
├── artisan                           # Laravel CLI tool
├── composer.json                     # PHP dependencies
└── README.md                         # This file
```

## Database Schema

### Tasks Table

| Column | Type | Description |
|--------|------|-------------|
| id | BIGINT | Primary key (auto-increment) |
| title | VARCHAR(255) | Task title (required) |
| description | TEXT | Task description (optional) |
| due_date | DATE | Due date (optional) |
| priority | ENUM | Priority level: low, medium, high |
| category | VARCHAR(100) | Task category (optional) |
| status | ENUM | Task status: pending, completed |
| created_at | TIMESTAMP | Creation timestamp |
| updated_at | TIMESTAMP | Last update timestamp |

## Features Comparison

This Laravel version maintains all features from the original Node.js version:

| Feature | Node.js Version | Laravel Version |
|---------|----------------|-----------------|
| RESTful API | ✅ Express | ✅ Laravel |
| Database | ✅ MySQL2 | ✅ Eloquent ORM |
| CORS Support | ✅ cors package | ✅ Built-in CORS |
| Input Validation | ✅ Manual | ✅ Laravel Validation |
| Task Filtering | ✅ | ✅ |
| Priority Levels | ✅ | ✅ |
| Categories | ✅ | ✅ |
| Modern UI | ✅ | ✅ |

## Development

### Running Tests

```bash
php artisan test
```

### Clear Cache

```bash
php artisan cache:clear
php artisan config:clear
php artisan route:clear
php artisan view:clear
```

### Database Operations

**Fresh migration (drops all tables):**
```bash
php artisan migrate:fresh
```

**Reset and seed:**
```bash
php artisan migrate:fresh --seed
```

## Production Deployment

### 1. Optimize Application

```bash
composer install --optimize-autoloader --no-dev
php artisan config:cache
php artisan route:cache
php artisan view:cache
```

### 2. Set Environment

Update `.env`:
```env
APP_ENV=production
APP_DEBUG=false
```

### 3. Set Permissions

```bash
chmod -R 775 storage bootstrap/cache
chown -R www-data:www-data storage bootstrap/cache
```

## Troubleshooting

### Database Connection Error

- Verify MySQL is running
- Check database credentials in `.env`
- Ensure the database exists

### Permission Errors

```bash
chmod -R 775 storage
chmod -R 775 bootstrap/cache
```

### 404 Errors

```bash
php artisan route:clear
php artisan config:clear
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is open-source and available under the MIT License.

## Credits

- Original Node.js version by Prathamesh
- Laravel conversion: 2024
- UI Design: Custom gradient design with modern components

## Support

For issues, questions, or contributions, please open an issue on the project repository.

---

**Note:** This is a complete Laravel conversion of the original Node.js task manager application. All functionality has been preserved and enhanced with Laravel's powerful features like Eloquent ORM, validation, and Blade templating.
