# Closure
Closure = function + lexical environment:

Closures are created when there is a function created by parent function or module which has access to enclosed scope — surrounding lexical environment at this function creation time.

## Simple example
Log a message referencing a variable from enclosed scope (surrounding lexical environment) of a function which creates a closure:

```js
function makeLogger(message) {
  const prefix = 'Logger says: '

  function log() { // <- this function creates closure
    console.log(prefix + message)
  }

  return log
}

const logger = makeLogger('Not life, but good life, is to be chiefly valued')

console.log(logger)
// -> f logger0 () { console.log(prefix + message) }
// ^
// Our newly created function tries to access constant
// 'prefix' and parameter 'message' values which don't
// belong to it!

logger()
// -> Logger says: Not life, but good life, is to be
// chiefly valued

// Success! A closure works, logger function can access
// surrounding lexical environment!
```

Example above shows how `logger` function can access lexical entities outside itself. So there is a mechanism which allows for a function access outer state and use it inside. More specifically access constant `prefix` and parameter `message` values declared outside of the function.

# No closure, just scope alternative

On the contrary, the same functionality can be rewritten without using a factory function and closure:

```js
function logger(message) {
  const prefix = 'Logger says: '

  function log() {
    console.log(prefix + message)
  }

  log()
}

logger('Not life, but good life, is to be chiefly valued')
// -> Logger says: Not life, but good life, is to be
// chiefly valued
```

This example shows how regular lexical scoping works — function scope is accessible via inner functions during parent function execution.

## More complex example: counter
```js
function makeCounter(count = 0) { // default parameter value
  function value() { // <- forms closure
    return count
  }

  function reset() { // <- also forms closure
    count = 0
  }

  function increment() { // <- also forms closure
    count += 1 // addition assignment operator
  }

  function decrement() { // <- also forms closure
    count -= 1 // subtraction assignment operator
  }

  return { value, reset, increment, decrement }
  // shorthand object property names
}

const counter0 = makeCounter(0)
const counter10 = makeCounter(10)

counter0.increment()
console.log(counter0.value()) // -> 1

counter10.decrement()
console.log(counter10.value()) // -> 9

counter10.reset()
console.log(counter10.value()) // -> 0
```

All these closures we created share the same lexical environment — parameter `count` value.

`counter0` differ from `counter10` only by lexical environment shared.

## Closures in modules
Functions from other modules can also form closures:
```js
// module greet.js
const message = 'Hello from other module!'

export function greet() {
  console.log(message)
}

// module user.js
import { greet } from './greet.js'

greet() // -> Hello from other module!
```

Constant `message` is accessed by imported function `greet` in a different module.
