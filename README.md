# commit-auto

提交自动化工具

## 标准化 Commit Message

### [commitizen/cz-cli](https://github.com/commitizen/cz-cli)

comitizen 用于标准化 Git 的 Commit Message。

- ### 全局安装 cz

```
npm install commitizen -g
```

## 生成符合 AngularJS 规范的 Commit Message

### [cz-conventional-changelog](https://github.com/commitizen/cz-conventional-changelog)

cz-conventional-changelog 使 commitizen 生成符合 AngularJS 规范的 Commit Message。

- ### 本地安装 cz-conventional-changelog

```
pnpm add cz-conventional-changelog -D
```

- ### 配置 package.json

```json
"config": {
  "commitizen": {
    "path": "./node_modules/cz-conventional-changelog"
  }
}
```

## 定制项目的 comit msg

### [cz-customizable](https://github.com/leoforfree/cz-customizable)

cz-customizable 用于定制项目的 Commit Message。

- ### 本地安装 cz-customizable

```
pnpm add cz-customizable -D
```

- ### 修改 package.json

```json
"config": {
  "commitizen": {
    "path": "node_modules/cz-customizable"
  }
}
```

- ### 添加配置文件 .cz-config.js

```javascript
'use strict';

module.exports = {

  types: [
    {value: '特性',     name: '特性:    一个新的特性'},
    {value: '修复',      name: '修复:    修复一个Bug'},
    {value: '文档',     name: '文档:    变更的只有文档'},
    {value: '格式',    name: '格式:    空格, 分号等格式修复'},
    {value: '重构', name: '重构:    代码重构，注意和特性、修复区分开'},
    {value: '性能',     name: '性能:    提升性能'},
    {value: '测试',     name: '测试:    添加一个测试'},
    {value: '工具',    name: '工具:    开发工具变动(构建、脚手架工具等)'},
    {value: '回滚',   name: '回滚:    代码回退'}
  ],

  scopes: [
    {name: '模块1'},
    {name: '模块2'},
    {name: '模块3'},
    {name: '模块4'}
  ],

  // it needs to match the value for field type. Eg.: 'fix'
  /*
  scopeOverrides: {
    fix: [
      {name: 'merge'},
      {name: 'style'},
      {name: 'e2eTest'},
      {name: 'unitTest'}
    ]
  },
  */
  // override the messages, defaults are as follows
  messages: {
    type: '选择一种你的提交类型:',
    scope: '选择一个scope (可选):',
    // used if allowCustomScopes is true
    customScope: 'Denote the SCOPE of this change:',
    subject: '短说明:\n',
    body: '长说明，使用"|"换行(可选)：\n',
    breaking: '非兼容性说明 (可选):\n',
    footer: '关联关闭的issue，例如：#31, #34(可选):\n',
    confirmCommit: '确定提交说明?'
  },

  allowCustomScopes: true,
  allowBreakingChanges: ['特性', '修复'],

  // limit subject length
  subjectLimit: 100

};
```

## 校验 Commit Message

### [commitlint](https://github.com/conventional-changelog/commitlint)

commitlint 用于对提交的 Commit Message 进行校验。

- ### 安装符合校验工具 commitlint

```
pnpm add @commitlint/cli -D
```

- ### 安装符合 Angular 风格的校验规则

```
pnpm add @commitlint/config-conventional -D
```

- ### 添加校验文件 commitlint.config.js

```javascript
module.exports = {
  extends: [
    '@commitlint/config-conventional'
  ]
}
```

## 添加 git 钩子工具

### [huksy](https://github.com/typicode/husky)

husky 用于添加 git 的钩子。

- ### 本地安装 husky
```
pnpm add husky -D
```

- ### 配置脚本
```
npm set-script prepare "husky install"
npm run prepare
```

- ### 添加钩子
```
npx husky add .husky/pre-commit "npm test"
git add .husky/pre-commit
```

## 自动生成开发日志

### [conventional-changelog](https://github.com/conventional-changelog/conventional-changelog)

conventional-changelog 用于自动生成开发日志。

- ### 全局安装 conventional-changelog
```
npm install conventional-changelog-cli -g
```

- ### 自动生成日志文件
```
conventional-changelog -p angular -i CHANGELOG.md -s
```

## ~~提交 Commit Message 后自动生成日志~~

- ### ~~添加钩子~~
```
npx husky add .husky/post-commit "conventional-changelog -p angular -i CHANGELOG.md -s" 
```

## 版本自动化管理

### [standard-version](https://github.com/conventional-changelog/standard-version)
standard-version 用于代码版本的管理自动化。

- ### 配置脚本

```
pnpm add standard-version -D
npm set-script release "standard-version"
```

