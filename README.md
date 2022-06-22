使用
首先需要在playbook目录创建files目录，按各role创建目录并放入各目录所需文件，可以从阿里云下载这个目录。

如果是离线部署，还需在basefirst.sh的同一目录创建baserpms和globalrpms,baserpms主要是ansible等包,globalrpms放所有节点需要的包

首先运行basefirst.sh。

然后在passwordless.sh创建文件hosts，写入ip及密码。运行passwordless.sh做无密码登录。

做完修改hosts配置，运行ansible-playbook deploy.sh --tags=common做基础设置，重启重启各节点

重启完ansible-playbook deploy.sh 部署k8s.

这个安装的是docker

受限于本地电脑资源，最多测试过6台虚拟机的部署。

离线部署时安装docker有点问题，可能是虚拟机资源不够导致。

docker版本为18.09.6，可在配置文件中更改，离线部署时需准备对应包。

离线安装内核升级至4.4.138，升级到最新版内核安装显卡驱动会有问题
