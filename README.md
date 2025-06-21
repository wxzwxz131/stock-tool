# 股票分析工具 📈

一个基于 Flask 和 Tushare 的股票行业对比分析工具，支持 A 股和港股数据分析。

![Python](https://img.shields.io/badge/python-3.7+-blue.svg)
![Flask](https://img.shields.io/badge/flask-2.0+-green.svg)
![License](https://img.shields.io/badge/license-MIT-yellow.svg)

## ✨ 功能特色

- 🔍 **多维度分析**: 价格、涨跌幅、交易量等多重指标
- 🌏 **双市场支持**: 同时支持 A 股和港股数据
- 📊 **行业对比**: 40+ 个热门行业分类，包含 AI、AR、新能源等
- 💾 **智能缓存**: 本地数据库存储，避免重复请求
- 📱 **响应式设计**: 支持桌面和移动端访问
- ⚡ **实时更新**: 支持手动刷新和自动数据同步

## 🖼️ 界面预览

### 主界面
- 简洁的导航界面
- 一键数据初始化功能

### 行业对比分析
- 按跌幅排序的行业排名
- 详细的股票数据表格
- 交互式图表显示
- 支持搜索和筛选

## 🚀 快速开始

### 环境要求

- Python 3.7+
- Tushare Pro 账户（免费注册）

### 安装步骤

1. **克隆项目**
```bash
git clone https://github.com/wxzwxz131/stock-analysis-tool.git
cd stock-analysis-tool
```

2. **安装依赖**
```bash
pip install -r requirements.txt
```

3. **配置 Tushare Token**

在 `stock_data.py` 文件中替换您的 Tushare token：
```python
ts.set_token('YOUR_TUSHARE_TOKEN_HERE')
```

获取 Token: [Tushare Pro 注册](https://tushare.pro/)

4. **启动应用**

```bash
# 方法1: 使用便捷脚本（推荐）
python run.py

# 方法2: 直接启动
python app.py

# 方法3: 快速启动（跳过数据初始化）
python run.py --quick
```

5. **访问应用**

打开浏览器访问: http://localhost:5000

## 📚 使用指南

### 首次使用

1. 启动应用后，点击 "初始化股票数据" 按钮
2. 等待数据下载完成（首次约需 5-10 分钟）
3. 访问 "行业对比分析" 页面查看结果

### 日常使用

- **查看分析**: 直接访问行业对比页面
- **刷新数据**: 点击 "刷新数据" 按钮获取最新信息
- **搜索股票**: 使用表格上方的搜索框

### 命令行选项

```bash
python app.py --help

选项:
  --no-init     跳过启动时的数据初始化
  --port 8080   指定端口号（默认 5000）
  --debug       启用调试模式
```

## 📊 数据指标说明

### 价格指标
- **最新价格**: 最近交易日收盘价
- **四月最高价格**: 过去 4 个月内最高价
- **从最高点跌幅**: 当前价格相对最高点的跌幅百分比

### 交易量指标
- **最新交易量**: 最近交易日成交量
- **最大交易量**: 过去 4 个月内最大成交量
- **交易量比值**: 当前交易量占最大交易量的百分比

### 行业评分
基于该行业所有股票的平均跌幅计算，分数越高表示该行业整体跌幅越大。

## 🏗️ 项目结构

```
stock-analysis-tool/
├── app.py                 # Flask 主应用
├── run.py                 # 启动脚本
├── stock_data.py          # 数据获取和处理
├── sector.py              # 行业分类配置
├── db.py                  # 数据库操作
├── hk_stock_utils.py      # 港股工具函数
├── templates/             # HTML 模板
│   ├── index.html
│   └── sector_comparison.html
├── static/css/            # 样式文件
│   └── style.css
├── pages/                 # Streamlit 页面（可选）
│   └── sector_comparison.py
└── requirements.txt       # 依赖包列表
```

## 🔧 技术栈

### 后端
- **Flask**: Web 框架
- **Tushare**: 股票数据源
- **SQLite**: 本地数据存储
- **Pandas**: 数据处理

### 前端
- **Bootstrap 5**: UI 框架
- **jQuery**: JavaScript 库
- **DataTables**: 表格组件
- **Chart.js**: 图表库（通过 CDN）

## 📈 支持的行业

涵盖 40+ 个热门行业，包括：

- **科技类**: AI、AR、芯片、服务器链
- **新能源**: 汽车、光伏、储能
- **消费类**: 美妆、餐饮、宠物经济
- **金融类**: 银行、保险、证券
- **医疗类**: 创新药、医疗器械
- **港股类**: 科技、金融、地产、消费

详细分类请查看 `sector.py` 文件。

## 🛠️ 自定义配置

### 添加新行业

在 `sector.py` 中添加：
```python
SECTORS = {
    # 现有行业...
    "您的行业名称": ['股票1', '股票2', '股票3'],
}
```

### 修改分析周期

在 `stock_data.py` 中修改默认天数：
```python
def get_all_sector_stocks_data(days=120):  # 修改此处
```

### 数据库配置

数据库文件默认存储在项目目录下的 `stock_data.db`，可在 `db.py` 中修改路径。

## 🚨 注意事项

1. **API 限制**: Tushare 对免费用户有调用频率限制
2. **数据延迟**: 股票数据可能有 15-20 分钟延迟
3. **网络要求**: 首次运行需要稳定的网络连接
4. **存储空间**: 完整数据约占用 50-100MB 磁盘空间

## 🤝 贡献指南

欢迎提交 Issue 和 Pull Request！

1. Fork 本项目
2. 创建您的特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交您的修改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 打开一个 Pull Request

## 📝 更新日志

### v1.2.0 (最新)
- ✅ 添加港股支持
- ✅ 新增交易量分析指标
- ✅ 优化数据缓存机制
- ✅ 改进用户界面

### v1.1.0
- ✅ 添加行业评分功能
- ✅ 支持数据自动刷新
- ✅ 增加响应式设计

### v1.0.0
- ✅ 基础行业对比功能
- ✅ A股数据支持
- ✅ Web界面

## 📄 许可证

本项目基于 [MIT License](LICENSE) 开源。

## 🙏 致谢

- [Tushare](https://tushare.pro/) - 提供股票数据 API
- [Bootstrap](https://getbootstrap.com/) - UI 框架
- [DataTables](https://datatables.net/) - 表格组件

## 📞 联系方式

- 项目主页: [GitHub Repository](https://github.com/yourusername/stock-analysis-tool)
- 问题反馈: [Issues](https://github.com/yourusername/stock-analysis-tool/issues)

---

⭐ 如果这个项目对您有帮助，请给个 Star 支持一下！
