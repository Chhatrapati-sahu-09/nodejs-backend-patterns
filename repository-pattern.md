# Repository Pattern

The Repository Pattern is used to separate database access logic from the rest of the application.

Instead of interacting with the database directly inside controllers or services, a repository layer is responsible for handling all data operations. This makes the codebase more organized and easier to maintain.

---

## Architecture

A typical request flow using the repository pattern looks like this:

```
Client Request
      │
      ▼
Route
      │
      ▼
Controller
      │
      ▼
Service
      │
      ▼
Repository
      │
      ▼
Database
```

Explanation:

- **Controller** handles HTTP requests and responses.
- **Service** contains business logic.
- **Repository** manages database queries.
- **Database** stores application data.

---

## Example Project Structure

```
project
│
├── controllers
│   └── userController.js
│
├── services
│   └── userService.js
│
├── repositories
│   └── userRepository.js
│
├── models
│   └── userModel.js
│
├── routes
│   └── userRoutes.js
│
└── server.js
```

---

## Example Repository

The repository handles all database operations.

```javascript
const User = require("../models/userModel");

async function findAllUsers() {
  return await User.find();
}

module.exports = {
  findAllUsers
};
```

Responsibilities of the repository layer:

- interacting with the database
- performing CRUD operations
- returning data to the service layer

---

## Service Using Repository

The service layer calls repository functions to perform data operations.

```javascript
const userRepository = require("../repositories/userRepository");

async function getUsers() {
  const users = await userRepository.findAllUsers();
  return users;
}

module.exports = {
  getUsers
};
```

The service layer focuses on business logic while the repository handles database access.

---

## Controller Using Service

```javascript
const userService = require("../services/userService");

exports.getUsers = async (req, res) => {

  try {

    const users = await userService.getUsers();

    res.status(200).json(users);

  } catch (error) {

    res.status(500).json({
      message: "Error fetching users"
    });

  }

};
```

---

## Benefits of Repository Pattern

- separates database logic from business logic
- centralizes database operations
- improves code maintainability
- makes testing easier
- allows switching databases with minimal code changes
- improves scalability of backend applications

---

## When to Use Repository Pattern

The repository pattern is useful in:

- large backend applications
- enterprise-level systems
- microservice architectures
- applications that may change databases in the future
