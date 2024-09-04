# Uni Playground

使用 uni 公共组件库的示例项目

## 拉取代码

```sh
git clone repository/path.git --recursive
```

通过 `--recursive` 拉取项目中所有仓库的代码

### 1. 组件库单独一个代码仓库，在项目中使用时通过 Submodule 的方式导入：

```sh
git submodule add http://qkl.develop.server:8083/front-group/uni packages/uni //添加子模块
```

这样会在项目的 packages 目录下把 uni 仓库克隆下来，并且 uni 仓库的代码变更不会记录到根项目的 git 记录中



### 2. 通过 `pnpm workspace` 的方式引用组件库：

在项目根目录新建 `pnpm-workspace.yaml` 文件：

```yaml
packages:
  - 'packages/*'
```

在 `package.json` 中添加组件依赖引用：

```json
...
"uni": "workspace:*"
...
```

新建 `.npmrc` 文件

```ini
ignore-workspace-root-check=true
```

这样在根目录使用 npm 安装依赖的时候会默认到根目录



### 3.在项目中使用组件

```vue
<template>
	<Button>Uni Button</Button>
</template>

<script setup lang="ts">
import { Button } from 'uni'
</script>
```