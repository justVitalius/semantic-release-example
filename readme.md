# Варианты настройки
## Основные тезисы
- Коммиты нужно именовать согласно [конвенции](https://www.conventionalcommits.org/en/v1.0.0/)
- Действие semantic-release выполняется над историей гит-коммитов, т.е.он не коммитит. И если текущие изменения не закоммичены, то они не учтутся при построении новой версии
- Для запуска выполняем `GITHUB_TOKEN=<add github personal token here> npx semantic-release` (при условии публикации репозитория в github)
- Все настраивается в файле `release.config.js`
- 
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
Дает такой вывод в терминал
```shell
[8:57:41 PM] [semantic-release] › ℹ  Running semantic-release version 18.0.0
[8:57:41 PM] [semantic-release] › ✔  Loaded plugin "verifyConditions" from "@semantic-release/github"
[8:57:41 PM] [semantic-release] › ✔  Loaded plugin "analyzeCommits" from "@semantic-release/commit-analyzer"
[8:57:41 PM] [semantic-release] › ✔  Loaded plugin "publish" from "@semantic-release/github"
[8:57:41 PM] [semantic-release] › ✔  Loaded plugin "addChannel" from "@semantic-release/github"
[8:57:41 PM] [semantic-release] › ✔  Loaded plugin "success" from "@semantic-release/github"
[8:57:41 PM] [semantic-release] › ✔  Loaded plugin "fail" from "@semantic-release/github"
[8:57:41 PM] [semantic-release] › ⚠  This run was not triggered in a known CI environment, running in dry-run mode.
[8:57:48 PM] [semantic-release] › ⚠  Run automated release from branch master on repository git@github.com:justVitalius/semantic-release-example.git in dry-run mode
[8:57:50 PM] [semantic-release] › ✔  Allowed to push to the Git repository
[8:57:50 PM] [semantic-release] › ℹ  Start step "verifyConditions" of plugin "@semantic-release/github"
[8:57:50 PM] [semantic-release] [@semantic-release/github] › ℹ  Verify GitHub authentication
[8:57:50 PM] [semantic-release] › ✔  Completed step "verifyConditions" of plugin "@semantic-release/github"
[8:57:50 PM] [semantic-release] › ℹ  Found git tag v1.2.1 associated with version 1.2.1 on branch master
[8:57:50 PM] [semantic-release] › ℹ  Found 2 commits since last release
[8:57:50 PM] [semantic-release] › ℹ  Start step "analyzeCommits" of plugin "@semantic-release/commit-analyzer"
[8:57:50 PM] [semantic-release] [@semantic-release/commit-analyzer] › ℹ  Analyzing commit: fix: remove npm plugin from configuraitons
[8:57:50 PM] [semantic-release] [@semantic-release/commit-analyzer] › ℹ  The release type for the commit is patch
[8:57:50 PM] [semantic-release] [@semantic-release/commit-analyzer] › ℹ  Analyzing commit: feat: simple setup with only git tag updating
[8:57:50 PM] [semantic-release] [@semantic-release/commit-analyzer] › ℹ  The release type for the commit is minor
[8:57:50 PM] [semantic-release] [@semantic-release/commit-analyzer] › ℹ  Analysis of 2 commits complete: minor release
[8:57:50 PM] [semantic-release] › ✔  Completed step "analyzeCommits" of plugin "@semantic-release/commit-analyzer"
[8:57:50 PM] [semantic-release] › ℹ  The next release version is 1.3.0
[8:57:50 PM] [semantic-release] › ⚠  Skip v1.3.0 tag creation in dry-run mode
[8:57:50 PM] [semantic-release] › ⚠  Skip step "publish" of plugin "@semantic-release/github" in dry-run mode
[8:57:50 PM] [semantic-release] › ⚠  Skip step "success" of plugin "@semantic-release/github" in dry-run mode
[8:57:50 PM] [semantic-release] › ✔  Published release 1.3.0 on default channel
[8:57:50 PM] [semantic-release] › ℹ  Release note for version 1.3.0:

```