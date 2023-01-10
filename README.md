# Type Aligned

[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/aaditmshah/type-aligned/continuous-deployment.yml?branch=main&logo=github)](https://github.com/aaditmshah/type-aligned/actions/workflows/continuous-deployment.yml)
[![GitHub license](https://img.shields.io/github/license/aaditmshah/type-aligned)](https://github.com/aaditmshah/type-aligned/blob/main/LICENSE)
[![npm](https://img.shields.io/npm/v/type-aligned?logo=npm)](https://www.npmjs.com/package/type-aligned)
[![semantic-release: gitmoji](https://img.shields.io/badge/semantic--release-gitmoji-E10079?logo=semantic-release)](https://github.com/semantic-release/semantic-release)
[![Twitter](https://img.shields.io/twitter/url?url=https%3A%2F%2Fgithub.com%2Faaditmshah%2Ftype-aligned)](https://twitter.com/intent/tweet?text=Wow:&url=https%3A%2F%2Fgithub.com%2Faaditmshah%2Ftype-aligned)

Various abstract data types of type-aligned sequences. A type-aligned sequence is a heterogeneous sequence where the types enforce the element order.

## Pipeline

A pipeline is a left-to-right composition of functions.

```typescript
import { tap, pipe, feed } from "type-aligned";

const length = (s: string) => s.length;
const even = (n: number) => n % 2 === 0;

const pipeline = pipe(length, pipe(even, tap()));
const morphism = feed(pipeline);

console.log(morphism("Hello World!")); // true
console.log(morphism("hello world")); // false
```

## Composition

A composition is a right-to-left composition of functions.

```typescript
import { id, compose, apply } from "type-aligned";

const length = (s: string) => s.length;
const even = (n: number) => n % 2 === 0;

const composition = compose(even, compose(length, id()));
const morphism = apply(composition);

console.log(morphism("Hello World!")); // true
console.log(morphism("hello world")); // false
```
