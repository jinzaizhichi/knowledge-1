# 自动伸缩

Kubernetes 集群传统的水平伸缩 HPA 所使用的指标，主要有两个来源：

- [metrics-server](https://github.com/kubernetes-sigs/metrics-server): 仅提供了 cpu/memory 两个指标
- [prometheus-adapter](https://github.com/kubernetes-sigs/prometheus-adapter): 使用 prometheus 中的 metrics 定义自定义指标用于 HPA
- [keda](https://github.com/kedacore/keda): 一个 Kubernetes 弹性伸缩控制器，支持从多种数据源（prometheus/mysql/postgresql/NATS/kafka...）获取指标进行弹性伸缩。

如果你只需要从 Prometheus 指标进行弹性伸缩，prometheus-adapter 或者 keda 都能满足你的需求。

KEDA 比 prometheus-adapter 强的地方在于，它支持从多种事件来源获取数据，而且支持缩容到零。
它的这些特性使 KEDA 被 kubevela 用做底层的自动伸缩组件，knative 对它的支持也正在路上。