---
id: snapshot
title: 数据裁剪
---

> **注意! 此功能在 `v1.0.0` 版本中暂时不支持，计划后续实现**

CITA 提供了快照工具，给当前区块链某一个节点做快照，对节点数据进行了一定的裁剪，只保存某个高度的状态、区块等数据。

留存数据：

- 被裁剪后的节点数据只包含区块头 (block_header)；不包含 body，即没有交易相关内容。

使用场景：

- 新加入节点数据同步：然后将快照恢复到另一个节点/本节点，就可以在较短时间内同步/恢复区块链数据。
- 节约磁盘空间：节点数据被裁剪后可以达到节约磁盘空间的目的。

使用限制：

- 节点如果规划为全节点，则不应考虑快照方案去解决磁盘空间不足的问题，需要规划磁盘扩容方案，否则快照后数据不全，对于部分查询请求以及同步等操作，可能会带来失败。
- 如果链上所有节点都做过快照，则会导致直接增加节点失败，增加节点后需要从快照数据恢复，新增节点才能成功运行。

## 使用说明

snapshot-tool 有两个功能：创建快照和快照恢复

- 创建快照是将当前区块链的状态等数据保存到文件中。
- 快照恢复是根据保存下来的文件将区块链数据恢复到创建快照时的状态。

命令格式如下：

    snapshot-tool -m snapshot [-e HEIGHT]  [-f FILE]
    snapshot-tool -m restore [-f FILE]
    

中括号中的选项是可选的。

- -m 是指定功能，快照或者恢复。
- -e 是指定区块链高度，缺省值是区块链当前高度。
- -f 是指定快照文件的名字，如果指定为 FILE，chain 模块会生成 FILE_chain.rlp，executor 模块会生成 FILE_executor.rlp，缺省时是 snapshot_chain.rlp 和 snapshot_executor.rlp。

### 创建快照

以对节点 0 的 1000 高度做快照为例（当前链高度需大于 1000）：

    $ cd test-chain/0
    $ ../../bin/snapshot-tool -m snapshot -e 1000
    $ ls snap*
    snapshot_chain.rlp  snapshot_executor.rlp
    

-e 表示保存到 1000 块高结束，最后生成了两个 rlp 文件。

> 注意：由于区块链的区块数据和状态分别保存在 Chain 和 Executor 微服务中，所以需要两个模块都进行快照，生成快照文件，恢复的时候根据各自的快照文件进行恢复。

### 快照恢复

以将快照恢复到 node 1 为例：

1. 将上述生成的快照文件拷贝到需恢复链数据的节点目录下

   ```bash
   $ cd test-chain/1
   $ cp ../0/snapshot_chain.rlp ../0/snapshot_executor.rlp ./
   ```

2. 依快照文件快照恢复
    
    快照命令行工具接受恢复参数后，依据快照文件恢复数据。

   ```bash
   $ ../../bin/snapshot-tool -m restore
   ```

节点 1 恢复完后从块 1001 开始从链上同步数据达到当前链的高度。