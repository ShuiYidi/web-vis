# Git 工作流规范

本文档定义项目的 Git 工作流和提交规范。

## 分支策略

### 主分支

- **main** - 主分支，始终保持稳定可发布状态

### 功能分支

| 分支类型 | 命名格式 | 说明 |
|----------|----------|------|
| 功能开发 | `feature/功能名称` | 开发新功能 |
| Bug 修复 | `fix/问题描述` | 修复线上问题 |
| 文档更新 | `docs/文档说明` | 更新项目文档 |
| 代码重构 | `refactor/重构内容` | 代码重构（不改变功能） |
| 样式调整 | `style/样式调整` | 代码格式调整（不影响功能） |
| 性能优化 | `perf/性能优化` | 性能改进 |
| 测试相关 | `test/测试相关` | 添加或修改测试 |
| 构建工具 | `build/构建工具` | 构建工具或外部依赖相关 |
| CI 配置 | `ci/配置修改` | CI 配置修改（如 k8s、docker） |
| 依赖更新 | `chore/依赖工具` | 构建流程或依赖工具修改 |

### 分支命名示例

```
feature/homepage-hero
fix/navbar-mobile-menu
docs/installation-guide
refactor/card-component
style/code-formatting
perf/lazy-loading
test/unit-tests
build/vite-config
ci/github-actions
chore/update-dependencies
```

## 工作流程

### 开发流程

```mermaid
git checkout main
git pull origin main
git checkout -b feature/new-feature
# 开发代码
git add .
git commit -m "✨feat(feature): 添加新功能"
git push origin feature/new-feature
# 创建 Pull Request
# 代码审查
# 合并到 main
```

### 功能开发

```bash
# 1. 从 main 创建功能分支
git checkout main
git pull origin main
git checkout -b feature/user-profile

# 2. 开发并提交
git add .
git commit -m "✨feat(profile): 添加用户资料页面"

# 3. 推送到远程
git push origin feature/user-profile

# 4. 创建 Pull Request
# 在 GitHub/GitLab 上创建 PR，请求合并到 main
```

### Bug 修复

```bash
# 1. 从 main 创建修复分支
git checkout main
git pull origin main
git checkout -b fix/login-error

# 2. 修复并提交
git add .
git commit -m "🐛fix(auth): 修复登录页面验证错误"

# 3. 推送并创建 PR
git push origin fix/login-error
```

## 提交信息规范

### 提交作者规范

**重要**：所有提交必须由项目所有者作为唯一作者。

- **禁止**：在提交信息中添加 `Co-Authored-By`、`Co-authored-by` 或任何类似的共同作者脚注
- **禁止**：使用 `--author` 参数伪造作者信息
- **要求**：所有代码贡献的提交作者应为项目所有者本人

### 提交格式

```
<icon><space><类型>[可选作用域]: <简要描述>

[可选正文]

[可选脚注]
```

### 类型与图标对照表

| 类型 | 图标 | 描述 |
|------|------|------|
| `init` | 🎉 | 项目初始化 |
| `feat` | ✨ | 添加新特性 |
| `fix` | 🐛 | 修复 bug |
| `docs` | 📄 | 修改文档 |
| `style` | 🌈 | 仅修改了空格、格式缩进、逗号等 |
| `refactor` | 🦄 | 代码重构，没有新增功能或修复 bug |
| `perf` | 🎈 | 性能优化，提高性能、体验 |
| `test` | 🧪 | 添加测试用例 |
| `build` | 🔧 | 构建工具或外部依赖相关 |
| `ci` | 🐎 | CI 配置修改（如 k8s、docker） |
| `chore` | 🐳 | 构建流程或依赖工具修改 |
| `revert` | ↩️ | 回滚到上一个版本 |

### 作用域（Scope）

- `components` - 组件相关
- `styles` - 样式相关
- `router` - 路由相关
- `stores` - 状态管理相关
- `data` - 数据相关
- `layouts` - 布局相关
- `views` - 页面相关
- `config` - 配置相关
- `auth` - 认证相关
- `api` - API 相关

### 提交示例

#### 功能添加

```text
✨feat(home): 添加首页 Hero 区域

- 新增导师简介展示模块
- 新增统计卡片组件
- 添加响应式布局支持

Closes #123
```

#### Bug 修复

```text
🐛fix(navbar): 修复移动端菜单无法关闭的问题

修复点击菜单项后汉堡菜单未收起的 bug

Fixes #456
```

#### 文档更新

```text
📄docs(readme): 更新安装说明

添加 Node.js 版本要求说明
```

#### 样式调整

```text
🌈style(styles): 统一按钮样式格式化

调整按钮组件的缩进和空格
```

#### 代码重构

```text
🦄refactor(components): 重构卡片组件

抽取通用逻辑到 composables/useCard.js
```

#### 性能优化

```text
🎈perf(router): 优化路由懒加载

将路由组件改为动态导入，减少首屏加载时间
```

#### 测试添加

```text
🧪test(utils): 添加格式化工具函数测试

覆盖日期格式化和数字格式化的测试用例
```

#### 构建更新

```text
🔧build(vite): 更新 Vite 配置

添加路径别名和 SCSS 全局变量注入
```

#### CI 配置

```text
🐎ci(github): 添加 GitHub Actions 工作流

配置自动化测试和部署流程
```

#### 依赖更新

```text
🐳chore(deps): 更新 Element Plus 到 2.9.1

升级到最新版本以获得新特性和性能改进
```

#### 回滚

```text
↩️revert: 回滚"添加新功能"提交

This reverts commit 1234567890abcdef
```

## 提交前检查

在提交代码前，请确保：

- [ ] 代码运行正常，无控制台错误
- [ ] 遵循命名规范和代码风格
- [ ] 删除调试代码和 console.log
- [ ] 更新相关文档
- [ ] 提交信息清晰描述变更内容
- [ ] 代码已通过 ESLint 检查
- [ ] 新功能有对应的测试用例

## Pull Request 规范

### PR 标题格式

PR 标题应遵循与提交信息相同的格式：

```text
✨feat(feature): 功能描述
🐛fix(scope): 问题修复
📄docs: 文档更新
```

### PR 描述模板

```markdown
## 变更类型
- [ ] 新功能
- [ ] Bug 修复
- [ ] 代码重构
- [ ] 文档更新
- [ ] 性能优化
- [ ] 其他

## 变更说明
<!-- 描述本次变更的内容 -->

## 相关 Issue
Closes #123

## 测试
<!-- 描述测试情况 -->

## 截图
<!-- 如有 UI 变更，请提供截图 -->
```

### PR 审查清单

审查者应检查：

- [ ] 代码符合项目规范
- [ ] 功能实现正确
- [ ] 没有引入新的问题
- [ ] 有适当的测试覆盖
- [ ] 文档已更新
- [ ] 没有性能问题
- [ ] 没有安全漏洞

## 代码合并策略

### 合并方式

- **Squash and merge** - 将多个提交合并为一个，保持主分支整洁
- **Merge commit** - 保留完整历史，适用于大型功能分支
- **Rebase and merge** - 线性历史，适用于需要保持提交顺序的场景

### 合并前要求

1. **通过 CI 检查** - 所有自动化测试必须通过
2. **代码审查** - 至少一名团队成员审查批准
3. **无冲突** - 解决所有合并冲突
4. **更新文档** - 相关文档已同步更新

## 版本发布

### 版本号格式

遵循 [语义化版本 2.0.0](https://semver.org/lang/zh-CN/)：

```
MAJOR.MINOR.PATCH

例如：1.2.3
- MAJOR：不兼容的 API 变更
- MINOR：向后兼容的新功能
- PATCH：向后兼容的 Bug 修复
```

### 发布流程

```bash
# 1. 更新版本号
npm version patch  # 或 minor / major

# 2. 生成 CHANGELOG
# 手动更新 CHANGELOG.md

# 3. 推送标签
git push origin main --tags

# 4. 发布到 npm（如需要）
npm publish
```

### 发布类型

| 类型 | 示例 | 说明 |
|------|------|------|
| 补丁发布 | 1.0.0 → 1.0.1 | Bug 修复 |
| 次要发布 | 1.0.0 → 1.1.0 | 新功能，向后兼容 |
| 主要发布 | 1.0.0 → 2.0.0 | 重大变更，可能不兼容 |

## 常见问题

### 提交后发现错误

```bash
# 如果还没有推送到远程
git commit --amend -m "✨feat(feature): 修正提交信息"

# 如果已经推送到远程
git revert HEAD
git commit -m "↩️revert: 回滚错误的提交"
```

### 合并冲突处理

```bash
# 1. 拉取最新代码
git fetch origin main
git rebase origin/main

# 2. 解决冲突
# 编辑冲突文件，解决冲突标记

# 3. 标记冲突已解决
git add <conflicted-files>
git rebase --continue

# 4. 强制推送（谨慎使用）
git push origin feature-branch --force-with-lease
```

### 撤销已推送的提交

```bash
# 撤销最近的提交（保留更改）
git reset --soft HEAD~1

# 撤销最近的提交（丢弃更改）
git reset --hard HEAD~1

# 撤销多个提交
git reset --soft HEAD~3
```

## Git 配置

### 推荐的全局配置

```bash
# 设置用户名和邮箱
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# 设置默认分支名
git config --global init.defaultBranch main

# 设置拉取策略
git config --global pull.rebase false

# 设置提交模板（可选）
git config --global commit.template .gitmessage
```

### 提交模板文件 `.gitmessage`

```
<icon><type>(<scope>): <subject>

<body>

<footer>
```

## 最佳实践

1. **频繁提交** - 小步快跑，每次提交一个完整的逻辑单元
2. **清晰的提交信息** - 让其他人（以及未来的你）能理解做了什么
3. **不要提交未完成的代码** - 除非在功能分支上且有明确标识
4. **不要提交敏感信息** - 密钥、配置文件等应使用 .gitignore
5. **保持主分支稳定** - 只有测试通过的代码才能合并到 main
6. **及时同步** - 定期从 main 拉取最新代码，减少冲突
7. **审查自己的代码** - 提交前自己先审查一遍
8. **使用 .gitignore** - 排除不需要版本控制的文件

## .gitignore 推荐

```gitignore
# 依赖
node_modules/
.pnp
.pnp.js

# 构建输出
dist/
dist-ssr/
build/

# 开发工具
.vscode/*
!.vscode/extensions.json
.idea/
.DS_Store
*.suo
*.ntvs*
*.njsproj
*.sln
*.sw?

# 环境变量
.env
.env.local
.env.*.local

# 日志
npm-debug.log*
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*
lerna-debug.log*

# 测试覆盖率
coverage/
*.lcov

# 临时文件
*.tmp
*.temp
.cache/
```
