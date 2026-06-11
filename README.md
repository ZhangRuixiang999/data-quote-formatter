# 数据格式化工具

纯前端小工具，在浏览器本地运行，数据不上传服务器。

## 在线使用

部署完成后访问：**https://zhangruixiang999.github.io/data-quote-formatter/**

## 部署到 GitHub Pages

在项目目录执行（首次需登录 GitHub）：

```bash
chmod +x deploy.sh
./deploy.sh
```

或手动操作：

```bash
# 1. 安装并登录 GitHub CLI
brew install gh
gh auth login

# 2. 创建仓库并推送
gh repo create data-quote-formatter --public --source=. --remote=origin --push

# 3. 在仓库 Settings → Pages → Source 选择「GitHub Actions」
```

推送后 GitHub Actions 会自动构建，约 1～2 分钟可访问上述链接。

## 功能

### 数据加引号
- 粘贴文本 / Excel 表格 / 上传文件
- 自动识别分隔符，输出 `('值1','值2',…)` 格式
- 支持指定列（按列名或列号）、去重、SQL IN 子句等

### CSV 转 Excel
- 支持 UTF-8、GBK/GB18030、Big5 等编码
- 日期字段正确转为 Excel 日期格式
- 可自定义下载文件名

## 本地使用

直接用浏览器打开 `index.html` 即可，无需安装依赖。

## 技术说明

- 单文件 `index.html`，无构建步骤
- [SheetJS](https://sheetjs.com/) 用于 Excel 读写（CDN 加载）
