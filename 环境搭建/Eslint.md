[编码规范](http://www.mamicode.com/info-detail-2074085.html)
[用户手册](http://eslint.cn/docs/user-guide/configuring)

## 1. 配置文件 .eslintrc.js

- **root** - rrr
- **env** - g
- **extends** - r
- **rules**
- **parserOptions**
- **overrides**

### 1.1. 解析器选项

> parserOptions

## 附录

- 示例代码

```javascript
module.exports = {
    root: true,
    env: {
        node: true,
        es6: true
    },
    'extends': [
        'plugin:vue/essential',
        '@vue/standard',
        '@vue/typescript'
    ],
    rules: {
        'no-console': process.env.NODE_ENV === 'production' ? 'error' : 'off',
        'no-debugger': process.env.NODE_ENV === 'production' ? 'error' : 'off',
        'indent': [2, 4],
        'no-eval': 0,
        'no-console': 0
    },
    parserOptions: {
        parser: '@typescript-eslint/parser'
    },
    overrides: [
        {
            files: [
                '**/__tests__/*.{j,t}s?(x)',
                '**/tests/unit/**/*.spec.{j,t}s?(x)'
            ],
            env: {
                jest: true
            }
        }
    ]
}
```




