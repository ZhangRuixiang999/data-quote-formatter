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
- 自动识别分隔符，默认输出 `('值1','值2',…)` 格式
- 引号可选单引号、双引号或不加引号；项间连接可选逗号或竖线 `'a|b'`
- 支持指定列（按列名或列号）、去重、跳过表头、SQL IN 子句等

### CSV 转 Excel
- 支持 UTF-8、GBK/GB18030、Big5 等编码
- 支持逗号、中文逗号、制表符、分号分隔
- 日期字段转为 Excel 日期格式（直接写入日期数值，不经过时区换算）
- 可自定义下载文件名

### JSON 转 SQL
- 粘贴一条 JSON 样例，勾选字段后生成 Hive / ClickHouse 解析 SQL
- 支持嵌套对象、数组（取第 1 个 / 展开成多行 / 合并为数组）、字段值本身是 JSON 字符串
- 字段支持搜索、按类型筛选、反选
- 可填写表名、附带字段、分区字段和分区日期，直接生成可运行的 SQL
- 常用设置保存在浏览器里，刷新后不丢失

### 时间戳转换
- 10 位秒 / 13 位毫秒时间戳与日期时间双向转换，支持批量输入
- 可切换北京时间 / UTC
- 生成 Hive / ClickHouse 的转换 SQL（时间戳转 `yyyy-MM-dd`、日期转时间戳）

## 本地使用

直接用浏览器打开 `index.html` 即可，无需安装依赖。

## 技术说明

- 单文件 `index.html`，无构建步骤
- [SheetJS](https://sheetjs.com/) 用于 Excel 读写（CDN 加载）
