
# Service List Microservice

## Overview

The `ServiceListMicroservice` project is a Java-based microservice designed to manage and provide listings of various services. This microservice allows querying, filtering, and managing lists of services, facilitating easy access and organisation of available services. It integrates with databases to store service details and uses message queues for handling list-related tasks.

## Related Projects

- [LEI Schema](https://github.com/mahirgamal/LEI-schema): Defines the standardized schema for livestock event information.
- [LEISA](https://github.com/mahirgamal/LEISA): The architecture framework for sharing livestock event information.
- [LEI2JSON](https://github.com/mahirgamal/LEI2JSON): A tool to convert LEI data into JSON format for easy processing.
- [AgriVet Treatment Grapher](https://github.com/mahirgamal/AgriVet-Treatment-Grapher): A Python-based tool designed to visualise treatment data for animals, helping veterinarians and researchers analyse treatment patterns and dosages.
- [Cattle Location Monitor](https://github.com/mahirgamal/Cattle-Location-Monitor): A system that monitors cattle location using GPS data to provide real-time insights into cattle movements and positioning.
  
## Features

- **Service Listing**: Provides functionalities for listing available services, including search and filtering options.
- **Database Integration**: Uses MySQL for storing and retrieving service listing information.
- **Message Queuing**: Integrates with message queues to handle asynchronous processing of listing events.
- **REST API**: Exposes RESTful endpoints for querying and managing service listings.

## Architecture

The application is structured using a modular architecture, aligning with Domain-Driven Design (DDD) principles to ensure scalability, maintainability, and alignment with business logic. The main components include:

### 1. Function Layer (`com.function`)

- **Purpose**: Acts as the Application Layer in DDD. This layer contains the entry points to the application, handling incoming requests for service listings, searching, and filtering.

- **Components**:
  - **`Function.java`**: Contains core functions that serve as the entry point for processing requests related to service listings.
  - **`User.java`**: Manages user-related operations that interact with service listings, possibly including user-specific filtering or access control.

### 2. Domain Layer (`com.domain`)

- **Purpose**: Contains the business logic for managing service listings, ensuring data integrity, and providing business rules for listing management.

- **Components**:
  - **`ListingService.java`**: Represents the domain service responsible for handling business logic related to service listings, such as retrieving, sorting, and filtering service data.

### 3. Infrastructure Layer (`src/main/resources`)

- **Purpose**: Supports the infrastructure needs of the application, handling configurations, database connections, and integrations with external systems like message queues.

- **Components**:
  - **`mysqlconfig.json`**: Configuration for connecting to the MySQL database, managing service listing data.
  - **`rabbitmqconfig.json`**: Configuration for RabbitMQ, used to handle asynchronous messaging and listing event processing.

## Project Structure

```
/ServiceListMicroservice
│
├── .git                      # Git configuration directory
├── .gitignore                # Git ignore file
├── host.json                 # Configuration file for hosting on Azure Functions
├── local.settings.json       # Local environment settings file
├── pom.xml                   # Project Object Model file for Maven
├── src
│   ├── main
│   │   ├── java
│   │   │   └── com
│   │   │       └── function
│   │   │           ├── Function.java             # Core functions related to service listing operations
│   │   │           └── User.java                 # User management logic interacting with service listings
│   │   │
│   │   └── resources
│   │       ├── mysqlconfig.json                 # MySQL database configuration
│   │       └── rabbitmqconfig.json              # RabbitMQ configuration
│   │
│   └── test
│       └── java
│           └── com
│               └── function
│                   ├── FunctionTest.java         # Unit tests for Function class
│                   └── HttpResponseMessageMock.java # Mocking HTTP responses for tests
│
└── target                      # Directory for compiled classes and build artifacts
```

## Requirements

- **Java 8** or higher
- **Maven** for building the project and managing dependencies
- **MySQL** for database operations
- **RabbitMQ** for message queuing

## Setup

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/mahirgamal/ServiceListMicroservice.git
   ```
2. **Navigate to the Project Directory:**
   ```bash
   cd ServiceListMicroservice
   ```
3. **Configure Database and Message Queue:**
   - Update the `mysqlconfig.json` file with your MySQL connection details.
   - Update the `rabbitmqconfig.json` file with your RabbitMQ server details.

4. **Build the Project using Maven:**
   ```bash
   mvn clean install
   ```
5. **Run the Application:**
   ```bash
   java -jar target/ServiceListMicroservice-1.0-SNAPSHOT.jar
   ```

## Usage

1. **Service Listing:**
   - Use the `Function` class to handle requests for listing services.
   - Example usage:
     ```java
     Function.listServices(filters);
     ```

2. **User Interaction:**
   - Use the `User` class to manage user interactions with service listings.
   - Example usage:
     ```java
     User.getUserSpecificListings(userId);
     ```

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.

## Acknowledgments

This work originates from the Trakka project and builds on the existing TerraCipher Trakka implementation. We appreciate the support and resources provided by the Trakka project team. Special thanks to Dave Swain and Will Swain from TerraCipher for their guidance and assistance throughout this project

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](https://github.com/mahirgamal/ServiceListMicroservice/blob/main/LICENSE) file for details.

## Contact

If you have any questions, suggestions, or need assistance, please don't hesitate to contact us at [mhabib@csu.edu.au](mailto:mhabib@csu.edu.au) or [akabir@csu.edu.au](mailto:akabir@csu.edu.au).
