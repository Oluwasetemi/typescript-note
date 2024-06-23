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

- Downleveling: You can use the target flag to specify the version of JavaScript that the TypeScript compiler should output. The default is ES3.

- Emitting with Errors: You can use the noEmitOnError flag to prevent the TypeScript compiler from emitting JavaScript code if there are any errors.

- Explicit Types: You can use the noImplicitAny flag to prevent TypeScript from inferring the any type.

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

</v-clicks>

---

# Everyday Types
The primitives, any, Type annotations on variables, Functions, Object types, Union Types, Type Aliases, Interfaces, Type Assertions, Literal Types, null and undefined, Enums

````md magic-move
```ts
let person: string | number = "OjoT99";

if (typeof person === "string") {
  person.split("T");
} else {
  // only number
  // person.toFixed(2);
}

let age: number = 99;

let isAltSchoolStudent = false;
let nothing = null;
let something = undefined;

let arrayOfScores = [99, 45, 56, 67, 99];
let arrayOfScores2: number[] = [99, 45, 56, 67, 99];

let arrayOfNames: string[] = ["bisi", "sola", "augustina", "typescritina"];

let arrayOfTruths = [true, false];

let names: Array<string> = ["dancing", "eating", "sleeping"];
// <> -> generics  Array<number> Array<boolean> Array<null>

let arrayInsideArrays = [["a"], ["b"]];

let newArr = [undefined];

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

// mixing types
const specialArr: Array<number | string | [] | {}> = [
  "name",
  99,
  {},
  [],
  "ginia",
  100,
];

let result: number[] = person.split("T");

result;

console.log(result);
console.log("Hello", "AltSchool");

// any, function, specific type
let user: "student" | "admin";

user = "temi";

user = "admin";

// typing return values
function add(): number {
  console.log("hello");
  return 99;
}

// typing arguments
function add2(a: number, b: number): number {
  return a + b;
}

add2(99, 78);

// function overloading

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

// type assertion as
//

// type alias
type Person = {
  name: string;
  age: number;
};

let person2: Person = {
  name: "ade",
  age: 99,
};
//
//
// interface
interface Person2 {
  name: string;
  age: number;
}

function greet2(person: Person2): string {
  return `Hello ${person.name}`;
}

greet2({ name: "ade", age: 99 });
//
// let res = JSON.parse('{"name": "ade"}') as { name: string };

// 'satifies', 'as const', '!'
//
const addTwoNumbers = (a: number, b: number): number => {
  return a + b;
};

interface Params {
  a: number;
  b: number;
}

const addTwoNumberObject = (params: { a: number; b: number }): number => {
  return params.a + params.b;
};

interface ThreeParams extends Params {
  c: number;
}

// conditional type
type NewParams = ThreeParams extends Params ? string : number;

const addThreeNumberObject = (params: ThreeParams): number => {
  return params.a + params.b + params.c;
};

addThreeNumberObject({ a: 99, b: 78, c: 100 });

// make b optional
const addTwoNumberObject2 = (params: { a: number; b?: number }): number => {
  if (params.b) {
    return params.a + params.b;
  }
  return params.a;
};

console.log(addTwoNumberObject2({ a: 99 }));

const addTwoNumberObject3 = (params: { a?: number; b?: number }): number => {
  if (params.a) {
    return params.a;
  }

  if (params.b) {
    return params.b;
  }

  return 5;
};

addTwoNumberObject3({});

const addTwoNumber3 = (a: number = 2, b: number = 5) => {
  return a + b;
};

addTwoNumber3();

type Admin = {
  name: boolean;
};

function getPersonName(admin: Admin) {
  return admin.name;
}
let client = "name";
getPersonName({ name: false });

type AdminModified = {
  name: string;
  role: "client" | "admin" | "superadmin";
};

function getPersonString(admin: AdminModified) {
  return `${admin.name} is a ${admin.role}`;
}

getPersonString({ name: "ken", role: "superadmin" });

type Post = {
  title: string;
  author: string;
  id: number;
  body: string;
};

type AdminWithPosts = {
  posts: Array<Post>;
  name: string;
  role: "client" | "admin" | "superadmin";
};

function getPersonPost(person: AdminWithPosts): Array<Post> {
  return person.posts;
}

let res = getPersonPost({
  posts: [
    {
      title: "hello",
      author: "ken",
      id: 99,
      body: "hello blogpost content ",
    },
  ],
  name: "ken",
  role: "admin",
});

type NewPost = keyof (typeof res)[0]; // "title" | "author" | "id" | "body"
let newPostKey: NewPost = "author";
console.log(newPostKey);

console.log(res);
type GitHubUser = {
  login: string;
  id: number;
  node_id: string;
  avatar_url: string;
  gravatar_id: string;
  url: string;
  html_url: string;
  followers_url: string;
  following_url: string;
  gists_url: string;
  starred_url: string;
  subscriptions_url: string;
  organizations_url: string;
  repos_url: string;
  events_url: string;
  received_events_url: string;
  type: string;
  site_admin: boolean;
  name: string;
  company: string;
  blog: string;
  location: string;
  email: null;
  hireable: null;
  bio: string;
  twitter_username: string;
  public_repos: number;
  public_gists: number;
  followers: number;
  following: number;
  created_at: string;
  updated_at: string;
};

type NewGitHub = Pick<GitHubUser, "login" | "id" | "node_id">;

let newGitHub: NewGitHub = {
  login: "ade",
  id: 99,
  node_id: "node_id",
};

type newGitHubModified = Omit<NewGitHub, "node_id">;

let newGitHubModified: newGitHubModified = {
  login: "ade",
  id: 99,
};

async function fetchGitHubUser(username: string) {
  return fetch(`https://api.github.com/users/${username}`).then((res) =>
    res.json(),
  );
}



(async () => {
  let githubUser = await fetchGitHubUser("Oluwasetemi");
  console.log(githubUser.avatar_url);
})();

const listOfStudent = new Set<string>();
listOfStudent.add("ade");
listOfStudent.add("ade");

listOfStudent.has("ade");

console.log(listOfStudent);

let mapOfStudentToScores = new Map<string, number>();
mapOfStudentToScores.set("ade", 99);
console.log(mapOfStudentToScores);
mapOfStudentToScores;

// tuples
let tuple: [string, number] = ["ade", 99];

let color: [number, number, number, number?];

color = [255, 0, 0, 0.1];
// rgba

let colorString = `rgb(${color.join(", ")})`;

// unions |
let str: number | string;

// at the level of types and inteface
let advancePostU: Post | { tags: string[] } = {
  title: "hello",
  id: 1,
  author: "Authur Ts",
  body: "hello body",
  // tags: ['hello', 'world']
};

// intersection &
type Tags = { tags: string[] };
let advancePost: Post & Tags = {
  title: "hello",
  id: 1,
  author: "Authur Ts",
  body: "hello body",
  tags: ["hello", "world"],
};

let NewStringIndex: { [index: number]: string };

NewStringIndex = ["1", "2", "3", "4", "5"];

// NewStringIndex = {
//   name: "ade",
//   age: "99",
// };

NewStringIndex[0] = "hello";

NewStringIndex["job"] = "developer";

let arrOfCommenter: readonly string[] = ["ade", "bisi", "sola"];

arrOfCommenter.push("aderemi");

let arrOfCommenter2: ReadonlyArray<string> = ["ade", "bisi", "sola"];
arrOfCommenter2.push("aderemi");

function longest<Type extends { length: number }>(a: Type, b: Type) {
  if (a.length >= b.length) {
    return a;
  } else {
    return b;
  }
}

let res34 = longest({ length: 4 }, { length: 6 });

function merge<T, U>(firstObject: T, secondObject: U): T & U {
  return {
    ...firstObject,
    ...secondObject,
  };
}

type Result<T extends Function> = T extends (...args: never[]) => infer R
  ? R
  : never;

add2(2, 4);

let res35 = merge({ name: "ade" }, { age: 99 });
let res37 = merge({ school: "AltSchool" }, { job: "cleaner" });

// enums - user (ADMIN, CLIENT, SUPERADMIN)
//
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

function checkUserRole(user: User): string {
  const { role } = user;
  if (role === Role.ADMIN) {
    // narrowing
    // type guard
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

// Type manipulation - keyof, typeof, in, infer, extends, in, as, is, &

// keyof 'id' | role | 'name' | 'address'
// type U = keyof {x: string, y: number} // 'x' | 'y'
type KeyOfUserType = keyof User;
type Arrayish = { [n: number]: string }; // string[]
type keyOfArray = keyof Arrayish;

let sampleArray: { [n: number]: string } = ["ade", "bisi", "sola"];

let keyOfUser: KeyOfUserType = "name";

console.log(userAltSchool[keyOfUser]);

// typeof
let myName = "ade";
type Name = typeof myName;

type Predicate = (x: unknown) => boolean;
type K = ReturnType<Predicate>;

type CheckUserRole = ReturnType<typeof checkUserRole>;

function f() {
  return { x: 10, y: 3 };
}
// infer
type P = ReturnType<typeof f>;

// indexed access types
type Person3 = { name: string; age: number; address: string };
type Age = Person3["address" | "age"];

// Conditional Types
// SomeType extends OtherType ? TrueType : FalseType
// type Exclude<T, U> = T extends U ? never : T;
// type T = Exclude<"a" | "b" | "c", "a" | "c">; // "b"
//

// mapped types
//
//
type Person4 = {
  [key: string]: string;
};

// Template Literal Types

type World = "world";
type Greeting = `hello ${World}`;
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

```ts {monaco-run} {autorun: false}
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
