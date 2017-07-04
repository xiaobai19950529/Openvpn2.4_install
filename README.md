# Openvpn2.4_install
ubuntu install Openvpn from ipv6vpn.net

1. 首先，手动从官网下载openvpn最新的版本 
      https://openvpn.net/index.php/open-source/downloads.html
   当前最新是2.4.3
   下载后解压缩，可以放在 ~/Downloads/ 下
   
2. 下载安装OpenVPN所需的插件
   openssl
   pam
   lzo
   
   sudo apt-get install openssl
   sudo apt-get install libssl-dev
   
   sudo apt-get install libpam0g-dev
   
   sudo apt-get install liblzo2-dev
   
3. 进入之间Openvpn的目录
  
    cd ~/Downloads/openvpn-2.4.3/
    
    ./configure
    sudo make
    sudo make install
   
    完了之后检查是否安装成功
    
    openvpn --version  
    
    如果有版本号出来代表安装成功
    
4. 将/usr/local/share/doc/openvpn 文件夹拷贝到 /etc/ 下面  
   
   sudo cp -rf /usr/local/share/doc/openvpn /etc/
   
5. 去这个网址将 update-resolv-conf 弄下来
   https://github.com/masterkorp/openvpn-update-resolv-conf/blob/master/update-resolv-conf.sh 
   
   在/etc/openvpn 下 新建一个名为update-resolv-conf的文件
   
   sudo nano update-resolv-conf
   
   将上面网址的文本复制进去，保存退出
   
   sudo chmod +x update-resolv-conf  
   
   变成可执行文件
   
6. 根据ipv6vpn.net里的openvpn for linux 教程做下去吧！
   
   下载证书和相应的配置文件，之后将以下两行添加在配置文件中(后缀为.ovpn的文件)
   
   up /etc/openvpn/update-resolv-conf
   down /etc/openvpn/update-resolv-conf
   
7. sudo openvpn --cd /etc/openvpn --config xxxx_xxx.ovpn --daemon openvpn

   运行，成功连接！ 
   测试： ping www.youtube.com
   
   若要关闭连接： sudo pkill openvpn
   当然，为了方便，可以用脚本的方式来解决。

   
