# Ollama

Get up and running with large language models.

```shell
ollama list
ollama serve
export HF_ENDPOINT=https://hf-mirror.com
```

```shell
curl -fsSL https://ollama.com/install.sh | sh
```

```shell
# Create a user and group for Ollama:
sudo useradd -r -s /bin/false -U -m -d /usr/share/ollama ollama
sudo usermod -a -G ollama $(whoami)
```

Create a service file in `/etc/systemd/system/ollama.service`:

```shell
sudo vim /etc/systemd/system/ollama.service
```

```shell
[Unit]
Description=Ollama Service
After=network-online.target

[Service]
ExecStart=/usr/bin/ollama serve
# ExecStart=/usr/local/bin/ollama serve
User=ollama
Group=ollama
Restart=always
RestartSec=3
Environment="PATH=$PATH"

[Install]
WantedBy=default.target
```

```shell
# Then start the service:
sudo systemctl daemon-reload
sudo systemctl enable ollama
sudo systemctl status ollama
```