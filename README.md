# Airbnb Clone Project
## Team Roles
- **Backend Developer:** Responsible for creating API endpoints, designing database schemas, and implementing business logic. They also devise application architectures and implement advanced algorithms to enhance app performance.
- **Database Administrator:** Responsible for maintaining, architecting, optimizing, and indexing databases.
- **Quality Assurance Engineer:** Responsible for ensuring the application meets quality standards by thoroughly testing it against both functional and non-functional requirements. They ensure the app is free of bugs and is user-friendly.
- **Test Automation Engineer:** Responsible for writing test scripts for automated testing. They also design test automation frameworks that are easy to maintain and update.
- **Devops Engineer:** Responsible for fostering collaboration between the development and operations teams. They also monitor, deploy, and scale backend services to ensure reliability and performance.
## Technology Stack
- **Django:** A high-level Python web framework used for building the RESTful API.
- **Django REST Framework:** Provides tools for creating and managing RESTful APIs.
- **PostgreSQL:** A powerful relational database used for data storage.
- **GraphQL:** Allows for flexible and efficient querying of data.
- **Celery:** For handling asynchronous tasks such as sending notifications or processing payments.
- **Redis:** Used for caching and session management.
- **Docker** Containerization tool for consistent development and deployment environments.
- **CI/CD Pipelines:** Automated pipelines for testing and deploying code changes.
## Database Design
### Users Table
| **Field**   | **Description**                                   |
| ----------- | ------------------------------------------------- |
| user\_id    | Unique identifier for each user                   |
| first\_name | The user's first name                             |
| last\_name  | The user's last name                              |
| user\_type  | Defines the role of the user (e.g., guest, owner) |
| birth\_date | The user's date of birth                          |
### Properties Table
| **Field**      | **Description**                                      |
| -------------- | ---------------------------------------------------- |
| property\_id   | Unique identifier for each property                  |
| property\_name | Name of the property                                 |
| owner\_id      | References `user_id` of the owner in the Users table |
| location       | Physical location/address of the property            |
| total\_rooms   | Total number of rooms available in the property      |
| booking\_price | Price per booking or per night                       |
| description    | Detailed description of the property                 |
### Bookings Table
| **Field**     | **Description**                                                        |
| ------------- | ---------------------------------------------------------------------- |
| booking\_id   | Unique identifier for each booking                                     |
| property\_id  | References `property_id` in the Properties table                       |
| user\_id      | References `user_id` of the user making the booking in the Users table |
| date\_booked  | The date the booking starts                                            |
| leaving\_date | The date the user plans to leave the property                          |
### Reviews Table
| **Field**    | **Description**                                                           |
| ------------ | ------------------------------------------------------------------------- |
| review\_id   | Unique identifier for each review                                         |
| user\_id     | References `user_id` of the reviewer in the Users table                   |
| property\_id | References `property_id` of the reviewed property in the Properties table |
| title        | Short title or summary of the review                                      |
| description  | Full content/body of the review                                           |
### Payments Table
| **Field**       | **Description**                                                      |
| --------------- | -------------------------------------------------------------------- |
| payment\_id     | Unique identifier for each payment record                            |
| user\_id        | References `user_id` of the paying user in the Users table           |
| property\_id    | References `property_id` for which the payment was made              |
| payment\_method | Method used for the payment (e.g., credit card, PayPal, Mpesa, etc.) |
## Feature Breakdown
- **User Management:** This feature allows users to register either as guests or property owners, with the system distinguishing between the two roles. It includes profile management, enabling users to update and manage their personal information. Users can securely access their accounts and view content relevant to their role. The system ensures that each user has a protected, personalized space for managing their account activities.
- **Property Management:** This feature allows property owners to manage their properties within the app. They can add detailed information about each property, update existing property details, and list multiple properties if they own more than one. It provides a centralized and efficient way for property owners to keep their listings up to date.
- **Booking System:** This feature allows users to book a property for a specified period. Users can also extend or shorten their stay as needed. For property owners, it provides clear visibility into booking details, including which guest is staying and the duration of their stay. This ensures smooth coordination between guests and property owners.
- **Payment Processing:** This feature enables users to make payments for their bookings using various platforms such as M-Pesa or bank transfers. It offers flexibility in payment methods to suit user preferences. Additionally, property owners receive payments once their property is booked, ensuring a smooth and secure transaction process for both parties.
- **Review System:** This feature allows users to leave reviews about their experience staying at a property. Users can rate the property and share detailed feedback based on their stay. These reviews are visible to other users, helping them make informed decisions about whether or not to book a particular property.
- **Data Optimization:** This feature ensures that data is retrieved, updated, and deleted efficiently within the system. By optimizing database queries and data structures, the app can load information faster and respond more quickly to user actions. This improves the overall user experience by reducing wait times and making the application feel smooth and responsive.
