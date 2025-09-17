# Open-WebUI

Open WebUI is an extensible, feature-rich, and user-friendly self-hosted AI platform designed to operate entirely offline. It supports various LLM runners like Ollama and OpenAI-compatible APIs, with built-in inference engine for RAG, making it a powerful AI deployment solution.

```shell
sudo docker run -d -p 3000:8080 \
  --add-host=host.docker.internal:host-gateway \
  -v open-webui:/app/backend/data \
  --name open-webui \
  --restart always \
  -e OPENAI_API_KEY={sk-} \
  -e OPENAI_API_BASE_URL={YOUR_BASE_URL}/v1 \
  -e HF_ENDPOINT=https://hf-mirror.com \
  -e ENABLE_OLLAMA_API=False \
  ghcr.io/open-webui/open-webui:main
```

## Configurate Tika as a document parsing engine

```shell
# Create network to communication
docker network create openwebui-net

docker run -d --net=openwebui-net --name tika -p 9998:9998 apache/tika:latest-full

docker run -d --net=openwebui-net -p 3000:8080 \
  --add-host=host.docker.internal:host-gateway \
  -v open-webui:/app/backend/data \
  --name open-webui \
  --restart always \
  -e OPENAI_API_KEY={sk-} \
  -e OPENAI_API_BASE_URL={YOUR_BASE_URL}/v1 \
  -e HF_ENDPOINT=https://hf-mirror.com \
  -e ENABLE_OLLAMA_API=False \
  ghcr.io/open-webui/open-webui:main

# Test apache/tika
docker exec -it open-webui sh
curl http://tika:9998/tika
```

> ghcr.nju.edu.cn/open-webui/open-webui:main
