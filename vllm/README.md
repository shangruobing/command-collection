# VLLM

A high-throughput and memory-efficient inference and serving engine for LLMs.

``````shell
vllm serve /home/checkpoint/DeepSeek-R1-Distill-Qwen-14B/ \
  --tensor-parallel-size 1 \
  --max-model-len 32768 \
  --enforce-eager \
  --enable-reasoning \
  --reasoning-parser deepseek_r1
``````

## Case of Curl

```shell
curl http://127.0.0.1:8000/v1/chat/completions \
    -H "Content-Type: application/json" \
    -d '{
      "model": "/home/checkpoint/DeepSeek-R1-Distill-Qwen-14B/",
      "messages": [
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Who are you?"}
      ]
    }'
```

## Case of Python

```python
from openai import OpenAI
openai_api_key = "EMPTY"
openai_api_base = "http://localhost:8000/v1"

client = OpenAI(
    api_key=openai_api_key,
    base_url=openai_api_base,
)

models = client.models.list()
model = models.data[0].id

messages = [{"role": "user", "content": "9.11 and 9.8, which is greater?"}]
response = client.chat.completions.create(model=model, messages=messages)

reasoning_content = response.choices[0].message.reasoning_content
content = response.choices[0].message.content

print("reasoning_content:", reasoning_content)
print("content:", content)
```

