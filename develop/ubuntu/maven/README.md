# maven 解压安装
> 下载binary安装配置

## 下载binary,并安装
http://maven.apache.org/download.cgi  
shell> wget http://apache.fayea.com/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.tar.gz  
shell> tar -zxvf apache-maven-3.3.9-bin.tar.gz  
shell> mv apache-maven-3.3.9 /opt/maven-3.3.9  
   
## 修改环境变量，在/etc/profile中添加以下几行
export MAVEN_HOME=/opt/maven-3.3.9  
export PATH=${PATH}:${MAVEN_HOME}/bin  

shell> source /etc/profile   
> 使环境变量生效。
   
shell> mvn -v
   
> ok
   
## ref
http://www.tuicool.com/articles/IruUBb

## 镜像
见 上上级

