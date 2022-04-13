# commit-auto

# ![](https://img.shields.io/badge/commit-AUTO-brightgreen)![](https://img.shields.io/badge/hlg-hpz-blue)

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

- ### 添加配置文件 package.json

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

- ### 修改配置文件 package.json

```json
"config": {
  "commitizen": {
    "path": "node_modules/cz-customizable"
  }
}
```

- ### 添加配置文件 .cz-config.js

```javascript
'use strict'

module.exports = {
  types: [
    { value: '特性', name: '特性:    一个新的特性' },
    { value: '修复', name: '修复:    修复一个Bug' },
    { value: '文档', name: '文档:    变更的只有文档' },
    { value: '格式', name: '格式:    空格, 分号等格式修复' },
    { value: '重构', name: '重构:    代码重构，注意和特性、修复区分开' },
    { value: '性能', name: '性能:    提升性能' },
    { value: '测试', name: '测试:    添加一个测试' },
    { value: '工具', name: '工具:    开发工具变动(构建、脚手架工具等)' },
    { value: '回滚', name: '回滚:    代码回退' }
  ],

  scopes: [
    { name: '模块1' },
    { name: '模块2' },
    { name: '模块3' },
    { name: '模块4' }
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
}
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
  extends: ['@commitlint/config-conventional']
}
```

## 检验提交的文件格式

### [ESLint](https://eslint.bootcss.com/)

ESLint 用于对代码进行检查。

- ### 安装代码检查 ESlint

```
pnpm add eslint -D
```

- ### 生成配置文件 .eslintrc.js

```
npx eslint --init
```

- ### 添加忽略文件 .eslintignore

```
*.sh
node_modules
*.md
*.woff
*.ttf
.vscode
.idea
dist
/public
/docs
.husky
.local
/bin
/src/mock
Dockerfile
```

- ### 代码检查

```
npx eslint . --ext .js,.ts
```

- ### 代码修复

```
npx eslint . --fix
```

### [Prettier](https://prettier.io/)

Prettier 用于对代码格式进行配置。

- ### 安装 Prettier

```
pnpm add prettier -D
```

- ### 添加配置文件 .prettierrc.js

```js
// .preitterrc.js
module.exports = {
  // 一行的字符数，如果超过会进行换行，默认为80
  printWidth: 80,
  // 一个tab代表几个空格数，默认为80
  tabWidth: 2,
  // 是否使用tab进行缩进，默认为false，表示用空格进行缩减
  useTabs: false,
  // 字符串是否使用单引号，默认为false，使用双引号
  singleQuote: true,
  // 行位是否使用分号，默认为true
  semi: false,
  // 是否使用尾逗号，有三个可选值"<none|es5|all>"
  trailingComma: 'none',
  // 对象大括号直接是否有空格，默认为true，效果：{ foo: bar }
  bracketSpacing: true,
  // 代码的解析引擎，默认为babylon，与babel相同
  // "parser": "babylon",

  // 开启 eslint 支持
  eslintIntegration: true
}
```

- ### 解决 ESlint 与 Prettier 的冲突

```
pnpm add eslint-config-prettier -D
```

### [stylelint](https://stylelint.io/)

stylelint 用于对样式文件进行格式化。

- ### 安装 stylelint 与 Standard 规范

```shell
pnpm add stylelint stylelint-config-standard
```

- ### 添加配置文件 .stylelintrc.js

```js
module.exports = {
  root: true,
  plugins: ['stylelint-order'],
  customSyntax: 'postcss-html',
  extends: ['stylelint-config-standard', 'stylelint-config-prettier'],
  rules: {
    'function-no-unknown': null,
    'selector-class-pattern': null,
    'selector-pseudo-class-no-unknown': [
      true,
      {
        ignorePseudoClasses: ['global']
      }
    ],
    'selector-pseudo-element-no-unknown': [
      true,
      {
        ignorePseudoElements: ['v-deep']
      }
    ],
    'at-rule-no-unknown': [
      true,
      {
        ignoreAtRules: [
          'tailwind',
          'apply',
          'variants',
          'responsive',
          'screen',
          'function',
          'if',
          'each',
          'include',
          'mixin'
        ]
      }
    ],
    'no-empty-source': null,
    'string-quotes': null,
    'named-grid-areas-no-invalid': null,
    'unicode-bom': 'never',
    'no-descending-specificity': null,
    'font-family-no-missing-generic-family-keyword': null,
    'declaration-colon-space-after': 'always-single-line',
    'declaration-colon-space-before': 'never',
    // 'declaration-block-trailing-semicolon': 'always',
    'rule-empty-line-before': [
      'always',
      {
        ignore: ['after-comment', 'first-nested']
      }
    ],
    'unit-no-unknown': [true, { ignoreUnits: ['rpx'] }],
    'order/order': [
      [
        'dollar-variables',
        'custom-properties',
        'at-rules',
        'declarations',
        {
          type: 'at-rule',
          name: 'supports'
        },
        {
          type: 'at-rule',
          name: 'media'
        },
        'rules'
      ],
      { severity: 'warning' }
    ]
  },
  ignoreFiles: ['**/*.js', '**/*.jsx', '**/*.tsx', '**/*.ts'],
  overrides: [
    {
      files: ['*.vue', '**/*.vue', '*.html', '**/*.html'],
      extends: ['stylelint-config-recommended', 'stylelint-config-html'],
      rules: {
        'keyframes-name-pattern': null,
        'selector-pseudo-class-no-unknown': [
          true,
          {
            ignorePseudoClasses: ['deep', 'global']
          }
        ],
        'selector-pseudo-element-no-unknown': [
          true,
          {
            ignorePseudoElements: ['v-deep', 'v-global', 'v-slotted']
          }
        ]
      }
    },
    {
      files: ['*.less', '**/*.less'],
      customSyntax: 'postcss-less',
      extends: ['stylelint-config-standard', 'stylelint-config-recommended-vue']
    }
  ]
}
```

### [lint-staged](https://github.com/okonet/lint-staged)

lint-staged 用于过滤被 committed 的文件。

- ### 安装文件过滤器 lint-staged

```
pnpm add lint-staged -D
```

- ### 添加配置文件 .lintstagedrc.json

```json
{
  "*.{js,jsx,ts,tsx}": ["eslint --fix", "prettier --write"],
  "{!(package)*.json,*.code-snippets,.!(browserslist)*rc}": [
    "prettier --write--parser json"
  ],
  "package.json": ["prettier --write"],
  "*.vue": ["eslint --fix", "prettier --write", "stylelint --fix"],
  "*.{scss,less,styl,html}": ["stylelint --fix", "prettier --write"],
  "*.md": ["prettier --write"]
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
npx husky add .husky/pre-commit "npx lint-staged"
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

## _~~提交 Commit Message 后自动生成日志~~_

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
