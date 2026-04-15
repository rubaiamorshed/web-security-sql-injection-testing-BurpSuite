# web-security-sql-injection-testing-BurpSuite
Performed SQL injection testing using Burp Suite to exploit vulnerabilities for data extraction and authentication bypass.
# 🔐 Web Application Penetration Testing: SQL Injection Exploitation via Burp Suite

## 📌 Overview

Conducted web application penetration testing using Burp Suite to identify and exploit SQL injection vulnerabilities. The assessment demonstrated the ability to retrieve restricted data and bypass authentication mechanisms due to improper input validation.

---

## 🎯 Objectives

* Identify SQL injection vulnerabilities
* Exploit query manipulation for data extraction
* Perform authentication bypass
* Assess impact of insecure input handling

---

## 🛠️ Tools Used

* Burp Suite
* Web Browser

---

## 🔍 Lab 1: SQL Injection in WHERE Clause (Data Extraction)

### 📖 Description

A SQL injection vulnerability was identified in the product category filter. The application executed the following query:

```sql
SELECT * FROM products WHERE category = 'Gifts' AND released = 1;
```

---

### ⚔️ Exploitation Steps

1. Navigated to the target web application <img width="961" height="528" alt="Screenshot 2026-04-15 181343" src="https://github.com/user-attachments/assets/86b03857-1d08-4a55-bf2e-f2bdf49fcf3b" />

2. Selected the **“Gifts”** category from the filter <img width="947" height="507" alt="Screenshot 2026-04-15 181359" src="https://github.com/user-attachments/assets/2d34aba9-512c-45ee-bb25-832dd2946655" />

3. Intercepted and modified the `category` parameter in the request <img width="939" height="516" alt="Screenshot 2026-04-15 181412" src="https://github.com/user-attachments/assets/df7c11a7-df95-4ac4-8c40-5c05ea6b4c42" />

4. Injected payload:

   ```
   ' OR 1=1-- 

   ```
   <img width="940" height="503" alt="Screenshot 2026-04-15 181426" src="https://github.com/user-attachments/assets/25abf0ee-2888-453b-84b3-0e40e689270c" />
5. Forwarded the modified request 

---

### 🚨 Result

* The query logic was altered to return all records
* Unreleased (hidden) products were displayed 
<img width="963" height="464" alt="Screenshot 2026-04-15 181438" src="https://github.com/user-attachments/assets/009935bb-69cb-4b18-9bdd-7875f8194ec2" />

---

### 💡 Impact

This vulnerability allows attackers to:

* Access restricted or hidden data
* Bypass application logic controls
* Potentially extract sensitive database information

---

## 🔍 Lab 2: SQL Injection Authentication Bypass

### 📖 Description

A SQL injection vulnerability was discovered in the login functionality, allowing authentication bypass.

---

### ⚔️ Exploitation Steps

1. Navigated to the **My Account** login page
2. Intercepted the login request
3. Modified the username parameter with payload:

   ```
   administrator'--
   ```
   

4. Entered arbitrary input in the password field <img width="961" height="454" alt="Screenshot 2026-04-15 181949" src="https://github.com/user-attachments/assets/0c55bb74-ddcd-493f-9e06-76467cda4cfd" />
5. Submitted the request

---

### 🚨 Result

* Successfully logged in as **administrator**
* Authentication controls were bypassed
<img width="943" height="474" alt="Screenshot 2026-04-15 182004" src="https://github.com/user-attachments/assets/c3b190a8-2303-4bd8-af6e-96dd18913ec5" />

---

### 💡 Impact

* Unauthorized access to privileged accounts
* Compromise of application security
* Potential full system takeover

---

## ⚠️ Key Security Issue

Authentication was bypassed due to improper input validation in the login query. The injected username disabled password verification, allowing arbitrary input to be accepted as valid credentials.

---

## 🛡️ Recommendations

* Implement parameterized queries (prepared statements)
* Use input validation and sanitization
* Apply least privilege access control
* Deploy Web Application Firewall (WAF)
* Perform regular security testing

---

## 📚 Conclusion

This assessment highlights the critical risks of SQL injection vulnerabilities in web applications. Proper input validation and secure coding practices are essential to prevent data exposure and unauthorized access.

---

## 👩‍💻 Author

Rubaia Morshed
Cybersecurity Analyst (Student)
