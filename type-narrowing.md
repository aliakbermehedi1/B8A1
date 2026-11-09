# Understanding Type Narrowing in TypeScript

## Introduction
In TypeScript, a variable can often hold more than one type, especially when working with union types. Type narrowing is the process where TypeScript figures out a specific type based on runtime checks. This helps us avoid bugs and runtime errors. It gives us confidence when calling methods on different types.

## Narrowing with typeof and instanceof
The most common way to narrow types is by using the typeof operator. It checks primitive types like string, number, and boolean. Inside the checked block, TypeScript unlocks the methods for that type.

```ts
function printValue(input: string | number): void {
  if (typeof input === "string") {
    console.log(input.toUpperCase());
  } else {
    console.log(input.toFixed(2));
  }
}
```

For objects created from classes, we use the instanceof operator. It checks if an object was created using a specific class constructor. This is helpful when handling class hierarchies.

```ts
class Dog {
  bark() {}
}

function handlePet(pet: Dog | { name: string }): void {
  if (pet instanceof Dog) {
    pet.bark();
  }
}
```

## Narrowing with the in Operator
When working with plain JavaScript objects, the in operator is the best choice. It checks whether a specific property exists inside the given object. Once verified, TypeScript knows exactly which object shape you are using.

```ts
type Fish = { swim: () => void };
type Bird = { fly: () => void };

function move(animal: Fish | Bird): void {
  if ("swim" in animal) {
    animal.swim();
  } else {
    animal.fly();
  }
}
```

## Conclusion
Type narrowing is one of the most useful features in TypeScript. By using typeof, instanceof, and the in operator, we can write safe code without any type assertions. It makes our programs easier to understand and maintain.
