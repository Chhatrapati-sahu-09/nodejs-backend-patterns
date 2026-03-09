# Service Layer Pattern

The service layer pattern separates business logic from controllers.

Controllers handle HTTP requests while services handle application logic.

---

## Architecture

```
Route → Controller → Service → Database
```

---

## Example Service

```javascript
const User = require("../models/user");

async function getAllUsers() {
  return await User.find();
}

module.exports = { getAllUsers };
```

---

## Controller Using Service

```javascript
const userService = require("../services/userService");

exports.getUsers = async (req, res) => {
  const users = await userService.getAllUsers();
  res.json(users);
};
```

---

## Benefits

- reusable business logic
- cleaner controllers
- easier testing
- better project organization
