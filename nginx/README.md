# Nginx

```shell
# Install
sudo apt-get install nginx

# Check version
nginx -v

# Launch service
service nginx start

# Configuration
sudo vim /etc/nginx/sites-available/default

# Check configuration
sudo nginx -t

# Reload configuration
sudo nginx -s reload

# Reboot
service nginx restart
```

## Location Match Rule

1. Exact matching ( = )
2. Prefix matching, longest path first
3. Regular expression matching ( \~ or \~\* ), The first match is selected

## Configuration Example

```
server {
	listen 80;
	listen 443 ssl http2;
	root /home/ubuntu/homepage/dist;
	index index.html;
	server_name www.XXX.cn;
	ssl_certificate /home/ubuntu/homepage/ssl/fullchain.crt;
	ssl_certificate_key /home/ubuntu/homepage/ssl/private.pem;
	ssl_session_timeout 5m;
	ssl_session_cache shared:SSL:5m;
	ssl_protocols TLSv1.1 TLSv1.2;
	ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:HIGH:!aNULL:!MD5:!RC4:!DHE;
	ssl_prefer_server_ciphers on;

	location / {
		try_files $uri $uri/ /index.html;
	}

	# Backend(Springboot) Production
	location /backend/api/ {
		rewrite ^/backend/api(/.*)$ /api$1 break;
		proxy_pass http://localhost:8000;
	}

	# Backend(Springboot) Development
	location /backend/dev/api {
		rewrite ^/backend/dev/api(/.*)$ /api$1 break;
		proxy_pass http://localhost:18000;
	}

	# Frontend(Vue.js) Production
	location /frontend {
		alias /home/ubuntu/frontend/prod/dist;
		index index.html;
		try_files $uri $uri/ /index.html;
	}
	
	# Frontend(Vue.js) Development
	location /frontend/dev {
		alias /home/ubuntu/frontend/dev/dist;
		index index.html;
		try_files $uri $uri/ /index.html;
	}

	# Homepage Backend(Flask) Production
	location /api/ {
		proxy_pass http://localhost:5000;
	}
	
	# Static Files
	location ~ .*\.(gif|jip|jpeg|png|svg|bmp|swf)$ {
		proxy_pass http://localhost:8000;
		expires 30d;
	}
}
```
