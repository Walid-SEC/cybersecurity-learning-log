# Software Basics

## Key Topics
- Data representation (binary, decimal, hex)
- Data encoding (ASCII, Unicode, Base64)
- Python basics with simple demos
- JavaScript basics
- Database & SQL basics

---

## Introduction — What Is Software?

Software is a set of instructions that tells the computer what to do. It sits on top of the OS and uses hardware resources to perform tasks.

| Type                  | Description                                       | Examples                        |
|-----------------------|---------------------------------------------------|---------------------------------|
| System Software       | Manages hardware and provides a platform for apps | Operating systems, drivers      |
| Application Software  | Performs tasks for the user                       | Browsers, editors, games        |
| Programming Languages | Used to write software                            | Python, JavaScript, C, Java     |

At the lowest level, all software and data is just **numbers** — and all numbers are stored as **binary**.

---

## Data Representation

### Binary (Base-2)
- Computers only understand **1s and 0s** — called bits
- A group of 8 bits = **1 byte**
- Everything — text, images, video, code — is ultimately stored as binary

| Unit  | Size          |
|-------|---------------|
| 1 Bit | A single 0 or 1 |
| 1 Byte | 8 bits       |
| 1 KB  | 1,024 bytes   |
| 1 MB  | 1,024 KB      |
| 1 GB  | 1,024 MB      |
| 1 TB  | 1,024 GB      |

### Converting Binary → Decimal
Each position represents a power of 2, starting from the right:

```
Binary:   1  0  1  1
Position: 8  4  2  1

= (1×8) + (0×4) + (1×2) + (1×1) = 11
```

### Decimal → Binary (Divide by 2 Method)
```
11 ÷ 2 = 5 remainder 1
 5 ÷ 2 = 2 remainder 1
 2 ÷ 2 = 1 remainder 0
 1 ÷ 2 = 0 remainder 1

Read remainders bottom to top → 1011
```

### Hexadecimal (Base-16)
Hex uses 16 symbols: `0–9` and `A–F`. One hex digit = 4 bits — a compact way to write binary.

| Decimal | Binary   | Hex |
|---------|----------|-----|
| 0       | 0000     | 0   |
| 9       | 1001     | 9   |
| 10      | 1010     | A   |
| 15      | 1111     | F   |
| 255     | 11111111 | FF  |

**Common uses of hex:**
- Memory addresses: `0x7FFF`
- Colour codes: `#FF5733`
- MAC addresses: `A1:B2:C3:D4:E5:F6`
- Hash values: `5d41402abc4b2a76b9719d911017c592`

---

## Data Encoding

Encoding converts data into a different format for storage or transmission. It is **not encryption** — it can be reversed without a key.

### ASCII
- Maps characters to numbers (0–127)
- Covers English letters, digits, and basic symbols
- `A = 65`, `a = 97`, `0 = 48`, `space = 32`

```
H  E  L  L  O
72 69 76 76 79
```

### Unicode (UTF-8)
- Extends ASCII to support every language and symbol in the world
- UTF-8 is the dominant encoding on the web
- Backwards compatible with ASCII for the first 127 characters
- `€ = U+20AC`, `😊 = U+1F60A`

### Base64
- Encodes binary data as printable ASCII characters
- Used to safely send binary data (files, images) over text-based systems
- Output uses: `A–Z`, `a–z`, `0–9`, `+`, `/`
- **Not encryption** — anyone can decode it instantly

```
Text:    Hello
Base64:  SGVsbG8=
```

### Encoding vs Hashing

| Method   | Purpose                                   | Reversible? |
|----------|-------------------------------------------|-------------|
| ASCII    | Represent text as numbers                 | Yes         |
| Unicode  | Represent all world languages and symbols | Yes         |
| Base64   | Encode binary as safe printable text      | Yes         |
| Hashing  | Verify integrity (SHA256, MD5)            | No          |

---

## Python Basics

Python is one of the most beginner-friendly and widely used languages — especially in data, automation, and cybersecurity.

### Variables & Output

```python
# Variables
name = "Alice"
age = 25
is_admin = True

# Print output
print("Hello,", name)
print(f"Name: {name}, Age: {age}")   # f-string formatting

# User input
user = input("Enter your name: ")
```

### Data Types

| Type    | Example            |
|---------|--------------------|
| String  | `"hello"`          |
| Integer | `42`               |
| Float   | `3.14`             |
| Boolean | `True` / `False`   |
| List    | `[1, 2, 3]`        |
| Dict    | `{"key": "value"}` |

### Control Flow

```python
# If / else
age = 18
if age >= 18:
    print("Adult")
else:
    print("Minor")

# For loop
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

# While loop
count = 0
while count < 3:
    print(count)
    count += 1
```

### Functions

```python
def greet(name):
    return f"Hello, {name}!"

print(greet("Bob"))   # Hello, Bob!
```

### Simple Demo — Password Checker

```python
stored_password = "secure123"
attempts = 0

while attempts < 3:
    guess = input("Enter password: ")
    if guess == stored_password:
        print("Access granted!")
        break
    else:
        print("Incorrect. Try again.")
        attempts += 1
else:
    print("Too many failed attempts. Locked out.")
```

### Useful Modules for Security Work

```python
import os           # interact with the OS
import hashlib      # hashing (md5, sha256)
import requests     # make HTTP requests
import socket       # low-level networking

# Example: Hash a string with SHA256
import hashlib
h = hashlib.sha256("password".encode()).hexdigest()
print(h)
# → 5e884898da28047151d0e56f8dc6292773603d0d6aabbdd62a11ef721d1542d8
```

---

## JavaScript Basics

JavaScript is the language of the web — it runs in the browser and makes pages interactive. It also runs server-side via Node.js.

### Variables & Output

```javascript
let name = "Alice";        // block-scoped, can be reassigned
const age = 25;            // block-scoped, cannot be reassigned
var isAdmin = false;       // function-scoped, older style — avoid

console.log("Hello, " + name);
console.log(`Name: ${name}, Age: ${age}`);   // template literals
```

### Data Types

| Type      | Example          |
|-----------|------------------|
| String    | `"hello"`        |
| Number    | `42`, `3.14`     |
| Boolean   | `true` / `false` |
| Array     | `[1, 2, 3]`      |
| Object    | `{key: "value"}` |
| Null      | `null`           |
| Undefined | `undefined`      |

### Control Flow

```javascript
// If / else
let age = 20;
if (age >= 18) {
    console.log("Adult");
} else {
    console.log("Minor");
}

// For loop
let fruits = ["apple", "banana", "cherry"];
for (let i = 0; i < fruits.length; i++) {
    console.log(fruits[i]);
}

// forEach (modern, cleaner)
fruits.forEach(fruit => console.log(fruit));
```

### Functions

```javascript
// Standard function
function greet(name) {
    return `Hello, ${name}!`;
}

// Arrow function (modern preferred)
const greet = (name) => `Hello, ${name}!`;

console.log(greet("Bob"));   // Hello, Bob!
```

### DOM Interaction (Browser Only)

```javascript
// Change element content
document.getElementById("title").innerText = "New Title";

// React to a button click
document.getElementById("btn").addEventListener("click", () => {
    alert("Button clicked!");
});
```

### Python vs JavaScript

| Feature     | Python                    | JavaScript                    |
|-------------|---------------------------|-------------------------------|
| Runs on     | Server / local machine    | Browser + server (Node.js)    |
| Syntax      | Indentation-based         | Curly braces `{}`             |
| Main use    | Scripting, data, security | Web frontend & backend        |
| Typing      | Dynamic                   | Dynamic                       |
| Best for    | Automation, pentesting    | Web development               |

---

## Database & SQL Basics

A **database** stores structured data so applications can create, read, update, and delete it efficiently (CRUD).

### Types of Databases

| Type           | Structure                 | Examples                         |
|----------------|---------------------------|----------------------------------|
| Relational     | Tables with rows/columns  | MySQL, PostgreSQL, SQLite, MSSQL |
| Non-relational | Documents, key-value      | MongoDB, Redis, DynamoDB         |

### Core SQL Commands

```sql
-- Retrieve all records
SELECT * FROM users;

-- Retrieve specific columns
SELECT username, email FROM users;

-- Filter with a condition
SELECT * FROM users WHERE username = 'admin';

-- Insert a new record
INSERT INTO users (username, email, password)
VALUES ('alice', 'alice@email.com', 'hashed_pw');

-- Update a record
UPDATE users SET email = 'new@email.com' WHERE username = 'alice';

-- Delete a record
DELETE FROM users WHERE username = 'alice';
```

### Creating a Table

```sql
CREATE TABLE users (
    id        INT PRIMARY KEY AUTO_INCREMENT,
    username  VARCHAR(50) NOT NULL,
    email     VARCHAR(100),
    password  VARCHAR(255),
    is_admin  BOOLEAN DEFAULT FALSE
);
```

### Useful Clauses

| Clause     | Purpose                                      |
|------------|----------------------------------------------|
| `WHERE`    | Filter rows by condition                     |
| `ORDER BY` | Sort results (`ASC` / `DESC`)                |
| `LIMIT`    | Cap the number of rows returned              |
| `JOIN`     | Combine rows from two or more tables         |
| `LIKE`     | Pattern match (`%` = wildcard)               |
| `GROUP BY` | Group rows for aggregation functions         |

```sql
-- Latest 10 users
SELECT * FROM users ORDER BY id DESC LIMIT 10;

-- Search by pattern
SELECT * FROM users WHERE username LIKE 'ad%';
```

### SQL Injection — Security Relevance

When user input is not sanitised and is inserted directly into a query, attackers can manipulate it:

```sql
-- Normal login query
SELECT * FROM users WHERE username = 'alice' AND password = 'password123';

-- Attacker inputs: username = ' OR '1'='1
SELECT * FROM users WHERE username = '' OR '1'='1' AND password = '';
-- '1'='1' is always true → bypasses authentication entirely
```

**Prevention:** Always use **parameterised queries / prepared statements** — never build SQL from raw user input.

---

## Takeaways
- All data is binary at its core — hex and encodings are just human-friendly representations
- Encoding (ASCII, Base64) is not encryption — it can always be reversed
- Python is the dominant language in security tooling, scripting, and automation
- JavaScript runs the web — understanding it is key for both web dev and attacking web apps
- SQL is how applications talk to databases — and SQL injection is one of the most common web vulnerabilities
- Always use parameterised queries to prevent SQL injection
