# RBAC Project

This project demonstrates a basic implementation of Role-Based Access Control (RBAC) using Express.js, MongoDB, and JWT (JSON Web Tokens). To get started, clone the repository with `git clone <repository_url>` and navigate to the project directory with `cd rbac_project`. Install the required npm packages by running `npm install`, and ensure MongoDB is running with `mongod`. Start the server with `node server.js`, which will be available at `http://localhost:5000`.

The API includes the following endpoints: 

1. **Register a New User**: `POST /auth/register` - Register a user by sending a JSON body with `username`, `password`, and `role` (either `user` or `admin`). Expect a response of `User registered successfully` or `Registration failed!`.

2. **Log In**: `POST /auth/login` - Log in by sending a JSON body with `username` and `password`. You will receive a JWT token in the response, which is used for authentication.

3. **Access Protected Admin Route**: `GET /admin/users` - Access this route by including the JWT token in the `Authorization` header as `Bearer <your_jwt_token>`. Only users with an `admin` role can access this route. A valid admin token will return a list of users; otherwise, you will receive an error message.

To test with Postman:
1. **Register an Admin User**: Create a `POST` request to `http://localhost:5000/auth/register` with a JSON body like `{"username": "adminuser", "password": "adminpass", "role": "admin"}` and send the request.
2. **Log In**: Create a `POST` request to `http://localhost:5000/auth/login` with `{"username": "adminuser", "password": "adminpass"}`. Copy the token from the response.
3. **Access Protected Route**: Create a `GET` request to `http://localhost:5000/admin/users`, add an `Authorization` header with `Bearer <your_jwt_token>`, and send the request to see the list of users if authenticated as admin.

For troubleshooting, ensure the correct role and token are used. A `403 Forbidden` error indicates incorrect permissions, while a `401 Unauthorized` error means issues with the token. Server issues may result in a `500 Internal Server Error`. This project is licensed under the MIT License.

