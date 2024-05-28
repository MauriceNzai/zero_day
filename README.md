# Harvest-Hub API

Harvest-Hub is an API for user registration, verification, authentication, and management. This project uses Node.js, Express.js, MongoDB, JWT, and Nodemailer.

## Table of Contents

- [Features](#features)
- [Technology Stack](#technology-stack)
- [Installation](#installation)
- [Environment Variables](#environment-variables)
- [API Endpoints](#api-endpoints)
- [Usage](#usage)
- [License](#license)

## Features

- User Registration
- User Email Verification
- User Authentication (Login)
- User Logout
- Password Reset

## Technology Stack

- **Backend:** Node.js, Express.js
- **Database:** MongoDB (Mongoose)
- **Authentication:** JWT (JSON Web Tokens), Bcrypt for password hashing
- **Email Service:** Nodemailer with Gmail SMTP

## Installation

1. **Clone the repository:**

    ```bash
    git clone https://github.com/your-username/harvest-hub.git
    cd harvest-hub
    ```

2. **Install dependencies:**

    ```bash
    npm install
    ```

3. **Set up environment variables:**

    Create a `.env` file in the root directory and add the following variables:

    ```plaintext
    PORT=5000
    MONGODB_URI=your_mongodb_connection_string
    JWT_SECRET=your_jwt_secret
    EMAIL_USERNAME=your_gmail_username
    EMAIL_PASSWORD=your_gmail_password
    ```

4. **Run the application:**

    ```bash
    npm start
    ```

## Environment Variables

- `PORT`: Port number on which the server runs.
- `MONGODB_URI`: MongoDB connection string.
- `JWT_SECRET`: Secret key for signing JWT tokens.
- `EMAIL_USERNAME`: Gmail username for sending emails.
- `EMAIL_PASSWORD`: Gmail password for sending emails.

## API Endpoints

### User Registration

- **Endpoint:** `POST /api/users/register`
- **Description:** Registers a new user.
- **Request Body:**

    ```json
    {
        "name": "John Doe",
        "email": "john.doe@example.com",
        "password": "password123",
        "role": "user"
    }
    ```

- **Response:**

    ```json
    {
        "message": "Verification email sent"
    }
    ```

### User Verification

- **Endpoint:** `GET /api/users/verify/:token`
- **Description:** Verifies a user's email address.
- **Response:**

    ```json
    {
        "message": "Account verified"
    }
    ```

### User Login

- **Endpoint:** `POST /api/users/login`
- **Description:** Authenticates a user and returns a JWT token.
- **Request Body:**

    ```json
    {
        "email": "john.doe@example.com",
        "password": "password123"
    }
    ```

- **Response:**

    ```json
    {
        "token": "your_jwt_token"
    }
    ```

### User Logout

- **Endpoint:** `POST /api/users/logout`
- **Description:** Logs out a user (optional server-side tasks).
- **Headers:**

    ```plaintext
    Authorization: Bearer your_jwt_token
    ```

- **Response:**

    ```json
    {
        "message": "Logged out successfully"
    }
    ```

### Password Reset

- **Request Password Reset:**

    - **Endpoint:** `POST /api/users/reset-password-request`
    - **Description:** Sends a password reset email.
    - **Request Body:**

        ```json
        {
            "email": "john.doe@example.com"
        }
        ```

    - **Response:**

        ```json
        {
            "message": "Password reset email sent"
        }
        ```

- **Reset Password:**

    - **Endpoint:** `POST /api/users/reset-password/:token`
    - **Description:** Resets the user's password.
    - **Request Body:**

        ```json
        {
            "password": "newpassword123"
        }
        ```

    - **Response:**

        ```json
        {
            "message": "Password has been reset"
        }
        ```

## Usage

1. **Register a new user:**

    ```bash
    curl -X POST http://localhost:5000/api/users/register -H "Content-Type: application/json" -d '{
        "name": "John Doe",
        "email": "john.doe@example.com",
        "password": "password123",
        "role": "user"
    }'
    ```

2. **Verify the user's email address:**

    Follow the link sent to the user's email to verify their account.

3. **Log in the user:**

    ```bash
    curl -X POST http://localhost:5000/api/users/login -H "Content-Type: application/json" -d '{
        "email": "john.doe@example.com",
        "password": "password123"
    }'
    ```

4. **Log out the user:**

    ```bash
    curl -X POST http://localhost:5000/api/users/logout -H "Authorization: Bearer your_jwt_token"
    ```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

