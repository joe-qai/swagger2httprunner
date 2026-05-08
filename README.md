# HttpRunner Swagger 解析器

![GitHub Stars](https://img.shields.io/github/stars/joe-qai/httprunner_swagger)
![GitHub Forks](https://img.shields.io/github/forks/joe-qai/httprunner_swagger)
![Python Version](https://img.shields.io/badge/python-3.x-blue)
![License](https://img.shields.io/badge/license-MIT-green)

## 项目简介

`httprunner_swagger` 是一个基于 Python 3 的接口自动化测试工具，能够解析 Swagger 2.x 版本的接口文档，自动生成多种格式的测试数据文件，为接口自动化测试提供完整的解决方案。

## 核心功能

- 📊 **Swagger 解析**: 支持解析 Swagger 2.x 接口文档
- 📤 **多格式导出**: 支持生成 JSON、YAML、CSV、XLSX 格式的测试数据
- 🔌 **框架集成**: 完美支持 HttpRunner 2.x 接口自动化测试框架
- 🚀 **JMeter 支持**: 生成的 CSV 文件可直接用于 JMeter 数据驱动测试
- ⚡ **快速上手**: 简单配置即可自动生成测试用例

## 技术栈

- **Python**: 3.6+
- **依赖库**: `requests`, `pandas`, `openpyxl`, `pyyaml`

## 快速开始

### 环境要求

```bash
# 安装 Python 依赖
pip install -r requirements.txt
```

### 配置说明

1. 编辑 `properties/config.ini` 配置文件
2. 设置需要解析的 Swagger 接口文档地址

### 运行方式

```bash
# 方式一：直接运行主脚本
python swaggerLib/swagger2.py

# 方式二：运行独立入口
python swagger.py
```

## 使用流程

```
1. 配置 Swagger 文档地址 → config.ini
2. 运行解析脚本 → 生成测试数据
3. 选择输出格式 → JSON/YAML/CSV/XLSX
4. 导入测试框架 → HttpRunner/JMeter
5. 执行自动化测试 → 查看报告
```

## 项目结构

```
httprunner_swagger/
├── common/           # 公共模块
│   ├── dir_config.py    # 路径配置
│   ├── get_file.py      # 文件操作
│   └── get_values.py    # 数据提取
├── properties/       # 配置文件
│   └── config.ini       # 主配置
├── swaggerLib/       # Swagger 解析核心
│   ├── swagger2.py      # Swagger 2.x 解析器
│   ├── swagger3.py      # Swagger 3.x 解析器（实验性）
│   └── SwaggerForHttprunnerManager.py  # HttpRunner 集成
├── utils/            # 工具类
│   ├── handle_config.py # 配置处理
│   ├── handle_excel.py  # Excel 处理
│   ├── handle_json.py   # JSON 处理
│   ├── handle_folder.py # 文件夹操作
│   └── logger.py        # 日志管理
├── logs/             # 日志目录
├── swagger/          # 生成的测试数据
├── .env              # 环境变量
├── .gitignore
├── requirements.txt
└── README.md
```

## 输出格式示例

### JSON 格式（HttpRunner 2.x）

```json
{
    "name": "用户登录接口",
    "request": {
        "url": "/api/login",
        "method": "POST",
        "json": {
            "username": "${username}",
            "password": "${password}"
        }
    },
    "validate": [
        {"eq": ["status_code", 200]}
    ]
}
```

### Excel 格式

| 用例名称 | URL | 方法 | 参数 | 预期结果 |
|---------|-----|------|------|---------|
| 用户登录 | /api/login | POST | {"username": "test"} | {"code": 200} |

## 背景与价值

### 为什么需要接口测试？

- **更早发现问题**: 接口测试可以在 UI 开发完成前进行
- **降低成本**: 接口层问题修复成本远低于 UI 层
- **持续集成**: 接口测试是 CI/CD 的重要组成部分
- **性能基准**: 后端性能测试依赖接口测试基础

### 为什么选择本工具？

- **自动化生成**: 告别手工编写测试用例
- **多框架支持**: 适配 HttpRunner 和 JMeter
- **灵活配置**: 支持多种输出格式和定制选项
- **易于扩展**: 模块化设计，便于二次开发

## 使用场景

1. **接口自动化测试**: 快速生成测试用例
2. **持续集成**: 集成到 CI/CD 流水线
3. **服务监控**: 通过定时执行监控接口健康状态
4. **性能测试**: 生成 JMeter 数据文件进行压测

## 注意事项

- 仅支持 **Swagger 2.0** 版本，3.0 版本部分数据存在解析错误
- 建议使用 Python 3.6+ 版本
- 生成的测试用例建议进行人工评审后再投入使用

## 贡献指南

欢迎提交 Issue 和 Pull Request！

1. Fork 仓库
2. 创建功能分支 `feature/xxx`
3. 提交代码
4. 创建 Pull Request

## 许可证

MIT License

## 联系方式

如有问题或建议，欢迎通过 GitHub Issues 联系。