# TypeScript Quiz and Test - Answer Key

## Part A: Multiple Choice Questions (30 points)

### Section 1: Primitives and Basic Types

**1. C) array**
- Explanation: Arrays are not primitive types. Primitives are: string, number, boolean, null, undefined, bigint, and symbol.

**2. B) `unknown` requires type checking before use, `any` doesn't**
- Explanation: `unknown` is type-safe and requires narrowing before use, while `any` bypasses all type checking.

**3. C) string**
- Explanation: TypeScript infers the type as `string` (lowercase), not `String` (the wrapper object).

**4. C) void**
- Explanation: `void` is used for functions that don't return a value. `never` is for functions that never return.

**5. B) A function that never returns (throws error or infinite loop)**
- Explanation: `never` represents functions that throw errors or have infinite loops.

**6. A) `name?: string`**
- Explanation: The `?` after the property name makes it optional.

**7. A) `[string, number]`**
- Explanation: Tuples use square brackets with types in order.

**8. B) |**
- Explanation: Union types use the pipe `|` operator (e.g., `string | number`).

**9. B) Prevents modification of the array**
- Explanation: `readonly` makes the array immutable - you can't push, pop, or modify elements.

**10. B) A type that represents specific values (e.g., "admin" | "user")**
- Explanation: Literal types are exact values as types, not just the general type.

### Section 2: Functions and Generics

**11. B) void**
- Explanation: Functions with no return statement have return type `void`.

**12. A) `...args: number[]`**
- Explanation: Rest parameters use the spread syntax `...` followed by the parameter name and array type.

**13. B) Multiple function signatures for the same function name**
- Explanation: Overloading allows different parameter types for the same function.

**14. B) A placeholder for any type that will be determined later**
- Explanation: Generic type parameters are placeholders resolved when the function is called.

**15. A) `<T extends { length: number }>`**
- Explanation: The `extends` keyword is used for generic constraints.

**16. B) To create reusable, type-safe components**
- Explanation: Generics allow writing flexible code that maintains type safety.

**17. B) Yes, like `<T, U>`**
- Explanation: You can use multiple type parameters separated by commas.

**18. B) A promise that resolves to a string**
- Explanation: `Promise<T>` is a Promise that will resolve to type `T`.

**19. B) To extract the return type of a function**
- Explanation: `ReturnType<typeof fn>` extracts what a function returns.

**20. B) To unwrap the type from a Promise**
- Explanation: `Awaited<Promise<T>>` gives you `T`.

### Section 3: Advanced Types

**21. B) Extracts the keys of an object type as a union**
- Explanation: `keyof User` creates a union of all property keys.

**22. A) `Type[Key]`**
- Explanation: Indexed access types use bracket notation like `Person["name"]`.

**23. B) Selects specific properties from a type**
- Explanation: `Pick<User, "id" | "name">` creates a type with only those properties.

**24. B) `T extends string ? true : false`**
- Explanation: Conditional types use ternary-like syntax with `extends`.

**25. B) Extracts a type from a conditional type**
- Explanation: `infer` allows extracting types within conditional types.

**26. A) Makes all properties optional**
- Explanation: `Partial<T>` transforms all properties to optional.

**27. B) Excludes specific properties from a type**
- Explanation: `Omit<User, "password">` removes specified properties.

**28. B) A type that transforms properties of another type**
- Explanation: Mapped types iterate over properties to create new types.

**29. B) A string type constructed from other string types**
- Explanation: Template literal types like `` `hello ${World}` `` create new string types.

**30. B) Type checks without widening the type**
- Explanation: `satisfies` validates a type while preserving the specific type.

---

## Part B: True or False (10 points)

**31. False**
- TypeScript must be compiled to JavaScript before running in browsers.

**32. True**
- Interfaces can extend other interfaces using the `extends` keyword.

**33. True**
- Both `type` and `interface` can define object shapes.

**34. True**
- The non-null assertion operator `!` tells TypeScript a value is not null/undefined.

**35. False**
- Enums can have string values, numeric values, or heterogeneous values.

**36. True**
- `as const` creates deeply readonly types and narrows to literal types.

**37. False**
- Intersection types use the `&` operator, not `|` (which is for unions).

**38. True**
- TypeScript supports function overloading with multiple signatures.

**39. True**
- Generic constraints use `extends` (e.g., `<T extends string>`).

**40. False**
- In TypeScript, `typeof` at the type level extracts types, different from runtime JavaScript `typeof`.

---

## Part C: Code Analysis (20 points)

**41. Error: Type mismatch**
```ts
// Error: Type 'string' is not assignable to type 'number'
let user: { name: string; age: number } = {
  name: "Ade",
  age: "25"  // Should be: age: 25 (number, not string)
};
```

**42. Error: Possible undefined value**
```ts
// Error: 'name' is possibly undefined
function greet(name?: string): string {
  return "Hello, " + name.toUpperCase();
  // Fix: Check if name exists first
  // return "Hello, " + (name?.toUpperCase() ?? "Guest");
}
```

**43. Error: Property doesn't exist on all types**
```ts
// Error: Property 'permissions' does not exist on type 'User'
function checkRole(person: Admin | User) {
  console.log(person.permissions);
  // Fix: Use type narrowing
  // if ("permissions" in person) {
  //   console.log(person.permissions);
  // }
}
```

**44. Error: Generic constraint missing**
```ts
// Error: Property 'length' does not exist on type 'T'
function process<T>(value: T): T {
  return value.length;
  // Fix: Add constraint
  // function process<T extends { length: number }>(value: T): number {
  //   return value.length;
  // }
}
```

**45. Error: Type mismatch with enum**
```ts
// Error: Type '"ACTIVE"' is not assignable to type 'Status'
let status: Status = "ACTIVE";
// Fix: Use the enum value
// let status: Status = Status.Active;
```

---

## Part D: Practical Coding Exercises (40 points)

**46. Generic first element function:**
```ts
function firstElement<T>(arr: T[]): T | undefined {
  return arr[0];
}

// Usage:
const num = firstElement([1, 2, 3]); // number | undefined
const str = firstElement(["a", "b"]); // string | undefined
const empty = firstElement([]); // undefined
```

**47. Product type alias:**
```ts
type Product = {
  id: number;
  name: string;
  price: number;
  description?: string;
  inStock: boolean;
};

// Usage:
const product: Product = {
  id: 1,
  name: "Laptop",
  price: 999.99,
  inStock: true
};
```

**48. Generic filter by property function:**
```ts
function filterByProperty<T, K extends keyof T>(
  arr: T[],
  property: K,
  value: T[K]
): T[] {
  return arr.filter(item => item[property] === value);
}

// Usage:
const users = [
  { name: "Ade", age: 25 },
  { name: "Bisi", age: 30 },
  { name: "Ojo", age: 25 }
];

const result = filterByProperty(users, "age", 25);
// [{ name: "Ade", age: 25 }, { name: "Ojo", age: 25 }]
```

**49. Utility types exercise:**
```ts
type User = {
  id: string;
  name: string;
  email: string;
  password: string;
};

type UserProfile = Pick<User, "id" | "name" | "email">;
// { id: string; name: string; email: string; }

type UserUpdate = Partial<User>;
// { id?: string; name?: string; email?: string; password?: string; }

// Usage:
const profile: UserProfile = {
  id: "123",
  name: "Ade",
  email: "ade@example.com"
  // password not included
};

const update: UserUpdate = {
  name: "New Name"
  // all properties are optional
};
```

**50. Any vs Unknown demonstration:**
```ts
function processAny(value: any) {
  // No type checking - dangerous!
  value.toUpperCase(); // No error, but could crash at runtime
  value.forEach(); // No error, but could crash at runtime
  return value;
}

function processUnknown(value: unknown) {
  // Type checking required - safe!

  // value.toUpperCase(); // Error: Object is of type 'unknown'

  // Must check type first
  if (typeof value === "string") {
    return value.toUpperCase(); // OK - TypeScript knows it's a string
  }

  if (Array.isArray(value)) {
    value.forEach(item => console.log(item)); // OK - it's an array
  }

  return value;
}

// Usage:
processAny("hello"); // Works
processAny(123); // Runtime error when calling toUpperCase()

processUnknown("hello"); // Safe - type is checked
processUnknown(123); // Safe - won't call toUpperCase()
```

---

## Bonus Questions (10 points)

**51. Type vs Interface:**

**Use `type` when:**
- Defining unions: `type ID = string | number`
- Defining tuples: `type Point = [number, number]`
- Defining primitives: `type Name = string`
- Using mapped types: `type Readonly<T> = { readonly [K in keyof T]: T[K] }`
- Creating complex type combinations

**Use `interface` when:**
- Defining object shapes that might be extended
- You want declaration merging (multiple declarations combine)
- Working with classes (better error messages)
- Building public APIs (more familiar to OOP developers)

**Examples:**
```ts
// Type - for unions and primitives
type Status = "active" | "inactive" | "pending";
type ID = string | number;

// Interface - for object shapes
interface User {
  id: ID;
  name: string;
  status: Status;
}

// Interface - can be extended
interface Admin extends User {
  permissions: string[];
}

// Interface - declaration merging
interface Window {
  customProperty: string;
}
interface Window {
  anotherProperty: number;
}
// Both properties are now on Window
```

**52. IsArray conditional type:**
```ts
type IsArray<T> = T extends any[] ? true : false;

// Test cases:
type Test1 = IsArray<string[]>; // true
type Test2 = IsArray<number[]>; // true
type Test3 = IsArray<string>; // false
type Test4 = IsArray<number>; // false
type Test5 = IsArray<[]>; // true
type Test6 = IsArray<[1, 2, 3]>; // true

// Alternative using Array<any>:
type IsArray2<T> = T extends Array<any> ? true : false;
```

---

## Grading Rubric

### Part A (30 points): 1 point per question
- Correct answer: 1 point
- Incorrect answer: 0 points

### Part B (10 points): 1 point per question
- Correct answer: 1 point
- Incorrect answer: 0 points

### Part C (20 points): 4 points per question
- Identified error correctly: 2 points
- Explained why it's an error: 1 point
- Provided correct fix: 1 point

### Part D (40 points): 8 points per question
- Working code: 5 points
- Proper TypeScript types: 2 points
- Code quality and best practices: 1 point

### Bonus (10 points)
- Question 51: 5 points (explanation, examples, understanding)
- Question 52: 5 points (correct implementation)

---

## Common Mistakes to Avoid

1. **Confusing `type` and `interface` syntax**
2. **Forgetting to handle optional properties with type guards**
3. **Using `any` when `unknown` would be safer**
4. **Not using generic constraints when accessing properties**
5. **Confusing union (`|`) and intersection (`&`) types**
6. **Forgetting that `enum` values need to use `Enum.Value` syntax**
7. **Not checking for null/undefined with optional parameters**
8. **Misusing the non-null assertion operator `!`**

---

## Additional Practice Resources

- [TypeScript Playground](https://www.typescriptlang.org/play)
- [TypeScript Exercises](https://typescript-exercises.github.io/)
- [Type Challenges](https://github.com/type-challenges/type-challenges)
- [TypeScript Deep Dive](https://basarat.gitbook.io/typescript/)

Good luck with your learning! 🚀
