# qinzx.hadoop

自动化部署hadoop集群及相关依赖 主角色
# 默认设置
ansible剧本默认的机器配置：
集群包含三台机器，主机名分别为
- hadoop1
- hadoop2
- hadoop3
设置ssh免密登录

# 角色
包含三个角色
- qinzx.jdk
- qinzx.zookeeper
- qinzx.hadoop
qinzx.hadoop依赖上面的两个角色
# 安装包下载
由于安装包过大导致下载缓慢，所以本仓库不提供安装包，本脚本采用的安装包分发方式，是将安装包放到主控端（即ansible运行的机器），解压到目标机器上。
可以使用以下命令下载安装包
```
# 国内的，较快
wget http://mirror.bit.edu.cn/apache/hadoop/common/hadoop-3.2.1/hadoop-3.2.1.tar.gz
# 国外的，较慢
wget https://archive.apache.org/dist/zookeeper/zookeeper-3.6.1/apache-zookeeper-3.6.1.tar.gz
# 国内的只找到了3.6.2的，没有测试，不过应该也可以用，需要修改`qinzx.zookeeper`中变量的zookeeper版本
wget https://mirrors.cnnic.cn/apache/zookeeper/zookeeper-3.6.2/apache-zookeeper-3.6.2.tar.gz
# 国内镜像，较快
wget https://mirrors.huaweicloud.com/java/jdk/8u171-b11/jdk-8u171-linux-x64.tar.gz
```
并将对应的安装包拷贝到对应的角色目录下的`files`目录中。
# 调用
将`start-hadoop.yml`拷贝到`roles`同级目录下，执行`ansible-playbook start-hadoop.yml`角色即可
