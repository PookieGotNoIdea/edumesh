# Backend Configuration — config

## 1. Overview

The `config/` directory contains configuration files required by the EduMesh backend application.

It centralizes environment variable handling, database connectivity and other application-level configuration.

Keeping configuration separate from business logic makes the backend easier to maintain, configure and deploy across different environments.

## 2. Responsibilities

The `config/` directory is responsible for:

- Managing environment variables.
- Validating required environment variables.
- Configuring the database connection.
- Initializing shared application configuration.
- Providing configuration values to other backend modules.
- Keeping sensitive configuration separate from application source code.

## 3. Planned Folder Structure

```text
config/
│
└── README.md
```

The following implementation files are planned:

```text
config/
│
├── README.md
├── env.js
└── database.js
```

### File Responsibilities

| File | Responsibility |
|---|---|
| `README.md` | Documents configuration architecture |
| `env.js` | Loads and validates environment variables |
| `database.js` | Configures and manages the Prisma database client |

These files will be created during backend implementation.

## 4. Environment Variables

Environment variables store configuration values separately from application source code.

EduMesh will use environment variables for:

- Database connection details.
- Server configuration.
- JWT authentication secrets.
- Cookie and authentication settings.
- Other environment-specific values.

### Planned Environment Variables

| Variable | Purpose |
|---|---|
| `PORT` | Backend server port |
| `NODE_ENV` | Application environment |
| `DATABASE_URL` | PostgreSQL database connection URL |
| `JWT_SECRET` | Secret used for JWT signing and verification |
| `JWT_EXPIRES_IN` | JWT expiration configuration |
| `CLIENT_URL` | Frontend application origin |

Additional variables may be introduced when required.

Actual values must be configured in the local environment and must never be committed to Git.

## 5. Environment Configuration

The `env.js` file will be responsible for:

- Reading environment variables.
- Checking required configuration values.
- Validating environment variable formats.
- Providing a centralized configuration interface.
- Preventing application startup when essential configuration is missing or invalid.

Environment variables should be validated before the application starts accepting requests.

## 6. Database Configuration

The `database.js` file will manage database connectivity through Prisma ORM.

Responsibilities include:

- Initializing Prisma Client.
- Providing a reusable database client.
- Managing database connection lifecycle.
- Supporting database operations across backend services.
- Handling database disconnection when the application shuts down.

Feature modules should access the shared Prisma Client instead of creating separate database clients unnecessarily.

## 7. Security Guidelines

- Never commit actual `.env` files.
- Maintain a `.env.example` containing variable names and safe placeholders.
- Never expose database credentials to the frontend.
- Never hardcode JWT secrets.
- Use strong, randomly generated authentication secrets.
- Validate required environment variables during startup.
- Keep development and production configurations separate.
- Restrict access to sensitive configuration values.

## 8. Integration with Other Directories

| Directory or File | Relationship |
|---|---|
| `backend/.env` | Supplies local environment configuration |
| `backend/.env.example` | Documents required environment variables |
| `prisma/` | Uses database connection configuration |
| `src/modules/` | Uses centralized application configuration and database access |
| `src/middleware/` | Uses authentication configuration |
| `server.js` | Uses configuration during server initialization |

## 9. Development Workflow

Configuration development will follow these steps:

1. Identify required environment variables.
2. Create the `.env.example` file.
3. Configure local environment variables.
4. Implement environment variable loading.
5. Validate required configuration values.
6. Initialize the Prisma database client.
7. Test database connectivity.
8. Integrate configuration with the Express application.
9. Verify configuration across development and deployment environments.

## 10. Development Rules

- Keep configuration separate from business logic.
- Use environment variables for sensitive and environment-specific values.
- Avoid duplicating database client initialization.
- Validate required configuration during application startup.
- Use meaningful and consistent environment variable names.
- Never commit secrets or real database credentials.
- Document new environment variables when introduced.

---

**EduMesh Backend Configuration**

Centralized configuration. Secure environment management. Reliable database connectivity.
