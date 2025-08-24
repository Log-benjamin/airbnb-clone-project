## 🚀 Project Overview
This project is a backend solution for an Airbnb clone, engineered to handle all the essential functionalities of a property rental platform. It provides a scalable and robust foundation for managing users, properties, bookings, and payments. The system is designed to ensure a seamless and efficient experience for both guests and hosts. The API is documented using the OpenAPI standard, offering both RESTful and GraphQL endpoints for flexible data interaction.


## 🏆 Project Goals
The primary objectives of this project are to:
*   User Management: Implement a secure system for user registration, authentication, and profile management.
*   Property Management: Develop comprehensive features for creating, updating, and retrieving property listings.
*   Booking System: Create a reliable mechanism for users to book properties and manage their reservations.
*   Payment Processing: Integrate a secure payment system to handle all transactional aspects of bookings.
*   Review System: Enable users to provide feedback and ratings for properties.
*   Data Optimization: Ensure high performance and efficiency through database indexing and caching strategies.


## ⚙️ Tech Stack
The backend of this project leverages a modern and powerful technology stack:
*   Django: A high-level Python web framework is used for building the robust RESTful API.
*   Django REST Framework: This toolkit is utilized for creating and managing the RESTful APIs efficiently.
*   PostgreSQL: A powerful, open-source relational database serves as the primary data storage.
*   GraphQL: This query language provides a flexible and efficient way to interact with the backend.
*   Celery: Asynchronous tasks, such as sending notifications and processing payments, are handled by Celery.
*   Redis: This in-memory data store is used for caching and session management to improve performance.
*   Docker: The application is containerized using Docker for consistency across development and deployment environments.
*   CI/CD Pipelines: Automated pipelines are set up for continuous integration and deployment, ensuring code quality and rapid delivery.


## 👥 Team Roles
This section outlines the key roles and responsibilities within the project, ensuring a clear division of tasks and effective collaboration

### Backend Developer
**Responsibility:** The Backend Developer is responsible for the core logic of the application. They implement the API endpoints, design the database schemas, and write the business logic that powers all features, from user authentication to booking processing.

### Database Administrator (DBA)
**Responsibility:** The Database Administrator focuses on the performance, integrity, and security of the database. Their tasks include managing the database design, implementing indexing for fast data retrieval, and performing optimizations to ensure the system can handle a high volume of transactions efficiently.

### DevOps Engineer
**Responsibility:** The DevOps Engineer bridges the gap between development and operations. They are responsible for automating the software delivery process by building and maintaining the CI/CD pipelines. This role also handles the deployment, monitoring, and scaling of the backend services to ensure the application is stable and available.

### QA Engineer
**Responsibility:** The Quality Assurance (QA) Engineer is responsible for ensuring the backend functionalities are thoroughly tested and meet the project's quality standards. They verify that the application performs according to its requirements by identifying and reporting both functional (e.g., an API not returning the correct data) and non-functional (e.g., slow response times) defects.


## ⚙️ Technology Stack
This project leverages a modern stack of technologies to ensure scalability, performance, and maintainability. Below is a detailed breakdown of each component and its role.

*   **Django:** A high-level Python web framework used as the foundation for building the project's robust and secure RESTful API.

*   **Django REST Framework (DRF):** A powerful and flexible toolkit built for Django that simplifies the process of creating and managing RESTful APIs, handling everything from data serialization to authentication.

*   **PostgreSQL:** A powerful, open-source object-relational database system used for the primary data storage. It is chosen for its reliability, feature robustness, and performance.

*   **GraphQL:** A query language for APIs that provides a more efficient and flexible alternative to REST. It allows clients to request exactly the data they need, making the application more performant.

*   **Celery:** An asynchronous task queue used for handling background tasks that would otherwise block the main application thread, such as sending email notifications, processing payments, or generating reports.

*   **Redis:** An in-memory data store used as a message broker for Celery and for caching frequently accessed data. This reduces database load and significantly improves the application's response times.

*   **Docker:** A containerization platform used to package the application and its dependencies into isolated containers. This ensures a consistent development, testing, and production environment, eliminating the "it works on my machine" problem.

*   **CI/CD Pipelines:** Automated workflows for Continuous Integration and Continuous Deployment. These pipelines automatically build, test, and deploy code changes, ensuring high code quality and enabling rapid, reliable releases.


## 🗂️ Database Design
The database schema is designed around the core entities of the application. The relationships are structured to ensure data integrity and efficient querying.

### Key Entities & Fields

**1. Users**
This entity stores information about registered users.
*   `id`: Unique identifier for the user (Primary Key).
*   `email`: User's email address, used for login and notifications.
*   `password`: Hashed password for security.
*   `full_name`: The user's full name.
*   `created_at`: Timestamp of when the user account was created.

**2. Properties**
This entity contains details about the property listings.
*   `id`: Unique identifier for the property (Primary Key).
*   `owner_id`: Foreign key referencing the `Users` table to identify the host.
*   `title`: The title of the property listing.
*   `description`: A detailed description of the property.
*   `location`: The physical address of the property.
*   `price_per_night`: The cost to book the property for one night.

**3. Bookings**
This entity manages reservation details made by users.
*   `id`: Unique identifier for the booking (Primary Key).
*   `user_id`: Foreign key referencing the `Users` table to identify the guest.
*   `property_id`: Foreign key referencing the `Properties` table.
*   `start_date`: The check-in date for the reservation.
*   `end_date`: The check-out date for the reservation.
*   `total_price`: The calculated total cost of the booking.

**4. Reviews**
This entity holds user-submitted reviews and ratings for properties.
*   `id`: Unique identifier for the review (Primary Key).
*   `user_id`: Foreign key referencing the `Users` table to identify the reviewer.
*   `property_id`: Foreign key referencing the `Properties` table that is being reviewed.
*   `rating`: A numerical rating (e.g., 1 to 5).
*   `comment`: The text content of the review.

**5. Payments**
This entity tracks payment information related to bookings.
*   `id`: Unique identifier for the payment (Primary Key).
*   `booking_id`: Foreign key referencing the `Bookings` table.
*   `amount`: The total amount paid.
*   `status`: The current status of the payment (e.g., 'pending', 'completed', 'failed').
*   `transaction_id`: A unique identifier provided by the payment gateway.

### Entity Relationships

*   A **User** can own multiple **Properties** (One-to-Many).
*   A **User** can make multiple **Bookings** (One-to-Many).
*   A **Property** can have multiple **Bookings** (One-to-Many).
*   A **Booking** belongs to exactly one **User** and one **Property**.
*   A **User** can write multiple **Reviews** for different properties.
*   A **Property** can receive multiple **Reviews** from different users.
*   Each **Booking** is associated with one **Payment** (One-to-One).