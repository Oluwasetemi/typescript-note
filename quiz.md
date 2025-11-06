# TypeScript Quiz and Test

## Part A: Multiple Choice Questions (30 points)

### Section 1: Primitives and Basic Types (10 questions)

**1. Which of the following is NOT a primitive type in TypeScript?**
   - A) string
   - B) number
   - C) array
   - D) boolean

**2. What is the difference between `any` and `unknown`?**
   - A) They are the same
   - B) `unknown` requires type checking before use, `any` doesn't
   - C) `any` is safer than `unknown`
   - D) `unknown` can only be used with strings

**3. What will be the type of `x` in this code: `let x = "hello"`?**
   - A) any
   - B) unknown
   - C) string
   - D) String

**4. Which type should a function use when it doesn't return a value?**
   - A) null
   - B) undefined
   - C) void
   - D) never

**5. What does the `never` type represent?**
   - A) A function that doesn't return anything
   - B) A function that never returns (throws error or infinite loop)
   - C) A variable that can never be assigned
   - D) An optional type

**6. How do you define an optional property in an interface?**
   - A) `name?: string`
   - B) `name: string?`
   - C) `optional name: string`
   - D) `name: string | undefined`

**7. What is the correct syntax for a tuple with a string and a number?**
   - A) `[string, number]`
   - B) `{string, number}`
   - C) `Array<string, number>`
   - D) `(string, number)`

**8. Which operator is used for union types?**
   - A) &
   - B) |
   - C) ||
   - D) +

**9. What does `readonly` do to an array?**
   - A) Makes it faster
   - B) Prevents modification of the array
   - C) Makes it private
   - D) Allows only reading one element

**10. What is a literal type?**
   - A) A type that uses the `literal` keyword
   - B) A type that represents specific values (e.g., "admin" | "user")
   - C) A type for strings only
   - D) A deprecated TypeScript feature

### Section 2: Functions and Generics (10 questions)

**11. What is the return type of this function: `function greet(name: string) { console.log(name); }`?**
   - A) string
   - B) void
   - C) undefined
   - D) never

**12. What syntax is used for rest parameters in TypeScript?**
   - A) `...args: number[]`
   - B) `args[]: number`
   - C) `args...: number`
   - D) `rest args: number[]`

**13. What is function overloading?**
   - A) Calling a function too many times
   - B) Multiple function signatures for the same function name
   - C) A function that never completes
   - D) Error handling in functions

**14. What does the generic type parameter `<T>` represent?**
   - A) A template
   - B) A placeholder for any type that will be determined later
   - C) The "Type" keyword
   - D) A required type annotation

**15. How do you constrain a generic type to have a `length` property?**
   - A) `<T extends { length: number }>`
   - B) `<T where length: number>`
   - C) `<T: { length: number }>`
   - D) `<T.length: number>`

**16. What is the purpose of generics?**
   - A) To make code run faster
   - B) To create reusable, type-safe components
   - C) To avoid writing functions
   - D) To generate random types

**17. Can you use multiple type parameters in a generic function?**
   - A) No, only one is allowed
   - B) Yes, like `<T, U>`
   - C) Only in classes
   - D) Only with interfaces

**18. What does this type mean: `Promise<string>`?**
   - A) A promise that might be a string
   - B) A promise that resolves to a string
   - C) A string that might be a promise
   - D) An error type

**19. What is the purpose of the `ReturnType` utility?**
   - A) To return a type
   - B) To extract the return type of a function
   - C) To define what a function returns
   - D) To check if a function returned

**20. What is the purpose of the `Awaited` utility type?**
   - A) To wait for a Promise
   - B) To unwrap the type from a Promise
   - C) To create async functions
   - D) To delay type checking

### Section 3: Advanced Types (10 questions)

**21. What does the `keyof` operator do?**
   - A) Creates a key in an object
   - B) Extracts the keys of an object type as a union
   - C) Deletes a key from an object
   - D) Checks if a key exists

**22. What is the syntax for indexed access types?**
   - A) `Type[Key]`
   - B) `Type.Key`
   - C) `Type->Key`
   - D) `Type::Key`

**23. What does the `Pick` utility type do?**
   - A) Picks a random property
   - B) Selects specific properties from a type
   - C) Removes properties from a type
   - D) Makes properties optional

**24. What is the syntax for a conditional type?**
   - A) `T if string then true else false`
   - B) `T extends string ? true : false`
   - C) `T === string ? true : false`
   - D) `if T extends string { true } else { false }`

**25. What does the `infer` keyword do in conditional types?**
   - A) Infers the type automatically
   - B) Extracts a type from a conditional type
   - C) Checks type compatibility
   - D) Creates an interface

**26. What does the `Partial` utility type do?**
   - A) Makes all properties optional
   - B) Makes all properties required
   - C) Makes all properties readonly
   - D) Selects part of a type

**27. What does the `Omit` utility type do?**
   - A) Makes properties optional
   - B) Excludes specific properties from a type
   - C) Includes only specific properties
   - D) Removes all properties

**28. What is a mapped type?**
   - A) A type that uses Maps
   - B) A type that transforms properties of another type
   - C) A type for mapping functions
   - D) A geographic type

**29. What is a template literal type?**
   - A) A type for HTML templates
   - B) A string type constructed from other string types
   - C) A type for template engines
   - D) A deprecated feature

**30. What does the `satisfies` operator do?**
   - A) Checks if a value satisfies a condition
   - B) Type checks without widening the type
   - C) Makes the compiler happy
   - D) Validates at runtime

---

## Part B: True or False (10 points)

**31.** TypeScript code runs directly in the browser without compilation. **T / F**

**32.** An interface can extend another interface in TypeScript. **T / F**

**33.** You can use both type aliases and interfaces to define object shapes. **T / F**

**34.** The `!` operator removes null and undefined from a type (non-null assertion). **T / F**

**35.** Enums in TypeScript can only have numeric values. **T / F**

**36.** `as const` makes an object deeply readonly and narrows types to literals. **T / F**

**37.** Intersection types use the `|` operator. **T / F**

**38.** TypeScript supports function overloading. **T / F**

**39.** Generic constraints use the `extends` keyword. **T / F**

**40.** The `typeof` operator works the same in TypeScript and JavaScript. **T / F**

---

## Part C: Code Analysis (20 points)

### Identify the errors in the following code snippets:

**41. (4 points)**
```ts
let user: { name: string; age: number } = {
  name: "Ade",
  age: "25"
};
```

**42. (4 points)**
```ts
function greet(name?: string): string {
  return "Hello, " + name.toUpperCase();
}
```

**43. (4 points)**
```ts
type Admin = {
  role: "admin";
  permissions: string[];
};

type User = {
  role: "user";
};

function checkRole(person: Admin | User) {
  console.log(person.permissions);
}
```

**44. (4 points)**
```ts
function process<T>(value: T): T {
  return value.length;
}
```

**45. (4 points)**
```ts
enum Status {
  Active = "ACTIVE",
  Inactive = "INACTIVE"
}

let status: Status = "ACTIVE";
```

---

## Part D: Practical Coding Exercises (40 points)

**46. (8 points) Write a function that accepts an array of any type and returns the first element or undefined if the array is empty. Use generics.**

```ts
// Your code here
```

**47. (8 points) Create a type alias called `Product` with the following properties:**
- `id`: number
- `name`: string
- `price`: number
- `description`: optional string
- `inStock`: boolean

```ts
// Your code here
```

**48. (8 points) Create a generic function called `filterByProperty` that:**
- Takes an array of objects
- Takes a property name
- Takes a value to match
- Returns an array of objects where the property matches the value

```ts
// Your code here
// Example usage:
// const users = [{ name: "Ade", age: 25 }, { name: "Bisi", age: 30 }];
// filterByProperty(users, "age", 25); // [{ name: "Ade", age: 25 }]
```

**49. (8 points) Using utility types, create:**
- A type `User` with properties: `id`, `name`, `email`, `password`
- A type `UserProfile` that picks only `id`, `name`, and `email` from `User`
- A type `UserUpdate` that makes all properties of `User` optional

```ts
// Your code here
```

**50. (8 points) Create a function that demonstrates the difference between `any` and `unknown`:**
- Create two functions: `processAny` and `processUnknown`
- Both should accept a parameter of their respective type
- Show how `unknown` requires type checking before use

```ts
// Your code here
```

---

## Bonus Questions (10 points)

**51. (5 points) Explain when you would use a `type` vs an `interface`. Give examples of scenarios where one is preferred over the other.**

**52. (5 points) Create a conditional type called `IsArray<T>` that returns `true` if `T` is an array, and `false` otherwise.**

```ts
// Your code here
// Example:
// type Test1 = IsArray<string[]>; // true
// type Test2 = IsArray<string>; // false
```

---

## Total: 110 points (100 + 10 bonus)

**Grading Scale:**
- 90-100: A (Excellent)
- 80-89: B (Very Good)
- 70-79: C (Good)
- 60-69: D (Satisfactory)
- Below 60: F (Needs Improvement)

**Instructions:**
1. You have 90 minutes to complete this test
2. You may use TypeScript documentation
3. Write clear, well-formatted code
4. Explain your reasoning for subjective questions
5. Check your work before submitting

Good luck! 🚀
