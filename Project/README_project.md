# Plainbase Project Diagrams - README

This document provides a detailed overview of the system architecture, workflows, and interactions for the Plainbase application.

## 1. Activity Diagram
The activity diagram outlines the step-by-step process of handling a natural language question.
* The system begins when it receives a question from the user.
* It immediately checks the request validity and applies rate limiting.
* If the request is invalid, the system halts and returns a `400` or `429` error.
* For valid requests, the system generates the corresponding SQL.
* The generated SQL is then validated; invalid SQL triggers a `400` error return.
* If the SQL is valid, it is executed against the database, and the system returns a `200` success response with the results.

## 2. Class Diagram
The detailed class diagram illustrates the structural foundation of the application, restricted to a maximum of six core classes.
* **PlainbaseApp:** Handles the client-side state, including `question`, `loading`, `error`, `queryResult`, and `schemaCache`. It includes methods for submitting questions, loading schemas, rendering results, and exporting CSVs.
* **QueryRouteHandler:** Manages the `POST /api/query` route, handling request payloads and formatting responses with request IDs.
* **SchemaRouteHandler:** Manages the `GET /api/schema` route to load table and column metadata.
* **SqlValidator:** Enforces read-only SQL execution, utilizing methods like `validateReadOnlySql` and `isReadOnlyStatement`.
* **DbPoolProvider:** Manages database connections by providing a connection pool (`getDbPool`) and running queries (`runQuery`).
* **LlmService:** Interacts with the language model to generate SQL from questions (`generateSqlFromQuestion`) and builds schema context.

## 3. Sequence Diagram
The short sequence diagram depicts the chronological flow of messages during a query execution.
* The **User** initiates the sequence by asking a question through the **PlainbaseApp**.
* The app sends a `POST` request to the `/api/query` endpoint.
* An **LlmService** generates the SQL and passes it to the **SqlValidator**.
* The validator checks the SQL:
    * If invalid, a `400` error is returned to the user.
    * If valid, the query is executed on the **PostgreSQL** database.
* The database returns the rows, which are passed back to the app as `200` results.

## 4. State Diagram
The state diagram tracks the lifecycle of a single query request.
* **Received:** The initial state when a request hits the system.
* **GeneratingSql:** Transitioned to if the request is accepted.
* **Rejected:** Reached if the initial request hits a rate limit, is a bad request, or if the generated SQL is invalid.
* **RunningSql:** Transitioned to once the generated SQL is deemed valid.
* **Failed:** Reached if there is an execution error while running the SQL.
* **Success:** Reached when the results are successfully returned from the database.

## 5. Use Case Diagram
The use case diagram defines the primary actors and their permissible actions within the system.
* **User Actors:** Can perform several direct actions, including typing a natural language question, viewing schema references, viewing query results, exporting results to CSV, viewing generated SQL, and submitting queries.
* **Submit Query (Core Action):** When a user submits a query, it internally triggers several system tasks.
* **System & API Actors:** The "Submit query" action `<includes>` translating natural language to SQL (which interfaces with the **Claude API** actor), validating read-only queries, executing SQL on the database (interfacing with the **System** actor), and handling query errors.
