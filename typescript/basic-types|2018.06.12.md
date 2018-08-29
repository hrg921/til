# Basic Types

Boolean, Number, String, Array는 알고 있던 type들.

하지만 Tuple은 처음 봤다.

## Tuple

Tuple types allow you to express an array where the type of a fixed number of elements is known, but need not be the same. For example, you may want to represent a value as a pair of a string and a number:

```typescript
// Declare a tuple type
let x: [string, number];
// Initialize it
x = ["hello", 10]; // OK
// Initialize it incorrectly
x = [10, "hello"]; // Error
```

그냥 한마디로 각 엘리먼트마다 다른 타입을 가지고 있는 Array인데 각 엘리먼트의 타입을 지정해 줄 수 있는 것 같다.

## Enum

A helpful addition to the standard set of datatypes from JavaScript is the enum. As in languages like C#, an enum is a way of giving more friendly names to sets of numeric values.

Enum은 본 적이 있지만 사용해본적은 없어 공부차 읽었다.

```typescript
enum Color {Red, Green, Blue}
let c: Color = Color.Green; // 1
```

```typescript
enum Color {Red = 1, Green, Blue}
let c: Color = Color.Green; // 2
```

```typescript
enum Color {Red = 1, Green = 2, Blue = 4}
let c: Color = Color.Green; // also 2
```

A handy feature of enums is that you can also go from a numeric value to the name of that value in the enum. For example, if we had the value 2 but weren’t sure what that mapped to in the Color enum above, we could look up the corresponding name:

```typescript
enum Color {Red = 1, Green, Blue}
let colorName: string = Color[2];

console.log(colorName); // Displays 'Green' as its value is 2 above
```

## Never

The never type represents the type of values that never occur. For instance, never is the return type for a function expression or an arrow function expression that always throws an exception or one that never returns; Variables also acquire the type never when narrowed by any type guards that can never be true.

never type은 절대 발생하지 않는 값을 나타낸다. 만약 함수의 리턴값이 never라면 이는 항상 error를 던져야 한다.

```typescript
// Function returning never must have unreachable end point
function error(message: string): never {
    throw new Error(message);
}

// Inferred return type is never
function fail() {
    return error("Something failed");
}

// Function returning never must have unreachable end point
function infiniteLoop(): never {
    while (true) {
    }
}
```

## Type assertions

그냥 타입캐스팅, 더 구체적인 타입을 지정하고 싶을 때

```Typescript
let someValue: any = "this is a string";

let strLength: number = (<string>someValue).length;
```

or

```Typescript
let someValue: any = "this is a string";

let strLength: number = (someValue as string).length;
```

## Others

이 외에도 any, void, null, undefined, object가 있는데 null과 undefined에서 주의할 점만 몇가지 기억하고 가자.

By default null and undefined are subtypes of all other types. That means **you can assign null and undefined to something like number**.

However, when using the **--strictNullChecks** flag, null and undefined are **only assignable to void and their respective types.** This helps avoid many common errors. In cases where you want to pass in either a string or null or undefined, you can use the union type string | null | undefined. Once again, more on union types later on.

공식문서에서는 strictNullChecks를 사용하는 것을 권장한다.


> As a note: we encourage the use of --strictNullChecks when possible, but for the purposes of this handbook, we will assume it is turned off.


