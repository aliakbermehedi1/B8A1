# Differences Between Type Aliases and Interfaces in TypeScript

## Introduction
In TypeScript, both type aliases and interfaces are used to define the shape of data. While they look similar in many situations, they have several important differences. Understanding when to use which helps write cleaner and better code.

## Declaration Merging
One of the biggest differences is declaration merging. If you define an interface with the same name twice, TypeScript automatically merges them together into one single interface. This is very helpful when building libraries or extending existing definitions.

```ts
interface User {
  name: string;
}

interface User {
  age: number;
}
```

On the other hand, type aliases cannot be created with the same name more than once. If you try to declare the same type alias twice, TypeScript gives a duplicate identifier error.

## Extending and Composing Types
Interfaces extend other interfaces using the extends keyword. This makes inheritance simple and readable for object oriented styles.

Type aliases cannot use extends directly. Instead, they use intersection operators with the ampersand symbol to combine multiple types together.

```ts
type Person = { name: string };
type Worker = Person & { company: string };
```

## Primitives and Unions
Type aliases are much more flexible when working with non-object types. A type alias can represent primitive types, union types, and tuples. An interface can only define object structures.

```ts
type Status = "pending" | "success" | "error";
type Point = [number, number];
```

## Conclusion
To sum up, both interfaces and type aliases are essential in TypeScript. Use interfaces when you are defining object shapes, class contracts, or public libraries that might need merging. Use type aliases when you need union types, tuples, or primitive aliases.
