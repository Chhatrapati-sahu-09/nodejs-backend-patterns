# Dependency Injection in Node.js

Dependency Injection (DI) is a design pattern used to make applications modular and testable.

Instead of creating dependencies inside a module, they are passed as parameters.

---

## Without Dependency Injection

```javascript
const userRepository = require("./repository");

function getUsers() {
  return userRepository.findAll();
}
```

---

## With Dependency Injection

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

## Benefits

- easier testing
- better modularity
- flexible architecture
