# What's Nginx?
```
Nginx is the popular webserver also be used as a reverse proxy, load balancer, mail proxy and HTTP cache.
```

## How to install Nginx on ubuntu 20.04
To install the Nginx service on you server please follow the steps below.


### 1. Update list of availabe packages on you system
```
apt-get update
```

### 2. Install Nginx from Advance Package tool (apt)
```
apt-get install nginx
or
apt-get install -y nginx
```

### 3. Start the Nginx service
```
systemctl start nginx.service
```

### 4. Enable the Nginx service (Auto started when server boot up)
```
systemctl enable nginx.service
```

### 5. Verify the Nginx status
```
systemctl status nginx.service
```

After you install sucessfully you access your browser and you should receive the default Nginx landing page:.
```
http://localhost
http://$your_server_ip
http://$your_domain_name
```
