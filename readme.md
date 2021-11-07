# Варианты настройки
## Обновляем только гит-тэг при коммите
```javascript
module.exports = {
  plugins: [
    '@semantic-release/commit-analyzer',
    '@semantic-release/npm',
    '@semantic-release/github'
  ]
}

```