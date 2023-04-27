# 第一步 : 配置代理

## 配置系统代理

``` bash
# 若需全局配置，将以下内容添加到 /etc/profile
# 若需仅配置当前用户，将以下内容添加到 ~/.bashrc
export http_proxy=http://user:password@host:port/ http 代理
export https_proxy=http://user:password@host:port/ https  理
export ftp_proxy=http://user:password@host:port/ # 代理
export no_proxy="localhost,192.168.0.0/16" # 址


unset http_proxy # 取消代理
unset https_proxy # 取消代理
unset ftp_proxy # 取消代理
unset no_proxy # 取消代理

```

## 配置apt代理

``` bash
# 全局配置
# 进入目录 /etc/apt/apt.conf.d
# 创建文件 *.conf(*为任意名称)
# 写入以下内容
#Acquire::http::Proxy "http:/  username:password@proxy-server-ip:8181/";
#Acquire::https::Proxy "https:/username:password@proxy-server-ip:8182/";
# this is a example
Acquire::http::Proxy "http://127.0.0.1:8889";
Acquire::https::Proxy "http://127.0.0.1:8889";  
# 也可以在命令行中使用
# 例如
sudo apt update -o Acquire::http::Proxy="http:/user:password@proxy_server:port/";

```

## 配置git代理

```bash
# 全局配置
git config --global http.proxy http:/user:password@host:port;
git config --global https.proxy <http:/user:password@host:port>;
```
