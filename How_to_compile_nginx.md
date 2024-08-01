# To compile Nginx from source on ubuntu 22.04, follow these steps:
Ensure you have the necessary dependencies installed. On Ubuntu, you can install them with:

1. Update your system
```
apt-get update
```
2. Install Development Libraries
```
apt-get install -y libgd-dev libmhash-dev libperl-dev dpkg-dev git autotools-dev debhelper libexpat1-dev libgeoip-dev libpam0g-dev libpcre3-dev libssl-dev libxslt1-dev po-debconf build-essential devscripts pbuilder cdbs checkinstall liblua5.2-dev git ntp
```
3. Add Nignx stable release repository on your ubuntu servers
```
echo -e "deb http://nginx.org/packages/ubuntu `lsb_release -cs` nginx\ndeb-src http://nginx.org/packages/ubuntu `lsb_release -cs` nginx"
apt-get update
```
4. Fix nginx error public key
```
wget http://nginx.org/keys/nginx_signing.key
apt-key add nginx_signing.key
cp /etc/apt/trusted.gpg /etc/apt/trusted.gpg.d
apt-get update
```
5. Get Nginx Build Tools and Source Code
The latest nginx version will pull to your system
```
cd /usr/local/src
apt-get build-dep nginx -y
apt-get source nginx
```
Note*: If you want install nginx with specific version just replace by number verion
Example
```
apt-get source nginx=xxx
```
6. Install Openresty Framework
```
cd /usr/local/src/nginx-1.26.1
wget https://openresty.org/download/openresty-1.19.3.1.tar.gz
tar -xvf openresty-1.19.3.1.tar.gz
mv openresty-1.19.3.1 openresty
```
After you download Openresty Framework to you system. Let change prefix
```
vim openresty/configure
Edit: my $prefix = '/usr/local/openresty'; => my $prefix = '/usr/local/src/nginx-1.26.1/openresty';
```
Compile and Install
```
cd /usr/local/src/nginx-1.26.1/openresty
 ./configure && make && make install
```
