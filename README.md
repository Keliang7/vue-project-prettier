# Prettier 配置流程（仅 Prettier + @vue/eslint-config-prettier）

## 1. 安装依赖

```bash
pnpm add -D prettier@3.5.3 @vue/eslint-config-prettier@^10.2.0
```

## 2. package.json 版本示例

```json
{
  "devDependencies": {
    "prettier": "3.5.3",
    "@vue/eslint-config-prettier": "^10.2.0"
  }
}
```

## 3. 配置文件

### `.prettierrc.json`

```json
{
  "$schema": "https://json.schemastore.org/prettierrc",
  "semi": false,
  "singleQuote": true,
  "printWidth": 100
}
```

### `.prettierignore` （可选）

```
node_modules
dist
coverage
.idea
.vscode
```

## 4. 与 ESLint 的最小集成 (Flat Config)

```js
import skipFormatting from '@vue/eslint-config-prettier/skip-formatting'

export default [...other, skipFormatting]
```

## 5. VSCode 设置

```json
{
  "recommendations": ["Vue.volar", "dbaeumer.vscode-eslint", "esbenp.prettier-vscode"]
}
```

## 6. scripts

```jsonc
{
  "scripts": {
    "format": "prettier --write src/",
    "format:check": "prettier --check src/",
  },
}
```

## 7. 验收

- 运行 `pnpm format:check` 查看格式是否符合要求
- 保存文件时自动格式化
- ESLint 不再报格式冲突（因为用了 skip-formatting）
