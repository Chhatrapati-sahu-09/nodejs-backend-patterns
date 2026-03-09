# Repository Pattern

The repository pattern abstracts database operations.

Instead of accessing the database directly in controllers or services, a repository manages all data access.

---

## Architecture

```
Controller → Service → Repository → Database
```

---

## Example Repository

```javascript
const User = require("../models/user");

function findAllUsers() {
  return User.find();
}

module.exports = { findAllUsers };
```

---

## Service Using Repository

```javascript
const userRepository = require("../repositories/userRepository");

async function getUsers() {
  return await userRepository.findAllUsers();
}
```

---

## Benefits

- database logic is centralized
- easier to switch databases
- cleaner code structure
