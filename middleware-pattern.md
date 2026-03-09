# Middleware Pattern in Node.js

Middleware functions run during the request–response cycle in Express applications.

They have access to:

- request object (req)
- response object (res)
- next middleware function (next)

---

## Basic Middleware Example

```javascript
app.use((req, res, next) => {
  console.log("Request received");
  next();
});
```

This middleware logs every request.

---

## Authentication Middleware Example

```javascript
function authMiddleware(req, res, next) {

  const token = req.headers.authorization;

  if (!token) {
    return res.status(401).json({ message: "Unauthorized" });
  }

  next();
}
```

---

## Middleware Usage

```
Client → Middleware → Route Handler → Response
```

---

## Common Uses

Middleware is commonly used for:

- authentication
- logging
- request validation
- error handling
