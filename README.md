# AirBnB Clone Project

## Overview
This project is a clone of the popular AirBnB platform. It replicates core functionalities such as property listing, user authentication, booking, and reviews. The goal is to develop a scalable and responsive full-stack application for educational and portfolio purposes.

## Project Goals
- Recreate a simplified version of the AirBnB platform
- Implement both front-end and back-end functionality
- Practice full-stack development with modern tools
- Learn clean code structure, version control, and collaboration

## Tech Stack
- **Frontend**: HTML5, CSS3, JavaScript, React (later)
- **Backend**: Python, Flask (or Django)
- **Database**: MySQL / PostgreSQL
- **Version Control**: Git & GitHub
- **Deployment**: (Optional) Heroku / Render / Docker

## Status
🚧 Project under development

# AirBnB Clone Project

=======
## Team Roles

In this project, our team was structured around key software development roles to ensure smooth collaboration and delivery of an Airbnb clone application.

### 1. **Backend Developer**
Responsible for building the server-side logic, APIs, and core functionality. Handles user authentication, listing management, and reservation processes. Also ensures data is correctly transferred between the client and the server.

### 2. **Frontend Developer**
Focuses on implementing the user interface and user experience using HTML, CSS, and JavaScript (or frontend frameworks). Integrates APIs and ensures a responsive and user-friendly design across devices.

### 3. **Database Administrator (DBA)**
Designs and manages the project's database structure. Responsible for ensuring data integrity, indexing, writing efficient SQL queries, and handling backups and migrations.

### 4. **DevOps Engineer**
Sets up and maintains deployment pipelines, manages cloud infrastructure (e.g., AWS, Heroku), and ensures continuous integration and continuous deployment (CI/CD). Handles server configuration, monitoring, and scalability.

### 5. **Project Manager**
Coordinates the team, tracks progress, assigns tasks, and ensures milestones are met. Acts as a liaison between stakeholders and developers to keep everyone aligned.

### 6. **Quality Assurance (QA) Engineer**
Tests the application for bugs and performance issues. Writes test cases and automates test suites to ensure the stability and reliability of the system across updates.


## Technology Stack

Below is a list of the core technologies used in this project and their respective roles:

### 1. **Django**
A high-level Python web framework used for building the backend of the application. It enables rapid development of secure and maintainable web APIs and views.

### 2. **PostgreSQL**
An open-source, advanced relational database used to store application data such as users, listings, bookings, and payments. It integrates well with Django using the ORM.

### 3. **HTML/CSS**
Used to create and style the frontend pages. HTML structures the content while CSS makes it visually appealing and responsive.

### 4. **JavaScript**
Adds interactivity to the frontend (e.g., date pickers, form validation, dynamic content loading).

### 5. **Bootstrap**
A frontend framework used to speed up UI development with pre-designed responsive components.

### 6. **REST Framework (Django REST Framework)**
Used to create RESTful APIs for the backend. Allows data exchange between frontend and backend in JSON format.

### 7. **Docker** *(Optional if used)*
Used to containerize the application for easy deployment and environment consistency.

### 8. **Git & GitHub**
Version control system and platform for code collaboration and project tracking.

---

This tech stack provides a solid foundation for building a scalable and maintainable Airbnb-like platform. 



## Database Design

The database schema is designed to capture all the core functionalities of the Airbnb clone system. Below are the main entities, their key fields, and relationships:

### 1. **User**
Represents people using the platform, either as hosts or guests.

**Key Fields:**
- `id`: Primary key
- `name`: Full name of the user
- `email`: Unique email address
- `password`: Hashed password
- `is_host`: Boolean flag to identify hosts

**Relationships:**
- A user can host multiple properties.
- A user can make multiple bookings and leave reviews.

---

### 2. **Property**
Represents listings posted by hosts.

**Key Fields:**
- `id`: Primary key
- `title`: Name of the property
- `description`: Detailed info
- `location`: Address or city
- `price_per_night`: Cost per night
- `host_id`: Foreign key to User

**Relationships:**
- A property belongs to one host (User).
- A property can have multiple bookings and reviews.

---

### 3. **Booking**
Represents a reservation made by a guest.

**Key Fields:**
- `id`: Primary key
- `user_id`: Foreign key to User
- `property_id`: Foreign key to Property
- `start_date`: Check-in date
- `end_date`: Check-out date
- `total_price`: Calculated total cost

**Relationships:**
- A booking is made by one user for one property.

---

### 4. **Review**
Represents feedback left by users after staying at a property.

**Key Fields:**
- `id`: Primary key
- `user_id`: Foreign key to User
- `property_id`: Foreign key to Property
- `rating`: Numeric score (e.g., 1 to 5)
- `comment`: Review text
- `created_at`: Date and time of review

**Relationships:**
- A review is linked to both a user and a property.

---

### 5. **Payment**
Represents transaction details for bookings.

**Key Fields:**
- `id`: Primary key
- `booking_id`: Foreign key to Booking
- `payment_method`: e.g., credit card, PayPal
- `amount`: Total amount paid
- `payment_date`: Date of payment
- `status`: e.g., completed, pending, failed

**Relationships:**
- A payment is linked to one booking.

---

### ⚙️ Entity Relationships Summary:
- One **User** can have many **Properties** and **Bookings**.
- One **Property** can have many **Bookings** and **Reviews**.
- One **Booking** has one **Payment**.
- One **User** can leave many **Reviews** for different **Properties**.


## Feature Breakdown

This project replicates key functionalities of the Airbnb platform. Below are the main features that power the user experience and application logic:

### 1. **User Management**
Users can register, log in, and manage their profiles. The system supports both guests and hosts, with role-based access to different functionalities.

### 2. **Property Management**
Hosts can list new properties by providing details like title, description, location, price per night, and photos. They can also edit or delete their listings.

### 3. **Booking System**
Guests can search for available properties based on location and date. They can book properties for specific dates, and the system calculates the total price and prevents double booking.

### 4. **Review and Rating System**
After a stay, guests can leave a rating and written review for a property. This helps build trust and gives future guests insights into the quality of each listing.

### 5. **Payment Integration**
Secure payment handling is provided for bookings. The system records payment status, method, and associates each payment with the respective booking.

### 6. **Search and Filtering**
Users can search for properties by location, date range, price, and other filters to find listings that meet their needs.

### 7. **Responsive User Interface**
The application offers a user-friendly, responsive UI across devices using modern frontend technologies and frameworks like Bootstrap.

### 8. **Admin Dashboard (Optional if implemented)**
Admins can manage users, listings, bookings, and view platform statistics, enabling easier moderation and platform oversight.




## API Security

Securing the backend API is critical to protecting user data, preventing abuse, and ensuring the platform's integrity. This project applies several key security practices:

### 1. **Authentication**
Only registered users can access protected resources. We use secure methods like token-based authentication (e.g., JWT or session tokens) to verify identities and prevent unauthorized access.

### 2. **Authorization**
Role-based access control ensures that only authorized users can perform certain actions (e.g., only hosts can create properties, only guests can book). This prevents privilege escalation.

### 3. **Rate Limiting**
To prevent brute-force attacks and abuse of APIs, rate limits are implemented using tools like Django Ratelimit or middleware to restrict excessive requests.

### 4. **Input Validation and Sanitization**
All user input is validated to prevent SQL injection, XSS, and other injection attacks. The use of Django’s ORM also protects against raw SQL vulnerabilities.

### 5. **Secure Payment Handling**
Payment-related APIs are encrypted and integrated with third-party providers (e.g., Stripe or PayPal) to ensure safe handling of sensitive financial data.

### 6. **HTTPS Enforcement**
All API communications occur over HTTPS to encrypt data in transit and protect against man-in-the-middle attacks.



## CI/CD Pipeline

CI/CD (Continuous Integration and Continuous Deployment) automates the process of testing, building, and deploying code, ensuring rapid and reliable development workflows.

### Why CI/CD Matters:
- Automatically tests code on every push to catch bugs early.
- Speeds up deployment and reduces human error.
- Maintains code quality and consistency across environments.

### Tools Used:
- **GitHub Actions**: For automating tests, linting, and deployment steps on every push or pull request.
- **Docker**: Ensures consistent runtime environments across development, testing, and production.
- **Heroku / Render / AWS / Vercel (Optional)**: Platforms for automated deployment pipelines.

A properly configured CI/CD pipeline helps the team deploy updates quickly and safely while focusing on writing quality code.

