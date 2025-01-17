# Recipe-App-Api

## Introduction


The Recipe App API is a robust and scalable RESTful platform that allows users to efficiently manage their favorite recipes. With features like user authentication, recipe filtering, and image uploads, it enhances how users organize, explore, and personalize their culinary collections.

## Features

- **User Authentication**: A secure registration and login system that allows users to manage their personal recipe collections with ease.

- **Recipe Management**: Create, update, delete, and manage recipes, including details like titles, prices, link, cooking times, ingredients, tags, and images.

- **Image Uploads**: Upload and associate photos with recipes, offering a visual recipe management experience.

- **Filtering and Sorting**: Easily find recipes using filters like tags or ingredients, and sort results by various criteria.


## Tech Stack

- **Python**: Core programming language.

- **Django**: Web framework for building the API.

- **Django REST Framework (DRF)**: A toolkit for building RESTful APIs, handling serialization and views

- **PostgreSQL**: Database management system for storing recipes and user data.

- **Swagger**: A tool that generates interactive API documentation, enabling easy exploration and testing of endpoints.

- **Docker**: A platform for containerized development and deployment.


## Installation

Follow these steps to set up the Recipe App API locally, including installing dependencies and configuring the environment.

### Prerequisites

Before you begin, ensure you have the following installed:

- **Docker** and **Docker Compose**


### Steps:

1. **Clone the repository:**

   ```sh
   git clone https://github.com/vazhaberdzenishvili/recipe-app-api.git
   ```
2. **Build and initialize the Docker containers:**

   ```sh
   docker compose up --build
   ```

## Admin Setup

To manage recipes and user data through the admin panel, you'll need to create a superuser. Ensure that Docker containers are already running before proceeding.

Run the command inside the Docker container:
   ```sh
   docker compose run --rm app sh -c "python manage.py createsuperuser"
   ```
   Follow the prompts to set up your admin email and password.


## Usage

### User Authentication

The Recipe App API uses **token-based authentication.** Users can obtain a token by logging in, which is then used to authorize access to protected endpoints.

- #### Obtain a token for authentication.

   - **POST** `/api/user/token/`

- #### Retrieve details of the authenticated user.

   - **GET** `/api/user/me/`


### Recipes

- #### Retrieve all recipes:

   - **GET** `/api/recipe/recipes/ `

- #### Create a new recipe (authentication required).

   - **POST** `/api/recipe/recipes/`

   - **Example Payload:**
   ```json
   {
      "title": "string",
      "time_minutes": 0,
      "price": "string",
      "link": "string",
      "tags": [
         {
            "name": "string"
         }
      ],
      "ingredients": [
         {
            "name": "string"
         }
      ],
      "description": "string",
      "image": "string"
   }
   ```

- ####  Retrieve a specific recipe by its ID.

   - **GET** `/api/recipe/recipes/{id}/`

- ####  Update a specific recipe by its ID (authentication required).

   - **PUT** `/api/recipe/recipes/{id}/`

- #### Delete a recipe by its ID (authentication required).

   - **DELETE** `/api/recipe/recipes/{id}/`

- #### Upload an image for a specific recipe.

   - **POST** `/api/recipe/recipes/{id}/upload-image/`


### Ingredients

- #### Retrieve a list of all ingredients.
   - GET `/api/recipe/ingredients/`

- #### Create a new ingredient (authentication required).
   - POST `/api/recipe/ingredients/`


### Tags
-  #### Retrieve a list of all tags.
   - GET `/api/recipe/tags/`

## API Documentation

The Recipe App API includes Swagger, an interactive interface for exploring and testing all available endpoints. It provides a user-friendly way to understand the API structure and functionality.

### Accessing the Documentation

Once the server is running, open your browser and navigate to:

```bash
http://localhost:8000/api/docs/
```
## Testing

The test suite ensures that all features of the Recipe App API work as intended, offering reliability and confidence in your deployment. To run the tests, use the following command:
```sh
   docker compose run --rm app sh -c "python manage.py test"
```

## Linting

To ensure high code quality and maintain consistency, the project utilizes flake8 for linting. Execute the following command to inspect the codebase for formatting errors and possible issues:

```sh
   docker compose run --rm app sh -c "flake8"
```