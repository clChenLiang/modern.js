---
sidebar_position: 4
---

# 使用微生成器

Modern.js Module 提供了微生成器工具，它可以为当前项目：

- 新增目录和文件
- 修改 `package.json`
- 执行命令

因此通过这些能力，**微生成器可以为项目开启额外的特性功能**。

可以通过 [`modern new`](/guide/basic/command-preview) 启动微生成器。目前 Modern.js Module 支持的微生成器功能有：

## Test 测试

当我们想要对一些模块进行测试的时候，可以启用测试功能。启动该功能后，**会在项目目录下创建 `tests` 目录以及相关文件，在 package.json 中新增 `"@modern-js/plugin-testing"` 依赖**。

:::tip
在成功开启后，会提示需要手动在配置中增加如下类似的代码。

```ts
import { moduleTools, defineConfig } from '@modern-js/module-tools';
import { testingPlugin } from '@modern-js/plugin-testing';

export default defineConfig({
  plugins: [moduleTools(), testingPlugin()],
});
```

:::

## Storybook 调试

当我们想要对组件或者普通模块进行调试的时候，可以启用 Storybook 调试功能。启动该功能后，**会在项目目录下创建 `stories` 目录以及相关文件，在 package.json 中新增 `"@modern-js/storybook"` 依赖**。

关于如何启动 Storybook 以及如何使用 Storybook，可以查看下面的链接：

- [使用 Storybook](https://modernjs.dev/builder/guide/advanced/storybook.html)

## Tailwind CSS 支持

[Tailwind CSS](https://tailwindcss.com/) 是一个以 Utility Class 为基础的 CSS 框架和设计系统，可以快速地为组件添加常用样式，同时支持主题样式的灵活扩展。

如果你想要在项目使用 [Tailwind CSS](https://tailwindcss.com/)，可以参考 [「使用 Tailwind CSS」](https://modernjs.dev/module-tools/guide/best-practices/components.html#tailwind-css)。

## Modern.js Runtime API 支持

**Modern.js 提供了 [Runtime API](https://modernjs.dev/configure/app/runtime/intro) 能力，这些 API 只能在 Modern.js 的应用项目环境中使用**。如果你需要开发一个 Modern.js 应用环境中使用的组件，那么你可以开启该特性，微生成器会增加 `"@modern-js/runtime"`依赖。

另外，Storybook 调试工具也会通过检测项目的依赖确定项目是否需要使用 Runtime API，并且提供与 Modern.js 应用项目一样的 Runtime API 运行环境。

:::tip
在成功开启后，会提示需要手动在配置中增加如下类似的代码。

```ts
import { moduleTools, defineConfig } from '@modern-js/module-tools';
import runtime from '@modern-js/runtime/cli';

export default defineConfig({
  plugins: [moduleTools(), runtime()],
});
```

:::
