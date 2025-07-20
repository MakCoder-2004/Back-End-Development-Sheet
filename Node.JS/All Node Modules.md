## 📘 Node.js Core Modules

Node.js comes with a set of built-in modules. You can use them without installing anything via `require('module_name')`.

---

### 📂 `fs` (File System)

Handles file operations.

```js
const fs = require('fs');

// Read a file
fs.readFileSync('file.txt', 'utf8', (err, data) => {
    if (err) throw err;
    console.log(data);
});
```

---

### 🌸 `http`

Creates an HTTP server.

```js
const http = require('http');

const server = http.createServer((req, res) => {
    res.write('Hello World!');
    res.end();
});

server.listen(3000);
```

---

### 🌐 `https`

Creates HTTPS servers.

```js
const https = require('https');
const fs = require('fs');

const options = {
    key: fs.readFileSync('key.pem'),
    cert: fs.readFileSync('cert.pem')
};

https.createServer(options, (req, res) => {
    res.write('Secure Hello!');
    res.end();
}).listen(443);
```

---

### 📦 `path`

Handles and transforms file paths.

```js
const path = require('path');

const fullPath = path.join(__dirname, 'folder', 'file.txt');
console.log(fullPath);
```

---

### 🧠 `os`

Provides information about the operating system.

```js
const os = require('os');

console.log(os.platform());
console.log(os.freemem());
```

---

### ⌚ `timers`

Scheduling functions.

```js
setTimeout(() => {
    console.log('Executed after delay');
}, 1000);
```

> No `require` needed. Built-in globally.

---

### 💾 `buffer`

Used for binary data manipulation.

```js
const buf = Buffer.from('Hello');
console.log(buf.toString());
```

> Also global, but `require('buffer')` for advanced usage.

---

### 📥 `stream`

Handles streaming data.

```js
const fs = require('fs');

const readStream = fs.createReadStream('file.txt');
readStream.on('data', chunk => {
    console.log(chunk.toString());
});
```

---

### 🔀 `events`

Implements EventEmitter.

```js
const EventEmitter = require('events');

const emitter = new EventEmitter();
emitter.on('greet', () => {
    console.log('Hello!');
});

emitter.emit('greet');
```

---

### 🔐 `crypto`

Provides cryptographic functionality.

```js
const crypto = require('crypto');

const hash = crypto.createHash('sha256').update('data').digest('hex');
console.log(hash);
```

---

### 🧼 `util`

Utilities for debugging and inheritance.

```js
const util = require('util');

const debuglog = util.debuglog('foo');
debuglog('message from %s', 'debugger');
```

---

### 🪒 `querystring`

Parses and formats URL query strings.

```js
const qs = require('querystring');

const parsed = qs.parse('name=John&age=30');
console.log(parsed);
```

---

### 🌍 `url`

URL resolution and parsing.

```js
const url = require('url');

const parsedUrl = new URL('https://example.com/path?name=John');
console.log(parsedUrl.hostname);
```

---

### 🧱 `zlib`

Compression utilities.

```js
const zlib = require('zlib');
const fs = require('fs');

const gzip = zlib.createGzip();
fs.createReadStream('input.txt')
  .pipe(gzip)
  .pipe(fs.createWriteStream('input.txt.gz'));
```

---

### 🧲 `assert`

Used for writing tests and making assertions.

```js
const assert = require('assert');

assert.strictEqual(1, 1); // passes
```

---

### ⏱️ `process`

Provides information and control over the current process.

```js
console.log(process.argv); // command-line args
console.log(process.env);  // environment vars
```

> No `require` needed. Built-in globally.

---

### 🪡 `console`

Used to print to stdout/stderr.

```js
console.log('Standard output');
console.error('Standard error');
```

> No `require` needed. Built-in globally.

---

### 📁 `child_process`

Executes shell commands or external programs.

```js
const { exec } = require('child_process');

exec('ls', (err, stdout, stderr) => {
    console.log(stdout);
});
```

---

### 📅 `module` & `require`

Used internally for module management.

```js
// You use `require()` to include other modules.
const fs = require('fs');
```

> Advanced usage involves custom module loading.

---

### 🤩 `repl`

Read-Eval-Print-Loop interface.

```js
const repl = require('repl');

repl.start('> ');
```

---

### 📒 `vm`

Run code in a virtual machine context.

```js
const vm = require('vm');

const script = new vm.Script('x + 1');
const context = { x: 2 };
script.runInNewContext(context);
console.log(context.x); // 2
```

---

### 📚 `readline`

Read from input stream line-by-line.

```js
const readline = require('readline');

const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});

rl.question('Your name? ', answer => {
    console.log(`Hello, ${answer}`);
    rl.close();
});
```

---

## ✅ Usage Summary

```js
// General pattern
const moduleName = require('module_name');
```

* No installation is needed for **core modules**.
* For **external modules**, use: `npm install module_name`.

---
