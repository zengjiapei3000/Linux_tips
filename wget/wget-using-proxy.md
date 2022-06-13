# wget-using-proxy

Sometimes we need using wget on proxy.

## references

1. wget official document:
<https://www.gnu.org/software/wget/manual/wget.html#Proxies>

>

2. Linux设置wget下载http/https代理的两种方法:
<https://www.jb51.net/LINUXjishu/331842.html>

>**方法一，直接在命令后面带参数**
>
>　使用wget命令可以设置http代理
>
>　`wget http://www.baidu.com/ -e use_proxy=yes -e http_proxy=yourproxy.com:port`
>
>　下载https的文件就要其他的额外参数了。
>
>```bash
>    wget --no-check-certificate https://www.google.com/ \
>    -e use_proxy=yes -e https_proxy=yourproxy.com:port ##使用https_proxy才可以哟
>```
>
>　参数--no-check-certificate可以不检查服务器的证书。
>
>　如果你觉得麻烦，可以对shell进行http proxy的代理设置：
>```.bashrc
>　export http_porxy=yourproxy.com:port
>
>　export https_proxy=yourproxy.com:port
>```
>　这样其他的程序就可以通过这个代理进行网络访问了。
>
>　如果wget不需要代理可以使用参数--no-proxy取消代理。
>
>**方法二，配置文件中设置**
>
>　在~/.wgetrc中设定代理
>
>```.wgetrc
>    http_proxy = http://ip_or_domainname:80/
>
>    ftp_proxy = http://ip_or_domainname:80/
>
>    use_proxy = on
>
>    wait = 15
>```

## operations

1. `wget https://github.com/DavidGriffith/frotz/archive/refs/tags/2.44.tar.gz -e 
use_proxy=yes -e http_proxy=192.168.124.189:8889`
实现代理下载.

