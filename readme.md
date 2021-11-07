# Варианты настройки
## Основные тезисы
- Нужно вызвать npx 
## Обновляем только гит-тэг при коммите
```javascript
// release.config.js
module.exports = {
  plugins: [
    '@semantic-release/commit-analyzer',
    '@semantic-release/github'
  ]
}

```
