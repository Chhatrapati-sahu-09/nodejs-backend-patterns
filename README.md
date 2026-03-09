# Node.js Backend Patterns

![Node.js](https://img.shields.io/badge/Node.js-Backend-green)
![Express](https://img.shields.io/badge/Express.js-Framework-lightgrey)
![JavaScript](https://img.shields.io/badge/JavaScript-Language-yellow)

## Overview

This repository demonstrates commonly used backend architecture patterns in Node.js applications.

Modern backend systems require clean architecture, maintainable code, and scalable design patterns. This repository provides explanations and examples of patterns widely used in production Node.js applications.

---

## Table of Contents

- MVC Pattern
- Middleware Pattern
- Service Layer Pattern
- Repository Pattern
- Dependency Injection
- Error Handling
- Project Structure
- Environment Configuration

---

## MVC Pattern

The MVC (Model-View-Controller) pattern separates application logic into three components.

Model  
Handles database logic.

View  
Handles UI (mainly used in frontend frameworks).

Controller  
Handles requests and responses.

Example structure:

```
controllers/
models/
routes/
server.js
```

---

## Middleware Pattern

Middleware functions execute during the request-response cycle.

Example:

```javascript
app.use((req, res, next) => {
  console.log("Request received");
  next();
});
```

Middleware is commonly used for:

- logging
- authentication
- validation

---

## Service Layer Pattern

The service layer contains business logic separated from controllers.

Example:

```
controllers → services → models
```

Benefits:

- cleaner controllers
- reusable logic
- easier testing

---

## Repository Pattern

The repository pattern abstracts database logic.

Instead of calling the database directly in controllers, the repository manages data operations.

Example:

```
controllers → services → repositories → database
```

---

## Dependency Injection

Dependency injection helps make applications modular and easier to test.

Example:

```javascript
function userService(userRepository) {
  return {
    getUsers() {
      return userRepository.findAll();
    }
  };
}
```

---

## Best Practices

Recommended practices for Node.js backend development:

- use environment variables
- implement centralized error handling
- separate business logic from controllers
- structure project folders properly

---

## Learning Goals

This repository helps developers understand:

- scalable backend architecture
- Node.js project organization
- common backend design patterns
- best practices for production applications

---

## Contributing

Contributions are welcome.

You can contribute by:

- adding more backend patterns
- improving documentation
- adding example projects
