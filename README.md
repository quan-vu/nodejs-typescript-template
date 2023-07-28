# Nodejs Typescript Template

This tutorial will show you how to setup nodejs project with typescript.

Prerequites

- Nodejs v18.x
- Yarn

## Quickstart

Step 1: Installing TypeScript

```shell
yarn -D typescript @types/express @types/node
```

Step 2: Generating tsconfig.json

```shell
npx tsc --init
```

Update outout Dir as follows:

```javascript
{
  "compilerOptions": {
    "outDir": "./dist",
    "rootDir": "./src",

    // rest options remain
  }
}
```

Step 3: Create index.ts file for express application

```typescript
import express, { Express, Request, Response } from 'express';
import dotenv from 'dotenv';

dotenv.config();

const app: Express = express();
const port = process.env.PORT;

app.get('/', (req: Request, res: Response) => {
  res.send('Express + TypeScript Server');
});

app.listen(port, () => {
  console.log(`⚡️[server]: Server is running at http://localhost:${port}`);
});
```

Step 4: Run application

```shell
yarn dev
```

Result

```shell
10:47:06 AM - Starting compilation in watch mode...
[0] 10:47:06 AM - Found 0 errors. Watching for file changes.
[1] ⚡️[server]: Server is running at http://localhost:5000
```

**If has this error on run application like:** `ReferenceError: exports is not defined in ES module scope`

- Open package.json
- Remove this property: "type": "module",