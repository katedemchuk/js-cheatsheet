# Increment and decrement operators
*Increment operator* performs operation on operand, a number, and increases its value by 1 (+1)

*Decrement operator* performs operation on operand, a number, and decreases its value by 1 (-1)

Both operators **require a variable with numeric value** as an operand.

```js
let n = 5

// Increment operator
++n
n++
console.log(n) // -> 7, increment twice

let m = 10

// Decrement operator
--m
m--
console.log(m) // -> 8, decrement twice
```

## Prefix vs postfix position of operators
### Prefix
Result of operation = changed number

### Postfix
Result of operation = unchanged number

*In both cases operand variable value is changed.*

So there are 2 aspects:
1. Variable value is changed in both cases
2. There is also a return value of this operation, and it differs depending on the position of the operator

```js
let k = 89
// Used before the variable, PREfix
console.log(++k) // -> 90 (return product of operation)
console.log(k) // -> 90 (value of var)

// Used after the variable, POSTfix
let l = 100
console.log(l++) // -> 100 (return product of operation)
console.log(l) // -> 101 (value of var)
```
