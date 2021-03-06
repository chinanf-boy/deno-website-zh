# Deno 风格指南

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [使用 TypeScript](#%E4%BD%BF%E7%94%A8-typescript)
- [使用术语"模块(module)"，而不是"库(library)"或"包(package)"](#%E4%BD%BF%E7%94%A8%E6%9C%AF%E8%AF%AD%E6%A8%A1%E5%9D%97module%E8%80%8C%E4%B8%8D%E6%98%AF%E5%BA%93library%E6%88%96%E5%8C%85package)
- [不要使用文件名`"index.ts"或"index.js"`](#%E4%B8%8D%E8%A6%81%E4%BD%BF%E7%94%A8%E6%96%87%E4%BB%B6%E5%90%8Dindexts%E6%88%96indexjs)
- [在"deno-std"中，不依赖外部代码](#%E5%9C%A8deno-std%E4%B8%AD%E4%B8%8D%E4%BE%9D%E8%B5%96%E5%A4%96%E9%83%A8%E4%BB%A3%E7%A0%81)
- [在"deno-std"中，最小化依赖关系；不要进行循环导入。](#%E5%9C%A8deno-std%E4%B8%AD%E6%9C%80%E5%B0%8F%E5%8C%96%E4%BE%9D%E8%B5%96%E5%85%B3%E7%B3%BB%E4%B8%8D%E8%A6%81%E8%BF%9B%E8%A1%8C%E5%BE%AA%E7%8E%AF%E5%AF%BC%E5%85%A5)
- [为了保持一致性，文件名请使用下划线，而不是短划线。](#%E4%B8%BA%E4%BA%86%E4%BF%9D%E6%8C%81%E4%B8%80%E8%87%B4%E6%80%A7%E6%96%87%E4%BB%B6%E5%90%8D%E8%AF%B7%E4%BD%BF%E7%94%A8%E4%B8%8B%E5%88%92%E7%BA%BF%E8%80%8C%E4%B8%8D%E6%98%AF%E7%9F%AD%E5%88%92%E7%BA%BF)
- [使用 prettier 格式化代码。](#%E4%BD%BF%E7%94%A8-prettier-%E6%A0%BC%E5%BC%8F%E5%8C%96%E4%BB%A3%E7%A0%81)
- [导出的函数：最多 2 个参数，将其余的参数放入 options 对象。](#%E5%AF%BC%E5%87%BA%E7%9A%84%E5%87%BD%E6%95%B0%E6%9C%80%E5%A4%9A-2-%E4%B8%AA%E5%8F%82%E6%95%B0%E5%B0%86%E5%85%B6%E4%BD%99%E7%9A%84%E5%8F%82%E6%95%B0%E6%94%BE%E5%85%A5-options-%E5%AF%B9%E8%B1%A1)
- [TODO 注释(待续讨论)](#todo-%E6%B3%A8%E9%87%8A%E5%BE%85%E7%BB%AD%E8%AE%A8%E8%AE%BA)
- [版权标题](#%E7%89%88%E6%9D%83%E6%A0%87%E9%A2%98)
- [顶级函数，不应使用箭头语法](#%E9%A1%B6%E7%BA%A7%E5%87%BD%E6%95%B0%E4%B8%8D%E5%BA%94%E4%BD%BF%E7%94%A8%E7%AE%AD%E5%A4%B4%E8%AF%AD%E6%B3%95)
- [不鼓励，使用元编程。包括代理的用法。](#%E4%B8%8D%E9%BC%93%E5%8A%B1%E4%BD%BF%E7%94%A8%E5%85%83%E7%BC%96%E7%A8%8B%E5%8C%85%E6%8B%AC%E4%BB%A3%E7%90%86%E7%9A%84%E7%94%A8%E6%B3%95)
- [如果文件名，以下划线开头，请不要链接到它："_foo.ts"`](#%E5%A6%82%E6%9E%9C%E6%96%87%E4%BB%B6%E5%90%8D%E4%BB%A5%E4%B8%8B%E5%88%92%E7%BA%BF%E5%BC%80%E5%A4%B4%E8%AF%B7%E4%B8%8D%E8%A6%81%E9%93%BE%E6%8E%A5%E5%88%B0%E5%AE%83_foots)
- [使用 jsdoc 文档化，导出 API 的情况](#%E4%BD%BF%E7%94%A8-jsdoc-%E6%96%87%E6%A1%A3%E5%8C%96%E5%AF%BC%E5%87%BA-api-%E7%9A%84%E6%83%85%E5%86%B5)
- [每个模块都应该有测试](#%E6%AF%8F%E4%B8%AA%E6%A8%A1%E5%9D%97%E9%83%BD%E5%BA%94%E8%AF%A5%E6%9C%89%E6%B5%8B%E8%AF%95)
- [单元测试应该是明确的](#%E5%8D%95%E5%85%83%E6%B5%8B%E8%AF%95%E5%BA%94%E8%AF%A5%E6%98%AF%E6%98%8E%E7%A1%AE%E7%9A%84)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 使用 TypeScript

## 使用术语"模块(module)"，而不是"库(library)"或"包(package)"

为了明确性和一致性，请避免使用术语"库"和"包"。而是使用"module"来指明单个 JS 或 TS 文件，当然还包括 TS / JS 代码的目录。

## 不要使用文件名`"index.ts"或"index.js"`

Deno 不会对"index.js"或"index.ts"特殊处理。这些文件名的使用，会对当不用它们时，却可以被排除在模块描述之外，感到困惑。

如果代码目录需要默认入口点，请使用文件名`mod.ts`。文件名`mod.ts`遵循 Rust 的惯例，比`index.ts`简短，并且没有任何先入为主，关于其应该如何运作的观念。

## 在"deno-std"中，不依赖外部代码

`deno_std`旨在成为所有 Deno 程序可以依赖的地基功能。我们希望向用户保证此代码，不包含可能未经审核的第三方代码。

## 在"deno-std"中，最小化依赖关系；不要进行循环导入。

虽然`deno_std`是一个独立的代码库，我们仍然必须小心保持，内部依赖关系的简单和易于管理。特别要注意，不要产生(死)循环导入。

## 为了保持一致性，文件名请使用下划线，而不是短划线。

示例：不是`file-server.ts`，使用`file_server.ts`。

## 使用 prettier 格式化代码。

更具体地说，代码行应在 80 列内，使用 2 空格缩进，并使用驼峰式。使用`//format.ts`调用 prettier。

## 导出的函数：最多 2 个参数，将其余的参数放入 options 对象。

设计函数接口时，请遵守以下规则。

1.  作为公有 API 一部分的函数需要 0-2 个必需参数，如果需要的话，加上一个选项(options)对象（总共最多 3 个）。

2.  可选参数，通常应该放进 options 对象。

    如果只有一个参数，且我们将来不太可能添加更多可选参数，那么不在选项对象中的可选参数，是能够接受的。

3.  'options'参数是唯一的常规'Object'类型。

    其他参数可以是对象(/容器类型)，但它们必须与"普通"对象(`Object`)运行时，区分开来，方法是：

    - 一个有区别的原型（例如`Array`，`Map`，`Date`，`class MyThing`）
    - 一个众所周知的符号属性（例如，一个可迭代的`Symbol.iterator`）。

    这允许 API 以向后兼容的方式扩展，即使选项对象的位置，发生变化也能行。

```ts
// 不好的方式: 可选参数，不是options 对象的一部分。 (#2)
export function resolve(
  hostname: string,
  family?: 'ipv4' | 'ipv6',
  timeout?: number
): IPAddress[] {}

// 好的方式.
export interface ResolveOptions {
  family?: 'ipv4' | 'ipv6';
  timeout?: number;
}
export function resolve(
  hostname: string,
  options: ResolveOptions = {}
): IPAddress[] {}
```

```ts
export interface Environment {
  [key: string]: string;
}

// 不好的方式: `env` 可能是常规对象，因此无法区分是否为一个选项对象. (#3)
export function runShellWithEnv(cmdline: string, env: Environment): string {}

// 好的方式.
export interface RunShellOptions {
  env: Environment;
}
export function runShellWithEnv(
  cmdline: string,
  options: RunShellOptions
): string {}
```

```ts
// 不好的方式: 超过 3 参数 (#1), 过多可选参数 (#2).
export function renameSync(
  oldname: string,
  newname: string,
  replaceExisting?: boolean,
  followLinks?: boolean
) {}

// 好的方式.
interface RenameOptions {
  replaceExisting?: boolean;
  followLinks?: boolean;
}
export function renameSync(
  oldname: string,
  newname: string,
  options: RenameOptions = {}
) {}
```

```ts
// 不好的方式: 过多参数. (#1)
export function pwrite(
  fd: number,
  buffer: TypedArray,
  offset: number,
  length: number,
  position: number
) {}

// 更好.
export interface PWrite {
  fd: number;
  buffer: TypedArray;
  offset: number;
  length: number;
  position: number;
}
export function pwrite(options: PWrite) {}
```

## TODO 注释(待续讨论)

TODO 注释应该在括号中，包含问题或作者的 github 用户名。例：

```ts
// TODO(ry) Add tests.
// TODO(#123) Support Windows.
```

## 版权标题

`deno_std`大多数文件，应具有以下版权标题：

```ts
// Copyright 2018-2019 the Deno authors. All rights reserved. MIT license.
```

如果代码来自其他地方，请确保该文件，具有适当的版权标题。我们`deno_std`只允许使用 MIT，BSD 和 Apache 许可代码。

## 顶级函数，不应使用箭头语法

顶级函数应该使用`function`关键词。箭头语法，应仅限闭包使用。

坏

```ts
export const foo(): string => {
  return "bar";
}
```

好

```ts
export function foo(): string {
  return 'bar';
}
```

## 不鼓励，使用元编程。包括代理的用法。

即使它意味着更多的代码，也要代码具备明确性。

在某些情况下，使用这些技术，可能是有意义的，但在绝大多数情况下，没有。

## 如果文件名，以下划线开头，请不要链接到它："_foo.ts"`

有时可能存在内部模块的需要，但其 API 不是稳定或可供链接的情况。在这种情况下，用下划线作为前缀。按照惯例，只有本文件目录中的(文件)，才能导入它。

## 使用 jsdoc 文档化，导出 API 的情况

我们力求完整的文档。理想情况下，每个导出的符号，都应该有文档行。

如果可能，请编写 JS 文档。例：

```ts
/** foo 做了某 bar. */
export function foo() {
  // ...
}
```

重要的是文档，易于给人阅读，但还需要提供额外的样式信息，以确保生成的文档是，更丰富的文本。因此，JSDoc 通常遵循 markdown 标记，来丰富文本。

虽然 markdown 支持 HTML 标签，但在 JSDoc 区块中，禁止使用。

代码格式字符串，应使用反引号（\`)标记而不是引号。例如：

```ts
/** Import something from the `deno` module. */
```

不要文档化函数参数，除非它们的意图不明显（尽管它们，具有不明显意图，但 API 无论如何都应该考虑清楚）。因此`@param`通常，不应该使用。如果`@param`真使用了，那它不应该包括`type`，因为 TypeScript 已经是强类型的。

```ts
/**
 * 带有不明显意图参数的函数
 * @param foo 描述不明显意图的参数
 */
```

应尽可能减小垂直间距。因此，单行注释应写为：

```ts
/** JSDoc 单行标准写法 */
```

而不是

```ts
/**
 * JSDoc 差的示例
 */
```

代码示例(区块)，不应使用三个反引号（\`\`\`）表示。它们应该只用缩进：具体需要在区块之前空一行，并为示例的每一行，添加 6 个额外的空格。这比注释的第一列，多 4 个。例如：

```ts
/** A straight forward comment and an example:
 *
 *       import { foo } from "deno";
 *       foo("bar");
 */
```

代码示例，不应包含其他注释。它已经在外注释中。如果它需要进一步的注释，那就不是一个很好的例子。

## 每个模块都应该有测试

每个模块应该有个测试文件`modulename_test.ts`，作为它的兄弟姐妹。例如模块`foo.ts`应该带着它的兄弟姐妹`foo_test.ts`。

## 单元测试应该是明确的

为了更好地理解测试，应在整个测试命令中，正确命名函数，比如：

```
test myTestFunction ... ok
```

测试示例：

```ts
import {assertEquals} from 'https://deno.land/std@v0.3.1/testing/asserts.ts';
import {test} from 'https://deno.land/std@v0.3.1/testing/mod.ts';
import {foo} from './mod.ts';

test(function myTestFunction() {
  assertEquals(foo(), {bar: 'bar'});
});
```
