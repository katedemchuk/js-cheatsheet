# var, let, const

## Basic usage

Declaration with initialization:

| Keyword | Symbolic name | Assignment operator | Value |
|---------|---------------|---------------------|-------|
| `var`   | one           | =                   | 1     |
| `let`   | two           | =                   | 2     |
| `const` | THREE         | =                   | 3*    |

*const **must have initializer**

## Main differences

|                         | `var`    | `let`            | `const`          |
|-------------------------|----------|------------------|------------------|
| Must have initializer   | no       | no               | yes              |
| Scope defined by        | function | block            | block            |
| Hoisting                | yes      | `ReferenceError` | `ReferenceError` |
| Redeclaration           | works    | `SyntaxError`    | `SyntaxError`    |
| Reassignment            | works    | works            | `TypeError`      |
| Creates window property | yes      | no               | no               |

### Initializer
```js
var a // ok
let b // ok


const C // -> SyntaxError, const always must have initializer
const C = 'C' // ok
```

### Scope
```js
// Function scoped - var
function log() {
  var number = 1
  console.log(number) // -> 1

  {
    var number = 8
    console.log(number) // -> 8
  }

  console.log(number) // -> 8
}


// Block scoped - let, const
function log() {
  let word = 'one'
  console.log(word) // -> 'one'

  {
    let word = 'eight'
    console.log(word) // -> 'eight'
  }

  console.log(word) // -> 'one'
}
```

### Hoisting
```js
one = 1 // ok, has implicit hoisting
var one

two = 2 // -> ReferenceError, can not assign a value to a variable before its declaration
let two
```

### Redeclaration

```js
var a = 10
var a = 20 // ok

let b = 10
let b = 10 // -> SyntaxError, a variable can not be declared more than once
```

### Reassignment

```js
var text = 'jjj'
text = 'ttt' // ok

let digits = 4567
digits = 1000 // ok

const FLOAT = 5.6
FLOAT = 6.7 // -> TypeError, const variables can not be reassigned
```

### Creates window property

```js
var world = 'world'
window.world // -> 'world'

let space = 'space'
window.space // -> undefined
```
