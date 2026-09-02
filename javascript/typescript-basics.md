# Typescript Basics

Typescript:

* is a superset of Javascript
* transpiles to javascript
* offers strict typing features
* which help catch typing errors sooner

## Typescript Syntax

We can (must) set variable types:

```ts
let name: string = "Michael";
let IQ: number = 215;
```

or function argument and return types:

```ts
function processThing(thingId: string ): string{
    // do something
    return "output";
}
```

We have 7ish primitive types available:

1. `string`
2. `number`
3. `boolean`
4. `bigint`
5. `undefined`
6. `null`
7. `symbol` (ES6+)

We also have some other, more special types:

1. `object`
2. `any` see [gradual typing](#gradual-typing)

## Object Typing

It can be as simple as this:

```ts
let myFoo: object = {};
```

or we can also specify the object with fields itself:

```ts
let myFoo: object = {
    name: string;
    rank: number;
    createDate: Date;
};
```

## Type Inference

Typescript can "infer" types from method return values, for example:

```ts
function getItem(): string {
    return "hi!";
}
// type is automatically inferred to be a String
let myItem = getItem();
```

## Gradual Typing

Allows you to choose how and when types are applied by using the `any` type:

```ts
// basically, fall back to dynamic javascript typing
let cost: any = 425;
// alternate syntax
let cost = 425 as any;
```

Using the `any` type is essentially "opting out" of typescript static typing features.

## Interfaces

A minimal interface might look like this:

```ts
interface book {
    name: string;
    rank: number;
    publishDate: Date;
};
```