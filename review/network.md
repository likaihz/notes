# 第一章 引言
## 网络硬件
* 传输技术
  point-to-point
  broadcast

#### 个域网 PAN

#### 局域网 LAN
* 有线局域网的拓扑结构是以点到点链路为基础的
* 俗称以太网（Ethernet）的是最常见的一种有线局域网
* 交换式以太网（switched Ethernet）
    交换机
####城域网 MAN
####广域网 WAN
* **主机 host** 运行用户程序的计算机
* 连接主机的网络的其余部分为**子网 subnet**
子网的最初含义是一组路由器和通信线路的集合
子网的工作是把信息从一个主机携带到另一个主机
子网由两个部分组成：**传输线路 transmission line 和 交换元素 switching element**

* 传输线路：负责在机器之间移动比特 （铜线、光纤、无线）
* 交换元素：简称为交换机，就是现在的路由器router
* 广域网和局域网的区别：  
广域网中主机和子网由不同的人拥有和经营
广域网中路由器连接不同类型的网络技术
广域网中子网可以连接单个计算机或者连接整个局域网

* 两种类型的广域网
VPN：办事处直接连接到Internet
ISP：子网由不同的公司负责运营，成为ISP

## 网络软件
####协议层次结构
* 每一层向上一层提供特定的服务
* 协议：**对等体peer** （不同机器上构成相应层次的实体） 之间通信的约定
* 实际上，数据是从当前层向下传递一直到物理介质再进行实际的通信。
* 接口：一对相邻层次之间的是**接口interface**

####层次设计问题
* 可靠性：
   检错和纠错  error detection 、  error correction
    路由 routing
* 网络演进
寻址和命名 addressing and naming
网络互联 internetworking
可扩展 scalable
* 资源分配
统计复用 statistical multiplexing
流量控制 flow control

####面向连接与无连接服务

####服务原语 Service primitive
一个服务由一组原语正式说明

####服务与协议的关系
* 服务是指某一层向它的上一层提供的一组原语（操作），定义了盖层代表器其用户执行哪些操作，而不涉及如何实现这些操作。
* 协议是一组规则，规定了同一层上对等实体之间交换的数据包或者报文的格式和含义。

##参考模型
####OSI参考模型
* 共有7层：物理层 -> 数据链路层 -> 网络层 -> 传输层 -> 会话层 -> 表示层 -> 应用层
* 物理层：关注在一条通信信道上传输的原始比特。
* 数据链路层 data link：将一个原始的传输设施转变成一条没有漏检传输错误的线路。
为此，发送方将输入的数据拆分成**数据帧data frame**，接收方回复**确认帧 acknowledgement frame**。
* 网络层：控制子网的运行。路由、处理拥塞。
* 传输层transport layer：接收来自上一层的数据。
* 会话层session layer：允许不同机器上的用户建立会话。
* 表示层presentation layer：
* 应用层application layer：包含了用户通常需要的协议（HTTP等）

#### TCP/IP参考模型
* 链路层link layer：不是一个真正意义上的层，而是主机与传输线路之间的一个接口。
* 互联网层internet layer：该层的任务时允许允许主机将数据包注入到任何网络，并且让这些数据包独立地到达接收方。
互联网层定义了官方的数据包格式和协议，称为因特网协议IP Internet Protocol。**互联网层的任务是将IP分组投递到它们该去的地方**。还有一个辅助协议，称为因特网控制报文协议（ICMP）
* 传输层：目标是允许源主机和目标主机上的对等实体进行对话。这里定义了两个端到端的传输协议，一个是**传输控制协议（TCP）**，另一个是用户数据报协议（UDP）
* 应用层：包含了所有的高层协议（FTP、SMTP等）


# 第二章 物理层
## 理论基础

####带宽
* 一般情况下对导线而言，在0到某个频率f的这段范围内，振幅在传输过程中不会衰减，这段频率的宽度就称为带宽。

####信道的最大数据速率
* **尼奎斯特定理 （无噪声信道）**：如果一个任意信号通过一个带宽为Bde低通滤波器，那么只要进行2BHz的采样就可以完全重构出被过滤的信号，如果信号包含了V个离散等级（如二进制信号的V=2），则 **最大数据速率 = 2B log<sub>2</sub>V (bits/S) **

* **香农定理（有噪声信道）**：将信号功率记做S，噪声功率记做N，则S/N称为信噪比，如果信道带宽为BHz，那么**最大数据速率 = B log<sub>2</sub> (1+S/N) (bits/S)**

## 引导性传输介质 Guided Transmission Data
* 磁介质
* 双绞线 twisted pair
* 同轴电缆 coaxial cable
* 电力线 power lines
* 光纤 fiber optics

## 无线传输
* 电磁波谱 The Electromagnetic Spectrum
* 无线电传输 Radio Transmission
* 微波传输 Microwave Transmission
* 红外传输 Infrared and Millimeter Waves
* 光波传输 Lightwave Transmission

##通信卫星

##数字调制与多路复用 Digital Modulation and Multiplexing
* 数字调制：比特与信号之间的转换称为数字调制

####基带传输
* 不归零 NRZ，Non-Return-Zero：用正电压表示1，负电压表示0
* 带宽效率：用单个符号一次携带多个比特，因此减少了所需的带宽，把信号改变的速率称为符号率，又称波特率。

####通带传输？
####频分复用 Frequency Division Multiplexing
* 正交频分复用，OFDM

####时分复用 Time Division Multiplexing

####码分复用 Code Division Multiplexing


# 第三章 数据链路层
学习内容涉及两台相邻机器实现可靠有效的完整信息块（帧）通信的一些算法。
##数据链路层的设计问题
从网络层获得数据包，然后将这些数据包封装成**帧**一边传输，每个帧包含一个帧头、一个有效载荷（存放数据包）以及一个帧尾。
####提供给网络层的服务
* 无确认的无连接服务 Unacknowledged connectionless service
* 有确认的无连接服务 Acknowledged connectionless service
* 有确认的有连接的服务 Acknowledged connection-oriented service
####成帧方法
* 字节计数法 Byte Count
每一帧头部用一个字段来标识该帧中得字符数（不能错误 -> 很少使用）
* 字节填充的标志字节法 Flag bytes with byte stuffing
每一帧用一些特殊的字节作为开始和结束，这些特殊字节通常相同，称为**标志字节 flag byte**，两个连续的标志字节代表两帧之间。为了避免数据中出现的标志字节干扰边界，转义标志字节，这种计数称为**字节填充**
PPP协议（Point-to-Point Protocol）：字节填充方案的协议
* 比特填充的标志比特法 Flag bits with bit stuffing
每个帧的起始都用一个特殊的比特模式标志
* 物理层编码违禁法 Physical layer coding violations

####差错控制
####流量控制 Flow Control
* 基于反馈的流量控制 Feedback-based flow control
* 基于速率的流量控制 Rate-based flow control

##差错检测和纠正

####纠错码 Error-Correcting Codes
* 也称为向前纠错 FEC
*  r个校验位和m位数据，令数据块总长度为n = m + r， 将此描述为（n，m）码。这n位单元称为n位**码字**。m/n称为**码率**。
* **海明距离 Hamming distance**：两个码字中不相同的位的个数。（如果两个码字的海明距离为d，则需要d个1位错误才能将一个码字转变成另一个码字）。
* 为了可靠地检测d个错误，需要距离为d+1的编码方案；
    为了纠正d个错误，需要距离为2d+1的编码方案。
* 纠正所有单个错误： （m+r+1）<=  2 <sup>r</sup>
* 海明方法：码字的位从左开始从1编号，2的幂次方位是校验位。
卧槽也太特么复杂了吧！！！书上就两段话你能信？
* 卷积码
* 里德所罗门码
* 低密度奇偶校验码 LDPC
####检错码 Error-Detecting Codes
* 三种检错码，都是线性的系统块码
* 奇偶校验 Parity
* 校验和 Checksums
* 循环冗余校验（CRC）
生成多项式有r+1位则在帧低位续上r个0，将结果和生成多项式G（x）模2除，的到得余数再和被除数做异或，最终得到发出的帧。
r位检测位的多项式能检测所有长度<=r的错误。

##基本数据链路层协议
* 一些约定：wait_for_event(&event)