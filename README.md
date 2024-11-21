# 📖 API Library Management System  

## 📓 Description 
*The **API Library Management System** is a RESTful application that facilitates user registration, authentication, and management of the library's book collection. The system allows users to securely sign in, add books to the library, and view the available books. It uses **JSON Web Token** for secure authentication and token-based authorization, ensuring that only authorized users can access specific features.*

## 🛠️ Software and Tools 
- **<span style="color: green;">MySQL:</span>** The database management system for storing user credentials and book. 
- **<span style="color: green;">JSON:</span>** Data format used for API request and response communication.
- **<span style="color: green;">Slim Framework:</span>** A lightweight framework designed for building RESTful APIs  
- **<span style="color: green;">PHP:</span>** Used for server-side development and application logic.   
- **<span style="color: green;">JWT:</span>** Provides secure user authentication and controls access to protected.  


# ⭐ Features

## 🛡️ JWT Middleware  
 *The system implements middleware to validate JWT tokens, ensuring all incoming requests are authenticated,extracting user information from valid tokens to process requests efficiently, and rejecting invalid or expired tokens to maintain security and integrity.*

## 🔑 Token Generation  
- The generateToken() function generates JWT tokens that expire after 1 hour.



# Endpoints

### Register a new User 👤

- **Method:** <span style="color: green;">POST
- **Endpoint:** *user/register*
- **Description:** This API endpoint facilitates user registration by accepting a username and password.

## 📄  Request and Response

### 📨 Request (JSON)  
```json
{
    "username": "Mugiwara Luffy",
    "password": "Meshii"
}
```
### ✅ Response on Success
```json
{
    "status": "success",
    "data": null
}
```
### ❌ Response on Failure
```json
{
    "status": "fail",
    "data": "Username already exists"
}
```

## 🔑 Authenticate a User  

- **Method:** <span style="color: green;">POST</span>  
- **Endpoint:** *user/authenticate*  
- **Description:** This API endpoint authenticates user credentials by validating the provided username and password against the database. Upon successful authentication, it generates and returns a secure JSON Web Token (JWT), granting the user access to protected resources.

---

## 📄 Request and Response    

### 📨 Sample Request (JSON)  
```json
{
    "username": "Mugiwara Luffyy",
    "password": "Meshiii"
}
```
Here's the information formatted in Markdown:

markdown
Copy code
## 🔑 Authenticate a User  

### 🌐 Endpoint  
**`POST /user/authenticate`**  

### 📜 Description  
This API endpoint authenticates a user by validating their provided credentials (username and password) against the database. Upon successful verification, a **JSON Web Token (JWT)** is generated and returned, allowing the user to access protected resources.  

---

### 📨 Sample Request (JSON)  
```json
{
    "username": "example_username",
    "password": "example_password"
}
```
### ✅ Response
```json
{
    "status": "success",
    "token": "e1eq23JhbGUi21r5gH6BhbqeVCJ9...",
    "data": null
}
```
### ❌ Response on Failure
```json
{
    "status": "fail",
    "data": {
        "title": "Invalid input data"
    }
}
```
### ❌If the Username is incorrect
```json
{
    "status": "fail",
    "data": {
        "title": "Incorrect username"
    }
}
```
### ❌If the Password is incorrect
```json
{
    "status": "fail",
    "data": {
        "title": "Incorrect password"
    }
}
```

## Display Users 👥  

- **Method:** <span style="color: blue;">GET</span>  
- **Endpoint:** *user/display*  
- **Description:** This API endpoint provides a list of all registered users. To access this endpoint, clients must include an Authorization header containing a valid **JSON Web Token (JWT)**. On successful execution, the response includes the user data and a refreshed JWT for maintaining secure and uninterrupted access.

## 📄 Request and Response

### Request
```json
```
### ✅ Response on Success  
```json
{
    "status": "success",
    "data": [
        {
            "userId": 1,
            "username": "username 1"
        },
        {
            "userId": 2,
            "username": "username 2"
        }
    ],
    "token": "eyJ1c2VySWQiOjEsInVzf"
}
```
### ❌ Response on Failure
```json
{
    "status": "fail",
    "data": "null"
}
```


## Adding Author and Books ✍️  

- **Method:** <span style="color: green;">POST</span>  
- **Endpoint:** *author/add*  
- **Description:** This API endpoint allows users to add a new author along with their associated books. It validates the author's name to ensure it’s not empty and checks that the author does not already exist in the database before proceeding with the insertion. Upon successful addition, the system generates a new **JWT (JSON Web Token)** and revokes the previous one for enhanced security.  

---

## 📄 Request and Response  

### 📨 Request (JSON)  
```json
{
    "name": "Nosi Balasi",
    "book": "Sino Basila"
}
```
### ✅ Response on Success
```json 
{
    "status": "success",
    "token": "Jk2aQhdKTywn2tYbH...",
    "data": null
}
```
### ❌ Response on Failure
```json
{
    "status": "fail",
    "data": "Error"
}
```

## Deleting Author and Books 🗑️

- **Method:** <span style="color: red;">DELETE</span>  
- **Endpoint:** *author/delete*  
- **Description:** This API endpoint allows users to delete an author and their associated books by providing the author's **ID**. It first checks if the author exists in the database using the ID. If found, it proceeds with the deletion. After a successful deletion, the system generates a new **JWT (JSON Web Token)**, and the previous token is revoked for enhanced security.

---

## 📄 Sample API Request and Response  

### ✅ Response on Success

### 📨 Request (JSON)  
```json
{
    "authorId": 1
}

{
    "status": "success",
    "token": "t4trq8IrwJk2aQhdKTywn2tYbH.",
    "data": null
}
```
### ❌ Response on Failure
```json
{
    "status": "fail",
    "data": "Author with the provided ID does not exist"
}
```

## Display Author and Books 📚  

- **Method:** <span style="color: blue;">GET</span>  
- **Endpoint:** *author/display*  
- **Description:** This API endpoint retrieves and displays an author's details (name) along with the associated books, based on the provided **author ID**. It requires an **Authorization** header with a valid **JWT (JSON Web Token)** for access. If the author exists, the response includes the author's name and their list of books.

---

## 📄 Request and Response  

### 📨 Request (JSON)  
```json
{
  
}
```
### ✅ Response on Success
```json
{
    "status": "success",
    "data": {
        "authorId": 123,
        "name": "Author Name",
        "books": [
            {
                "title": "Book Title 1"
            },
            {
                "title": "Book Title 2"
            }
        ]
    },
    "token": "tGzv3JOkF0XG5Qx2TlKWIA..."
}
```

### ❌ Response on Failure
```json
```

## Update Author and Books ✏️  

- **Method:** <span style="color: orange;">PUT</span>  
- **Endpoint:** *author/update*  
- **Description:** This API endpoint allows users to update an existing author's name and associated books based on the **author ID**. The request requires the **author ID**, along with the new **author name** and the list of **books** (titles) to be updated. It checks whether the author exists in the database before proceeding with the update. Once the update is successful, the system generates a new **JWT (JSON Web Token)** and revokes the previous one to maintain secure access.

## 📄 Request and Response 
```json
{
    "authorId": 123,
    "name": "Updated Author Name",
    "books": [
        {
            "title": "Updated Book Title 1"
        },
        {
            "title": "Updated Book Title 2"
        }
    ]
}
```
### ✅ Response on Success
```json
{
    "status": "success",
    "token": "tGzv3JOkF0XG5Qx2TlKWIA...",
    "data": null
}
```

### ❌ Response on Failure
```json
```
