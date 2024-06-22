---
theme: seriph
background: https://res.cloudinary.com/drnqdd87d/image/upload/f_auto/nmgakkzd3lmlibnfosps
title: TypeScript Class Notes
info: |
  ## TypeScript Class Notes

  making of world class developers with AltSchool Africa.

  Join at [AltSchool Africa](https://altschoolafrica.com)
class: text-center center
highlighter: shiki
drawings:
  persist: false
transition: slide-left
mdc: true
hideInToc: true
---

# TypeScript Class Notes

AltSchool Africa

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Are you ready to learn TypeScript? Press <kbd>space</kbd> on your keyboard <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/Oluwasetemi/typescript-class-note" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->
---
class: grid place-content-center
hideInToc: true
---

# What is TypeScript?

<br>
TypeScript is a strongly typed programming language that builds on JavaScript, giving you better tooling at any scale.

<v-click>

## JavaScript and More

TypeScript adds additional syntax to JavaScript to support a tighter integration with your editor. Catch errors early in your editor.
A Result You Can Trust

</v-click>

<v-click>

TypeScript code converts to JavaScript, which runs anywhere JavaScript runs: In a browser, on Node.js or Deno and in your apps.
Safety at Scale

</v-click>

<v-click>
TypeScript understands JavaScript and uses type inference to give you great tooling without additional code

</v-click>
<br>
<br>

Read more about [TypeScript?](https://www.typescriptlang.org/)

<style>
h1,h2 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
layout: two-cols
layoutClass: gap-16
transition: slide-up
class: grid place-content-center
hideInToc: true
---

# Table of Content

What are the things we will be covering?

::right::

<Toc v-click minDepth="1" maxDepth="2"></Toc>

---

# The Basics

- Static type-checking
- Non-exception Failures
- Types for Tooling
- tsc, the TypeScript compiler
- Emitting with Errors
- Explicit Types
- Erased Types
- Downleveling
- Strictness
- noImplicitAny
- strictNullChecks

---

# Everyday Types

````md magic-move
```ts {*|1|3-10|12|14-16|*}
let person: string | number = "helloTtypescript";

let result: number[] = person.split("T");

let age: number = 99;

let isAltSchoolStudent = false;
let nothing = null;
let something = undefined;
```

```ts
if (typeof person === "string") {
  person.split("Y");
} else if (typeof person === "number") {
  // only number
  // person.toFixed(2);
} else {
  person;
}
```

```ts
let arrayOfScores = [99, 45, 56, 67, 99];
let arrayOfScores2: number[] = [99, 45, 56, 67, 99];

let arrayOfNames: string[] = ["bisi", "sola", "augustina", "typescritina"];

let arrayOfTruths = [true, false];

let names: Array<string> = ["dancing", "eating", "sleeping"];
// <> -> generics  Array<number> Array<boolean> Array<null>

let arrayInsideArrays = [["a"], ["b"]];

let newArr = [undefined];
```

```ts
let obj: { name: string; age: number; job?: string } = {
  name: "ade",
  age: 99,
};

function greet(msg: string): string {
  return msg + "Hi :dance:";
}

if (typeof obj.job === "string") {
  // typeguard
  greet(obj.job);
} else {
  // strictly undefined
  obj.job;
}
```

```ts
let profile: Record<string, number> = {
  age: 99,
  height: 6,
  weight: 100,
};

let objFlex: Record<string | symbol, string | boolean | number> = {};

objFlex.name = "lagbaja";
objFlex.animal = "cat";
objFlex[Symbol("id")] = true;
// any or never
//
let objFlexNumber: Record<string, number> = {
  age: 99,
};
```

```ts
const specialArr: Array<number | string | [] | {}> = [
  99,
  "name",
  {},
  [],
  "ginia",
  100,
];
```

```ts
let user: "student" | "admin";

user = "temi";

user = "admin";
```
````


---

```ts twoslash
let person: string | number = "helloTtypescript";

let result: number[] = person.split("T");
//  ^?

console.log(result);
console.log("Hello", "AltSchool");
```


---

# functions
````md magic-move
```ts
function greeter(fn: (a: string) => void) {
  fn("Hello, World");
}

function printToConsole(s: string) {
  console.log(s);
}

greeter(printToConsole);
```

```ts
type GreetFunction = (a: string) => void;

function greeter(fn: GreetFunction) {
  fn("Hello, World");
}

function printToConsole(s: string) {
  console.log(s);
}

greeter(printToConsole);
```

```ts
type DescribableFunction = {
  description: string;
  (someArg: number): boolean;
};

function doSomething(fn: DescribableFunction) {
  console.log(fn.description + " returned " + fn(6));
};

function myFunc(someArg: number) {
  return someArg > 3;
}
myFunc.description = "default description";

doSomething(myFunc);
```

```ts
// call signatures and constructors
type DescribableFunction = {
  description: string;
  (someArg: number): boolean;
};

type SomeConstructor = {
  new (s: string): SomeObject;
};
function fn(ctor: SomeConstructor) {
  return new ctor("hello");
}
```
````

---

```ts {monaco-run} {autorun: false, line: true}
type DescribableFunction = {
  description: string;
  (someArg: number): boolean;
};
function doSomething(fn: DescribableFunction) {
  console.log(fn.description + " returned " + fn(6));
}

function myFunc(someArg: number) {
  return someArg > 3;
}
myFunc.description = "default description";

doSomething(myFunc);
```

---

# Peek into Generics

<!-- This allow you to embed external code blocks -->
<<< @/snippets/external.ts#snippet

<br />

# Put `emptyArray` function to work


<v-click>

```ts {monaco-run} {autorun: false}
import { emptyArray } from './external'

console.log(emptyArray<number>(10).reduce(fib => [...fib, fib.at(-1)! + fib.at(-2)!], [1, 1]))
```

</v-click>

<v-click>

```ts twoslash
function firstElement<Type>(arr: Type[]): Type | undefined {
  return arr[0];
}
// Note that we didn’t have to specify Type in this sample.
// The type was inferred - chosen automatically - by TypeScript.
let s1 = firstElement([1, 2, 4, 5])
let s2 = firstElement(['hello', 'dance'])
```

</v-click>

---
hideInToc: true
---
## Solve this using TS Generics

```ts {monaco-run} {autorun: false}
function getRandomNumberElement(items: number[]): number {
  let randomIndex = Math.floor(Math.random() * items.length);
  return items[randomIndex];
}

let randyValue = getRandomNumberElement(['ayo', 'ade', 'ojo', 'jerry'])

console.log(randyValue)
```
---
hideInToc: true

---
```ts {monaco}
function map<Input, Output>(arr: Input[], func: (arg: Input) => Output): Output[] {
  return arr.map(func);
}

// Parameter 'n' is of type 'string'
// 'parsed' is of type 'number[]'
const parsed = map(["1", "2", "3"], (n) => parseInt(n));
```

<v-click>

```ts twoslash
function longest<Type extends { length: number }>(a: Type, b: Type) {
  if (a.length >= b.length) {
    return a;
  } else {
    return b;
  }
}

// longerArray is of type 'number[]'
const longerArray = longest([1, 2], [1, 2, 3]);
// longerString is of type 'alice' | 'bob'
const longerString = longest("alice", "bob");
// Error! Numbers don't have a 'length' property
const notOK = longest(10, 100);
```

</v-click>
---
hideInToc: true
---

```ts {monaco-run}
function minimumLength<Type extends { length: number }>(
  obj: Type,
  minimum: number
): Type {
  if (obj.length >= minimum) {
    return obj;
  } else {
    return { length: minimum };
  }
}

// 'arr' gets value { length: 6 }
const arr = minimumLength([1, 2, 3], 6);
// and crashes here because arrays have
// a 'slice' method, but not the returned object!
console.log(arr.slice(0));
```

---
hideInToc: true
---

```ts {monaco-run} {autorun: false}
function combine<Type>(arr1: Type[], arr2: Type[]): Type[] {
  return arr1.concat(arr2);
}

// const arr = combine([1, 2, 3], ["hello"]);
const arr = combine<string | number>([1, 2, 3], ["hello"]);

console.log(arr)

```

---
hideInToc: true
---

# Guideline to writing good generics

<v-click>

- Push Type Parameters Down

</v-click>
<v-click>

- Use Fewer Type Parameters

```ts twoslash
function filter1<Type>(arr: Type[], func: (arg: Type) => boolean): Type[] {
  return arr.filter(func);
}

function filter2<Type, Func extends (arg: Type) => boolean>(
  arr: Type[],
  func: Func
): Type[] {
  return arr.filter(func);
}

const val = filter1([1, 2, 3, 4], n => n % 2 === 0)
const val2 = filter2([1, 2, 3, 4], n => n % 2 === 0)

```

</v-click>
<v-click>

- Type Parameters(Or any annotation used) Should Appear Twice

</v-click>

---

# function overloading

```ts twoslash

function add3(a: number, b: number): number;
function add3(a: string, b: string): string;
function add3(a: any, b: any): any {
  return a + b;
}

add3("na", "me");
add3(99, 78);
let name2: any = "wale";
let age2: any = 99;
add3(name2, age2);
```



---
