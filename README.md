<div align="center">

<image src="https://github.com/user-attachments/assets/83078bfd-fb6a-4ffd-90b2-27bf7f611bf9" height="86"/>

# APICORE v1

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
![Python版本](https://img.shields.io/badge/Python-3.8%2B-brightgreen)
![版本号](https://img.shields.io/badge/Version-1.0.0-orange)

API Configuration & Orchestration Runtime Engine​

​​API 配置与编排运行时规范​格式标准

</div>

## 简介

APICORE 是一个由 SRON 团队 研发的​​统一API配置解决方案​​，通过声明式配置文件实现：

- **🔄 ​广泛兼容性**: APICORE 规范自身具有强大的可扩展性，无论是各种参数或响应格式都可以轻松兼容。
- **⚡ 简明易读性**: APICORE 的标准参数关键词均为日常生活中的通俗用语，简单易懂。
- **📦 ​​描述标准化​**: APICORE 专注于解决多个应用程序之间API配置管理中的碎片化问题，让开发者告别重复对接工作，专注于核心业务逻辑。

## 为什么选择我们的 APICORE

**更灵活、更强大的可扩展性，和标准规范性**

| 特性           | 	APICORE 标准规范                                    | 传统对接方式        | 
| -------------- | --------------------------------------- | ----------------------------------------- |
| **​​开发效率​​**       | **配置文件驱动**          | 手工编写调用代码                  |
| **维护成本​**       | **单点配置全局生效**           | 多处修改难以同步                    |
| **​​错误处理​**       | **统一异常规范**                | 接口差异处理                      |
| **强大生态**       | **基于 JSON ：更方便地拓展生态**                | 需要单独适配每个API的请求    |

### 与 OpenAPI 规范的区别
OpenAPI 的配置文件主要用途是存储API的所有信息，包括参数值等信息。而 APICORE 虽然也可以存储API的完整信息，但其主要用途是使程序通过读取配置文件，将API的参数以用户可读的方式展现在UI上，使用户可以动态编辑API的每个参数值，最后再进行请求。同时，借助强大的 [**APIKernal**](https://github.com/SRInternet/APIKernal) 项目，仅需几行代码即可实现API从请求到解析值的一步到位

## 编写

欢迎访问本仓库 [Wiki](https://github.com/SRON-org/APICORE/wiki) 

这里有详细的[编写指南](https://github.com/SRON-org/APICORE/wiki/Create-a-New-APICORE-Configuration-File)。通过指南，你可以详细和准确地编写符合 APICORE 规范的API配置

## 生态

[**APICORE_Python**](https://github.com/SRON-org/APICORE_Python)：在 Python 上提供对使用 APICORE 规范 格式的文件的进行解析

[**APIKernal**](https://github.com/SRInternet/APIKernal)：只需传入接口、参数和响应路径，实现API从请求到解析值的一步到位

[**API 市场**](https://github.com/IntelliMarkets/Wallpaper_API_Index/)：壁纸生成器 NEXT 的 API 图片源市场

## 代码补全

你可以通过引入 [Schema 文件](https://raw.githubusercontent.com/SRON-org/APICORE/refs/heads/main/APICORE.Schema.json)，并进行以下配置来启用 JSON 代码的自动补全。

### VS Code 配置方法
1. 在或创建 .vscode/settings.json 文件
2. 添加以下配置：
```json
{
  "json.schemas": [
    {
      "fileMatch": ["*.api.json"],
      "url": "https://raw.githubusercontent.com/SRON-org/APICORE/refs/heads/main/APICORE.Schema.json"
    }
  ],
  "yaml.schemas": {
    "https://raw.githubusercontent.com/SRON-org/APICORE/refs/heads/main/APICORE.Schema.json": "*.api.yaml"
  }
}
```

### JetBrains IDE 配置方法
1. 打开 Preferences > Languages & Frameworks > Schemas and DTDs > JSON Schema Mappings
2. 添加新映射：
- Schema file or URL: https://raw.githubusercontent.com/SRON-org/APICORE/refs/heads/main/APICORE.Schema.json
- File path pattern: *.api.json
- Schema version: Draft 7

## 标准和示例

编码: UTF-8

参考：[config_file.json](https://github.com/SRON-org/APICORE_Python/blob/main/config_file.json)

## 开放

我们时刻欢迎各位开发者完善和更新协议，欢迎提交 Pull Request 来改进 APICORE ！

## 协议

[MIT](./LICENSE)
