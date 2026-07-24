# Why did `npm run build` fail with "Missing script: build"?

## Interview Question

Why does `npm run build` show the following error?

```bash
npm ERR! Missing script: "build"
```

---

## Answer

`npm run build` executes the **build** script defined inside the `scripts` section of `package.json`.

If the `build` script is not available, npm throws the error:

```bash
npm ERR! Missing script: "build"
```

---

## Example

### package.json

```json
{
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
  }
}
```

Since there is **no build script**, running:

```bash
npm run build
```

returns:

```bash
npm ERR! Missing script: "build"
```

---

## Why?

Node.js checks the `scripts` section of `package.json`.

Available scripts:

- start
- dev
- test

Missing script:

- build ❌

Therefore, npm cannot execute `npm run build`.

---

## How to check available scripts

Run:

```bash
npm run
```

Example output:

```text
Lifecycle scripts:
  start
    node server.js

Available via npm run:
  dev
    nodemon server.js
```

This confirms that the project has no `build` script.

---

## When is `npm run build` required?

### React / Vite

```bash
npm run build
```

Creates:

```text
dist/
```

The `dist` folder is deployed to Cloudflare, Nginx, or another web server.

---

### Express.js Backend

Normally, no build step is required.

Run:

```bash
npm install
npm start
```

or

```bash
npm run dev
```

Node.js runs `server.js` directly.

---

## Difference

| Frontend (React/Vite) | Backend (Express.js) |
|------------------------|----------------------|
| Requires build | No build required |
| Creates `dist/` | Runs `server.js` directly |
| `npm run build` | `npm start` / `npm run dev` |

---

## Real Project Example

Project:

```
Travel_Server_Crm
```

package.json:

```json
"scripts": {
  "start": "nodemon server.js",
  "dev": "nodemon server.js"
}
```

There is no `build` script.

Therefore:

```bash
npm run build
```

fails with:

```bash
npm ERR! Missing script: "build"
```

The correct commands are:

```bash
npm install
npm run dev
```

or

```bash
npm start
```

---

## Interview Answer (30 Seconds)

`npm run build` executes the `build` script defined in the `scripts` section of `package.json`. If the project does not contain a `build` script, npm returns `Missing script: "build"`. This is common in Express.js backend projects because they usually run directly using `server.js` without generating a build folder. In such cases, I use `npm start` or `npm run dev` instead.
