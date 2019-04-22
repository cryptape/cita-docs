---
id: version-0.20-glossary
title: Glossary
original_id: glossary
---
## 区块链

- 区块
    
    一个区块是一个数据包，其中包含零个或多个交易，父块的哈希值，以及其他数据。除了初始的“创世区块”以外每个区块 都包含它父块的哈希值，区块的全部集合被称为区块链，并且包含了一个网络里的全部交易历史。

- 账户
    
    账户是在总账中的记录，由它的地址来索引，总账包含有关该账户的状态的完整的数据。在一个货币系统里，这包含了货币余额。

- 挖矿
    
    通过暴力尝试来找到一个字符串，使得它加上一组交易信息后的哈希值符合特定规则（例如前缀包括若干个 0），找到的人可以宣称新区块被发现，并获得系统奖励。

- 矿工
    
    参与挖矿的人或组织。

- 矿机
    
    专门为比特币挖矿而设计得设备，包括基于软件、GPU、FPGA 和专用芯片等多种实现。

- 矿池
    
    采用团队协作方式来集中算力进行挖矿，对产出的虚拟货币进行分配。

- P2P
    
    点到点的通信网络，网络中所有节点地位均等，不存在中心化的控制机制。

- 去中心化
    
    不存在第三方中心机构，全体网民可以共同参与、权级平等。

- 分布式账本
    
    可以在多个站点、不同地理位置或者多个机构组成的网络里进行分享的资产数据库。

- EVM
    
    以太坊的虚拟机，智能合约运行的环境。

- FLP Impossibility
    
    FLP 不可能性。分布式领域的一个著名理论，它的结论是：在网络可靠，存在节点失效（即便只有一个）的最小化异步模型系统中，不存在一个可以解决一致性问题的确定性算法。

- CAP
    
    分布式计算系统不可能同时确保一致性（Consistency）、可用性（Availability）和分区容忍性（Partition），设计中往往需要弱化对某个特性的保证。一致性指等同于所有节点访问同一份最新的数据副本；可用性指每次请求都能获取到非错的响应，但是不保证获取的数据为最新数据；分区容忍性指以实际效果而言，分区相当于对通信的时限要求。系统如果不能在时限内达成数据一致性，就意味着发生了分区的情况，必须就当前操作在 C 和 A 之间做出选择。

- 女巫攻击
    
    少数节点通过伪造或盗用身份伪装成大量节点，进而对分布式系统进行破坏。

- UTXO
    
    未花费的输出（Unspent Transaction Outputs）。每一笔交易的输入都会引用先前有效交易的未花费输出，再创建新的未花费输出。账户余额就是发往该账户地址的一笔笔未花费输出的累加。

## 密码学

密码学是数学和计算机科学的分支，研究如何在有敌人存在的环境中安全通信。

- 哈希
    
    即散列算法，将任意长度的二进制值映射为较短的固定长度的二进制值的算法。

- 非对称加密
    
    一种特殊的加密，具有在同一时间生成两个密钥的处理（通常称为私钥和公钥），使得利用一个密钥对文档进行加密后，可以用另一个密钥进行解密。一般地，公钥是公开的，私钥自己保留。

- 数字签名
    
    用户用私钥为文档产生一段叫做签名的短字符串数据，任何拥有相应公钥的人都可以验证该签名。

- CA
    
    Certificate Authority，负责证书的创建、颁发，在 PKI 体系中最为核心的角色。

- PKI
    
    Public Key Infrastructure，基于公钥体系的安全基础设施，是一组由硬件、软件、参与者、管理政策与流程组成的基础架构，其目的在于创造、管理、分配、使用、存储以及撤销数字证书。

- Zero-knowledge Proofs
    
    零知识证明，一种密码学技术，允许两方（证明者和验证者）来证明某个提议是真实的，而且无需泄露除了它是真实的之外的任何信息。

- Merkle Tree
    
    中文名叫默克尔树，又叫哈希树，是一种二叉树，由一个根节点、一组中间节点和一组叶节点组成。最下面的叶节点包含存储数据或其哈希值，每个中间节点是它的两个孩子节点内容的哈希值，根节点也是由它的两个子节点内容的哈希值组成。

## CITA

即分布式企业间流程自动化系统（Cryptape Inter-enterprise Trust Automation），本质是一个支持智能合约的区块链框架。CITA 将区块链节点的必要功能解耦，通过消息总线交换信息相互协作，各组件是可拔插的，可以配置和定制相应的服务，能够满足企业级用户的全部需求。

- 智能合约
    
    一段代码，被部署在分享的、复制的账本上，它可以维持自己的状态，控制自己的资产和对接收到的外界信息或者资产进行回应。

- 微服务
    
    即 CITA 将区块链节点的各功能解耦之后的组件，如共识，交易处理，点对点网络协议等这些都是微服务。微服务架构能够有效提高节点处理能力，并且使 CITA 非常容易水平扩展。

- 异步交易处理
    
    即 CITA 将共识和交易处理解耦为独立的微服务，共识只负责各节点对交易共识并对交易进行排序，而交易内容的处理交给交易处理服务，从而实现共识过程和交易处理异步执行。异步处理技术不仅使 CITA 具有更好的共识性能，还带来了更具弹性的交易处理能力。

- 执行器
    
    执行器以排好序的交易为输入，在处理过程中相应的更新对应的视图。不同的执行器对于不同的交易输入可能产生不同的视图。

- 配额
    
    即支持智能合约的区块链用来限制资源使用的机制。由于交易会被复制到多个节点执行和存储，过重的负荷会使有限的资源消耗殆尽从而导致节点失去响应。

- View
    
    即将执行器的处理结构最终展现给具体应用的组件，用户在配置 CITA 区块链网络时可设定多个视图，视图相互独立。每个视图都可以设定相应的交易执行器和状态存储模型，并将交易执行器注册到交易路由，不同视图处理的交易子集可以有交集，也可以没有交集。

- 隐私交易
    
    即无关节点不能看见交易中的数据，但是执行和验证智能合约要求所有共识节点都能看到交易中的数据，二者存在天然矛盾。CITA 采用了交易局部执行技术，实现了一种隐私方案。

## Consensus

- PoW
    
    Proof of Work，工作量证明。

- PoS
    
    Proof of Stake，权益证明。

- PBFT
    
    Practical Byzantine Fault Tolerance，实用拜占庭容错算法。

- Raft 算法
    
    一种非拜占庭容错的共识算法，比 Paxos 更容易理解。

- 拜占庭将军问题
    
    LESLIE LAMPORT 为了更形象的介绍分布式系统共识问题，而杜撰的一个故事。拜占庭帝国军队的将军们必须全体一致的决定是否攻击某一支敌军。问题是这些将军在地理上是分隔开来的，并且将军中存在叛徒。叛徒可以任意行动以达到以下目标：欺骗某些将军采取进攻行动；促成一个不是所有将军都同意的决定，如当将军们不希望进攻时促成进攻行动；或者迷惑某些将军，使他们无法做出决定。如果叛徒达到了这些目的之一，则任何攻击行动的结果都是注定要失败的，只有完全达成一致的努力才能获得胜利。