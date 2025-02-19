# KubeOperator - 从这里开启您的 Kubernetes 之旅

[![License](http://img.shields.io/badge/license-apache%20v2-blue.svg)](https://github.com/KubeOperatpr/KubeOperatpr/blob/master/LICENSE)
[![Python3](https://img.shields.io/badge/python-3.6-green.svg?style=plastic)](https://www.python.org/)
[![Django](https://img.shields.io/badge/django-2.1-brightgreen.svg?style=plastic)](https://www.djangoproject.com/)
[![Ansible](https://img.shields.io/badge/ansible-2.6.5-blue.svg?style=plastic)](https://www.ansible.com/)
[![Angular](https://img.shields.io/badge/angular-7.0.4-red.svg?style=plastic)](https://www.angular.cn/)

KubeOperator 是一个开源项目，在离线网络环境下，通过可视化 Web UI 在 VMware、Openstack 或者物理机上规划、部署和运营生产级别的 Kubernetes 集群。KubeOperator 是 [Jumpserver](https://github.com/jumpserver/jumpserver) 明星开源团队在 Kubernetes 领域的的又一全新力作。

![overview](https://github.com/KubeOperator/docs/blob/master/website/static/img/overview.png?raw=true)

> 注： KubeOperator 2.1 已通过云原生基金会（CNCF）的 [Kubernetes 软件一致性认证](https://landscape.cncf.io/selected=kube-operator)。

## Web UI 展示

![overview](https://raw.githubusercontent.com/KubeOperator/website/master/images/kubeoperator-ui.jpg)

>更多功能截屏请查看：https://docs.kubeoperator.io/kubeoperator-v2.1/screenshot

## 整体架构

KubeOperator 使用 Terraform 在 IaaS 平台上自动创建主机（用户也可以自行准备主机，比如物理机或者虚机），通过 Ansible 完成自动化部署和变更操作，支持 Kubernetes 集群 从 Day 0 规划，到 Day 1 部署，到 Day 2 运营的全生命周期管理。

![overview](https://github.com/KubeOperator/docs/blob/master/website/static/img/KubeOperator.jpeg?raw=true)

## 技术优势

-  按需创建：调用云平台 API，一键快速创建和部署 Kubernetes 集群 (即 Kubernetes as a Service)；
-  按需伸缩：快速伸缩 Kubernetes 集群，优化资源使用效率；
-  按需修补：快速升级和修补 Kubernetes 集群，并与社区最新版本同步，保证安全性；
-  自我修复：通过重建故障节点确保集群可用性；
-  离线部署：持续更新包括 Kubernetes 及常用组件（即内置应用）的离线包；
-  Multi-AZ 支持：通过把 Kubernetes 集群 Master 节点分布在不同的故障域上确保的高可用；

## 功能列表

<table class="subscription-level-table">
    <tr class="subscription-level-tr-border">
        <td class="features-first-td-background-style" rowspan="13">集群 Day 0 规划</td>
        </td>
        <td class="features-third-td-background-style" rowspan="2">集群模式
        </td>
        <td class="features-third-td-background-style">1 个 Master 节点 n 个 Worker 节点模式：适合开发测试用途
        </td>       
    </tr>
    <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style">3 个 Master 节点 n 个 Worker 节点模式， Master 节点分布在不同故障域：适合生产用途
        </td>
    </tr>    
    <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style" rowspan="3">计算方案
        </td>
        <td class="features-third-td-background-style">独立主机：支持自行准备的虚机和物理机
        </td>  
    </tr>    
    <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style">vSphere 平台：支持自动创建主机（使用 Terraform）
        </td>
    </tr>
    <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style">Openstack 平台：支持自动创建主机 （使用 Terraform）
        </td>
    </tr>
    <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style" rowspan="3">存储方案
        </td>
        <td class="features-third-td-background-style">独立主机：支持 NFS / Ceph RBD (通过 Rook) / NetApp （通过Trident)
        </td>
    </tr>
    <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style">vSphere 平台：支持 vSphere Datastore （vSAN 及 vSphere 兼容的各种集中存储）
        </td>
    </tr> 
     <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style">Openstack 平台：支持 Openstack Cinder （Ceph 及 Cinder 兼容的各种集中存储）
        </td>
    </tr>
    <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style" rowspan="4">网络方案
        </td>
        <td class="features-third-td-background-style">支持 Flannel / Calico 网络插件
        </td>
    </tr>
    <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style">支持通过 F5 Big IP 对外暴露服务
        </td>
    </tr> 
    <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style">支持 Traefik
        </td>
    </tr>    
    <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style">支持 CoreDNS
        </td>
    </tr>
    <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style">操作系统
        </td>
        <td class="features-third-td-background-style">支持 CentOS 7.4 / 7.5 / 7.6 / 7.7
        </td>
    </tr>    
    <tr class="subscription-level-tr-border">
        <td class="features-first-td-background-style" rowspan="3">集群 Day 1 部署
        </td>
        <td class="features-third-td-background-style" rowspan="3">部署
        </td>  
        <td class="features-third-td-background-style">提供离线环境下的完整安装包
        </td>         
    </tr>
     <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style">支持可视化方式展示部署过程
        </td>
    </tr>
     <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style">支持一键自动化部署（使用 Ansible）
        </td>
    </tr> 
    <tr class="subscription-level-tr-border">
        <td class="features-first-td-background-style" rowspan="11">集群 Day 2 运营
        </td>
        <td class="features-third-td-background-style" rowspan="4">管理
        </td>  
        <td class="features-third-td-background-style">内置 K8s 官方的 Dashboard 管理应用
        </td>         
    </tr>
     <tr class="subscription-level-tr-border">
         <td class="features-third-td-background-style">内置 Weave Scope 管理应用
        </td>
    </tr>  
    <tr class="subscription-level-tr-border">
         <td class="features-third-td-background-style">提供 Web Kubectl 界面
        </td>
    </tr> 
    <tr class="subscription-level-tr-border">
         <td class="features-third-td-background-style">内置 Helm 
        </td>
    </tr>   
    <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style" rowspan="3">可观察性
        </td>
         <td class="features-third-td-background-style">内置 Promethus 监控和告警方案，支持对集群、节点、Pod、Container的全方位监控
        </td>
    </tr>
     <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style">内置 Loki 日志方案
        </td>
    </tr> 
    <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style">内置 Grafana 作为监控和日志展示
        </td>
    </tr>  
    <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style">升级
        </td>
         <td class="features-third-td-background-style">支持集群升级
        </td>
    </tr> 
    <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style">伸缩
        </td>
         <td class="features-third-td-background-style">支持增加或者减少 Worker 节点
        </td>
    </tr>
    <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style">备份
        </td>
         <td class="features-third-td-background-style">支持 etcd 定期备份
        </td>
    </tr>     
     <tr class="subscription-level-tr-border">
        <td class="features-third-td-background-style">应用商店
        </td>
         <td class="features-third-td-background-style">集成 KubeApps 应用商店
        </td>
    </tr>     
 </table>

 ## Demo 视频、使用文档

-  [:tv:8 分钟演示视频]( https://kubeoperator-1256577600.file.myqcloud.com/video/KubeOperator2.1.mp4)：详细演示 KubeOperator 的功能。
-  [:books:安装及使用文档](https://docs.kubeoperator.io/)：包括 KubeOperator 安装文档、使用文档、功能截屏、常见问题等。

 ## Kubernetes 离线安装包

KubeOperator 提供完整的离线 Kubernetes 安装包（包括 Kubernetes、Docker、etcd、Dashboard、Promethus、OS 补丁等），每个安装包会被构建成一个独立容器镜像供 KubeOperator 使用，具体信息请参考：[k8s-package](https://github.com/KubeOperator/k8s-package)。


## 沟通交流
 
- 技术交流 QQ 群：825046920；
- 技术支持邮箱：support@fit2cloud.com；
- 微信群： 搜索微信号 wh_it0224，添加好友，备注（城市-github用户名）, 验证通过会加入群聊；

## 致谢

- [Terraform](https://github.com/hashicorp/terraform): KubeOperator 采用 Terraform 来自动创建虚机；
- [Clarity](https://github.com/vmware/clarity/): KubeOperator 采用 Clarity 作为前端 Web 框架；
- [Ansible](https://github.com/ansible/ansible): KubeOperator 采用 Ansible 作为自动化部署工具；
- [kubeasz](https://github.com/easzlab/kubeasz): 提供各种 Kubernetes Ansible 脚本；

## License

Copyright (c) 2014-2019 FIT2CLOUD 飞致云

[https://www.fit2cloud.com](https://www.fit2cloud.com)<br>

KubeOperator is licensed under the Apache License, Version 2.0.
