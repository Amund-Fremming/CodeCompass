**Function Level Access Control**
- Use deny by default principle
- Use functions to check if a user is auth

**Sensitive data exposure**
- Protect information
- Has and salt passwords
- Encrypt data during transport and at rest
- Encrypt all data in transit sith secure protocols like TLS
- For data that dont nedd to be hashed use symmetric encryption
- Use Argon2, bcrypt or PBKDF2 for password hashing (Has auto salting)
- Salt, pepper and use work factors for passwords

**SQL injection**
- Never concatenate user-controllable input with application SQL sendt to db, use parameterized queries:
```sql
insert_user = db.prepare "INSERT INTO users (name, age) VALUES (?, ?)"
insert_user.execute (request_user_name, request_user_age)
```
- Use allowlist validation on all user input


