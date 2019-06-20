# linux-repo

## Nginx Repo

### RHEL/CentOS
Install the prerequisites:
```bash
sudo yum install yum-utils
```
To set up the yum repository, create the file named /etc/yum.repos.d/nginx.repo with the following contents:
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
By default, the repository for stable nginx packages is used. If you would like to use mainline nginx packages, run the following command:
```

```bash
sudo yum-config-manager --enable nginx-mainline
```
To install nginx, run the following command:

```bash
sudo yum install nginx
```
When prompted to accept the GPG key, verify that the fingerprint matches 573B FD6B 3D8F BC64 1079 A6AB ABF5 BD82 7BD9 BF62, and if so, accept it.


### Ubuntu
Install the prerequisites:

```bash
sudo apt install curl gnupg2 ca-certificates lsb-release
```
To set up the apt repository for stable nginx packages, run the following command:

```bash
echo "deb http://nginx.org/packages/ubuntu `lsb_release -cs` nginx" \
    | sudo tee /etc/apt/sources.list.d/nginx.list
```
If you would like to use mainline nginx packages, run the following command instead:

```bash
echo "deb http://nginx.org/packages/mainline/ubuntu `lsb_release -cs` nginx" \
    | sudo tee /etc/apt/sources.list.d/nginx.list
```
Next, import an official nginx signing key so apt could verify the packages authenticity:

```bash
curl -fsSL https://nginx.org/keys/nginx_signing.key | sudo apt-key add -
Verify that you now have the proper key:

sudo apt-key fingerprint ABF5BD827BD9BF62
```
The output should contain the full fingerprint 573B FD6B 3D8F BC64 1079 A6AB ABF5 BD82 7BD9 BF62 as follows:

```bash
pub   rsa2048 2011-08-19 [SC] [expires: 2024-06-14]
      573B FD6B 3D8F BC64 1079  A6AB ABF5 BD82 7BD9 BF62
uid   [ unknown] nginx signing key <signing-key@nginx.com>
```
To install nginx, run the following commands:

```bash
sudo apt update
sudo apt install nginx
```

rpm -ivh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm 
 

## Mysql YUM

https://dev.mysql.com/downloads/repo/yum/
