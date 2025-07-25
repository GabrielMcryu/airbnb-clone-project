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
## API Security
### Key Security Measures
- **Authentication:** Ensures that only authorized users can access their accounts using valid credentials. This protects private user information and prevents unauthorized access, maintaining the confidentiality and security of each account.
- **Authorization:** Ensures that users can only access the content and features they are permitted to use based on their role or permissions. This prevents unauthorized access to sensitive data and reduces the risk of users tampering with content they shouldn't have access to.
- **Rate Limiting:** Rate limiting restricts the number of requests a user or system can make within a specific time period. It helps prevent abuse, such as brute-force attacks or spamming, and protects the system from being overloaded by excessive traffic.
- **Encryption:** Encryption protects sensitive data by converting it into a secure, unreadable format that can only be accessed with the correct decryption key. It ensures that even if data is intercepted or compromised, it remains confidential and protected from unauthorized access.
### Why Security is Crucial
- **Protects User Data:** Security helps safeguard personal user information, ensuring it is not exposed or accessed by unauthorized individuals. This protects users’ privacy and builds trust in the system.
- **Securing Payments:** Security ensures that payment information, such as card or mobile money details, is protected from unauthorized access. This prevents fraud and misuse, giving users confidence that their transactions are safe.
- **Maintains System Integrity:** Strong security prevents data tampering, ensuring that information in the system remains accurate, consistent, and trustworthy.
- **Ensures Compliance with Regulations::** Many regions require businesses to follow data protection laws. Proper security helps avoid legal penalties and reputational damage.
## CI/CD Pipeline
CI/CD stands for **Continuous Integration** and **Continuous Deployment**. It refers to a set of automated steps that developers follow to build, test, and deliver new versions of software efficiently.
### Implementing CI/CD is important in this project because it:
- **Speeds up delivery** of new features and updates.
- **Automates testing and deployment**, reducing human error.
- **Improves code quality** through frequent integration and testing.
- **Enhances security** by identifying issues early in the development cycle.
- **Enables monitoring** of builds, deployments, and system behavior.
### The techologies we are going to use for CI/CI are:
- **Github actions:** Automates the CI/CD workflow by running tests, builds, and deployments whenever code is pushed or merged. It integrates directly with GitHub repositories, making automation easy to configure and maintain.
- **Docker:** Packages applications and their dependencies into lightweight, portable containers. In CI/CD, Docker ensures consistency across development, testing, and production environments.
- **Kubernetes:** Manages and orchestrates the deployment, scaling, and operation of containerized applications. In CI/CD, it automates the rollout and management of Docker containers in production.
- **Jenkins:** An open-source automation server that helps build, test, and deploy software. Jenkins supports custom pipelines and integrates with many tools to facilitate CI/CD workflows.
