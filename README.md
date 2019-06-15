# simple-json-log

A simple JSON logger for Node.js.

Light weight. No external dependencies. Great for application code or
libraries.

To use with a library, set the `level` based on an environment variable.

```js
const level = process.env.AWESOME_LIBRARY_LOG_LEVEL || 'off'
```

## Quick Start

```js
const log = new(require('simple-json-log'))({ level: 'info' })
log.info('Hello log world!')
```

Output

```json
{"time":"2019-06-15T08:57:41.016Z","info":"Hello log world!"}
```

We make it easy to log a string message and/or a JSON object.
The string message always comes first.

```js
log.info('Hello log world!')
log.info('Hello log world!', { some: 'nice JSON here' })
log.info({ some: 'nice JSON here' })
```

Output

```json
{"time":"2019-06-15T09:02:20.144Z","info":"Hello log world!"}
{"time":"2019-06-15T09:02:20.144Z","info":"Hello log world!","some":"nice JSON here"}
{"time":"2019-06-15T09:02:20.144Z","some":"nice JSON here"}
```

## Options

**`out`**

Defaults to `process.stdout`. You can use any output stream you
like.

**`level`**

Defaults to 'off'. We do nothing unless you specify a level.

**`levelAsLabel` and `label`**

`levelAsLabel` defaults to `true`.
`label` defaults to 'message'.

If `levelAsLabel` is `true`, we use `level` as the message label.
Otherwise we use `label` as the message label.

**`levelElement`**

Defaults to `false`. If `true` we add a 'level' element to the JSON output.

**`time`**

Defaults to a function that outputs `new Date().toISOString()`.
If `false`, we don't add a 'time' element to the JSON output.
You can also use your own function to format time however you like.

**`indent`**

Defaults to `0`. This is the number of spaces to indent the JSON output.

**`levels`**

Defaults to the following levels. You can specify any levels you like.

```js
{
  trace: 0,
  debug: 1,
  info: 2,
  warn: 3,
  error: 4,
  fatal: 5,
  off: 6
}
```
