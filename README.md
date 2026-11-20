# API Tests — Part C (Postman Collection)

## Overview
This folder contains the Postman collection for automated API testing of the [JSONPlaceholder](https://jsonplaceholder.typicode.com/users) Users API.

## Folder Structure

## API Under Test
**Base URL:** `https://jsonplaceholder.typicode.com`

## Test Scenarios

### Step 1 — GET All Users
- **Endpoint:** `GET /users`
- **Validations:**
  - Status code is 200
  - Response is a non-empty array
  - Response contains user information
  - Each user has `id`, `name`, and `email`
- **Post-response:** Saves first user's `id` into `userId` variable

### Step 2 — Save User ID
- After GET /users runs, the first user's `id` is automatically saved as `userId` in the environment variable for use in subsequent requests.

### Step 3 — GET User by ID
- **Endpoint:** `GET /users/{{userId}}`
- **Validations:**
  - Status code is 200
  - Returned object has the correct `id`
  - User has `id`, `name`, and `email`

### Step 4 — PUT Update User
- **Endpoint:** `PUT /users/{{userId}}`
- **Dynamic Data:** `name`, `email`, and `company.name` are auto-generated using random values in the pre-request script
- **Body:**
```json
{
  "name": "{{updatedName}}",
  "email": "{{updatedEmail}}",
  "company": {
    "name": "{{updatedCompany}}"
  }
}