# typescript-nodejs-express

- Node.js executes JavaScript, not TypeScript.
- We'll use `tsc` to compile ts->js and then have `nodemon` serve the js app.

## Setup (this was already done)

```bash
nvm install --lts
nvm use --lts
node -v > .nvmrc
```

```bash
npm init  # set up package.json
npm install typescript
node_modules/typescript/bin/tsc --init  # create tsconfig.json
```

In `tsconfig.json`, set `target`, `moduleResolution`, `outDir` and `rootDir` accordingly.

```bash
npm install --save express body-parser
npm install --save-dev nodemon
```

Install types:

```bash
npm install --save-dev @types/node @types/express
```

Add a new `start` script to `package.json`:

```json
"start": "nodemon dist/app.js"
```

## Run

```bash
node_modules/typescript/bin/tsc -w
npm start  # the new start script we added to package.json
```

## Perform REST API calls

Launch e.g. Postman or Thunder Client in vscode, then send a `POST` request to `http://localhost:3000/todos/` with json `{"text": "hello world"}`. This will add a todo. Example response:

```json
{
  "message": "Created the todo.",
  "createdTodo": {
    "id": "0.4701661299147384",
    "text": "hello"
  }
}
```

Making a `GET` request to `http://localhost:3000/todos/` will return all todos in the response.

A todo can be updated by making a `PATCH` request to `http://localhost:3000/todos/$ID` (where `$ID` is one of the ids returned in the previous `GET` request) with json data `{"text": "updated value"}`.

This would return a response such as:

```json
{
  "message": "Updated!",
  "updatedTodo": {
    "id": "0.527784891057566",
    "text": "updated value"
  }
}
```
