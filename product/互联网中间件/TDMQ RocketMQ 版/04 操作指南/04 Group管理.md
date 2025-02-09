## 操作场景
Group 用于标识一类 Consumer，这类 Consumer 通常消费同一类消息，且消息订阅的逻辑一致。

该任务指导您使用消息队列 TDMQ RocketMQ 版时在控制台上创建，删除和查询 Group。

## 前提条件

- 需要提前创建好对应的命名空间。
- 根据 TDMQ 提供的 SDK 创建好消息的生产者和消费者并正常运行。

## 操作步骤

### 创建Group

1. 登录 [TDMQ 控制台](https://console.cloud.tencent.com/tdmq)，选择地域后，单击目标集群的“ID”进入集群基本信息页面。
2. 单击顶部【Group】页签，选择命名空间后，单击【新建】进入创建 Group 页面。

3. 填写 Group 相关信息。

   ![](https://main.qcloudimg.com/raw/534f1e4d860ea033a0654ea01ae5e436.png)

   - Group 名称：填写 Group 名称（创建后不可修改），3-64个字符，只能包含字母、数字、“-”及“_”

   - Group 说明：填写 Group 说明

   - 高级设置：

     - 开启消费：关闭后 Group 下的所有消费会暂停，重新开启可继续消费

     - 开启广播模式：关闭后 Group 下的所有声明为广播模式的消费者会暂停，重新开启可继续消费

4. 单击【提交】，完成 Group 创建。

### 查看消费者详情

1. 在【Group】列表，单击操作列的【查看消费者详情】，进入订阅列表。

2. 展开列表后可以看到 Group 的基本信息和连接的客户端信息。

   - 消费模式：集群模式或者广播模式
     - 集群消费：当使用集群消费模式时，任意一条消息只需要被集群内的任意一个消费者处理即可。
     - 广播消费：当使用广播消费模式时，每条消息会被推送给集群内所有注册过的消费者，保证消息至少被每个消费者消费一次。

   - 客户端协议：目前仅支持 TCP 协议

   - 总消息堆积：消息堆积的总数量

   - 消费者类型：ACTIVELY 或 PASSIVELY  

     ![](https://main.qcloudimg.com/raw/dc75a357f6a3f910cd86c099bde6a4b8.png)

3. 单击客户端操作栏的**查看详情**可查看消费者详情。

   ![](https://main.qcloudimg.com/raw/de8b5d914ce93f5140c59dce9652f820.png)

### 设置 offset

1. 在 Group 列表中，单击目标 Group 操作列的【重置 offset】。
2. 在弹窗中，可以选择**从最新位点开始**或者**按从指定时间点开始**设定Topic的**消费位移 offset**（即指定该订阅下的消费者从哪里开始消费消息）。
3. 单击【提交】，完成设置。
    ![](https://main.qcloudimg.com/raw/925796ef91aff53610512b7ee082ed0b.png)

### 编辑 Group

1. 在 Group 列表中，单击目标 Group 操作列的【编辑】。
2. 在弹窗中，对 Group 信息进行编辑。
3. 单击【提交】，完成修改。

### 删除 Group
>!删除 Group 后，由该 Group 标识的消费者将立即停止接收消息，该 Group 下的所有配置将会被清空，且无法恢复，请您谨慎执行该操作。

1. 在 Group 列表中，找到需要删除的 Group，单击操作列的【删除】。
2. 在弹出的提示框中，单击【提交】，完成删除。

