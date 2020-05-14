###什么是Docker？
    Docker是一个开源的应用容器引擎，基于GO语言并总从Apache2.0协议开源   
    开发者可以打包应用以及依赖包到一个轻量级    
    可移植的容器中然后发布到任何流行的Linux机器上  
###应用场景
    1). Web应用自动化打包和发布
    2). 自动化测试和持续集成、发布
    3). 在服务型环境中部署和调整数据库或其他的后台应用
    4). 从头编译或者扩展现有的 OpenShift 或 Cloud Foundry 平台来搭建自己的 PaaS 环境
    
###优点
开发、交付和运行应用程序的开放平台，将应用程序与基础架构分开，从而快速交付软件。  
1. 快速，一致地交付您的应用程序  
    Docker 允许开发人员使用您提供的应用程序或服务的本地容器在标准化环境中工作，从而简化了开发的生命周期。  
    容器非常适合持续集成和持续交付（CI / CD）工作流程  
2. 响应式部署和扩展
    Docker 是基于容器的平台，允许高度可移植的工作负载。Docker 容器可以在开发人员的本机上，数据中心的物理或虚拟机上，云服务上或混合环境中运行。  
    Docker 的可移植性和轻量级的特性，还可以使您轻松地完成动态管理的工作负担，并根据业务需求指示，实时扩展或拆除应用程序和服务。  
3. 在同一硬件上运行更多工作负载
    Docker 轻巧快速。它为基于虚拟机管理程序的虚拟机提供了可行、经济、高效的替代方案，因此您可以利用更多的计算能力来实现业务目标。  
    Docker 非常适合于高密度环境以及中小型部署，而您可以用更少的资源做更多的事情。  
###CentOS Docker 安装
    
####1. 卸载旧版本
较旧的 Docker 版本称为 docker 或 docker-engine 。如果已安装这些程序，请卸载它们以及相关的依赖项。
    
    $ sudo yum remove docker \
                      docker-client \
                      docker-client-latest \
                      docker-common \
                      docker-latest \
                      docker-latest-logrotate \
                      docker-logrotate \
                      docker-engine
####2. 设置Docker仓库
    $ sudo yum install -y yum-utils \
      device-mapper-persistent-data \
      lvm2
      
    $ sudo yum-config-manager \
          --add-repo \
          https://download.docker.com/linux/centos/docker-ce.repo
####3. 安装 Docker Engine-Community
安装最新版本的 Docker Engine-Community 和 containerd：  

    $ sudo yum install docker-ce docker-ce-cli containerd.io
    
要安装特定版本的 Docker Engine-Community，请在存储库中列出可用版本，然后选择并安装：
    
    $ yum list docker-ce --showduplicates | sort -r
    
    docker-ce.x86_64  3:18.09.1-3.el7                     docker-ce-stable
    docker-ce.x86_64  3:18.09.0-3.el7                     docker-ce-stable
    docker-ce.x86_64  18.06.1.ce-3.el7                    docker-ce-stable
    docker-ce.x86_64  18.06.0.ce-3.el7                    docker-ce-stable

通过其完整的软件包名称安装特定版本，该软件包名称是软件包名称（docker-ce）加上版本字符串（第二列），从第一个冒号（:）一直到第一个连字符，并用连字符（-）分隔。例如：docker-ce-18.09.1。

    $ sudo yum install docker-ce-<VERSION_STRING> docker-ce-cli-<VERSION_STRING> containerd.io
    
启动Docker
    
    $ sudo systemctl start docker
    
通过运行 hello-world 映像来验证是否正确安装了 Docker Engine-Community 。
    
    $ sudo docker run hello-world
    