# 简约导航页面

一个简洁、现代的网址导航页面，基于 Cloudflare Workers 和 D1 数据库构建。支持分组管理、链接管理、搜索功能等。

## 在线演示

🌐 [在线预览](https://my.yvyan.top/)

## 功能特点

- 🎯 简洁优雅的界面设计
- 📂 支持链接分组管理
- 🔍 集成多引擎搜索功能（百度、Google、Bing）
- 🔒 支持私密分组
- 🎨 自动获取网站图标和描述
- 📱 响应式设计，支持移动端
- ⚡ 基于 Cloudflare Workers，快速且可靠
- 🔑 简单的管理员验证机制

## 部署教程

### 1. 创建 Worker

1. 登录 [Cloudflare Dashboard](https://dash.cloudflare.com)
2. 点击左侧菜单的 "Workers & Pages"
3. 点击 "Create application"
4. 选择 "Create Worker"
5. 为你的 Worker 起一个名字，点击 "Deploy"
6. 部署完成后，点击 "Edit code"

### 2. 创建 D1 数据库

1. 在 Cloudflare Dashboard 左侧菜单中点击 "D1"
2. 点击 "Create database"
3. 为数据库起一个名字（如：nav-db），点击 "Create"
4. 创建完成后，点击数据库名称进入详情页
5. 点击 "Quick query" 按钮
6. 复制 `schema.sql` 中的内容到查询框，点击 "Run query" 创建表

### 3. 绑定数据库

1. 回到 Worker 页面
2. 点击 "Settings" 标签
3. 在 "D1 database bindings" 部分
4. 点击 "Add binding"
5. 设置变量名为 `DB`
6. 选择刚才创建的数据库
7. 点击 "Save binding"

### 4. 配置环境变量

1. 在 Worker 的 "Settings" 标签页中
2. 找到 "Environment Variables" 部分
3. 添加以下变量：
   - `ADMIN_PASSWORD`: 设置你的管理员密码
   - `JWT_SECRET`: 设置一个随机字符串作为 JWT 密钥

### 5. 部署代码

1. 回到 Worker 的 "Code" 标签页
2. 将 `src/index.js` 的内容复制到编辑器中
3. 点击 "Save and deploy"

### 6. 部署前端文件

1. 在 GitHub 上 fork [本仓库](https://github.com/yvyan/MyPage)

3. 在 Cloudflare Dashboard 中：
   - 点击左侧菜单的 "Pages"
   - 点击 "Create a project"
   - 选择 "Connect to Git"
   - 选择你 fork 的仓库
   - 设置构建配置：
     - 构建命令：留空
     - 构建输出目录：static
   - 点击 "Save and Deploy"

4. 部署完成后，你会得到一个 `*.pages.dev` 的域名

5. 配置 API 地址：
   - 在 Pages 项目的 "Settings" > "Environment variables" 中
   - 添加变量 `API_BASE_URL`，值为你的 Worker 地址
   - 点击 "Save" 并重新部署

6. （可选）自定义域名：
   - 在 Pages 项目的 "Custom domains" 中
   - 点击 "Set up a custom domain"
   - 按照提示配置你的域名

## 使用说明

### 管理员功能

1. 点击右上角的"管理员登录"
2. 输入设置的管理员密码
3. 登录后可以：
   - 添加/编辑/删除分组
   - 添加/编辑/删除链接
   - 设置私密分组
   - 调整分组和链接顺序

### 链接管理

- 添加链接时会自动获取网站标题和描述
- 支持自定义图标地址
- 可以拖动调整链接顺序
- 支持按分组组织链接

### 搜索功能

- 支持在搜索框直接搜索
- 可以切换搜索引擎（百度/Google/Bing）
- 搜索引擎选择会被保存

## 项目结构

```
.
├── src/
│   └── index.js      # Worker 后端代码
├── static/
│   ├── index.html    # 前端页面
│   ├── app.js        # 前端逻辑
│   ├── api.js        # API 调用封装
│   └── styles.css    # 样式文件
└── schema.sql        # 数据库结构
```

## 技术栈

- 后端：Cloudflare Workers + D1 数据库
- 前端：原生 JavaScript + CSS
- 图标：Font Awesome
- 认证：简单的 JWT 实现

## 贡献

欢迎提交 Issue 和 Pull Request！

## 许可证

MIT License

## 作者

[Yvyan](https://github.com/yvyan)

## 鸣谢

- [Cloudflare Workers](https://workers.cloudflare.com/)
- [Font Awesome](https://fontawesome.com/)
- [DuckDuckGo](https://duckduckgo.com/) (图标 API) 
- 代码由Cursor编写，仍存在少量bug未解决，欢迎大家提出问题和建议
- 所有贡献者和使用者