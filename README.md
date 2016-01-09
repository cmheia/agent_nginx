# Agent_nginx
一个方便快速的代理由nginx搭建

## 安装
安装nginx+lua+ngx_http_sub_module</br>
建议直接安装openresty</br>
前往openresty官网下载最新版。[go](http://openresty.org/#Download)</br>
安装时必须加入参数--with-http_sub_module --with-luajit</br>
## 使用
```
git clone https://github.com/chunsh/agent_nginx.git
perl -p -i -e "s/yourdomain/你的域名/g" ./agent_chunsh/agent.conf
vim ./agent_chunsh/agent.conf   #向http字段添加resolver 8.8.8.8;include vhost/agent.conf;
openssl genrsa -des3 -out agent.key 1024
openssl req -new -subj "/C=US/ST=Mars/L=Ltd/O=Ltd/OU=Ltd/CN=github.com" -key agent.key -out agent.csr     #由于大量子域名，证书无法签发，均会不信任，所以随便一个证书就行。机制将在下一个版本进行改进。
sudo cp ./agent_chunsh/agent.conf /usr/local/nginx/conf/vhost/agent.conf
service nginx restart
```
在想使用代理的网址后加.youdomain.com即可</br>
```Example:www.google.com.chunsh.com;s.w.org.chunsh.com;
```
</br>

欢迎提交issues。
