# Readonly
<p align="center">
  <a href="https://github.com/Bytebit-Org/roblox-Readonly/actions">
      <img src="https://github.com/Bytebit-Org/roblox-Readonly/workflows/CI/badge.svg" alt="CI status" />
  </a>
  <a href="http://makeapullrequest.com">
    <img src="https://img.shields.io/badge/PRs-welcome-blue.svg" alt="PRs Welcome" />
  </a>
  <a href="https://opensource.org/licenses/MIT">
    <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License: MIT" />
  </a>
  <a href="https://discord.gg/QEz3v8y">
    <img src="https://img.shields.io/badge/discord-join-7289DA.svg?logo=discord&longCache=true&style=flat" alt="Discord server" />
  </a>
</p>

Readonly is just a simple function that is really only useful in roblox-ts for forcing the value to be inferred as readonly. Note that it is not a deep readonly - nested objects will still be just as mutable as they were without this function.

## Installation
### roblox-ts
Simply install to your [roblox-ts](https://roblox-ts.com/) project as follows:
```
npm i @rbxts/readonly
```

## Documentation
Documentation can be found [here](https://github.com/Bytebit-Org/roblox-Readonly/tree/master/docs), is included in the TypeScript files directly, and was generated using [TypeDoc](https://typedoc.org/).

## Example
Here's a simple example of just getting a reference to an object and forcing the reference to be marked as readonly. Note that the nested value is still mutable.

```ts
import { readonly } from "@rbxts/readonly";

type SomeValue = {
  message: string,
  someOtherValue: SomeValue,
};

declare function getSomeValue(): SomeValue;

export class Foo {
  public bar() {
    const value = readonly(getSomeValue());

	value.someOtherValue.message = "can mutate this"; // perfectly fine
	value.message = "can't mutate this"; // TypeScript error

    // more logic
  }
}
```
