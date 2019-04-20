# denoland/deno [![explain]][source] [![translate-svg]][translate-list]

<!-- [![size-img]][size] -->

[explain]: http://llever.com/explain.svg
[source]: https://github.com/chinanf-boy/Source-Explain
[translate-svg]: http://llever.com/translate.svg
[translate-list]: https://github.com/chinanf-boy/chinese-translate-list
[size-img]: https://packagephobia.now.sh/badge?p=Name
[size]: https://packagephobia.now.sh/result?p=Name

「 JavaScript 和 TypeScript 安全运行时，由 V8, Rust, 和 Tokio 构建。」

[中文](./readme.md) | [english](https://github.com/denoland/deno)

---

## 校对 ✅

<!-- doc-templite START generated -->
<!-- repo = 'denoland/deno' -->
<!-- commit = '3324afbd404a4237f0339e50a345a5f20c4ea7dd' -->
<!-- time = '2019-04-07' -->

| 翻译的原文 | 与日期        | 最新更新 | 更多                       |
| ---------- | ------------- | -------- | -------------------------- |
| [commit]   | ⏰ 2019-04-07 | ![last]  | [中文翻译][translate-list] |

[last]: https://img.shields.io/github/last-commit/denoland/deno.svg
[commit]: https://github.com/denoland/deno/tree/3324afbd404a4237f0339e50a345a5f20c4ea7dd

<!-- doc-templite END generated -->

原文：denoland/deno/website

- [x] readme
- [x] [手册](./manual.zh.md)
- [x] [风格指南](./style_guide.zh.md)


### 贡献

欢迎 👏 勘误/校对/更新贡献 😊 [具体贡献请看](https://github.com/chinanf-boy/chinese-translate-list#贡献)

## 生活

[help me live , live need money 💰](https://github.com/chinanf-boy/live-need-money)

---

![](images/deno_logo_3.svg)

# Deno

JavaScript 和 TypeScript 安全运行时，由 V8, Rust, 和 Tokio 构建。

<table>
        <tr>
          <th></th>
          <th>Linux &amp; Mac</th>
          <th>Windows</th>
        </tr>
        <tr>
          <th><a href="https://github.com/denoland/deno">deno</a></th>
          <td>
            <a class="badge" href="https://travis-ci.com/denoland/deno">
              <img
                src="https://travis-ci.com/denoland/deno.svg?branch=master"
              />
            </a>
          </td>
          <td>
            <a class="badge" href="https://ci.appveyor.com/project/deno/deno">
              <img
                src="https://ci.appveyor.com/api/projects/status/yel7wtcqwoy0to8x/branch/master?svg=true"
              />
            </a>
          </td>
        </tr>
        <tr>
          <th><a href="https://github.com/denoland/deno_std">deno_std</a></th>
          <td colspan="2">
            <a
              class="badge"
              href="https://dev.azure.com/denoland/deno_std/_build?definitionId=2"
            >
              <img
                src="https://dev.azure.com/denoland/deno_std/_apis/build/status/denoland.deno_std?branchName=master"
              />
            </a>
          </td>
        </tr>
        <tr>
          <th>
            <a href="https://github.com/denoland/deno_install">deno_install</a>
          </th>
          <td>
            <a class="badge" href="https://travis-ci.com/denoland/deno_install">
              <img
                src="https://travis-ci.com/denoland/deno_install.svg?branch=master"
              />
            </a>
          </td>
          <td>
            <a
              class="badge"
              href="https://ci.appveyor.com/project/deno/deno-install"
            >
              <img
                src="https://ci.appveyor.com/api/projects/status/gtekeaf7r60xa896?branch=master&svg=true"
              />
            </a>
          </td>
        </tr>
        <tr>
          <th><a href="https://github.com/denoland/registry">registry</a></th>
          <td colspan=2>
            <a class="badge" href="https://travis-ci.com/denoland/registry">
              <img
                src="https://travis-ci.com/denoland/registry.svg?branch=master"
              />
            </a>
          </td>
        </tr>
      </table>

## 安装

使用 Shell:

```bash
curl -fsSL https://github.com/denoland/deno_install/blob/master/install.sh | sh
```

Or 使用 PowerShell:

```
iwr https://github.com/denoland/deno_install/blob/master/install.ps1 | iex
```

查看 [deno_install](https://github.com/denoland/deno_install) ，了解更多

## 例子

尝试运行一个简单程序:

```bash
deno https://deno.land/welcome.ts
```

或更为复杂点的:

```typescript
import {serve} from 'https://deno.land/std@v0.3.2/http/server.ts';

async function main() {
  const body = new TextEncoder().encode('Hello World\n');
  for await (const req of serve(':8000')) {
    req.respond({body});
  }
}

main();
```

## 深挖...

**[手册](http://llever.com/deno-website-zh/manual.html)**

[API 参考](https://deno.land/typedoc/)

[风格指南](http://llever.com/deno-website-zh/style_guide.html)

[模块 存储库](https://deno.land/x/)

[Twitter](https://twitter.com/deno_land)

[发布记录](https://github.com/denoland/deno/blob/master/Releases.md)

[社区聊天室](https://gitter.im/denolife/Lobby)

[基准](benchmarks.html)

[awesome Deno](https://github.com/denolib/awesome-deno)
