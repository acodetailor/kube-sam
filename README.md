# kube-sam
kubebuilder + code-generator 搭建问题过程记录

1、搭建kubuilder的开发环境。

--命令： 主要涉及k8s资源的gvc概念。

kubebuilder init --domain my.crd.com

kubebuilder create api --group custom --version v1 --kind Unit

执行完毕后，kubebuilder的开发框架基本搭建完毕，你可以尝试编写控制器，控制k8s的原生资源。

2、控制其他资源

需要将自定义或者其他（istio、knative）注册到schema。即可像操作原生资源一样操作自定义资源。（main.go的init方法）

3、需要在其他的服务中使用client-go操作你的CRD资源，则需要有自己的clientset。通过 code-generator 。自动生成clientset

--配置hack 和 code-generator .

--api目录下添加doc.go和register.go

--type.go添加 // +genclient 注释。

--注意go mod引入的包的版本和 k8s环境版本的兼容性。
