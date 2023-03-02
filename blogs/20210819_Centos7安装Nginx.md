# Centos7安装Nginx（非YUM）

## 安装依赖

```shell
yum install gcc-c++ openssl openssl-devel zlib zlib-devel pcre pcre-devel -y
```

## 下载Nginx

- 手动下载Nginx：<http://nginx.org/en/download.html>
- 使用 `wget` 命令下载
    ```shell
    wget http://nginx.org/download/nginx-1.18.0.tar.gz
    ```

## 解压

```shell
tar -xvf nginx-1.18.0.tar.gz
```

## 安装

```shell
cd nginx-1.18.0/
./configure --prefix=/usr/local/nginx --with-http_stub_status_module --with-http_ssl_module
make
make install
```

## 环境变量

```shell
vi /etc/profile
```
在最后面加入：
```shell
export NGINX_HOME=/usr/local/nginx
export PATH=$PATH:$NGINX_HOME/sbin
```
然后运行：
```shell
source /etc/profile
```
查看是否成功：
```shell
nginx -v
```

## Nginx常用参数

- 启动Nginx：`nginx`
- 停止Ngxin：`nginx -s stop` 或者 `nginx -s quit`
- 重载Nginx配置：`nginx -s reload` 或者 `nginx -s quit`
- 指定配置文件：`nginx -c /usr/local/nginx/config/nginx.conf`
- 检查配置文件是否正确：`nginx -t`
- 帮助信息：`nginx -h` 或者 `nginx -?`
- 版本信息：`nginx -v` 或者 `nginx -V`
- 获取PID：`ps aux | grep nginx` 或者 `cat /path/to/nginx.pid`
- 从容停止Nginx，等所有请求结束后关闭服务：
    ```shell
    ps aux | grep nginx
    kill -QUIT <pid>
    ```
- Nginx快速停止，立刻关闭进程：
    ```shell
    ps aux | grep nginx
    kill -TERM <pid>
    ```
- Nginx强制停止命令：
    ```shell
    ps aux | grep nginx
    kill -9 <pid>
    ```
- Nginx平滑重启：
    ```shell
    nginx -t
    ps aux | grep nginx
    kill -HUP <pid>
    # OR
    nginx -s reload
    ```