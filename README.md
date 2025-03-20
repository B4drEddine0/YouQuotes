
YouQuotes API
<p align="center"> <img src="https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white" alt="Laravel"> <img src="https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white" alt="PHP"> <img src="https://img.shields.io/badge/MySQL-005C84?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL"> <img src="https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=JSON%20web%20tokens&logoColor=white" alt="JWT"> </p>
About YouQuotes
YouQuotes is an API that allows users to manage quotes. Users can create, read, update, and delete quotes, as well as get random quotes and filter quotes based on length. The API also tracks the popularity of the most requested quotes and offers a bonus feature of generating images for popular quotes. Authentication is an essential feature that allows users to securely manage their own quotes, with different access levels and permissions.

Features
Core Features
Quote Management (CRUD): Create, read, update, and delete quotes.
Random Quotes: Generate one or more random quotes on demand.
Quote Filtering by Length: Filter quotes based on their word count.
Quote Popularity Tracking: Track and record the frequency of requests for each quote.
Bonus Features
Quote Image Generation: Generate images containing the most popular quotes.
Authentication: Register, login, and securely manage personal quotes.
User Roles and Permissions: Admins can manage all quotes (CRUD and moderation), while regular users can manage only their own quotes.
Categories and Tags: Assign categories and tags to quotes for better organization and easier search.
Likes and Favorites: Users can like quotes and add them to their favorites for easy access later.
Technical Requirements
Architecture
Monolithic architecture using Laravel framework
Database
MySQL or PostgreSQL for storing quotes, popularity metrics, user information, categories, tags, and favorite quotes
Image Generation
Intervention Image library for stylized quote images
Authentication
JWT (JSON Web Tokens) for user authentication and feature access control
User Roles
Admin: Full access to all quotes and management features
User: Limited to managing only their own quotes
Installation
Clone the repository:

bash
Copier le code
git clone https://github.com/yourusername/YouQuotes.git
Navigate to the project directory:

bash
Copier le code
cd YouQuotes
Install the dependencies:

nginx
Copier le code
composer install
Copy the example environment file and make the required configuration changes:

bash
Copier le code
cp .env.example .env
Generate an application key:

vbnet
Copier le code
php artisan key:generate
Run the database migrations and seed the database with sample quotes:

css
Copier le code
php artisan migrate --seed
Start the local development server:

nginx
Copier le code
php artisan serve
API Endpoints
Quote Management
GET /api/quotes - Get all quotes (Admin only)
GET /api/quotes/{id} - Get a specific quote
POST /api/quotes - Create a new quote
PUT /api/quotes/{id} - Update an existing quote (only own quotes for users)
DELETE /api/quotes/{id} - Delete a quote (only own quotes for users)
Random Quotes
GET /api/quotes/random - Get a random quote
GET /api/quotes/random/{count} - Get multiple random quotes
Quote Filtering
GET /api/quotes/filter?min_words={min}&max_words={max} - Filter quotes by word count
Popular Quotes
GET /api/quotes/popular - Get the most popular quotes
Quote Image Generation
GET /api/quotes/{id}/image - Generate an image for a specific quote
GET /api/quotes/popular/images - Generate images for popular quotes
Categories and Tags
POST /api/categories - Create a new category
POST /api/tags - Create a new tag
GET /api/quotes/category/{category_id} - Get quotes by category
GET /api/quotes/tag/{tag_id} - Get quotes by tag
Likes and Favorites
POST /api/quotes/{id}/like - Like a quote
POST /api/quotes/{id}/favorite - Add a quote to favorites
GET /api/user/favorites - Get all favorite quotes for the authenticated user
Authentication
POST /api/register - Register a new user
POST /api/login - Login and receive JWT token
GET /api/user - Get authenticated user information
POST /api/logout - Logout and invalidate token
Usage Examples
Creating a Quote
http
Copier le code
POST /api/quotes
Content-Type: application/json
Authorization: Bearer your_jwt_token

{
  "text": "The only limit to our realization of tomorrow will be our doubts of today.",
  "author": "Franklin D. Roosevelt"
}
Getting Random Quotes
http
Copier le code
GET /api/quotes/random/3
Authorization: Bearer your_jwt_token
Filtering Quotes by Length
http
Copier le code
GET /api/quotes/filter?min_words=5&max_words=10
Authorization: Bearer your_jwt_token
Generating an Image for a Quote
http
Copier le code
GET /api/quotes/5/image
Authorization: Bearer your_jwt_token
Liking a Quote
http
Copier le code
POST /api/quotes/5/like
Authorization: Bearer your_jwt_token
Adding a Quote to Favorites
http
Copier le code
POST /api/quotes/5/favorite
Authorization: Bearer your_jwt_token
Creating a New Category
http
Copier le code
POST /api/categories
Authorization: Bearer your_jwt_token

{
  "name": "Motivation"
}
License
This project is open-sourced software licensed under the MIT license.
