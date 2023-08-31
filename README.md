# aaPanel Tools

此工具可以在 CentOS/Debian/Ubuntu 客户端上使用，满足自己的一些使用需求。

### 功能

- CentOS/Debian/Ubuntu 安装 aaPanel
- CentOS/Debian/Ubuntu 安装 宝塔面板
- 降级 6.8.23 版本 aaPanel
- 降级 7.7.0  版本 宝塔面板
- 开心破解
- 汉化 aaPanel 面板
- 删除日志文件，锁定文件写入权限
- 卸载 aaPanel 面板
- 清理脚本产生垃圾文件

### 使用方法

##### 国外VPS
~~~
wget https://raw.githubusercontent.com/ONKK/aaBT/main/script/aabt.sh  -O aabt.sh && chmod +x aabt.sh && clear && ./aabt.sh
~~~
##### 国内VPS
~~~
wget https://ghproxy.com/https://raw.githubusercontent.com/ONKK/aaBT/main/script/aabt.sh  -O aabt.sh && chmod +x aabt.sh && clear && ./aabt.sh
~~~

### 更新说明

- 7.4.5之后的版本（不包括7.4.5）需要强制绑定手机号
- aaPane官网旧版本地址被修改，将下载路径修改为GitHub仓库
- 直接安装V7.7.0的版本，之后的版本都会验证userInfo.json
- aapanel升级后关闭首页强制广告和首页软件推荐
搜索/www/server/panel/BTPanel/static/js/index.js  
~~~
setTimeout(function () { index.get_cloud_list() }, 800); 取消 // 注释
~~~
搜索product_recommend.init 函数，注释如下内容  
~~~
/*product_recommend.init(function(){
   index.get_product_status(function(){
     index.recommend_paid_version()
   });
  index.get_index_list();
})*/
~~~
清除浏览器缓存或更换浏览器 重新访问登录aaPanel panel即可  

- 降级常见问题
Q1：降级后显示宝塔无法启动，但无任何报错  
S1：需要将markupsafe==2.0.1添加到panel目录下的requirements.txt文件中并执行/www/server/panel/pyenv/bin/pip3 install -r requirements.txt安装python库后重启面板即可  
Q2：降级后登录宝塔面板时提示密码错误  
S2：需要在终端修改宝塔密码  
Q3：降级后登录宝塔面板时无法显示验证码图片或无法下载文件  
S3：需要将/www/server/panel/BTPanel/__init__.py文件中的send_file函数中的cache_timeout参数名改为max_age