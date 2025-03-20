# YouQuotes API

<p align="center">
  <img src="https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white" alt="Laravel">
  <img src="https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white" alt="PHP">
  <img src="https://img.shields.io/badge/MySQL-005C84?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL">
  <img src="https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=JSON%20web%20tokens&logoColor=white" alt="JWT">
</p>

## About YouQuotes

YouQuotes is an API that allows users to manage quotes. Users can create, read, update, and delete quotes, as well as get random quotes and filter quotes based on length. Additionally, the API tracks the popularity of the most requested quotes and offers a bonus feature of generating images for popular quotes. Authentication is an optional feature that allows users to securely manage their own quotes.

## Features

### Core Features

- **Quote Management (CRUD)**: Create, read, update, and delete quotes
- **Random Quotes**: Generate one or more random quotes on demand
- **Quote Filtering by Length**: Filter quotes based on their word count
- **Quote Popularity Tracking**: Track and record the frequency of requests for each quote

### Bonus Features

- **Quote Image Generation**: Generate images containing the most popular quotes
- **Authentication**: Register, login, and securely manage personal quotes

## Technical Requirements

### Architecture
- Monolithic architecture using Laravel framework

### Database
- MySQL or PostgreSQL for storing quotes, popularity metrics, and user information

### Image Generation
- Intervention Image library for stylized quote images

### Authentication
- JWT (JSON Web Tokens) for user authentication and feature access control

## Installation

1. Clone the repository:
   ```
   git clone https://github.com/yourusername/YouQuotes.git
   ```

2. Navigate to the project directory:
   ```
   cd YouQuotes
   ```

3. Install the dependencies:
   ```
   composer install
   ```

4. Copy the example environment file and make the required configuration changes:
   ```
   cp .env.example .env
   ```

5. Generate an application key:
   ```
   php artisan key:generate
   ```

6. Run the database migrations and seed the database with sample quotes:
   ```
   php artisan migrate --seed
   ```

7. Start the local development server:
   ```
   php artisan serve
   ```

## API Endpoints

### Quote Management
- `GET /api/quotes` - Get all quotes
- `GET /api/quotes/{id}` - Get a specific quote
- `POST /api/quotes` - Create a new quote
- `PUT /api/quotes/{id}` - Update an existing quote
- `DELETE /api/quotes/{id}` - Delete a quote

### Random Quotes
- `GET /api/quotes/random` - Get a random quote
- `GET /api/quotes/random/{count}` - Get multiple random quotes

### Quote Filtering
- `GET /api/quotes/filter?min_words={min}&max_words={max}` - Filter quotes by word count

### Popular Quotes
- `GET /api/quotes/popular` - Get the most popular quotes

### Quote Image Generation
- `GET /api/quotes/{id}/image` - Generate an image for a specific quote
- `GET /api/quotes/popular/images` - Generate images for popular quotes

### Authentication
- `POST /api/register` - Register a new user
- `POST /api/login` - Login and receive JWT token
- `GET /api/user` - Get authenticated user information
- `POST /api/logout` - Logout and invalidate token

## Usage Examples

### Creating a Quote

```http
POST /api/quotes
Content-Type: application/json
Authorization: Bearer your_jwt_token

{
  "text": "The only limit to our realization of tomorrow will be our doubts of today.",
  "author": "Franklin D. Roosevelt"
}
```

### Getting Random Quotes

```http
GET /api/quotes/random/3
Authorization: Bearer your_jwt_token
```

### Filtering Quotes by Length

```http
GET /api/quotes/filter?min_words=5&max_words=10
Authorization: Bearer your_jwt_token
```

### Generating an Image for a Quote

```http
GET /api/quotes/5/image
Authorization: Bearer your_jwt_token
```

## License

This project is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
