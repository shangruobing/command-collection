# Nginx

```shell
sudo apt-get install nginx
nginx -v
service nginx start

sudo vim /etc/nginx/sites-available/default
root /home/ubuntu/NFQA/frontend/dist;
sudo nginx -t
service nginx restart 
```