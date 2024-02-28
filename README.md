# Kruger_challenge

# Kruger Employees Front End App

## React + TypeScript + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh


Project Name

## Brief description of what this project does and who it's for.
Prerequisites

Before you begin, ensure you have met the following requirements:

    Node.js installed (preferably the latest LTS version)
    Yarn package manager (This project uses Yarn for dependency management)

Getting Started

To get a local copy up and running, follow these simple steps.
Installation

    Clone the repository:

    git clone https://github.com/alejandrotoledoweb/kruger_employees_reactjs.git

Navigate into the project directory:


    cd kruger_employees_reactjs

Install the project dependencies using Yarn:


    yarn install

Running the App

To start the development server:

    yarn dev

This command will compile your TypeScript app and serve it locally. By default, Vite serves the app on http://localhost:5173, but this can vary based on your configuration. Check the terminal output to be sure.
Building for Production

To create a production build:

    yarn build


Deployment

Provide instructions on how to deploy the production build of the app. This might vary greatly depending on the hosting service (Netlify, Vercel, AWS, etc.) and the specifics of your project.
Contributing

If you have suggestions for how to improve the app, or want to contribute to the development, consider the following steps:

    Fork the project repository.
    Create a new branch (git checkout -b feature/AmazingFeature).
    Make your changes and commit them (git commit -m 'Add some AmazingFeature').
    Push to the branch (git push origin feature/AmazingFeature).
    Open a pull request.

License

Distributed under the MIT License. See LICENSE file for more information.
Contact

Your Name - atoledofr@gmail.com

Project Link: https://github.com/alejandrotoledoweb/kruger_employees_reactjs

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type aware lint rules:

- Configure the top-level `parserOptions` property like this:

```js
export default {
  // other rules...
  parserOptions: {
    ecmaVersion: 'latest',
    sourceType: 'module',
    project: ['./tsconfig.json', './tsconfig.node.json'],
    tsconfigRootDir: __dirname,
  },
}
```



# Kruger Employees API Documentation

![](./ERD diagram.png)

This document outlines the usage of the Kruger Employees API endpoints. The API is designed to manage employee records, including creating employees, managing employee details, and user authentication.
Base URL

Create the database for the Kruger Employees API. Replace kruger_employees with your desired database name if you prefer a different one:

    CREATE DATABASE kruger_employees;

Credentials for admin user:

    username: admin
    password: password

All URLs referenced in the documentation have the following base:


    http://localhost:8080/api

The base URL will change depending on the environment where the API is deployed.
Authentication

Several endpoints require a valid JWT token provided in the request header:



    Authorization: Bearer YOUR_JWT_TOKEN

Login

    Endpoint: /auth/login
    Method: POST
    Description: Authenticates a user and returns a JWT token.
    Body:

    json

    {
      "username": "alex1",
      "password": "password"
    }

    Responses:
        status: 200 OK:
        {
            "accessToken": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhbGVqYW5kcm90IiwiaWF0IjoxNzA5MTM2MDQ3LCJleHAiOjE3MDkxMzYxMTd9.SD2vPbUUQCCBAoD0qhRz0P4c8sbsec_mpCpvtvP-CCjQYjCqmZSud-vghkLxceZ31f0OJcNJoaevXDoJ2-_M3w",
            "tokenType": "Bearer ",
            "userId": 13,
            "employeeDetailId": 6,
            "role": "EMPLOYEE"
        }


Employee Management

## Create Employee

    Endpoint: /employee
    Method: POST
    Description: Creates a new employee record.
    Header: Authorization: Bearer YOUR_JWT_TOKEN
    Body:

    json

    {
      "names": "Alejandro Andrés",
      "lastNames": "Toledo Freire",
      "email": "atoledofr@gmail.com",
      "cedula": "1716191927"
    }

    Responses:
        status: 200 OK
        {
            "id": 10,
            "names": "alejandro",
            "lastNames": "toledo",
            "email": "atoledofr@gmail.com",
            "cedula": "3377449927",
            "employeeDetail": {
                "id": 10,
                "fechaNacimiento": null,
                "direccionDomicilio": null,
                "telefonoMovil": null,
                "vacunado": false,
                "tipoVacuna": null,
                "fechaVacunacion": null,
                "numeroDosis": null
            },
            "username": "alejandrot3",
            "password": "6WsouSydro"
        }

### Update Employee Detail

    Endpoint: /employee-detail/update
    Method: PUT
    Description: Updates details for an existing employee.
    Body:

    json

    {
        "userId": 13,
        "id": 6,
        "fechaNacimiento": "1990-01-01",
        "direccionDomicilio": "123 Main St",
        "telefonoMovil": "555-1234",
        "vacunado": true,
        "tipoVacuna": "Pfizer",
        "fechaVacunacion": "2021-04-15",
        "numeroDosis": 2
    }

Responses:

    status: 200 OK:
    {
        "id": 6,
        "fechaNacimiento": "2000-02-09",
        "direccionDomicilio": "Quito",
        "telefonoMovil": "0992601505",
        "vacunado": true,
        "tipoVacuna": "Pfizer",
        "fechaVacunacion": "2024-02-02",
        "numeroDosis": 2
    }

