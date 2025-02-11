# LUDEX INTERNSHIP TEST

## Getting Started

### Prerequisites

Ensure you have the following installed:

- [Node.js](https://nodejs.org)
- [Docker](https://www.docker.com/get-started/)
- [Git](https://git-scm.com/)
- _(Recommended)_ [VS Code](https://code.visualstudio.com/)
  - If you install VS Code, it is recommended to also install the following extensions:
    - **ESLint** (for linting and code formatting)
    - **GraphQL** (for syntax highlighting and validation)
    - **Prisma** (for schema editing and database insights)

### Running the Project

#### Launch the Database

First, ensure that you have **Docker Desktop** installed and running. To verify that Docker is installed and accessible from your terminal, run:

```sh
docker --version
```

If Docker is installed, navigate to the project directory and start the database container by running:

```sh
docker compose up -d
```

This will launch a **PostgreSQL** database inside a Docker container, which will be used in later steps.

#### Run Migrations

With the database running, install the project dependencies by executing:

```sh
npm install
```

Once all dependencies are installed, apply database migrations to ensure the schema is correctly set up:

```sh
npm run prisma:migrate
```

#### Run the Application

Now that everything is set up, you can start the application. To run it in **watch mode** (which automatically restarts the app on file changes), use the following command:

```sh
npm run dev:watch
```

This command also performs two additional tasks before starting the app:

1. **Generates TypeScript types** from the Prisma schema.
2. **Generates GraphQL types** in `typeDefinitions`.

These generated types will help improve your development experience, especially if you have **ESLint** enabled in your IDE.

#### Testing Using GraphQL Playground

Once the application is running, open your browser and navigate to:

```
http://localhost:4000/graphql
```

This will open the GraphQL Playground, a UI where you can execute GraphQL queries and mutations.

To run a **query**, use the following example:

```graphql
query {
  hello
}
```

To run a **mutation**, use:

```graphql
mutation {
  createSomething(input: { name: "Bob" }) {
    id
    name
  }
}
```

The response from the backend will appear on the right-hand side of the UI.

## The Test

Your task is to implement a **CRUD (Create, Read, Update, Delete) Todo backend** using GraphQL. The backend should support the following functionalities:

- Create todos
- Mark todos as complete or incomplete
- Update the title of a todo
- Retrieve all todos
- Retrieve all incomplete todos
- Retrieve all completed todos
- Retrieve a single todo by ID
- Delete todos

## Relevant Documentation

- [Prisma Documentation](https://www.prisma.io/docs/orm/prisma-client/queries/crud)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/typescript-from-scratch.html)
- [GraphQL Guide](https://graphql.org/learn/)
