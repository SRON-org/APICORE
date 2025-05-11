<div align="center">

<image src="https://github.com/user-attachments/assets/9e91bfd4-4448-4668-bede-6eafb0b42888" height="86"/>

# APICORE v1

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
![Python版本](https://img.shields.io/badge/Python-3.8%2B-brightgreen)
![版本号](https://img.shields.io/badge/Version-1.0.0-orange)

API Configuration & Orchestration Runtime Engine​

​​API 配置与编排运行时规范​格式标准

</div>

## 简介

APICORE 是一款智能API配置引擎，可将任意图像生成API转化为可视化交互系统。通过JSON配置文件实现：

• 🎚 动态生成参数控制面板（滑块/下拉框/文本框）

• 🔍 智能解析API响应数据结构

• ⚡ 一键式API请求构建系统

• 🎨 多类型图片输出支持（URL/二进制流）


核心功能

🌟 动态UI生成器
| 参数类型 | 控件示例                     | 支持配置               |
|----------|------------------------------|------------------------|
| `slider` | ![滑块控件]                    | 范围/步长/默认值       |
| `combo`  | ![下拉框控件]                  | 可选项列表/默认选择    |
| `text`   | ![文本框控件]                  | 输入校验/最大长度限制  |

🚀 智能API适配器
```python
# 典型使用场景
config = APICore.load_config("stable_diffusion.json")
user_params = {
    "prompt": "Cyborg cat in cyberpunk city", 
    "quality": 95,  # 自动映射到滑动条比例
    "style": "cyberpunk"  # 来自预定义选项
}
response = APICore.execute_request(config, user_params)
APICore.save_images(response)  # 自动处理URL和二进制数据
```

快速开始

安装
```bash
git clone https://github.com/yourusername/apicore.git
cd apicore
pip install -r requirements.txt
```

基本使用
```python
from apicore import APIConfigManager

# 加载配置
config = APIConfigManager.load_config('configs/art_generator.json')

# 构建动态界面
ui_builder = UIBuilder(config)
ui_builder.render_controls()  # 自动生成参数控制面板

# 执行API请求
params = ui_builder.get_user_inputs()
response_handler = APIExecutor(config).execute(params)

# 处理结果
if response_handler.success:
    print(f"生成成功！作品ID: {response_handler.get_metadata('id')}")
    response_handler.save_images("output/") 
else:
    print(f"错误代码 {response_handler.error_code}: {response_handler.error_message}")
```

配置规范

标准结构模板
```json
{
  "api_config": {
    "name": "CyberArt Generator Pro",
    "version": "2.3",
    "api_url": "https://api.cyberart.io/v2/generate",
    "method": "POST",
    "headers": {
      "Authorization": "Bearer ${API_KEY}"
    },
    "parameters": [
      {
        "param_name": "resolution",
        "display_name": "作品分辨率",
        "param_type": "combo",
        "options": ["1024x768", "1920x1080", "3840x2160"],
        "default": "1920x1080",
        "advanced": true
      },
      {
        "param_name": "artistic_level",
        "display_name": "艺术化强度",
        "param_type": "slider",
        "min_value": 1,
        "max_value": 10,
        "step": 0.5,
        "default": 7.5
      }
    ],
    "response": {
      "image_type": "url",
      "data_path": "output.result_images[0].hd_url",
      "metadata_mapping": {
        "request_id": "transaction.id",
        "generation_time": "metrics.duration"
      }
    }
  }
}
```

响应处理机制
```python
# 智能元数据提取
response_handler.get_metadata('request_id')  # 返回交易ID

# 多格式图片保存
response_handler.save_images(
    output_dir="gallery",
    naming_strategy="{timestamp}_{param[style]}",  # 自定义文件名模板
    format="webp"  # 自动格式转换
)
```

进阶功能

🔒 安全配置
```json
{
  "security": {
    "auth_type": "oauth2",
    "credential_path": "~/.config/apicore/credentials.json",
    "token_refresh": {
      "endpoint": "https://api.example.com/auth/token",
      "expires_in": 3600
    }
  }
}
```

⏱ 性能监控
```python
APICore.enable_telemetry()  # 启用性能监控
APICore.monitor.dashboard()  # 实时查看API调用指标
```

贡献指南

我们欢迎各种形式的贡献！请通过以下方式参与：

1. 提交issue报告问题
2. 创建pull request改进代码
3. 在discussion区分享配置模板

许可证

本项目采用 [MIT License](LICENSE)

---

特别推荐：查看[示例配置库](examples/)获取Stable Diffusion、Midjourney等流行服务的现成配置模板！
