# Javascript code style

We adhere to most of the rules in the [JavaScript Standard Style](https://standardjs.com/rules.html) document but we differ in some ways.

#### 1.Semicolons
- If you join a project that is not using them, please do not add them
- If you join a project that is using them, please do not remove them
- They are optional in javascript so you don't have to use them if you don't want to 
TODO: Do some research into the pitfalls

#### 2.Variables
- Always use const or let to declare variables. Not doing so will result in global variables.
- Use const for all of your references; avoid using var (prevents you reassign your references)
- Use let if you must re-assign references (let is block-scoped rather than function-scoped)
- Group all your consts and then group all your lets

```js
// Bad
let i
const items = getItems()
let dragonball
const goSportsTeam = true
let len
```

```js
// Good
const goSportsTeam = true
const items = getItems()
let dragonball
let i
let length
```

#### 3.No leading commas
- Do not end arrays with a comma

```js
// Bad
const story = [
    once
  , upon
  , aTime
]
```

```js
// Good
const story = [
  once,
  upon,
  aTime
]
```

#### 4.Prefer the object spread operator over Object.assign to shallow-copy objects

```js
const original = { a: 1, b: 2 }
// Bad
const copy = Object.assign(original, { c: 3 })
// Good
const copy = { ...original, c: 3 }
```

#### 5.Use the literal syntax for array & object creation

```js
// Bad
const items = new Array()
const item = new Object()
 
// Good
const items = []
const item = {}
```

#### 6.Use object [destructuring](https://wesbos.com/destructuring-objects/) where possible

```js
const obj = {
  one: 1,
  two: 2
}
 
// Bad
const first = obj.one
const second = obj.two
 
// Good
const {one, two} = obj
```

#### 7.Use double quotes for strings
Unless project is using single quotes then stick with that and do not change it.

```js
const str = "Test's name"
```


#### 8.When programmatically building up strings, use template strings instead of concatenation

```js
// Bad
return 'How are you, ' + name + '?'
// Good
return `How are you, ${name}?`
```

#### 9.Always put default parameters last.

```js
// Bad
function handleThings(opts = {}, name) {
  // ...
}
// Good
function handleThings(name, opts = {}) {
  // ...
}
```

#### 10.When you must use an anonymous function use arrow function notation

```js
// Bad
[1, 2, 3].map(function (x) {
  const y = x + 1
  return x * y
})
 
// Good
[1, 2, 3].map(x => {
  const y = x + 1
  return x * y
})
```

#### 11.If your function takes a single argument and doesn’t use braces, omit the parentheses

```js
// Bad
[1, 2, 3].map((x) => x * x)
 
// Good
[1, 2, 3].map(x => x * x)
```
