# [野火IM](https://github.com/wildfirechat)

## 目标

  - 了解项目是什么，能干什么
  - 简单上手部署，使用
  - 简单介绍几个API在具体项目使用
  - 简单答疑
  
## 项目介绍

- 什么是野火IM

  野火IM是一套开源通用的即时通讯组件，能够更加容易地赋予客户IM能力，使客户可以快速的在自有产品上添加聊天功能。使用野火可以替代云通讯产品或减少自研IM的工作量。降低客户使用IM的成本和难度。

- 野火IM的目标是什么

  一直以来给自己的产品加上IM能力都是一件比较困难的事情，要么是架构落后性能不好（XMPP），要么是费用贵业务受制于人安全有隐忧（云通讯公司）。我们的目标是提供一个免费可控高效易用的IM组件，让拥有IM能力不再是一种奢望，让沟通不再是难事。


- 野火IM技术特点

  野火IM使用了微信Mars连接库，序列化使用protobuf，协议使用MQTT修改的私有协议，借鉴了微软ActiveSync的思路。做到不丢消息，不重复，完美地支持多端。另外针对安全性做了仔细的设计，链路层全程加密，本地数据库加密。提供了UI库，大大减少开发者的工作量。野火IM可能是世界上内核最像微信的一个IM（使用了微信的连接库，使用了微信类似的协议）。

- 野火IM都有什么功能

  野火IM提供能力库和UI库，支持单聊、群聊、聊天室、频道（类似与微信的公众号)和机器人。支持Server API。提供用户信息、好友关系和群组信息托管。支持常见消息类型和自定义消息。提供单人的音视频通话能力。

## [系统架构](./architecture/README.md)

## 服务器部署

  服务器提供[社区版](https://github.com/wildfirechat/server/releases)和[Demo应用服务](https://github.com/wildfirechat/app_server/releases)软件。社区版是IM通讯服务器，负责发送消息等IM业务；Demo服务是模拟客户的应用服务，提供登陆等功能。

- 环境需求

  Windows/Linux/MacOS都可以，需要JRE1.8以上，需要网络环境。如果没有公网IP，也可以在局域网内体验。需要开通1883、80和8888端口。

- 野火IM服务器的部署

  - 配置修改

    解压后，修改/config/wildfirechat.conf文件，修改http_port为80，修改server.ip为服务器ip地址。*注意一定要改成客户端可以访问的地址，不能用127.0.0.1或localhost, 另外要注意是使用软件包，不是源码，如果您下载的是源码的话需要先编译。*

  - 运行

    使用root用户，执行
    ```
    cd /home/user/distribution-0.29
    nohup sudo sh ./bin/wildfirechat.sh &
    ```

    *注意一定到在bin的同级目录下执行命令，不要到bin内执行*

  - 查看启动是否成功

    执行相应系统的启动命令之后，等待10秒钟后，在浏览器中输入[http://${服务器的IP}/api/version](http://192.168.244.62/api/version)，查看版本信息。

 - Demo Server 部署

  - 配置修改

    本演示服务有3个配置文件在工程的config目录下，分别是application.properties, im.properties和tencent_sms.properties。请正确配置放到jar包所在的目录下的config目录下。

    app软件下载解压后，修改/config/sms.properties文件，设置`superCode`为`66666`

  - 运行

    ```
    cd /home/user/app_demo
    nohup java -jar app-0.29.jar &
    ```
  
  - 查看启动是否成功

    等待10秒钟，在浏览器中输入[http://${服务器的IP}:8888/](http://192.168.244.62:8888)，查看是否返回OK。

## 基础知识

  - [SDK与Demo的关系](./base_knowledge/sdk_demo.md)

  - [用户](./base_knowledge/user.md)

  - [SDK的功能](./base_knowledge/sdk_abilities.md)

  - [连接](./base_knowledge/connect.md)

  - [会话](./base_knowledge/conversation.md)

  - [消息](./base_knowledge/message.md)

  - [消息内容](./base_knowledge/message_content.md)

  - [消息负载](./base_knowledge/message_payload.md)

  - [存储与同步](./base_knowledge/storage_and_sync.md)

  - [离线消息](./base_knowledge/offline_message.md)

## iOS开发

  - [代码编译与工程说明](./ios/compile.md)

  - [ChatClient简介](./ios/chatclient.md)

  - [ChatUIKit简介](./ios/chatuikit.md)

  - [Wildfire Chat简介](./ios/wildfirechat.md)

  - [推送集成](./ios/push.md)

## Android开发

  - [代码编译与工程说明](./android/compile.md)

  - [ChatClient简介](./android/chatclient.md)

  - [ChatUIKit简介](./android/chatuikit.md)

  - [Wildfire Chat简介](./android/wildfirechat.md)

  - [推送集成](./android/push.md)

## [音视频](./webrtc/README.md)

---
---
