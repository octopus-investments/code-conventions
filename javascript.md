# Javascript code style

We adhere to most of the rules in the [JavaScript Standard Style](https://standardjs.com/rules.html) document but we differ in some ways.

#### 1.Semicolons
- If you join a project that is not using them, do not add them
- If you join a project that is using them, do not remove them
- If you are starting a new project then use semicolons

#### 2.Variables
- Always use const or let to declare variables. Not doing so will result in global variables.
- Use const for all of your references; avoid using var (prevents you reassign your references)
- Use let if you must re-assign references (let is block-scoped rather than function-scoped)
- Group all your consts and then group all your lets

```js
// Bad
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
let length
```

- Use readable variable names
```js
// Bad
setTimeout(blastOff, 86400000);
```

```js
// Good
const MILLISECONDS_IN_A_DAY = 86_400_000;

setTimeout(blastOff, MILLISECONDS_IN_A_DAY);
```

- [use searchable names](https://github.com/ryanmcdermott/clean-code-javascript#use-searchable-names)
```js
// Bad
let i;
```

```js
// Good
let integer;
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
 
// Goodx
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

#### 12.For functions with more than 3 arguments use an object instead of multiple arguments


```js
// Bad
function createMenu(title, body, buttonText, cancellable) {
  // ...
}

createMenu("Foo", "Bar", "Baz", true);
 
// Good
function createMenu({ title, body, buttonText, cancellable }) {
  // ...
}

createMenu({
  title: "Foo",
  body: "Bar",
  buttonText: "Baz",
  cancellable: true
});
```

** Possibly add eslint rule for this**

#### 13.Functions should do one thing

Farid to find goo example of this


#### 14.Functions names should describe what the function does


```js
// Bad
function addToDate(date, month) {
  // ...
}

const date = new Date();

// It's hard to tell from the function name what is added
addToDate(date, 1);

 
// Good
function addMonthToDate(month, date) {
  // ...
}

const date = new Date();
addMonthToDate(1, date);
```
** [Read avoid side effects part 2](https://github.com/ryanmcdermott/clean-code-javascript#avoid-side-effects-part-2) **


#### 14.Avoid negative conditionals


```js
// Bad
function isDOMNodeNotPresent(node) {
  // ...
}

if (!isDOMNodeNotPresent(node)) {
  // ...
}
 
// Good
function isDOMNodePresent(node) {
  // ...
}

if (isDOMNodePresent(node)) {
  // ...
}
```
#### 15. Use the correct console method && don't ignore errors

Bad:
```js
try {
  functionThatMightThrow();
} catch (error) {
  console.log(error);
}
```

Good:
```js
try {
  functionThatMightThrow();
} catch (error) {
  // One option (more noisy than console.log):
  console.error(error);
  // Another option:
  notifyUserOfError(error);
  // Another option:
  reportErrorToService(error);
  // OR do all three!
}
```

### Formatting

#### 1. Use consistent capitalization

Bad:
```js
const DAYS_IN_WEEK = 7;
const daysInMonth = 30;

const songs = ["Back In Black", "Stairway to Heaven", "Hey Jude"];
const Artists = ["ACDC", "Led Zeppelin", "The Beatles"];

function eraseDatabase() {}
function restore_database() {}

class animal {}
class Alpaca {}
```

Good:
```js
const DAYS_IN_WEEK = 7;
const DAYS_IN_MONTH = 30;

const SONGS = ["Back In Black", "Stairway to Heaven", "Hey Jude"];
const ARTISTS = ["ACDC", "Led Zeppelin", "The Beatles"];

function eraseDatabase() {}
function restoreDatabase() {}

class Animal {}
class Alpaca {}
```

#### 2. Function callers and callees should be close
https://github.com/ryanmcdermott/clean-code-javascript#function-callers-and-callees-should-be-close

#### 3.Only comment things that have business logic complexity.
https://github.com/ryanmcdermott/clean-code-javascript#only-comment-things-that-have-business-logic-complexity

