---
description: >-
  Explain how to use `npm install` to install 3rd-party libraries to Proxyman
  Script
---

# Use npm install

## Use npm Packages in Proxyman Scripting

Proxyman Scripting supports `require()` for compatible npm packages installed in Proxyman's Application Support folder. This lets a script reuse popular JavaScript utilities instead of rewriting common logic by hand.

This feature keeps the same `require()` keyword that Proxyman already uses for built-in libraries and user add-ons. Existing imports such as `@libs`, `@addons`, `@users`, JSON files, text files, and local files continue to work.

### Install a package

Open Terminal and install packages into Proxyman's Application Support folder:

* Install `dayjs`

```bash
$ cd "$HOME/Library/Application Support/com.proxyman.NSProxy"
$ npm install --prefix . dayjs --ignore-scripts --no-audit --no-fund
```

After installation, the package should exist in:

```
~/Library/Application Support/com.proxyman.NSProxy/node_modules
```

### Use a package in a script

Use the package name with `require()`:

```javascript
const dayjs = require("dayjs");

async function onRequest(context, url, request) {
  const formattedDate = dayjs("2026-05-05T13:00:00Z").format("YYYY-MM-DD");
  request.headers["X-Proxyman-Dayjs"] = formattedDate;
  return request;
}
```

### Examples

#### Format a date with `dayjs`

Install:

```bash
cd "$HOME/Library/Application Support/com.proxyman.NSProxy" && npm install --prefix . dayjs --ignore-scripts --no-audit --no-fund
```

Script:

```javascript
const dayjs = require("dayjs");

async function onRequest(context, url, request) {
  request.headers["X-Request-Date"] = dayjs().format("YYYY-MM-DD");
  return request;
}
```

#### Normalize text with `lodash`

Install:

```bash
cd "$HOME/Library/Application Support/com.proxyman.NSProxy" && npm install --prefix . lodash --ignore-scripts --no-audit --no-fund
```

Script:

```javascript
const _ = require("lodash");

async function onRequest(context, url, request) {
  const label = _.kebabCase("Hello Proxyman Scripts");
  request.headers["X-Proxyman-Label"] = label;
  return request;
}
```

#### Validate input with `validator`

Install:

```bash
cd "$HOME/Library/Application Support/com.proxyman.NSProxy" && npm install --prefix . validator --ignore-scripts --no-audit --no-fund
```

Script:

```javascript
const validator = require("validator");

async function onRequest(context, url, request) {
  const email = url.searchParams.get("email") || "";
  request.headers["X-Email-Is-Valid"] = validator.isEmail(email) ? "true" : "false";
  return request;
}
```

#### Create slugs with `slugify`

Install:

```bash
cd "$HOME/Library/Application Support/com.proxyman.NSProxy" && npm install --prefix . slugify --ignore-scripts --no-audit --no-fund
```

Script:

```javascript
const slugify = require("slugify");

async function onRequest(context, url, request) {
  const title = url.searchParams.get("title") || "Hello Proxyman";
  request.headers["X-Proxyman-Slug"] = slugify(title, { lower: true });
  return request;
}
```

#### Encode data with `js-base64`

Install:

```bash
cd "$HOME/Library/Application Support/com.proxyman.NSProxy" && npm install --prefix . js-base64 --ignore-scripts --no-audit --no-fund
```

Script:

```javascript
const { Base64 } = require("js-base64");

async function onResponse(context, url, request, response) {
  response.headers["X-Proxyman-Encoded"] = Base64.encode("Proxyman");
  return response;
}
```

#### Decode HTML entities with `he`

Install:

```bash
cd "$HOME/Library/Application Support/com.proxyman.NSProxy" && npm install --prefix . he --ignore-scripts --no-audit --no-fund
```

Script:

```javascript
const he = require("he");

async function onResponse(context, url, request, response) {
  response.headers["X-Decoded-Title"] = he.decode("Proxyman &amp; Scripting");
  return response;
}
```

### Compatibility

Proxyman runs scripts with JavaScriptCore, not Node.js. npm packages work best when they are pure JavaScript and compatible with CommonJS.

Supported:

* CommonJS packages loaded with `require("package-name")`
* Package entry points from `package.json` such as `main` and simple `exports`
* Relative imports used inside installed packages, such as `require("./helper")`
* JSON files required by packages

Not supported:

* Node.js built-in modules such as `fs`, `path`, `crypto`, `http`, or `child_process`
* Native `.node` add-ons
* Packages that require a full Node.js runtime
* ESM-only packages that cannot be loaded with CommonJS `require()`

### Node.js native libraries

Proxyman Scripting does not run inside the Node.js runtime. It only uses Node/npm as a package installation tool, then loads compatible JavaScript files with JavaScriptCore.

Because of that, Node.js native libraries are not supported:

* `require("fs")`, `require("path")`, `require("crypto")`, and other Node.js built-in modules are blocked.
* `require("node:fs")` and built-in subpaths such as `require("fs/promises")` are blocked.
* Native C/C++ add-ons compiled as `.node` files are blocked.
* Packages that call Node-specific APIs such as `process.dlopen`, filesystem APIs, network sockets, or child processes will not work.

Examples of packages that usually do not work in Proxyman Scripting:

* `sharp`
* `sqlite3`
* `bcrypt`
* `canvas`
* `puppeteer`
* packages that require `fs`, `path`, `crypto`, `http`, `https`, `net`, or `child_process`

Use pure JavaScript packages or packages that provide a CommonJS browser-compatible build instead.

### Troubleshooting

If `require("dayjs")` or another package returns `undefined`, check that the package is installed in the expected folder:

```bash
ls "$HOME/Library/Application Support/com.proxyman.NSProxy/node_modules"
```

If `node_modules` is missing, install again with `--prefix .`:

```bash
cd "$HOME/Library/Application Support/com.proxyman.NSProxy" && npm install --prefix . dayjs --ignore-scripts --no-audit --no-fund
```

The `--prefix .` option is important because npm may otherwise walk up to a parent `package.json` and install packages outside Proxyman's folder.
