### JWT Summary

- **Generate Token**:
  Use `jwt.sign(payload, secretKey, options)`
  → Example: `const token = jwt.sign({ id, name }, "secretKey", { expiresIn: "1h" });`

- **Verify Token**:
  Use `jwt.verify(token, secretKey)`
  → Example: `const decoded = jwt.verify(token, "secretKey");`

- **Decode Token Without Verification**:
  Use `jwt.decode(token)`
  → Example: `const decoded = jwt.decode(token);`
