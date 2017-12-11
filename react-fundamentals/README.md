# ES6 Fundamentals

## ECMA & Standardisation

### ECMA International

The industry association dedicated to the Standardisation of information and communication systems

### TC-39

**Technical Committee 39** is the committee responsible for pushing and agreeing changes to the standard.

### Stages
 * **Stage 0** - Strawman
Reviewed at a TC-39 meeting
 * **Stage 1** - Proposal
Champion identified, Examples of usage. Identify concerns.
 * **Stage 2** - Draft
Description of syntax.
 * **Stage 3** - Candidate
Tests written. Spec signoff

New release every year. Stage 4 features included in new release.

# New Cool Stuff

## Array/Object De-structuring! Yay!

Array/object de-structuring allows us more easily extract each of the array/objects properties into user readable variables

```
// Object de-structuring
var user = {
  name: 'Ross',
  email: 'rossdowthwaite@gmail.com',
  location: 'Brighton'
}
var { name, email, location } = user;

// Array de-structuring
var user = ['Ross', 'rossdowthwaite@gmail.com', 'Brighton' ];
var [name, email, location] = user;

// CSV de-structuring
var csv = 'Ross, rossdowthwaite@gmail.com, Brighton';
var [name, email, location] = csv.split(',');
```

Rename properties during extraction:

```
var user = {
  n: 'Ross',
  e: 'rossdowthwaite@gmail.com',
  l: 'Brighton'
}
var { n: name, e: email, l: location } = user;
```

Default values:

```
function getUser({name='defaultName', email='defaultEmail', location='defaultLocation' }){
  // stuff
}

getUser({
  name: 'Ross',
  email: 'rossdowthwaite@gmail.com',
  location: 'Brighton'
})
```

## Shorthand property methods

```
function formatMessage (name, avatar) {
  return {
    name: name,
    avatar: avatar,
    save: function () {
      //save
    }
  }
}
```
can become

```
function formatMessage (name, avatar) {
  return {
    name, // no need for prop name if it is the same
    avatar,
    save () { // Can remove function def too :)
      //save
    }
  }
}
```

## Computed Property names
old way

```
function objectify (key, value) {
  let obj = {}
    obj[key] = value;
    return obj
}
```
new way

```
function objectify () {
  return {
    [key]: value
  }
}
```

### Template strings
```
function greeting(name) {
  return `hello, ${name}`;
}
```
**note:** back ticks!!!


## Arrow functions

* **Implicit return**: return block can be removed if all on same line. 
* **this** context is passed down to the function scope. So no need to use ```bind()```

## Default Parameters

**Old way**

```
function calculatePayment(price, salesTax, discount) {
	salesTax = salesTax || 0.047;
	discount = discount || 0 
}
```
above method breaks when new value is ```0``` because it is falsey

so...

```
function calculatePayment(price, salesTax, discount) {
	salesTax = typeof salesTax === 'undefined' ? 0.047 : salesTax;
	discount = typeof discount === 'undefined' ? 0 : discount; 
}
```
even worse :(

**New way**

```
function calculatePayment(price, salesTax = 0.047, discount = 0) {
	// 
}
```
Wow! :)

## Modules, Exports, Imports and named imports


```
// math.js
export function add(x,y) {
	return x + y
}

export function multiply(x,y) {
	return x * y
}

export default function divide(x,y) {
	return x / y
}

// main.js
import divide, {add, mulitply} from './math'
// or
import * from './math'

add(1,2) // 3
multiply(2,4) // 12
```

#### Named imports

**Old way**

```
import ReactRouter from 'react-router';
const Route = ReactRouter.Route;
const Link = ReactRouter.Link;
const Router = ReactRouter.Router;
```

**New Way**

Because of de-structuring we can do this:

```
import { Route, Link, Router } from 'react-router';
```

## Async/Await

**Allows you to write asynchronous code that appears sychronous**

**note:** 

 * Every async function you write will return a promise.
 * Every single thing you await will ordinarily be a promise.

e.g. Given the promise below

```
// The promise 
function getUser() {
	return new Promise((resolve, reject) => {
		setTimout(() => resolve({name: 'Ross'}), 200)
	}
}
```
We can then use async/await to get the result instead on using ```.then```

```
async function handleGetUser() {
	var user = await getUser()
	console.log(user);
}
```

extended with error handling:

```
async function handleGetUser() {
	try {
		var user = await getUser()
		console.log(user);
	} catch (error) {
		console.log('Error in handleGetUser', error)
	}
}
```

 