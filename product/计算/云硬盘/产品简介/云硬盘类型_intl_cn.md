云硬盘是一种高可用、高可靠、低成本、可定制化的网络块设备，可以作为云服务器的独立可扩展硬盘使用。它提供数据块级别的数据存储，采用三副本的分布式机制，为云服务器提供数据可靠性保证。云硬盘提供以下三种云硬盘类型，不同的硬盘类型性能特点和价格均不同，用户可根据部署的应用要求自行选择。

## 高性能云硬盘

### 简介
高性能云硬盘是腾讯云推出的混合型存储类型，通过 Cache 机制提供接近固态存储的高性能存储能力，同时采用三副本的分布式机制保障数据可靠性。高性能云硬盘适用于高数据可靠性要求、普通中度性能要求的中小型应用和 MySQL、SQL Server、PostgreSQL 等中小型关系数据库应用的场景。

### 规格及性能
提供50GB - 16000GB的规格选择。

| 性能指标 |计算 |
|---------|---------|
| 随机 IOPS | 最大随机 IOPS = 1500 + 存储容量（GB）× 8，且最大随机 IOPS ≤ 4500|
| 吞吐量（MB/s） | 最大吞吐量 = 90 + 存储容量（GB）× 0.15，且最大吞吐量 ≤ 130MB/s|
| 时延 |	0.5ms - 3ms |

例如，单块高性能云硬盘存储容量为500GB。
- 1500 + 500 × 8 = 5500 > 4500，则最大随机 IOPS 为4500。
- 90 + 500 × 0.15 = 165 > 130，则最大吞吐量为130MB/s。

### 价格
各地域价格请参考 [价格总览](https://intl.cloud.tencent.com/document/product/362/2413)。

### 典型使用场景
高性能云硬盘旨在满足90%的 I/O 场景，主要应用于以下数据场景：
- 适用于中小型数据库、Web 服务器等，提供长期的稳定 I/O 性能输出
- 适用于企业办公业务、日志服务等对存储容量和性能有平衡诉求的场景
- 满足核心业务测试、开发联调环境的 I/O 需求

## SSD 云硬盘
### 简介
SSD 云硬盘基于全 NVMe SSD 存储介质，采用三副本的分布式机制，提供低时延、高随机 IOPS、高吞吐量的 I/O 能力及数据安全性高达99.9999999%的高性能存储。SSD 云硬盘适用于对 I/O 性能有较高要求的场景。

### 规格及性能
提供100GB - 16000GB的规格选择。
单块 SSD 云硬盘最高可提供24000随机读写 IOPS、260MB/s吞吐量的存储性能。具体性能值与购买的容量相关：

| 性能指标 |计算 |
|---------|---------|
| 随机 IOPS | 最大随机 IOPS = 1400 + 存储容量（GB）× 30，且最大随机 IOPS ≤ 24000|
| 吞吐量（MB/s） | 最大吞吐量 = 120 + 存储容量（GB）× 0.2，且最大吞吐量 ≤ 260MB/s|
| 时延 |	0.5ms - 2ms |

例如，单块 SSD 云硬盘存储容量为500GB。
- 1400 + 500 × 30 = 16400 < 24000，则最大随机 IOPS 为16400。
- 120 + 500 × 0.2 = 220 < 260，则最大吞吐量为220MB/s。

### 价格
各地域价格请参考 [价格总览](https://intl.cloud.tencent.com/document/product/362/2413)。

### 典型使用场景
SSD云硬盘旨在满足 I/O 密集型业务对存储性能的要求，主要应用于以下数据场景：
- 高性能、高数据可靠性： 适用于高负载、核心关键业务系统。提供三份数据冗余，具备完善的数据备份、快照、数据秒级恢复能力
- 中大型数据库：可支持百万行表级别的 MySQL、Oracle、SQL Server、MongoDB 等中大型关系数据库应用 
- 大型 NoSQL：满足 HBase、Cassandra 等 NoSQL 业务对存储的性能要求
- 核心业务系统：对数据可靠性要求高的 I/O 密集型等核心业务系统 
- 大数据分析： 提供针对 TB、PB 级数据的分布式处理能力，适用于数据分析、挖掘、商业智能等领域

## 普通云硬盘（上一代存储类型）
### 简介
普通云硬盘为腾讯云提供的上一代云硬盘类型，适用于数据不经常访问的低 I/O 负载的业务场景。采用磁介质作为存储介质，采用三副本的分布式机制实现高可靠的数据存储。

### 规格及性能
提供10GB - 16000GB的规格选择，支持40MB/s - 100MB/s的 I/O 吞吐性能和数百到1000的随机 IOPS 性能。

### 价格
各地域价格请参考 [价格总览](https://intl.cloud.tencent.com/document/product/362/2413)。
