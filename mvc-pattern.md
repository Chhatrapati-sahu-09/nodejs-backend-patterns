# MVC Pattern in Node.js

The MVC (Model–View–Controller) pattern is a common architectural pattern used to organize backend applications.

It separates application logic into three main components:

- Model
- View
- Controller

This separation helps keep the code organized and maintainable.

---

## Model

The model handles data and database logic.

Responsibilities:

- interacting with the database
- defining data schemas
- performing data operations

Example:

```javascript
const mongoose = require("mongoose");

const userSchema = new mongoose.Schema({
  name: String,
  email: String
});

module.exports = mongoose.model("User", userSchema);
```

---

## Controller

Controllers handle incoming HTTP requests and send responses.

Responsibilities:

- receiving request data
- calling business logic
- returning responses

Example:

```javascript
const User = require("../models/user");

exports.getUsers = async (req, res) => {
  const users = await User.find();
  res.json(users);
};
```

---

## Routes

Routes define the API endpoints and connect them to controllers.

Example:

```javascript
const express = require("express");
const router = express.Router();
const userController = require("../controllers/userController");

router.get("/users", userController.getUsers);

module.exports = router;
```

---

## Example Project Structure

```
project
│
├── controllers
│   └── userController.js
│
├── models
│   └── user.js
│
├── routes
│   └── userRoutes.js
│
└── server.js
```

---

## Benefits of MVC

- separation of concerns
- cleaner code structure
- easier maintenance
- improved scalability
