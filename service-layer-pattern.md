# Service Layer Pattern

The Service Layer Pattern is used to separate business logic from controllers in backend applications.

In a well-structured application, controllers should only handle HTTP requests and responses. The actual business logic should be placed in a separate service layer. This improves code organization and makes the application easier to maintain.

---

## Architecture

A typical request flow using the service layer pattern looks like this:

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
Service Layer
      │
      ▼
Database / Model
```

Explanation:

- **Route** maps the endpoint to the controller.
- **Controller** receives the request and sends the response.
- **Service Layer** contains the business logic.
- **Model / Database** handles data storage.

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
├── models
│   └── userModel.js
│
├── routes
│   └── userRoutes.js
│
└── server.js
```

---

## Example Service

The service contains the main business logic of the application.

```javascript
const User = require("../models/userModel");

async function getAllUsers() {
  const users = await User.find();
  return users;
}

module.exports = {
  getAllUsers
};
```

Responsibilities of the service layer:

- implement business logic
- interact with models
- process data before sending to controllers

---

## Controller Using Service

The controller calls the service and returns the response to the client.

```javascript
const userService = require("../services/userService");

exports.getUsers = async (req, res) => {

  try {

    const users = await userService.getAllUsers();

    res.status(200).json(users);

  } catch (error) {

    res.status(500).json({
      message: "Failed to fetch users"
    });

  }

};
```

The controller should focus on:

- handling requests
- calling services
- returning responses

---

## Benefits of Service Layer Pattern

- separates business logic from controllers
- improves code readability
- makes the application easier to maintain
- allows business logic to be reused across controllers
- simplifies testing of application logic
- improves scalability of backend systems

---

## When to Use This Pattern

The service layer pattern is useful in:

- REST API applications
- microservices architecture
- large backend systems
- applications with complex business logic
