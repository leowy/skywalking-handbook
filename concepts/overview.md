# 观察分布式服务

服务化的发展，以及容器化编排、微服务架构、Service Mesh 等各项技术的持续进化，为分布式服务化提供了技术层面的支持。
但是，仅仅构建微服务是不够的，对于一套完整的技术体系而言，除了开发，还需要运维给予强力支持。
随着微服务架构的持续演进，应用和服务数量不断增加，调用关系越来越复杂。所以，从运维的角度来看，首要任务便是保持可观擦性（Observability）。
我们再来大致看一下 CNCF 的全景图：

![landscape.png](../images/landscape.png)

我们着重看右上角的 Obervability And Analysis 模块：

![obervability_and_analysis](../images/obervability_and_analysis.png)

CNCF 赋予了可观察性极高的地位，可观察性和由操作系统、底层网络提供商构成的平台一样，贯穿整个云原生体系。

  变化是微服务的本质，也是应用系统设计和研发中唯一不变的准则。
  因此，无法通过一张静态的架构图来描述微服务架构下的系统部署情况。
  微服务集群的组成元素、依赖惯需、流量分布以及外部边界等都会随着事件发生变化。虽然微服务技术降低了应对变化的难度，
  但运维团队却依然需要明确地了解系统的运行情况，这就是微服务系统对可观察性的诉求。

  可观察性提供了穿越微服务边界的能力，它先对应用数据或管理平台数据进行观测及后台分析，然后通过高度可视化系统，直观地将系统当前的状态展现出来。

## 层次划分

根据观察层次的不同，谈论可观察性时一般涉及基础设施层、工具层和应用环境层。

- 基础设施层：对云主机、操作系统、云服务进行包括可用性在内的基础指标监控，提供云服务商的基础运维支持能力。
- 工具层：编排工具的可观察性是微服务体系中的重要一环，随着容器化的不断推进，对 Kubernetes 和 Mesos 等容器编排生态工具的监控也越来越多样化。另外，由于 DevOps 体系的发展，相关工具链（如Git、SVN、CI/CD等）的可观察性也成为当今的关注焦点。
- 应用环境层：应用环境层的可观察性是指对应用服务器、数据库、消息队列、缓存等中间件组件进行观察。

由于基础设施层的监控和系统健康度观察大多由平台提供商直接负责，而工具层的解决方案基本是由其核心产品以及周边生态提供的，因此对于微服务和云原生应用开发者来说，关注点应集中在应用环境层。
应用环境层因为涉及业务系统，所以场景变化也是最多的。后面就将具体介绍如何进行应用环境层的系统观察。