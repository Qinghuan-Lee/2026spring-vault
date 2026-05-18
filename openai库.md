# OpenAI 库 (openai) 功能完整指南

## 📋 概述

OpenAI Python 库（`from openai import OpenAI`）是与 OpenAI API 交互的官方客户端。它提供了对各种 OpenAI 服务的访问。

---

## 🎯 核心功能模块

### 1. **Chat 聊天接口** (`client.chat`)

最常用的功能——与 GPT 模型对话

```python
from openai import OpenAI
client = OpenAI(api_key="your-key")

response = client.chat.completions.create(
    model="gpt-4",
    messages=[{"role": "user", "content": "Hello"}]
)
```

**子功能:**

- `completions.create()` - 发送聊天请求
- `completions.list()` - 列出完成记录
- `completions.retrieve()` - 检索特定完成

---

### 2. **Text Completions 文本补全** (`client.completions`)

用于文本生成和补全任务

```python
response = client.completions.create(
    model="gpt-3.5-turbo",
    prompt="今天天气很"
)
```

---

### 3. **Images 图像生成** (`client.images`)

生成、编辑和变化图像

```python
image = client.images.generate(
    model="dall-e-3",
    prompt="A beautiful sunset",
    n=1
)
```

**子功能:**

- `generate()` - 生成新图像
- `edit()` - 编辑现有图像
- `create_variation()` - 生成图像变体

---

### 4. **Audio 音频处理** (`client.audio`)

语音识别和文本转语音

```python
# 语音识别
transcription = client.audio.transcriptions.create(
    model="whisper-1",
    file=open("audio.mp3", "rb")
)

# 文本转语音
speech = client.audio.speech.create(
    model="tts-1",
    voice="alloy",
    input="Hello world"
)
```

---

### 5. **Embeddings 向量化** (`client.embeddings`)

将文本转换为向量，用于语义搜索和相似度计算

```python
embeddings = client.embeddings.create(
    model="text-embedding-3-small",
    input="The quick brown fox"
)
```

---

### 6. **Models 模型管理** (`client.models`)

查看可用的 AI 模型

```python
models = client.models.list()
model_info = client.models.retrieve("gpt-4")
```

---

### 7. **Files 文件管理** (`client.files`)

上传和管理文件，用于微调和 Batch 处理

```python
file = client.files.create(
    file=open("data.jsonl", "rb"),
    purpose="fine-tune"
)

file_list = client.files.list()
client.files.delete(file.id)
```

---

### 8. **Fine-tuning 微调** (`client.fine_tuning`)

微调模型以适应特定任务

```python
job = client.fine_tuning.jobs.create(
    training_file="file-id",
    model="gpt-3.5-turbo"
)

jobs = client.fine_tuning.jobs.list()
job_info = client.fine_tuning.jobs.retrieve(job.id)
```

---

### 9. **Moderations 内容审核** (`client.moderations`)

检查文本是否违反使用政策

```python
moderation = client.moderations.create(
    model="text-moderation-latest",
    input="Some text to check"
)
```

---

### 10. **Batches 批处理** (`client.batches`)

高效处理多个请求

```python
batch = client.batches.create(
    input_file_id="file-id",
    endpoint="/v1/chat/completions",
    completion_window="24h"
)

batch_list = client.batches.list()
batch_status = client.batches.retrieve(batch.id)
```

---

### 11. **Vector Stores 向量存储** (`client.vector_stores`)

管理用于 RAG（检索增强生成）的向量数据库

```python
vs = client.beta.vector_stores.create(name="my-store")
files = client.beta.vector_stores.files.upload_and_poll(
    vector_store_id=vs.id,
    files=[open("data.pdf", "rb")]
)
```

---

### 12. **Uploads 大文件上传** (`client.uploads`)

处理大于 20MB 的文件上传

```python
upload = client.uploads.create(
    file=open("large-file.jsonl", "rb"),
    purpose="fine-tune"
)
```

---

### 13. **Realtime 实时 API** (`client.realtime`)

建立实时语音对话的 WebSocket 连接（测试版）

---

### 14. **Beta 功能** (`client.beta`)

访问测试阶段的新功能

- `client.beta.vector_stores` - 向量存储（Beta）
- `client.beta.assistants` - 助手 API（Beta）
- 其他实验性功能

---

## 🔧 HTTP 方法

底层 HTTP 操作，通常不直接使用：

```python
client.get(url)          # GET 请求
client.post(url, data)   # POST 请求
client.put(url, data)    # PUT 请求
client.patch(url, data)  # PATCH 请求
client.delete(url)       # DELETE 请求
client.request(...)      # 自定义请求
```

---

## ⚙️ 初始化参数

创建客户端时可配置：

```python
client = OpenAI(
    api_key="your-api-key",              # API 密钥（可省略，从环境变量读取）
    organization="org-id",                # 组织 ID
    project="project-id",                 # 项目 ID
    base_url="https://api.openai.com",   # API 基础 URL
    timeout=60.0,                         # 请求超时（秒）
    max_retries=2,                        # 最大重试次数
    default_headers={...},                # 默认请求头
    http_client=custom_client             # 自定义 HTTP 客户端
)
```

---

## 🎓 常用示例

### 简单聊天

```python
from openai import OpenAI

client = OpenAI()

response = client.chat.completions.create(
    model="gpt-4",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "What is Python?"}
    ]
)

print(response.choices[0].message.content)
```

### 流式输出

```python
with client.chat.completions.stream(
    model="gpt-4",
    messages=[{"role": "user", "content": "Write a poem"}]
) as stream:
    for text in stream.text_stream:
        print(text, end="", flush=True)
```

### 处理响应

```python
response = client.chat.completions.create(...)

# 访问完成结果
print(response.choices[0].message.content)
print(response.usage.prompt_tokens)
print(response.usage.completion_tokens)
```

---

## 📊 主要类和属性

|属性|功能|
|---|---|
|`chat`|聊天完成|
|`completions`|文本完成|
|`images`|图像生成、编辑|
|`audio`|语音处理|
|`embeddings`|向量化|
|`models`|模型列表|
|`files`|文件管理|
|`fine_tuning`|微调任务|
|`moderations`|内容审核|
|`batches`|批处理|
|`vector_stores`|向量存储|
|`uploads`|大文件上传|

---

## 🔐 认证

```python
# 方式 1: 直接传入密钥
client = OpenAI(api_key="sk-...")

# 方式 2: 从环境变量读取
# 设置环境变量: export OPENAI_API_KEY="sk-..."
client = OpenAI()

# 方式 3: 从 OPENAI_API_KEY 环境变量读取
import os
os.environ["OPENAI_API_KEY"] = "sk-..."
client = OpenAI()
```

---

## 📝 错误处理

```python
from openai import APIError, RateLimitError, AuthenticationError

try:
    response = client.chat.completions.create(...)
except AuthenticationError:
    print("API 密钥无效")
except RateLimitError:
    print("请求过于频繁")
except APIError as e:
    print(f"API 错误: {e}")
```

---

## 🚀 最佳实践

1. **保护 API 密钥** - 使用环境变量而不是硬编码
2. **处理错误** - 使用 try-except 捕获 API 异常
3. **流式输出** - 对长内容使用 `.stream()` 提高响应速度
4. **资源清理** - 使用完毕后调用 `client.close()`
5. **设置超时** - 避免请求无限期挂起

---

## 📖 更多资源

- [OpenAI API 文档](https://platform.openai.com/docs)
- [Python 客户端 GitHub](https://github.com/openai/openai-python)
- [API 参考](https://platform.openai.com/docs/api-reference)