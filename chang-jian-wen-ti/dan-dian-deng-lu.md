# 通过单点登录实现BI系统和其他系统的整合

睿思BI系统有自己一套登录，用户，角色管理模块，也可以通过单点登录功能实现和用户已有系统实现整合，整合步骤如下：

1.用户的系统提供Rest接口，BI系统通过次接口获取用户信息，接口返回信息如下:

```
{"userId":1,"staffId":"admin","loginName":"系统管理员","gender":"女","state":1,"deptCode":"002"}
```

其中：userId 用户ID, 和 bi系统的sc\_login\_user用户表ID对应。

2.把此接口配置到 bi 系统的
