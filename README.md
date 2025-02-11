# LUDEX INTERNSHIP TEST

## Getting started

### Prerequisits

Ensure you have installed

- [nodejs](https://nodejs.org)
- [docker](https://www.docker.com/get-started/)
- [git](https://git-scm.com/)
- [(recommended) vscode](https://code.visualstudio.com/)

### Running the project

#### Launch database

First ensure that you have docker desktop installed. Once that is done make sure the program is running and in your terminal run
`shell docker --version` to make sure it is currently installed to your path.

if it is first cd into this directory and run `shell docker compose up -d`

This will run a postgres database in a docker container which you will be using later.

#### Run Migration

Now that the database is running you should now run `shell npm install` to get all of the dependencies for this project.

Once everything is installed you can now run a migration to ensure the tables that are defined in the schema.prisma are now in your database.

To run the migration run `shell npm run prisma:migrate`

#### Run app

Now that everything else is setup we are going to run the app. To run it in watch mode (meaning whenever you change a file it will rerun the script) run in your terminal `shell npm run dev:watch`

Notice that this does two things before it actually runs the app. It first generates the typescript types from the prisma schema, and it generates the types from the graphql in typeDefinitions. This will be helpful if you have an eslint on your IDE.

#### Testing using graphql playground

When the app begins to run. You will see that the app is running on localhost:4000. Go to your browser and input http://localhost:4000/graphql. You will see a UI that you can run graphql queries in. To run a Query

```graphql
query {
  hello
}
```

to run a Mutation

```graphql
mutation {
  createSomething(input: { name: "bob" }) {
    id
    name
  }
}
```

and on the right you will see the response from the backend.

## The Test

You are to make a CRUD (create, read, update, delete) todo backend. Using graphql you need to be able to

- create todos,
- Mark them as complete or incomplete
- Change the title of the todo
- Get all todos
- Get all not completed todos
- Get completed todos
- Get a single todo by id
- Delete todos

## Relevant documentation

[prisma](https://www.prisma.io/docs/orm/prisma-client/queries/crud)
[typescript](https://www.typescriptlang.org/docs/handbook/typescript-from-scratch.html)
[graphql](https://graphql.org/learn/)
