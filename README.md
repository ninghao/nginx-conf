## Nginx Configuration

## Install Nginx

### CentOS

Create a file named `/etc/yum.repos.d/nginx.repo` with following contents:

```
[nginx-stable]
name=nginx stable repo
baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
gpgcheck=1
enabled=1
gpgkey=https://nginx.org/keys/nginx_signing.key

[nginx-mainline]
name=nginx mainline repo
baseurl=http://nginx.org/packages/mainline/centos/$releasever/$basearch/
gpgcheck=1
enabled=0
gpgkey=https://nginx.org/keys/nginx_signing.key
```

To install nginx, run the following command:

```
yum install nginx
```

## SSL

### CentOS

#### Install Certbot

```
yum install certbot python2-certbot-nginx
```

#### Install certificates

```
certbot --nginx

or

certbot certonly --nginx
```

#### Auto renewal

```
echo "0 0,12 * * * root python -c 'import random; import time; time.sleep(random.random() * 3600)' && certbot renew" | sudo tee -a /etc/crontab > /dev/null
```
