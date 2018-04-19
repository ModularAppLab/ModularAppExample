# ModularAppExample

## 一、维护各模块

UserModule 因为要引用到 ReservationModule 相关的逻辑，所以会依赖于 MediatorReservationModuleCategory，但不会依赖业务模块。
因为 MainProject 中要引用到 UserModule 相关的逻辑，所以会依赖于 MediatorUserModuleCategory。

MediatorUserModuleCategory 和 MediatorReservationModuleCategory 作为 Mediator 的扩展，都只依赖于 Mediator。


## 二、发布私有 pod

参考 upload.sh 文件

1. pod lib lint 与 pod spec lint

前者为验证远程仓库与本地仓库, 后者为仅验证本地仓库, 有时候会出现只有一个能通过, 那表明远程仓库与本地仓库没有完全对应

> 验证时，如果该 pod 依赖了其他私有 pod，就需要指定私有 pod 的 source 地址。

```
pod lib lint --sources='git@github.com:ModularAppLab/PrivatePods.git,https://github.com/CocoaPods/Specs' --verbose
```
