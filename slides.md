---
theme: seriph
background: https://res.cloudinary.com/drnqdd87d/image/upload/f_auto/nmgakkzd3lmlibnfosps
title: TypeScript Class Notes by @Oluwasetemi
info: |
  TypeScript Class Notes
  making of world class developers with AltSchool Africa.

  Join at [AltSchool Africa](https://altschoolafrica.com)
class: text-center center
highlighter: shiki
drawings:
  persist: false
transition: slide-left
mdc: true
hideInToc: true
titleTemplate: '%s - AltSchool Africa'
author: Oluwasetemi
download: true
exportFilename: ts-note
export:
  format: pdf
  timeout: 1600000
  dark: false
  withClicks: false
  withToc: false
# TODO: add a svg favicon
# favicon: https://oluwasetemi.dev/favicon-32x32.png
overviewSnapshots: true
selectable: true
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
  <a href="https://github.com/Oluwasetemi/typescript-class-note" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-download />
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
hideInToc: true
---

# TypeScript Compiler `tsc`

- The TypeScript compiler is a tool that takes TypeScript code and turns it into JavaScript code.

- The TypeScript compiler can be installed as a Node.js package.

- The TypeScript compiler can be run from the command line.

- The TypeScript compiler can be configured using a configuration file.

- The TypeScript compiler can be used to compile multiple files.

- The TypeScript compiler can be used to compile a project.

```shell
npm install -g typescript

tsc hello.ts

tsc --noEmitOnError hello.ts

tsc --init


```
---
hideInToc: true
---

# tsconfig.json

<v-clicks>


- The tsconfig.json file is a configuration file that tells the TypeScript compiler how to compile your TypeScript code.

- Strictness: You can use the strict flag to enable all strict type-checking options or in the config file. You can opt out of strictness by setting strict to false or `noImplicitAny` to false and `strictNullChecks` to false.

- Downleveling: You can use the target flag to specify the version of JavaScript that the TypeScript compiler should output. The default is ES5.

- Emitting with Errors: You can use the noEmitOnError flag to prevent the TypeScript compiler from emitting JavaScript code if there are any errors.

- Explicit Types: You can use the noImplicitAny flag to prevent TypeScript from inferring the any type.

</v-clicks>

---
hideInToc: true
---

# tsconfig.json

- Erased Types: You can use the noUnusedLocals and noUnusedParameters flags to prevent TypeScript from emitting JavaScript code if there are any unused variables or parameters.

```json
{
  "compilerOptions": {
    "strict": true,
    "noImplicitAny": true,
    "strictNullChecks": true,
    "target": "ES5",
    "noEmitOnError": true
  }
}
```

---

# Everyday Types
The primitives, arrays, objects, functions, type aliases, interfaces, unions, intersections, type assertions, and more

````md magic-move
```ts
// The Primitives - Basic building blocks
let name: string = "OjoT99";
let age: number = 99;
let isAltSchoolStudent: boolean = false;
let nothing: null = null;
let something: undefined = undefined;

// BigInt for large integers
let bigNumber: bigint = 9007199254740991n;

// Symbol for unique identifiers
let uniqueId: symbol = Symbol("id");
```

```ts
// any and unknown - When you don't know the type
let anyValue: any = "hello";
anyValue = 99; // no error
anyValue.toUpperCase(); // no type checking - dangerous!

let unknownValue: unknown = "hello";
// unknownValue.toUpperCase(); // Error! Must check type first
if (typeof unknownValue === "string") {
  unknownValue.toUpperCase(); // OK - type narrowed
}
```

```ts
// Union Types - A value can be one of several types
let person: string | number = "OjoT99";

if (typeof person === "string") {
  person.split("T");
} else {
  // only number
  person.toFixed(2);
}
```

```ts
// Arrays - Collections of values
let arrayOfScores: number[] = [99, 45, 56, 67, 99];
let arrayOfNames: string[] = ["bisi", "sola", "augustina"];

// Alternative generic syntax
let names: Array<string> = ["dancing", "eating", "sleeping"];

// Arrays can hold different types with union
let mixed: (string | number)[] = ["hello", 99, "world", 45];

// Nested arrays
let arrayInsideArrays: string[][] = [["a"], ["b"]];
```

```ts
// Objects - Inline object types
let obj: { name: string; age: number; job?: string } = {
  name: "ade",
  age: 99,
};

// Optional properties with type guards
if (typeof obj.job === "string") {
  console.log(obj.job.toUpperCase());
} else {
  console.log("No job specified");
}
```

```ts
// Record utility type - for flexible object shapes
let profile: Record<string, number> = {
  age: 99,
  height: 6,
  weight: 100,
};

// Record with multiple value types
let objFlex: Record<string, string | number> = {
  name: "lagbaja",
  age: 99,
};
```

```ts
// Literal Types - Specific values as types
let user: "student" | "admin";

user = "student"; // valid
user = "admin"; // valid
// user = "teacher"; // Error: not in the union
```

```ts
// Functions - Basic function typing
function add(a: number, b: number): number {
  return a + b;
}

// Arrow functions
const multiply = (a: number, b: number): number => a * b;

// Optional and default parameters
function greet(name: string, greeting: string = "Hello"): string {
  return `${greeting}, ${name}!`;
}

// Rest parameters
function sum(...numbers: number[]): number {
  return numbers.reduce((total, n) => total + n, 0);
}
```

```ts
// void and never return types
function logMessage(message: string): void {
  console.log(message);
  // no return value
}

function throwError(message: string): never {
  throw new Error(message);
  // never returns (throws or infinite loop)
}

function infiniteLoop(): never {
  while (true) {}
}
```

```ts
// Function overloading - multiple function signatures
function add3(a: number, b: number): number;
function add3(a: string, b: string): string;
function add3(a: any, b: any): any {
  return a + b;
}

add3("Hello", " World"); // string
add3(99, 78); // number
```

```ts
// Type Aliases - Reusable type definitions
type Person = {
  name: string;
  age: number;
  email?: string;
};

let student: Person = {
  name: "ade",
  age: 99,
};
```

```ts
// Interfaces - Another way to define object shapes
interface User {
  name: string;
  age: number;
  email?: string;
}

function greetUser(user: User): string {
  return `Hello ${user.name}`;
}

greetUser({ name: "ade", age: 99 });
```

```ts
// Type vs Interface - When to use which?
// Type: Can represent primitives, unions, tuples
type ID = string | number;
type Point = [number, number];

// Interface: Better for objects, can be extended/merged
interface Animal {
  name: string;
}

interface Dog extends Animal {
  breed: string;
}

// Both work for objects, choose based on your needs!
```

```ts
// Type Assertions - Telling TypeScript the specific type
let parsed = JSON.parse('{"name": "ade"}') as { name: string };
console.log(parsed.name);

// Alternative syntax (not common in JSX/TSX)
let parsed2 = <{ name: string }>JSON.parse('{"name": "ade"}');
```

```ts
// Function parameters as objects
interface Params {
  a: number;
  b: number;
}

const addTwoNumbers = (params: Params): number => {
  return params.a + params.b;
};

addTwoNumbers({ a: 99, b: 78 });
```
```ts
// Extending interfaces - Building on existing types
interface ThreeParams extends Params {
  c: number;
}

const addThreeNumbers = (params: ThreeParams): number => {
  return params.a + params.b + params.c;
};

addThreeNumbers({ a: 99, b: 78, c: 100 });
```

```ts
// Optional parameters in objects
const addNumbers = (params: { a: number; b?: number }): number => {
  if (params.b) {
    return params.a + params.b;
  }
  return params.a;
};

console.log(addNumbers({ a: 99 })); // 99
console.log(addNumbers({ a: 99, b: 1 })); // 100
```

```ts
// Type narrowing with 'in' operator
type Cat = { name: string; meow: () => void };
type Dog = { name: string; bark: () => void };

function makeSound(animal: Cat | Dog) {
  if ("meow" in animal) {
    animal.meow(); // TypeScript knows it's a Cat
  } else {
    animal.bark(); // TypeScript knows it's a Dog
  }
}

// Note: See dedicated Enums section below for detailed coverage
```
````
---
hideInToc: true
---

# Everyday Types - Advanced Patterns

````md magic-move
```ts
// Complex types with literal unions
type Admin = {
  name: string;
  role: "client" | "admin" | "superadmin";
};

function getPersonString(admin: Admin): string {
  return `${admin.name} is a ${admin.role}`;
}

getPersonString({ name: "ken", role: "superadmin" });
```

```ts
// Composing complex types
type Post = {
  title: string;
  author: string;
  id: number;
  body: string;
};

type AdminWithPosts = {
  posts: Post[];
  name: string;
  role: "client" | "admin" | "superadmin";
};

const admin: AdminWithPosts = {
  posts: [
    { title: "TypeScript Tips", author: "ken", id: 1, body: "Content..." }
  ],
  name: "ken",
  role: "admin",
};
```

```ts
// Utility Types - Pick and Omit
type GitHubUser = {
  login: string;
  id: number;
  node_id: string;
  avatar_url: string;
  name: string;
  email: string;
  bio: string;
};

// Pick - Select specific properties
type UserBasic = Pick<GitHubUser, "login" | "id" | "name">;

// Omit - Exclude specific properties
type UserPublic = Omit<GitHubUser, "email">;
```

```ts
// Async Functions and Promises
async function fetchGitHubUser(username: string): Promise<GitHubUser> {
  const response = await fetch(`https://api.github.com/users/${username}`);
  return response.json();
}

// ReturnType - Extract the return type of a function
type FetchResult = ReturnType<typeof fetchGitHubUser>;
// FetchResult is Promise<GitHubUser>

// Awaited - Unwrap a Promise type
type UnwrappedResult = Awaited<ReturnType<typeof fetchGitHubUser>>;
// UnwrappedResult is GitHubUser
```

```ts
// Built-in Collections - Set and Map
const students = new Set<string>();
students.add("ade");
students.add("ade"); // Duplicates ignored
students.has("ade"); // true

const scores = new Map<string, number>();
scores.set("ade", 99);
scores.set("bisi", 87);
scores.get("ade"); // 99
```

```ts
// Tuples - Fixed length arrays with specific types
let person: [string, number] = ["ade", 99];

// Optional tuple elements
let color: [number, number, number, number?];
color = [255, 0, 0, 0.5]; // RGBA

// Tuple with labels (TypeScript 4.0+)
let point: [x: number, y: number] = [10, 20];
```
```ts
// Union Types - OR relationship (can be one type or another)
let id: number | string;
id = 99; // valid
id = "user-123"; // also valid

type PostWithTags = Post | { tags: string[] };

// Intersection Types - AND relationship (must have all properties)
type Tags = { tags: string[] };
type PostWithTagsRequired = Post & Tags;

const blogPost: PostWithTagsRequired = {
  title: "TypeScript Guide",
  id: 1,
  author: "Ade",
  body: "Content here...",
  tags: ["typescript", "tutorial"],
};
```

```ts
// Index Signatures - Dynamic property names
type StringArray = { [index: number]: string };
const names: StringArray = ["ade", "bisi", "sola"];

type StringMap = { [key: string]: string };
const config: StringMap = {
  host: "localhost",
  port: "8080",
  protocol: "http"
};
```

```ts
// Readonly - Immutable types
let commenters: readonly string[] = ["ade", "bisi", "sola"];
// commenters.push("aderemi"); // Error: Property 'push' does not exist

let readonlyArray: ReadonlyArray<string> = ["ade", "bisi", "sola"];
// readonlyArray[0] = "changed"; // Error: Index signature is readonly

type ReadonlyPerson = {
  readonly name: string;
  readonly age: number;
};
```

```ts
// Generics - Write reusable, type-safe code
function longest<Type extends { length: number }>(a: Type, b: Type) {
  if (a.length >= b.length) {
    return a;
  } else {
    return b;
  }
}

longest([1, 2], [1, 2, 3]); // works with arrays
longest("hi", "hello"); // works with strings
```

```ts
// Type Manipulation - keyof operator
type User = {
  id: string;
  name: string;
  email: string;
  age: number;
};

type UserKeys = keyof User; // "id" | "name" | "email" | "age"
let key: UserKeys = "name"; // valid
// let invalid: UserKeys = "address"; // Error!
```

```ts
// typeof operator (type level)
let myName = "ade";
type NameType = typeof myName; // string

const person = { name: "ade", age: 99 };
type PersonType = typeof person; // { name: string; age: number }

function greet(name: string): string {
  return `Hello ${name}`;
}
type GreetType = typeof greet; // (name: string) => string
```

```ts
// Indexed Access Types
type Person = { name: string; age: number; address: string; isActive: boolean };

type PersonName = Person["name"]; // string
type PersonAge = Person["age"]; // number

// Access multiple properties
type PersonInfo = Person["name" | "age"]; // string | number

// Access array element type
type StringArray = string[];
type ArrayElement = StringArray[number]; // string
```

```ts
// Conditional Types - SomeType extends OtherType ? TrueType : FalseType
type IsString<T> = T extends string ? true : false;

type Test1 = IsString<string>; // true
type Test2 = IsString<number>; // false

// Practical example: Exclude utility type
type MyExclude<T, U> = T extends U ? never : T;
type Result = MyExclude<"a" | "b" | "c", "a" | "c">; // "b"
```

```ts
// Conditional Types with infer
type ReturnTypeCustom<T> = T extends (...args: any[]) => infer R ? R : never;

function getUser() {
  return { name: "ade", age: 99 };
}

type UserReturn = ReturnTypeCustom<typeof getUser>;
// { name: string; age: number }

// Extract array element type
type Flatten<T> = T extends Array<infer Item> ? Item : T;
type Num = Flatten<number[]>; // number
type Str = Flatten<string>; // string
```

```ts
// Mapped Types - Transform properties
type Person = {
  name: string;
  age: number;
  email: string;
};

// Make all properties optional
type PartialPerson = {
  [K in keyof Person]?: Person[K];
};

// Make all properties readonly
type ReadonlyPerson = {
  readonly [K in keyof Person]: Person[K];
};
```

```ts
// Built-in Mapped Types
type Person = {
  name: string;
  age: number;
  email: string;
};

// Partial - makes all properties optional
type PartialPerson = Partial<Person>;

// Required - makes all properties required
type RequiredPerson = Required<PartialPerson>;

// Readonly - makes all properties readonly
type ReadonlyPerson = Readonly<Person>;

// Record - construct object type
type Roles = Record<"admin" | "user" | "guest", { permissions: string[] }>;
```

```ts
// Template Literal Types
type World = "world";
type Greeting = `hello ${World}`; // "hello world"

type EmailDomain = "gmail" | "yahoo" | "outlook";
type Email = `user@${EmailDomain}.com`;
// "user@gmail.com" | "user@yahoo.com" | "user@outlook.com"

// Practical example: Event names
type Events = "click" | "focus" | "blur";
type EventHandlers = `on${Capitalize<Events>}`;
// "onClick" | "onFocus" | "onBlur"
```

```ts
// Advanced Operators - satisfies, as const, and !
type Color = { r: number; g: number; b: number } | string;

// satisfies - Type check without widening
const validColor = { r: 255, g: 0, b: 0 } satisfies Color;

// as const - Create readonly literal types
const config = {
  host: "localhost",
  port: 8080
} as const;

// ! - Non-null assertion (use with caution!)
const element = document.getElementById("app")!;
```
````


---
hideInToc: true
---

## Type Error Example

This example shows a common type error - assigning the wrong type:

```ts twoslash
let person: string | number = "helloTtypescript";

// Error: Type 'string[]' is not assignable to type 'number[]'
let result: number[] = person.split("T");
//  //^?

console.log(result);
console.log("Hello", "AltSchool");
```

---

# Function Signatures and Callbacks
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

// Define the object type that will be constructed
type SomeObject = {
  message: string;
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

```ts {monaco-run} {autorun: true}
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

```ts {monaco-run} {autorun: true}
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

# Creating Generic Functions

````md magic-move
```ts
// Problem: We need a function that works with numbers
function getFirstNumber(arr: number[]): number {
  return arr[0];
}

let num = getFirstNumber([1, 2, 3]); // Works!
// But what if we need strings?
```

```ts
// Problem: Now we need a separate function for strings
function getFirstNumber(arr: number[]): number {
  return arr[0];
}

function getFirstString(arr: string[]): string {
  return arr[0];
}

let num = getFirstNumber([1, 2, 3]);
let str = getFirstString(['a', 'b', 'c']);
// This is repetitive and not scalable!
```

```ts
// Bad Solution: Using 'any' loses type safety
function getFirst(arr: any[]): any {
  return arr[0];
}

let num = getFirst([1, 2, 3]); // Type is 'any' - not safe!
let str = getFirst(['a', 'b', 'c']); // Type is 'any' - not safe!

// We lost all type information
num.toUpperCase(); // No error but will crash at runtime!
```

```ts
// Solution: Generic Function - Use a Type Parameter
function getFirst<Type>(arr: Type[]): Type {
  return arr[0];
}

let num = getFirst([1, 2, 3]); // Type is 'number'
let str = getFirst(['a', 'b', 'c']); // Type is 'string'

// TypeScript inferred the types automatically!
// num.toUpperCase(); // Error: Property doesn't exist on number ✓
```

```ts
// Generic Function - Explicit Type Arguments
function getFirst<Type>(arr: Type[]): Type {
  return arr[0];
}

// TypeScript can infer the type
let num = getFirst([1, 2, 3]);

// Or you can be explicit
let str = getFirst<string>(['a', 'b', 'c']);
let bool = getFirst<boolean>([true, false]);

// Works with any type!
```

```ts
// Generic Function - Multiple Type Parameters
function pair<T, U>(first: T, second: U): [T, U] {
  return [first, second];
}

let p1 = pair("hello", 42); // [string, number]
let p2 = pair(true, "world"); // [boolean, string]
let p3 = pair(100, 200); // [number, number]

// Each parameter can be a different type!
```

```ts
// Generic Constraints - Limiting what types can be used
function getLength<Type extends { length: number }>(value: Type): number {
  return value.length;
}

getLength("hello"); // Works - strings have length
getLength([1, 2, 3]); // Works - arrays have length
getLength({ length: 10 }); // Works - object has length

// getLength(42); // Error: number doesn't have length property ✓
```

```ts
// Real-world Example: Generic Array Filter
function filterArray<T>(arr: T[], predicate: (item: T) => boolean): T[] {
  return arr.filter(predicate);
}

let numbers = filterArray([1, 2, 3, 4], n => n > 2);
// numbers is number[]

let names = filterArray(['ade', 'bisi', 'ojo'], name => name.length > 3);
// names is string[]

// One function, works with any type, keeps type safety!
```
````

---
hideInToc: true
---
## Exercise: Solve this using TS Generics

**Challenge**: The code below has a type error. Fix it by converting the function to use generics so it can work with any array type.

```ts {monaco-run} {autorun: true}
// TODO: Convert this to a generic function
function getRandomNumberElement(items: number[]): number {
  let randomIndex = Math.floor(Math.random() * items.length);
  return items[randomIndex];
}

// This will cause a type error - string[] is not assignable to number[]
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

```ts {monaco-run} {autorun: true}
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

```ts {monaco-run} {autorun: true}
function merge<T, U>(firstObject: T, secondObject: U): T & U {
  return {
    ...firstObject,
    ...secondObject,
  };
}

type Result<T extends Function> = T extends (...args: never[]) => infer R
  ? R
  : never;

let res35 = merge({ name: "ade" }, { age: 99 });
console.log(res35)
let res37 = merge({ school: "AltSchool" }, { job: "cleaner" });
console.log(res37)

```
---
hideInToc: true
---

```ts {monaco-run} {autorun: true}
type FuncWithOneObjectArgument<P extends { [x: string]: any }, R> = (
  props: P
) => R;

type DestructuredArgsOfFunction<
  F extends FuncWithOneObjectArgument<any, any>
> = F extends FuncWithOneObjectArgument<infer P, any> ? P : never;

const myFunction = (props: { x: number; y: number }): string => {
  return "OK";
};

const props: DestructuredArgsOfFunction<typeof myFunction> = {
  x: 1,
  y: 2
};


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

# Enums

```ts {monaco}
enum Role {
  ADMIN,
  CLIENT,
  SUPERADMIN,
}

type User = {
  id: string;
  // enum
  role: Role;
  // union types
  // role: "CLIENT" | "ADMIN" | "SUPERADMIN";
  name: string;
  address: string;
};
```

---
hideInToc: true
---


```ts {monaco-run}
enum Role { ADMIN, CLIENT, SUPERADMIN, };
type User = { id: string; role: Role; name: string; address: string; };
// union types // role: "CLIENT" | "ADMIN" | "SUPERADMIN";

function checkUserRole(user: User): string {
  const { role } = user;
  if (role === Role.ADMIN) {
    return "admin";
  } else if (role === Role.CLIENT) {
    return "client";
  }
  // Role.SUPERADMIN;
  return "superadmin";
}

let userAltSchool: User = {
  id: "001",
  role: Role.ADMIN,
  name: "ade ojo",
  address: "lagos",
};

let resultAltSchool = checkUserRole(userAltSchool);
console.log(resultAltSchool);
```

---
layout: center
class: text-center
hideInToc: true
---

# Thank You!

You've learned TypeScript fundamentals

<div class="pt-12">
  <span class="text-6xl">🎉</span>
</div>

## What's Next?

<v-clicks>

- Practice with real projects using vite
- Explore advanced TypeScript patterns
- Build type-safe applications
- Over to the [React TypeScript Cheatsheet](https://react-typescript-cheatsheet.netlify.app/docs/basic/getting-started/basic_type_example)

</v-clicks>

<style scoped>
ul {
  list-style-type: none;
}
</style>

<div class="pt-12 text-sm">
  <p>Follow me: <a href="https://twitter.com/setemiojo" target="_blank">@iamsetemi</a></p>
  <p>GitHub: <a href="https://github.com/Oluwasetemi" target="_blank">@Oluwasetemi</a></p>
</div>

<div class="abs-br m-6 flex gap-2">
  <a href="https://altschoolafrica.com" target="_blank" alt="AltSchool Africa"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    AltSchool Africa
  </a>
</div>

---
layout: center
class: text-center
hideInToc: true
---

# Questions?

<div class="pt-12">
  <span class="text-8xl">🤔</span>
</div>

<div class="pt-12">
  <p class="text-2xl">Feel free to ask anything about TypeScript</p>
</div>

<div class="pt-8 text-sm opacity-75">
  <p>Resources:</p>
  <p><a href="https://www.typescriptlang.org/" target="_blank">TypeScript Official Docs</a></p>
  <p><a href="https://github.com/Oluwasetemi/typescript-class-note" target="_blank">Course Repository</a></p>
</div>
