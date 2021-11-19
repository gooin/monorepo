## monorepo

### 使用 `lerna` 初始化仓库

> [lerna 中文网站](https://www.lernajs.cn/#command-run)

```shell
npx lerna init -i
```

安装完成后的目录结构:

```shell
└─monorepo
    │  lerna.json
    │  package.json
    │  yarn.lock
    └─packages
```

### 新建子项目

#### 使用 `lerna create` 创建仓库

`lerna create @gooin/example -y`
创建好后注意修改`package.json`中的 `publishConfig` 为 github 地址

```json
  "publishConfig": {
"registry": "https://npm.pkg.github.com/"
},
```

### 发布版本：

配置完成后执行 `lerna publish`

### 子仓库相互依赖

给 `@gooin/example` 添加 `@gooin/test-a` 依赖
`lerna add @gooin/test-a --scope=@gooin/example`

安装完成后可以在`@gooin/example`的`packages.json`中看到安装的包。

### 其他：

使用`lerna import` 可以导入已有的仓库

#### 使用github作为npm仓库

[github-working-with-the-npm-registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-npm-registry)

`.npmrc` 文件修改配置

```shell
@gooin:registry=https://npm.pkg.github.com
//npm.pkg.github.com/:_authToken=TOKEN
```

配置完成后，登录scope
`npm login --scope=@gooin --registry=https://npm.pkg.github.com`


