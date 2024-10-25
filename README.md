# **Dockerized-Django-FashionHub**

This project is a **Dockerized** Python and Django-based fashion website designed for consistent, scalable, and secure deployment. It includes essential e-commerce features like product catalog, user authentication, and shopping cart functionality.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Setup Instructions](#setup-instructions)
- [Dockerization Details](#dockerization-details)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Overview

This fashion website application is built with Django and containerized using Docker to simplify deployment and maintain a consistent environment. It uses **SQLite** as its default database, which can be reconfigured if needed for production.

## Features

- **Product Catalog**: Browse and view a range of fashion items.
- **User Authentication**: Sign-up, login, and profile management.
- **Shopping Cart**: Add products to the cart and checkout.
- **Admin Dashboard**: Manage products, orders, and users via Django’s built-in admin panel.
- **Search and Filter**: Search and filter products by various criteria.

## Technologies Used

- **Backend**: Python, Django
- **Frontend**: HTML, CSS, JavaScript
- **Database**: SQLite (default)
- **Containerization**: Docker

## Project Structure

```plaintext
.
├── Dockerfile               # Docker setup for the app
├── db.sqlite3               # SQLite database file
├── manage.py                # Django project manager
├── requirements.txt         # Python dependencies
├── home/                    # Django app for core website functionality
├── static/                  # Static files (CSS, JavaScript, images)
└── templates/               # HTML templates for frontend
Prerequisites
Ensure you have the following installed:

Docker
Git
Setup Instructions
1. Clone the Repository
Clone the repository to your local machine:

bash
Copy code
git clone https://github.com/Manreet28/Python-Django-Project.git
cd Python-Django-Project
2. Build and Run the Docker Container
Build the Docker image and start the container:

bash
Copy code
docker build -t django-fashion-app .
docker run -p 8000:8000 django-fashion-app
3. Run Database Migrations
To set up the database, open a terminal inside the running container and run the migrations:

bash
Copy code
docker exec -it <container_id> python manage.py migrate
Replace <container_id> with the ID of your running container.

4. Create a Superuser
To access the Django admin panel, create a superuser by running:

bash
Copy code
docker exec -it <container_id> python manage.py createsuperuser
5. Access the Application
Once running, the application will be accessible at:

Website: http://localhost:8000
Admin Panel: http://localhost:8000/admin
Dockerization Details
The Dockerfile defines a Python 3.8-slim-buster environment, installs dependencies, and serves the Django app on port 8000. Here’s the Dockerfile:

Dockerfile
Copy code
# Use Python 3.8 as the base image
FROM python:3.8-slim-buster

# Set the working directory inside the container
WORKDIR /app

# Copy the requirements file and install dependencies
COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

# Copy the entire project into the container
COPY . .

# Expose port 8000 for the Django app
EXPOSE 8000

# Start the Django development server
CMD ["python3", "manage.py", "runserver", "0.0.0.0:8000"]
Usage
To run the application in development mode:

bash
Copy code
docker build -t django-fashion-app .
docker run -p 8000:8000 django-fashion-app
To stop the container, you can find the container ID using:

bash
Copy code
docker ps
Then stop it with:

bash
Copy code
docker stop <container_id>
Contributing
Contributions are welcome! Please fork the repository, create a new branch for your feature or fix, and submit a pull request.

License
This project is licensed under the MIT License. See the LICENSE file for more details.
