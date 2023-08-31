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
- Stop writing dynamic queries using string concatenation
- Prevent user-supplied input that contains malicious SQL from affecting the logic of the executed query
- use prepared statements or parameterized queries
```sql
Set preparedStatement = "SELECT users FROM database WHERE user = {placeholderUser}"
Set placeholderUser of preparedStatement to inputUserValue
Call sql.executePreparedStatement with argument preparedStatement
Save it as results
```
- ORM (Object-Relational Mapping) siolutions map database tables to programming language objects in a more secure way if implemented correct

**Insufficent Validation**
- Consider all potential areas where input can enter the software and assume all input is malicious
Allowlist with valid parameters
Security checks on client and server side

**Disabled Security Features**
- IMportant that flags and headers are put on.

**Using Known Vulnerable Components**
- Manage security of third-partyy software and components, their versions and dependencies


