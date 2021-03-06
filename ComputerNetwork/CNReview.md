Computer Networks

###Overview

1. 现在有三种最主要的网络: 电信网络(电话网); 有线电视网络; 计算机(数据)网络

2. **电路交换的特点**
电路交换必定是**面向连接**的。 
电路交换的三个阶段: **建立连接; 通信; 释放连接**
电路交换传送计算机数据效率低, 因为计算机数据具有突发性, 这导致通信线路的利用率很低。

3. **分组交换的原理**
在发送端, 先**把较长的报文划分成较短的、固定长度的数据段**。
每一个数据段前面添加上**首部**构成分组。
分组交换网以“分组”作为数据传输单元, 依次把各分组发送到接收端。
最后, 在接收端把收到的数据恢复成为原来的报文。

> 分组首部的重要性
**每一个**分组的首部都含有**地址**等控制信息。
分组交换网中的结点交换机根据收到的分组的首部中的**地址信息**, 把分组**转发**到下一个结点交换机。
用这样的**存储转发方式**, 最后分组就能到达最终目的地。

4. 结点交换机
在结点交换机中的输入和输出端口之间**没有直接连线**。
结点交换机处理分组的过程是: 把收到的分组先放入**缓存(暂时存储)**; 查找**转发表**, 找出到某个目的地址应从哪个端口转发; 把分组送到适当的**端口**转发出去。 

5. 分组交换的优点
**高效**: 动态分配传输带宽，对通信链路是逐段占用。 
**灵活**: 以分组为传送单位和查找路由。
**迅速**: 不必先建立连接就能向其他主机发送分组；充分使用链路的带宽。
**可靠**: 完善的网络协议；自适应的路由选择协议使网络有很好的生存性。   

6. 分组交换带来的问题
分组在各结点存储转发时需要**排队**，这就会造成一定的**时延**。 
分组必须携带的**首部**(里面有必不可少的控制信息)也造成了一定的开销。 

<img src="./cn/00.png" width="70%">

> 早期的面向终端的计算机网络是以单个主机为中心的星形网
> 	各终端通过通信线路共享昂贵的中心主机的硬件和软件资源。 
> 分组交换网则是**以网络为中心**，主机都处在网络的外围。
> 	用户通过分组交换网可共享连接在网络上的许多硬件和各种丰富的软件资源。  

7. **计算机网络的不同定义**
计算机网络是一些互相连接的、自治的计算机的集合。

8. **计算机网络的主要性能指标**
**发送时延(传输时延)**: 发送数据时，数据块从结点进入到传输媒体所需要的时间。
**信道带宽**: 数据在信道上的发送速率。常称为数据在信道上的**传输速率**。
(例如，带宽是 10 M，实际上是 10 Mb/s。这里的 M 是 $10^6$。 ) 
**传播时延**: 电磁波在信道中需要传播一定的距离而花费的时间。 
(信号**传输速率**(即发送速率)和信号在信道上的**传播速率**是完全不同的概念。)
**处理时延**: 交换结点为存储转发而进行一些必要的处理所花费的时间。处理时延的长短往往取决于网络中当时的通信量。
- 发送时延 = 数据块长度(bit) / 信道带宽(bit/s)
- 传播时延 = 信道长度(米)/ 信号在信道上的传播速率(米/秒)
- 总时延 = 发送时延 + 传播时延 + 处理时延
- 时延带宽积 = 传播时延 * 带宽
- (链路的时延带宽积又称为以比特为单位的链路长度, 表示链路可容纳多少比特)
- **往返时延 RTT** (Round-Trip Time) 表示从发送端发送数据开始，到发送端收到来自接收端的确认(接收端收到数据后立即发送确认)，总共经历的时延。 
**评价计算机网络性能的指标: 发送延迟, 传播延迟。**

> 常见的错误混淆了两种速率
> 在网络中有两种不同的速率：
> - 信号(即电磁波)在传输媒体上的传播速率(米/秒，或公里/秒)
> - 计算机向网络发送比特的速率(比特/秒)
> 宽带线路：每秒有更多比特从计算机注入到线路。
> 宽带线路和窄带线路上比特的传播速率是一样的。
>
> 对于高速网络链路，我们提高的仅仅是**数据的发送速率**而**不是比特在链路上的传播速率**。

9. 常见的几种计算机连网方法
点对点, 星行网, 总线网, 环形网。

10. 计算机网络的分类
从网络的交换功能进行分类;(电路交换, 报文交换, 分组交换, 混合交换)
从网络的作用范围进行分类;(WAN, LAN, 城域网 MAN, 接入网 AN (Access Network))
从网络的使用者进行分类(公用网 (public network), 专用网 (private network) )

11. 计算机网络的体系结构 
计算机网络的**体系结构(architecture)**是**计算机网络的各层及其协议**的集合。 
体系结构就是这个计算机网络及其部件所应完成的功能的**精确定义**。
**实现(implementation)**是遵循这种体系结构的前提下用何种硬件或软件完成这些功能的问题。
体系结构是抽象的，而实现则是具体的，是真正在运行的计算机硬件和软件。  

12. **划分层次的必要性**
- 计算机网络中的数据交换必须遵守事先约定好的规则。 
- 这些规则明确规定了所交换的数据的格式以及有关的同步问题(同步含有时序的意思)。
- 为进行网络中的数据交换而建立的规则、标准或约定即网络协议(network protocol)，简称为协议。  

> 分层的好处: 各层之间是独立的; 灵活性好; 结构上可分割开; 易于实现和维护; 能促进标准化工作。  

13. **实体、协议、服务 和服务访问点**[极其重要]
**实体(entity)** 表示任何可发送或接收信息的硬件或软件进程。 
**协议**是控制**两个对等实体**进行通信的规则的集合。 
在协议的控制下，两个对等实体间的通信使得本层能够**向上一层提供服务**。
要实现本层协议，还需要使用下层所提供的服务。 
本层的服务用户只能看见服务而无法看见下面的协议。
下面的协议对上面的服务用户是透明的。 
**协议是“水平的”，即协议是控制对等实体之间通信的规则。**
**服务是“垂直的”，即服务是由下层向上层通过层间接口提供的。**
同一系统相邻两层的实体进行交互的地方，称为**服务访问点 SAP (Service Access Point)**。

> 在计算机网络中，协议(protocol)是通信双方必须严格遵守的规则。
> **协议**精确地规定在网络通信中使用的各种控制信息的格式、意义以及各种事件出现的先后顺序。
> 协议在计算机网络中起着非常重要的作用。
> 协议必须保证在任何复杂的情况下都能正确工作，因此网络协议非常复杂。

14. **网络协议的组成要素**
语法: 数据与控制信息的结构或格式 。 
语义: 需要发出何种控制信息，完成何种动作以及做出何种响应。 
同步: 事件实现顺序的详细说明。 

15. 分层
三种体系结构: OSI 7层, 每一层都提供了服务。
TCPIP结构, 四层结构。只提供三层服务, 网络结构层未提供服务。
将OSI的链路层拿到TCPIP中讨论则为5层, 但TCPIP是4层(严格)。

> **TCP/IP 是四层的体系结构：应用层、运输层、网际层和网络接口层。**最下面的网络接口层并没有具体内容。
> 因此往往采取折中的办法，即综合 OSI 和 TCP/IP 的优点，采用一种只有五层协议的体系结构 。 

16. 面向连接服务与 无连接服务
- 面向连接服务(connection-oriented): 面向连接服务具有连接建立、数据传输和连接释放这三个阶段。   
- 无连接服务(connectionless): 两个实体之间的通信不需要先建立好连接。是一种不可靠的服务。这种服务常被描述为“尽最大努力交付”(best effort delivery)或“尽力而为”。 

17. IP and everything
IP over Everything: IP 可应用到各式各样的网络上

18. **客户-服务器方式**
计算机的**进程(process)**就是运行着的计算机程序。为解决具体应用问题而彼此通信的进程称为“应用进程”。
应用层的具体内容就是规定应用进程在通信时所遵循的协议。在网络环境下，许多问题的解决往往是通过位于不同主机中的多个进程之间的通信和协同工作来完成的。在 TCP/IP 的应用层协议使用的是**客户-服务器**方式。
**客户(client)和服务器(server)都是指通信中所涉及的两个应用进程。**
客户-服务器方式所描述的是进程之间服务和被服务的关系。
**客户是服务请求方，服务器是服务提供方。**

> 客户软件的特点 
> 在进行通信时临时成为客户，但它也可在本地进行其他的计算。
> 被用户调用并在用户计算机上运行，在打算通信时主动向远地服务器发起通信。可与多个服务器进行通信。
> 不需要特殊的硬件和很复杂的操作系统。
> 服务器软件的特点
> 专门用来提供某种服务的程序，可同时处理多个远地或本地客户的请求。
> 在共享计算机上运行。当系统启动时即自动调用并一直不断地运行着。
> 被动等待并接受来自多个客户的通信请求。
> 一般需要强大的硬件和高级的操作系统支持。

19. 物理层 术语和概念
数据(data)——运送信息的实体。
信号(signal)——数据的电气的或电磁的表现。 
“模拟的”(analogous)——连续变化的。“数字的”(digital)——取值是离散数值。
调制——把数字信号转换为模拟信号的过程。解调——把模拟信号转换为数字信号的过程。 
**物理层的基本概念**: 物理层的主要任务为描述确定与传输媒体的接口的一些特性，即：
- **机械特性**: 指明接口所用接线器的形状和尺寸、引线数目和排列、固定和锁定装置等等。
- **电气特性**: 指明在接口电缆的各条线上出现的电压的范围。
- **功能特性**: 指明某条线上出现的某一电平的电压表示何种意义。
- **规程特性**: 指明对于不同功能的各种可能事件的出现顺序。 
目的: 尽量在最少的时间内将最多的信息正确地传递到最远的地方
主要任务: 描述确定与传输媒体的接口及其特性

20. 导向传输媒体和非导向传输媒体
**双绞线; 同轴电缆; 光缆**
短波通信主要是靠电离层的反射，但短波信道的通信质量较差。
微波在空间主要是直线传播。

> 有关信号的几个基本概念
> 单向通信(单工通信)——只能有一个方向的通信而没有反方向的交互。
> 双向交替通信(半双工通信)——通信的双方都可以发送信息，但不能双方同时发送(当然也就不能同时接收)。
> 双向同时通信(全双工通信)——通信的双方可以同时发送和接收信息。 
>
> **基带信号**就是将数字信号 1 或 0 直接用两种不同的电压来表示，然后送到线路上去传输。 
> **宽带信号**则是将基带信号进行调制后形成的频分复用模拟信号。 
>
> 波特是码元传输的速率单位(每秒传多少个码元)。码元传输速率也称为调制速率、波形速率或符号速率。信息的传输速率“比特/秒”与码元的传输速率“波特”在数量上有一定的关系。若 1 个码元只携带 1 bit 的信息量，则“比特/秒”和“波特”在数值上相等。若 1 个码元携带 n bit 的信息量，则 M Baud 的码元传输速率所对应的信息传输速率为 M × n b/s。 
> 比特是信息量的单位。  


###数据链路层

1. 基本概念
**链路(link)**: 是一条无源的点到点的物理线路段，中间没有任何其他的交换结点。
**数据链路(data link)**: 除了物理线路外，还必须有通信协议来控制这些数据的传输。若把实现这些协议的硬件和软件加到链路上，就构成了数据链路。
现在最常用的方法是使用适配器(即网卡)来实现这些协议的硬件和软件。一般的适配器都包括了数据链路层和物理层这两层的功能。   

2. **数据链路层的主要功能**(必考)
(1) 链路管理; 2)帧定界; 3)流量控制; 4)差错控制; 5)将数据和控制信息区分开; 6)透明传输; 7)寻址    

3. 实用的停止等待协议
![](./cn/01.png)
![](./cn/02.png)

> 超时计时器的作用
> 结点A发送完一个数据帧时，就启动一个超时计时器(timeout timer)。计时器又称为定时器。
> 若到了超时计时器所设置的重传时间 $t_{out}$ 而仍收不到结点 B 的任何确认帧，则结点 A 就重传前面所发送的这一数据帧。
> 一般可将重传时间选为略大于“从发完数据帧到收到确认帧所需的平均时间”。
>
> 解决重复帧的问题
> 使每一个数据帧带上不同的发送序号。每发送一个新的数据帧就把它的发送序号加 1。 
> 若结点 B 收到发送序号相同的数据帧，就表明出现了重复帧。这时应丢弃重复帧，因为已经收到过同样的数据帧并且也交给了主机 B。
> 但此时结点 B 还必须向 A 发送确认帧 ACK，因为 B 已经知道 A 还没有收到上一次发过去的确认帧 ACK。    
>
> 帧的编号问题 
> 任何一个编号系统的序号所占用的比特数一定是有限的。因此，经过一段时间后，发送序号就会重复。 
> 序号占用的比特数越少，数据传输的额外开销就越小。 
> 对于停止等待协议，由于每发送一个数据帧就停止等待，因此用一个比特来编号就够了。一个比特可表示 0 和 1 两种不同的序号。 
>
> 可靠传输 
> 虽然物理层在传输比特时会出现差错，但由于数据链路层的停止等待协议采用了有效的检错重传机制，数据链路层对上面的网络层就可以提供**可靠传输**的服务。 

4. 帧检验序列 FCS
**在数据后面添加上的冗余码称为帧检验序列 FCS (Frame Check Sequence)。**
**帧检验序列是必须的**, CRC不是必须的。
循环冗余检验 CRC 和帧检验序列 FCS并不等同。CRC 是一种常用的检错方法，而 FCS 是添加在数据后面的冗余码。FCS 可以用 CRC 这种方法得出，但 CRC 并非用来获得 FCS 的惟一方法。 

> Attention:
> 仅用循环冗余检验 CRC 差错检测技术**只能做到无差错接受(accept)**。
> “无差错接受”是指：“凡是接受的帧(即不包括丢弃的帧)，我们都能以非常接近于 1 的概率认为这些帧在传输过程中没有产生差错”。
> 也就是说：“凡是接受的帧都没有传输差错”(有差错的帧就丢弃而不接受)。
> **要做到“可靠传输”(即发送什么就收到什么)就必须再加上确认和重传机制。**

5. 停止等待协议 ARQ 的优缺点 
优点：比较简单 。
缺点：通信信道的利用率不高，也就是说，信道还远远没有被数据比特填满。
为了克服这一缺点，就产生了另外两种协议，即连续 ARQ 和选择重传 ARQ。这将在后面进一步讨论。  

6. 连续 ARQ 协议 
在发送完一个数据帧后，不是停下来等待确认帧，而是可以连续再发送若干个数据帧。
如果这时收到了接收端发来的确认帧，那么还可以接着发送数据帧。
由于减少了等待时间，整个通信的吞吐量就提高了。
Attention: 接收端只按序接收数据帧。虽然在有差错的 2号帧之后接着又收到了正确的 3 个数据帧，但接收端都必须将这些帧丢弃，因为在这些帧前面有一个 2 号帧还没有收到。虽然丢弃了这些不按序的无差错帧，但应重复发送已发送过的最后一个确认帧(防止确认帧丢失)。

7. 滑动窗口的概念
发送端和接收端分别设定发送窗口和接收窗口 。
**发送窗口用来对发送端进行流量控制。**
发送窗口的大小 $W_T$ 代表在还没有收到对方确认信息的情况下发送端最多可以发送多少个数据帧。
**接收端设置接收窗口**
在接收端只有当收到的数据帧的发送序号落入接收窗口内才允许将该数据帧收下。 
若接收到的数据帧落在接收窗口之外，则一律将其丢弃。 
在连续 ARQ 协议中，接收窗口的大小 WR = 1。只有当收到的帧的序号与接收窗口一致时才能接收该帧。否则，就丢弃它。每收到一个序号正确的帧，接收窗口就向前(即向右方)滑动一个帧的位置。同时发送对该帧的确认。     

> **滑动窗口的重要特性**
> 只有在接收窗口向前滑动时(与此同时也发送了确认)，发送窗口才有可能向前滑动。
> 收发两端的窗口按照以上规律不断地向前滑动，因此这种协议又称为滑动窗口协议。
> 当发送窗口和接收窗口的大小都等于 1时，就是停止等待协议。  
>
> 发送窗口的最大值 
> 当用 n 个比特进行编号时，若接收窗口的大小为 1，则只有在发送窗口的大小 $W_T ≤ 2^n − 1$时，连续 ARQ 协议才能正确运行。
> 例如，当采用 3 bit 编码时，发送窗口的最大值是 7 而不是 8。 

> 信道利用率
> 由于每个数据帧都必须包括一定的控制信息(如帧的序号、地址、同步信息以及其他的一些控制信息)，所以即使连续不停地发送数据帧，信道利用率(即扣除全部的控制信息后的数据率与信道容量之比)也不可能达到 100 %。 
> 当出现差错时(这是不可避免的)，数据帧的不断重传将进一步使信道利用率降低。 
> 若数据帧的帧长取得很短，那么控制信息在每一帧中所占的比例就增大，因而额外开销增大，这就导致信道利用率的下降。
> 若帧长取得太长，则数据帧在传输过程中出错的概率就增大，于是重传次数将增大，这也会使信道利用率下降。
> 由此可见，存在一个**最佳帧长**，在此帧长下信道的利用率最高。 

8. **选择重传 ARQ 协议**
可加大接收窗口，先收下发送序号不连续但仍处在接收窗口中的那些数据帧。等到所缺序号的数据帧收到后再一并送交主机。 
选择重传 ARQ 协议可避免重复传送那些本来已经正确到达接收端的数据帧。
但我们付出的代价是在接收端要设置具有相当容量的缓存空间。
对于选择重传 ARQ 协议，若用 n 比特进行编号，则接收窗口的最大值受下式的约束 $W_R ≤ 2^n/2$

> 发送和接收窗口的大小必须是相同的，而且是最大取值序列号的一半(序列号是假设编号从0到 n-1)，为了当所有数据包都丢失时避免出错。假设所有的ACK都丢失了，如果接收窗口大于最大序列号的一半，一些甚至可能是所有的超时重传的帧，都是不能被识别的重复发送。
> 接收窗口的尺寸不能超过序号范围的1/2，否则可能造成帧的重叠。另外，发送窗口的尺寸一般和接收窗口的尺寸相同，发送端为每一个发送缓存设置一个定时计数器，定时器一旦超时，相应输出缓存区中的帧就被重发。

9. **零比特填充法**
![](./cn/hdlc.png)
(标志字段 F (Flag) 为 6 个连续 1 加上两边各一个 0 共 8 bit。在接收端只要找到标志字段就可确定一个帧的位置)
HDLC 采用零比特填充法使一帧中两个 F 字段之间不会出现 6 个连续 1。
**方法：在帧的传输起始标志和结束标志之间，每当出现5个1之后，发送器就会插入一个附加的0。一旦有5个1模式出现，就会检查第6个比特。若为0，该比特将被删除。若为1，且第7个比特为0，那么这个组合被认为是标志字段。若第六位和第七位都为1，则此时处于异常终止状态。**
在接收帧时，先找到 F 字段以确定帧的边界。接着再对比特流进行扫描。每当发现 5 个连续 1 时，就将其后的一个 0 删除，以还原成原来的比特流。 

10. 字符填充法(PPP)
将信息字段中出现的每一个 0x7E 字节转变成为 2 字节序列(0x7D, 0x5E)。 
若信息字段中出现一个 0x7D 的字节, 则将其转变成为 2 字节序列(0x7D, 0x5D)。
若信息字段中出现 ASCII 码的控制字符(即数值小于 0x20 的字符)，则在该字符前面要加入一个 0x7D 字节，同时将该字符的编码加以改变。
\
PPP 协议之所以不使用序号和确认机制是出于以下的考虑：
- 在数据链路层出现差错的概率不大时，使用比较简单的 PPP 协议较为合理。
- 在因特网环境下，PPP 的信息字段放入的数据是 IP 数据报。数据链路层的可靠传输并不能够保证网络层的传输也是可靠的。
- 帧检验序列 FCS 字段可保证无差错接受。

> 透明传输 
> 采用零比特填充法就可传送任意组合的比特流，或者说，就可实现数据链路层的**透明传输**。
> 当连续传输两个帧时，前一个帧的结束标志字段 F 可以兼作后一帧的起始标志字段。
>
> PPP 是面向字节的，所有的 PPP 帧的长度都是整数字节。  



**由收方控制发方的数据流，乃是计算机网络中流量控制的一个基本方法。**






###Getting Connected

1. 什么是直连网络?
所有的主机通过某种物理媒质直接连接。

2. 直连网络问题在体系结构中所处的层次?
1) L1(物理层) 处理物理传输媒质上的数字通信问题, 特别是比特如何表示为模拟信号; 
2) 直连网络的研究主要集中于L2(数据链路层)

3. 适配器之间的通信
**发送端**
- 将分组封装为数据帧
- 增加差错检测、可靠传输、流量控制等功能
**接收端**
- 完成差错检测、实施可靠传输、流量控制等
- 提取分组并交付之上层协议

> 物理层为上层提供比特流传输服务
>
> 数据链路层在哪里实现?
> 1) 挂载在主机的系统总线上; 
> 2) 数据链路层以适配器的形式实现 (aka 网络接口卡NIC) 或者集成在芯片上。[以太网卡, 802.11无线网卡;以太网芯片] 通常数据链路层和物理层联合实现; 
> 3) 挂载在主机的系统总线上; 
> 4)包含硬件、软件和固件
>
> IEEE 802将数据链路层功能划分为两个子层
> **LLC (逻辑链路控制)** 子层(驱动程序实现)
> 功能: 差错检测, 可靠传输;
> **MAC (介质访问控制)** 子层(硬件实现)
> 功能: 帧定界, 寻址, 多路访问控制
> 与传输媒质特点和网络适配器的设计目前相关, NIC (网络接口卡)  

4. 节点能成功的交换分组之前, 需解决的五个问题
- 编码: 对发送到电缆或光纤上的比特进行编码, 使其能被接收主机所理解
- 帧定界: 把物理链路上传输的比特序列描述为完整的消息, 以便传送到端节点
- 差错检测: 检测帧传送过程种可能出现的错误, 并采取相应的动作
- 可靠传输: 保证链路在帧不时可能出现错误情况下的可靠性
- 通信链路共享(介质访问控制): 如果链路静态共享, 很容易处理; 如果链路动态共享, 如何控制多个主机的访问顺序? 

5. 关于网络节点
- 网络适配器是节点接入网络的专用设备
- 内存访问速度可能成为节点性能的瓶颈
- 网络中的两种稀缺资源: 节点的内存及网络链路带宽

6. 关于网络适配器
**功能**
- 进行串行/并行转换
- 对数据进行缓存
- 设备驱动程序(数据链路层协议)
**接口特性**
- 机械特性:接口所用接线器的形状和尺寸、引线数目和排列、固定和锁定装置等等.
- 电气特性:在接口电缆的各条线上出现的电压的范围.
- 功能特性:某条线上出现的某一电平的电压表示何种意义.
- 规程特性:对于不同功能的各种可能事件的出现顺序.

7. 链路
**物理传输媒质**
- 导向型媒质: 信号在固态媒质上传播, 例如同轴电缆, 光纤, 双绞线
- 非导向型媒质: 信号自由传播, 例如电磁波

8. 面向字节的协议
**面向字节**: 把每一帧看做一个字节(字符)集合
**两种方法**: 字符计数法; 起止标记法

9. 比特错误
**解决方案**
- 差错检测: 接收方可以通过编码方式检测到差错
- 差错纠正, 通常有两种方法: 1)接收方通知发送方重发消息; 2)接收方重新构造消息

10. 可靠传输
**基本解决方法**
- ACK (确认): 接收方根据差错检测的结果向发送方发送一个小的控制帧进行确认[ACK = 正确接收, NAK = 帧错误]
- 超时: 如果发送方在一定的时间范围内未收到来自接受方的确认, 则重传数据帧
- 帧序号: 识别数据帧

11. 自动请求重传 (ARQ)
- ARQ: 采用确认和超时定时器的可靠传输机制
- 链路层假设: 1)串行通信信道, 传输过程中不存在帧的乱序; 2)所有数据帧的传播时延相同
- 接收方: 1)对数据帧进行差错检测; 2)对正确帧进行确认, 丢失错误帧; 3)丢弃禁止接收的数据帧
- 发送方: 1)发送原始数据帧; 2)对错误帧和丢失帧进行重传

12. 停止等待协议
- 最简单的ARQ机制
- 每发送完一个数据帧, 发送方在继续发送下一个数据帧之前必须等待确认
- 如果在一定的时间范围内, 发送方未收到确认(ACK), 则发送定时器超时激发, 发送方重传原始数据帧
**缺点**: 链路带宽利用率较低
示例: 链路带宽为$2Mbps$, $RTT$为$45ms$, 数据帧大小为$1.5KB$
每一个$RTT$内, 发送方仅能发送一个数据帧; 吞吐量为$1500*8/0.045 = 266.7Kbps$
**如何改进**: 充分利用“管道”流水传送(连续ARQ协议)

13. 流水线协议
**流水线**: 允许发送端未收到确认, 连续发送多个“传输中”的数据帧
- 必须增加序列号的允许范围
- 发送端和接收端需要缓存
**流水线协议的两种基本形式**
- Go-Back-N
- 选择性重传

![](./cn/gobackn.png)
![](./cn/selective.png)

> 连续ARQ协议的两种策略
> **Go-Back-N**
> - 一次性发送N个数据帧；
> - 如果第k个帧丢失, 对[k, k+N-1]范围内的所有帧重传。
> - 优点: 接收方不需要缓存接收到的乱序帧, 确认简单
> - 缺点: 正确帧也可能被重传, 效率较低
> **选择性重传**
> - 一次性发送N个数据帧；
> - 如果第k个帧丢失, 仅重传第k个帧；
> - 接收方对每一个帧进行确认。
> - 优点: 链路利用率较高
> - 缺点: 接收方更复杂

14. 滑动窗口协议
引入滑动窗口对收发行为进行控制
**发送方**
- 发送窗口大小: 发送方在未收到确认前能够发送的数据帧的最大个数
- 发送方在未收到确认前最多可以发送多个数据帧 (受限于发送窗口大小)
- 对未确认的数据帧缓存
**接收方**
- 接收窗口大小: 接收方所能接收的乱序期望数据帧的最大个数
- 接收方通过ACK告知发送方下一次期望其传送的数据帧编号, 避免每次收到数据帧都发送确认

15. 有限范围的帧序号
发送方对数据帧编号, 帧中包含 k 比特的帧序号字段, 帧序号循环使用, 帧序号的有效取值范围: $0-2^k-1$

可以通过帧序号的周期区别相同序号的数据帧
- 如果接收窗口大小=1, 发送窗口大小$<=2^k-1$
- 如果接收窗口=发送窗口大小, 发送窗口大小$<= (2^k+1)/2$

> 小结: 滑动窗口协议
> 滑动窗口协议**不仅保证帧在物理链路上的可靠传输**, 而且: 
> **保证帧传送的顺序**: 通过帧序号和滑动窗口, 数据链路层协议可以将数据帧按发送顺序地交付给高层协议
> **支持流量控制, 接收方通过反馈机制可以压制发送方的速率**: 同步发送方的发送(帧)速率和接收方的接收(帧)速率
>
> 可靠传输的核心机制
> - CRC: 差错检测
> - ACK: 成功接收数据帧的确认(携带ACK序号)
> - 定时器: 检测发送方超时时间(帧丢失)
> - 帧序号: 识别不同的帧(避免帧丢失导致的重复帧)
> - 滑动窗口: 控制数据帧的收发; 流量控制(保证传输的顺序, 控制传输速率)"

![](./cn/proto.png)

16. 多路访问
两种类型的“链路”:
1)点到点链路; 2)**广播链路** (共享的有线/无线传输媒质)

> 共享广播链路通信的基本问题 
> **干扰**: 如果两个或多个节点同时传输
> **冲突**: 如果节点同时收到两个或多个信号

17. MAC 协议
**静态信道划分**
将信道划分为较小的 “分片” (时隙, 频率, 编码); 每一个分片被分配给某一节点专用; 广泛应用于数字通信
**随机接入**
不划分信道, 允许冲突发生; “避免” 冲突或冲突“恢复”; 更适合于基于分组的数据通信
案例: Aloha, CSMA, ...

> 随机接入方式
> 当节点有数据发送时: 以信道带宽R发送数据; 节点之间不进行事前的协调
> 两个或多个节点同时发送数据 -> “冲突”
> **随机接入MAC协议**: 1)如何检测冲突; 2)发生冲突后如何恢复 (例如, 延迟重传)
> 随机接入MAC协议的实例: ALOHA, 时隙ALOHA; CSMA, CSMA/CD, CSMA/CA
>
> 随机接入: 纯 ALOHA | 时隙ALOHA
> - 纯Aloha: 简单, 一旦数据帧到达, 立即发送, 如果发生冲突, 节点等待随机时间后重发数据直到发送成功
> - 时隙ALOHA: 
> 假设: 1)所有的数据帧长度相同; 2)时间轴被划分为等时长的时隙 (时长为发送1个数据帧的时延); 3)节点只能在时隙到达时开始发送数据; 4)节点之间同步; 5)如果2个或多个节点在同一时隙内发送数据, 所有节点均能检测到冲突的发生
> 操作: 1)当节点获得新的数据帧, 等待下一时隙到达开始发送; 2)如果不存在冲突: 节点可以在下一时隙到达发送新的数据帧; 3)如果发生冲突: 节点以概率p在每一个后续时隙内发送数据直到发送成功
> 优点: 一个活跃节点可以持续以全速(信道带宽)发送数据帧; 高度去中心化: 不需要中央调度; 简单
> 缺点: 存在冲突, 浪费时隙; 存在空闲时隙; 节点可能花费较长的时间进行冲突监测与退避重传; 要求时钟同步

18. 随机接入: CSMA
CSMA (载波监听多路访问): 发送前监听信道; 如果信道空闲, 发送整个数据帧; 如果信道忙, 延迟发送  
\*类比人类行为: 不打扰其他人!
- 说话之前先听是否有人说话 --> 载波监听
- 如果有其他人同时说话, 停止讲话 --> 冲突检测
**随机接入: CSMA 冲突**
冲突依然会发生: 传播时延导致两个节点无法监听到对方的发送
冲突: 整个数据帧传送时间被浪费
注意: 距离和传播时延对冲突检测概率的影响
![](./cn/csma.png)

> Ethernet 集线器 vs. Ethernet 交换机
> Ethernet 集线器: 层1设备; 简单的信号中继器; 为节点提供共享链路
> Ethernet Switch: 层2设备; 识别数据帧的地址, 完成数据帧的存储转发; 为节点提供独立的链接
>
> **无线链路特性**
> 信号强度递减: 电磁波在穿越物体时强度将减弱(路径损耗)
> 存在来自于其他信号源的干扰: 其他设备(如手机)也使用同一个无线频段(如2.4 GHz)发送信号; 环境中其他设备(如电动机)也能形成干扰
> 多径传播: 电磁破的一部分受物体和地面反射, 在不同的时间到达接收端
> **无线网络特性**
> 隐藏终端问题: A,C不确定它们的传输会不会在目的地B发生干扰
> 信号衰减问题: A,C不能监测到对方与自己的传输是否在目的地B形成干扰


19. 介质访问控制协议
**载波侦听多路访问／碰撞检测(英语：Carrier Sense Multiple Access with Collision Detection, CSMA/CD)**
此方案要求设备在发送帧的同时要对信道进行侦听, 以确定是否发生碰撞, 若在发送数据过程中检测到碰撞, 则进行如下碰撞处理操作：
1. 发送特殊阻塞信息并立即停止发送数据：特殊阻塞信息是连续几个字节的全1信号, 此举意在强化碰撞, 以使得其它设备能尽快检测到碰撞发生。
2. 在固定时间(一开始是1 contention period times)内等待随机的时间, 再次发送。
3. 若依旧碰撞, 则采用截断二进制指数避退算法进行发送。即十次之内停止前一次“固定时间”的两倍时间内随机再发送, 十次后则停止前一次「固定时间」内随机再发送。尝试16次之后仍然失败则放弃传送。
**载波侦听多路访问／碰撞避免(英语：Carrier Sense Multiple Access with Collision Avoidance, CSMA/CA)**
此种方案采用主动避免碰撞而非被动侦测的方式来解决碰撞问题。可以满足那些不易准确侦测是否有碰撞发生的需求, 如无线网域。
CSMA/CA协定主要使用两种方法来避免碰撞：
1. 设备欲发送讯框(Frame), 且讯框听到通道空闲时, 维持一段时间后, 再等待一段随机的时间依然空闲时, 才送出资料。由于各个设备的等待时间是分别随机产生的, 因此很大可能有所区别, 由此可以减少碰撞的可能性。
2. RTS-CTS三向握手(英语：handshake)：设备欲发送讯框前, 先发送一个很小的RTS(Request to Send)讯框给最近的接入点(Access Point), 等待目标端回应CTS( Clear to Send)帧后, 才开始传送。此方式可以确保接下来传送资料时, 不会发生碰撞。同时由于RTS帧与CTS帧都很小, 让传送的无效开销变小。
<PPT上>
**802.11 发送端**
- 如果监听到信道空闲: 它将在一个被称作分布式帧间间隔(DIFS)的短时间段后发送该帧
- 如果监听到信道正忙: 选取一个随机回退值计时, 当信道空闲时递减该值; 当计数值减为0时, 该站点发送整个数据帧并等待确认, 如果未收到确认, 增加回退值, 重复第2步
**802.11接收端**
- 如果数据帧接收成功: 在SIFS时间后返回确认信息(确认信息在隐藏终端问题中是必须的)

20. 虚拟载波监听
在发送数据帧之前交换控制信息
- 发送方 询问 “Request-to-Send” (RTS), 包括数据帧长度
- 接收方 响应 “Clear-to-Send” (CTS)
如果发送方收到 CTS, 则开始发送数据 (指定长度)
其他节点收到 CTS, 则保持指定长度数据帧发送时延的空闲状态
如果其他节点收到 RTS, 则禁止发送数据
**避免传输碰撞(Collision avoidance)(使用短预约帧可以完全避免数据帧碰撞)**
思路: 允许发送端“预约”信道, 优于随机访问, 避免了长数据帧的碰撞
- 发送端先用CSMA方式向AP发送一个短请求发送(RTS)帧: RTS帧有可能仍然会互相发生碰撞(但是它们很短)
- 当AP收到RTS后, 它广播一个允许发送(CTS)帧作为响应
- RTS帧能够被所有的节点监听到: 发送端发送数据帧; 其他站点推迟发送 

![](./cn/ap.png)


<hr>

###网络互联

1. 直接交付不需要使用路由器, 但间接交付就必须使用路由器
![](./cn/03.png)

2. **"转发"和"路由选择"的区别**
“转发”(forwarding)就是路由器根据转发表将用户的 IP 数据报从合适的端口转发出去。
“路由选择”(routing)则是按照分布式算法，根据从各相邻路由器得到的关于网络拓扑的变化情况，动态地改变所选择的路由。
**路由表是根据路由选择算法得出的。而转发表是从路由表得出的。**在讨论路由选择的原理时，往往不去区分转发表和路由表的区别。

3. 路由器中的处理过程
输入端口对线路上 收到的分组的处理: 数据链路层剥去帧首部和尾部后，将分组送到网络层的队列中排队等待处理。这会产生一定的时延。
输出端口将交换结构传送来的分组发送到线路: 当交换结构传送过来的分组先进行缓存。数据链路层处理模块将分组加上链路层的首部和尾部，交给物理层后发送到外部线路。 

4. 中间设备(中间设备又称为中间系统或中继(relay)系统)
- 物理层中继系统：转发器(repeater)。
- 数据链路层中继系统：网桥或桥接器(bridge)。
- 网络层中继系统：路由器(router)。
- 网桥和路由器的混合物：桥路器(brouter)。
- 网络层以上的中继系统：网关(gateway)。  
当中继系统是转发器或网桥时，一般并不称之为网络互连，因为这仅仅是把一个网络扩大了，而这仍然是一个网络。互联网都是指用路由器进行互连的网络。

5. 虚拟互连网络的意义 
**所谓虚拟互连网络也就是逻辑互连网络，它的意思就是互连起来的各种物理网络的异构性本来是客观存在的，但是我们利用 IP 协议就可以使这些性能各异的网络从用户看起来好像是一个统一的网络。**
使用 IP 协议的虚拟互连网络可简称为 IP 网。
使用虚拟互连网络的好处是：当互联网上的主机进行通信时，就好像在一个网络上通信一样，而看不见互连的各具体的网络异构细节。   

6. 因特网的网际协议 IP
网际协议 IP 是 TCP/IP 体系中两个最主要的协议之一 。与 IP 协议配套使用的还有四个协议: 
- 地址解析协议 ARP (Address Resolution Protocol)
- 逆地址解析协议 RARP(Reverse Address Resolution Protocol)
- 因特网控制报文协议 ICMP(Internet Control Message Protocol)
- 因特网组管理协议 IGMP(Internet Group Management Protocol) 

![](./cn/04.png)

7. IP 地址的编址方法 
- **分类的 IP 地址。**: 这是最基本的编址方法，在 1981 年就通过了相应的标准协议。
- **子网的划分。**: 这是对最基本的编址方法的改进，其标准[RFC 950]在 1985 年通过。
- **构成超网。**: 这是比较新的无分类编址方法。1993 年提出后很快就得到推广应用。

![](./cn/05.png)
![](./cn/06.png)

8. IP 地址的一些重要特点 
(1)  IP 地址是一种分等级的地址结构。分等级的好处是：
第一，IP 地址管理机构在分配 IP 地址时只分配网络号，而剩下的主机号则由得到该网络号的单位自行分配。这样就方便了 IP 地址的管理。第二，路由器仅根据目的主机所连接的网络号来转发分组(而不考虑目的主机号)，这样就可以使路由表中的项目数大幅度减少，从而减小了路由表所占的存储空间。 
(2)  **实际上 IP 地址是标志一个主机(或路由器)和一条链路的接口。**
当一个主机同时连接到两个网络上时，该主机就必须同时具有两个相应的 IP 地址，其网络号 net-id 必须是不同的。这种主机称为多接口主机(multihomed host)。由于一个路由器至少应当连接到两个网络(这样它才能将 IP 数据报从一个网络转发到另一个网络)，因此**一个路由器至少应当有两个不同的 IP 地址**。
(3) 用转发器或网桥连接起来的若干个局域网仍为一个网络，因此这些局域网都具有同样的网络号 net-id。
**注意:连接到一台交换机上的两个主机若具有不同的网络号 net-id,则他们属于两个LAN.即一个网络号 net-id标示一个LAN。**
(4) 所有分配到网络号 net-id 的网络，范围很小的局域网，还是可能覆盖很大地理范围的广域网，都是平等的。 

> 路由器总是具有两个或两个以上的 IP 地址。路由器的每一个接口都有一个不同网络号的 IP 地址。两个路由器直接相连的接口处，可指明也可不指明 IP 地址。如指明 IP 地址，则这一段连线就构成了一种只包含一段线路的特殊“网络” 。现在常不指明 IP 地址。
> 当网关路由器接收到以太网数据帧时，发现数据帧中的目标MAC地址是自己的某一个端口的物理地址，这时路由器会把以太网数据帧的封装去掉。路由器认为这个IP数据包是要通过自己进行转发，接着它就在匹配路由表。匹配到路由项后，它就将包发往下一条地址。**路由器转发数据包就是这样，所以它始终是不会改IP地址的, 只会改MAC。**
> 在 IP 层抽象的互联网上只能看到 IP 数据报, **两个路由器的 IP 地址并不出现在 IP 数据报的首部中**。

9. 地址解析协议 ARP 和 逆地址解析协议 RARP 
不管网络层使用的是什么协议，在实际网络的链路上传送数据帧时，最终还是必须使用硬件地址。 
每一个主机都设有一个 ARP 高速缓存(ARP cache)，里面有所在的局域网上的各主机和路由器的 IP 地址到硬件地址的映射表。每台安装有TCP/IP协议的电脑里都有一个ARP缓存表，表里的IP地址与MAC地址是一一对应的。(硬件地址也可以不是MAC地址)

10. ARP 高速缓存的作用
为了减少网络上的通信量，主机 A 在发送其 ARP 请求分组时，就将自己的 IP 地址到硬件地址的映射写入 ARP 请求分组。当主机 B 收到 A 的 ARP 请求分组时，就将主机 A 的这一地址映射写入主机 B 自己的 ARP 高速缓存中。这对主机 B 以后向 A 发送数据报时就更方便了。 

> 从IP地址到硬件地址的解析是自动进行的，主机的用户对这种地址解析过程是不知道的。
> 只要主机或路由器要和本网络上的另一个已知 IP 地址的主机或路由器进行通信，ARP 协议就会自动地将该 IP 地址解析为链路层所需要的硬件地址。  
> **ARP协议并不只在发送了ARP请求才接收ARP应答。**

11. 为什么不直接 使用硬件地址进行通信？
由于全世界存在着各式各样的网络，它们使用不同的硬件地址。要使这些异构网络能够互相通信就必须进行非常复杂的硬件地址转换工作，因此几乎是不可能的事。即路由表过大,无可操作性。
连接到因特网的主机都拥有统一的 IP 地址，它们之间的通信就像连接在同一个网络上那样简单方便，因为调用 ARP 来寻找某个路由器或主机的硬件地址都是由计算机软件自动进行的，对用户来说是看不见这种调用过程的。  

12. RARP
RARP(反向地址转换协议)用于一种特殊情况，如果站点初始化以后，只有自己的物理地址而没有IP地址，则它可以通过RARP协议，发出广播请求，征求自己的IP地址，而RARP服务器则负责回答。这样，无IP地址的站点可以通过RARP协议取得自己的IP地址，这个地址在下一次系统重新开始以前都有效，不用连续广播请求。RARP广泛用于获取无盘工作站的IP地址。

13. IP header
![](./cn/07.png)
首部长度——占 4 bit，可表示的最大数值是 15 个单位(一个单位为 4 字节), 因此 IP 的首部长度的最大值是60字节。
总长度——占 16 bit，指首部和数据之和的长度，**单位为字节**，因此数据报的最大长度为 65535 字节。总长度必须不超过最大传送单元 MTU。超过了被截断。
标识(identification)--占 16 bit，它是一个计数器，用来产生数据报的标识。当被传数据过大时,需要将数据分成多个包。 
标志(flag)--占 3 bit，标示该数据包能否分片以及是否”还有分片”。
片偏移(12 bit)指出：较长的分组在分片后某片在原分组中的相对位置。片偏移以 8 个字节为偏移单位。
协议(8 bit)--字段指出此数据报携带的数据使用何种协议, 以便目的主机的 IP 层将数据部分上交给哪个处理过程
首部检验和(16 bit)字段只检验数据报的首部不包括数据部分。这里不采用 CRC 检验码而采用简单的计算方法。

14. **转发分组的流程**
**IP 数据报的首部中没有地方可以用来指明“下一跳路由器的 IP 地址”。当路由器收到待转发的数据报，不是将下一跳路由器的 IP 地址填入IP数据报，而是送交下层的网络接口软件。**
网络接口软件使用 ARP 负责将下一跳路由器的 IP 地址转换成硬件地址，并将此硬件地址放在链路层的 MAC 帧的首部，然后根据这个硬件地址找到下一跳路由器。  

15. 划分子网
在 IP 地址中又增加了一个“子网号字段”，使两级的 IP 地址变成为三级的 IP 地址。
这种做法叫作划分子网(subnetting) 。划分子网已成为因特网的正式标准协议。
划分子网纯属一个单位内部的事情。**单位对外仍然表现为没有划分子网的网络。**
从主机号借用若干个比特作为子网号 subnet-id，而主机号 host-id 也就相应减少了若干个比特。
**IP地址 ::= {<网络号>, <子网号>, <主机号>}**
凡是从其他网络发送给本单位某个主机的 IP 数据报，仍然是根据 IP 数据报的目的网络号 net-id，先找到连接在本单位网络上的路由器。然后此路由器在收到 IP 数据报后，再按目的网络号 net-id 和子网号 subnet-id 找到目的子网。最后就将 IP 数据报直接交付给目的主机。
![](./cn/09.png)
当没有划分子网时，IP 地址是两级结构，地址的网络号字段也就是 IP 地址的“因特网部分”，而主机号字段是 IP 地址的“本地部分”。划分子网后 IP 地址就变成了三级结构。划分子网只是将 IP 地址的本地部分进行再划分，而**不改变 IP 地址的因特网部分。**

16. 子网掩码
从一个 I P数据报的首部并无法判断源主机或目的主机所连接的网络是否进行了子网的划分。
使用子网掩码(subnet mask)可以找出 IP 地址中的子网部分。
![](./cn/10.png)

> 使用子网掩码的分组转发过程
> 在**划分子网的情况下，从IP地址却不能惟一地得出网络地址来，这是因为网络地址取决于那个网络所采用的子网掩码，但数据报的首部并没有提供子网掩码的信息。**因此分组转发的算法也必须做相应的改动。

17. 无分类编址 CIDR (Classless Inter-Domain Routing)
CIDR使用各种长度的“网络前缀”(network-prefix)来代替分类地址中的网络号和子网号。
IP 地址从三级编址(使用子网掩码)又回到了两级编址。
**IP地址 ::= {<网络前缀>, <主机号>}**
CIDR 还使用“斜线记法”(slash notation)，它又称为CIDR记法，即在IP地址后面加上一个斜线“/”，然后写上网络前缀所占的比特数(这个数值对应于三级编址中子网掩码中比特 1 的个数)。
CIDR 将网络前缀都相同的连续的 IP 地址组成“CIDR地址块”。  

> 一个 CIDR 地址块可以表示很多地址，这种地址的聚合常称为路由聚合(route aggregation)，它使得路由表中的一个项目可以表示很多个(例如上千个)原来传统分类地址的路由。
> 设一个 ISP 共有 64 个 C 类网络。如果不采用 CIDR 技术，则在与该 ISP 的路由器交换路由信息的每一个路由器的路由表中，就需要有 64 个项目。但采用地址聚合后，只需用路由聚合后的 1 个项目 206.0.64.0/18 就能找到该 ISP。 
> **使用 CIDR 时，路由表中的每个项目由“网络前缀”和“下一跳地址”组成。在查找路由表时可能会得到不止一个匹配结果。应当从匹配结果中选择具有最长网络前缀的路由：最长前缀匹配(longest-prefix matching)。网络前缀越长，其地址块就越小，因而路由就越具体。最长前缀匹配又称为最长匹配或最佳匹配。**   
>
>考虑下面这个IPv4的路由表(这里用CIDR来表示):
> 192.168.20.16/28
> 192.168.0.0/16
> 在要查找地址192.168.20.19的时候，这两个表项都“匹配”。也就是说，两个表项都包含着要查找的地址。这种情况下，前缀最长的路由就是192.168.20.16/28，因为它的子网掩码(/28)比其他表项的掩码(/16)要长，使得它更加明确。

18. 因特网控制报文协议 ICMP
为了提高 IP 数据报交付成功的机会，在网际层使用了因特网控制报文协议 ICMP (Internet Control Message Protocol)。
ICMP 允许主机或路由器报告差错情况和提供有关异常情况的报告。ICMP 不是高层协议，而是 IP 层的协议。ICMP 报文作为 IP 层数据报的数据，加上数据报的首部，组成 IP 数据报发送出去。   

![](./cn/11.png)

> **ICMP 报文的种类有两种，即 ICMP 差错报告报文和 ICMP 询问报文。**
> ICMP 报文的前 4 个字节是统一的格式，共有三个字段：即类型、代码和检验和。接着的 4 个字节的内容与 ICMP 的类型有关。 
> ICMP 差错报告报文共有 5 种: 终点不可达; 源站抑制; 时间超过; 参数问题; 改变路由(重定向) 
> ICMP 询问报文有4种: 回送请求和回答报文; 时间戳请求和回答报文; 掩码地址请求和回答报文; 路由器询问和通告报文 
>
> PING (Packet InterNet Groper) 
> PING 用来测试两个主机之间的连通性。PING 使用了 ICMP 回送请求与回送回答报文。PING 是应用层直接使用网络层 ICMP 的例子，它没有通过运输层的 TCP 或UDP。 

19. 因特网的路由选择协议 中的概念
**代价**: 在研究路由选择时，需要给每一条链路指明一定的代价。这里“代价”并不是指“钱”，而是由一个或几个因素综合决定的一种度量(metric)，如链路长度、数据率、链路容量、是否要保密、传播时延等，甚至还可以是一天中某一个小时内的通信量、结点的缓存被占用的程度、链路差错率等。 

20. **路由算法的分类**
路由算法有多种分类方法：静态和动态、单路和多路、平等和分层(级)、源路由和分布式路由、域内和域间、链路状态和距离向(矢)量。
- 静态路由选择策略——即非自适应路由选择，其特点是简单和开销较小，但不能及时适应网络状态的变化。 
- 动态路由选择策略——即自适应路由选择，其特点是能较好地适应网络状态的变化，但实现起来较为复杂，开销也比较大。  

> 一些路由协议在平坦的空间里运作，其它的则有路由的层次。在平坦的路由系统中，每个路由器与其它所有路由器是对等的；**在分层次的路由系统中，一些路由器构成了路由主干，数据从非主干路由器流向主干路由器，然后在主干上传输直到它们到达目标所在区域，在这里，它们从最后的主干路由器通过一个或多个非主干路由器到达终点。**路由系统通常设计有逻辑节点组，称为域、自治系统或区间。在分层的系统中，一些路由器可以与其它域中的路由器通信，其它的则只能与域内的路由器通信。
> 链路状态算法(也称最短路径算法)发送路由信息到互联网上所有的结点，然而对于每个路由器，仅发送它的路由表中描述了其自身链路状态的那一部分。距离向量算法(也称为Bellman-Ford算法)则要求每个路由器发送其路由表全部或部分信息，但仅发送到邻近结点上。**从本质上来说，链路状态算法将少量更新信息发送至网络各处，而距离向量算法发送大量更新信息至邻接路由器。**
> 距离向量的方法是“告诉你的邻居你所知道的整个网络的状况”。算法要向所有的邻居广播整个路由表。这个“向量”就是目的地。“距离”实际上就是一个计量单位，可以是跳数。链路状态法的方法是“告诉外界有关你的邻居的情况”。整体思路是:搞清楚周围有谁在线并向其它路由器广播这个信息。**链路状态法需要更大的运算量，但它为网络中所有的路由器计算了关于整个网络的清晰全景图。**
>  分层次的路由选择协议
> 因特网采用分层次的路由选择协议。因特网的规模非常大。如果让所有的路由器知道所有的网络应怎样到达，则这种路由表将非常大，处理起来也太花时间。而所有这些路由器之间交换路由信息所需的带宽就会使因特网的通信链路饱和。
> 许多单位不愿意外界了解自己单位网络的布局细节和本部门所采用的路由选择协议(这属于本部门内部的事情)，但同时还希望连接到因特网上。   

21. 自治系统(autonomous system)
因特网将整个互联网划分为许多较小的自治系统 AS。**一个自治系统是一个互联网，其最重要的特点就是自治系统有权自主地决定在本系统内应采用何种路由选择协议。**
一个自治系统内的所有网络都属于一个行政单位(例如，一个公司，一所大学，政府的一个部门，等等)来管辖。**一个自治系统的所有路由器在本自治系统内都必须是连通的。**
\
因特网有两大类路由选择协议
- **内部网关协议 IGP** (Interior Gateway Protocol): 即在一个自治系统内部使用的路由选择协议。目前这类路由选择协议使用得最多，如 RIP 和 OSPF 协议。
- **外部网关协议 EGP** (External Gateway Protocol): 若源站和目的站处在不同的自治系统中，当数据报传到一个自治系统的边界时，就需要使用一种协议将路由选择信息传递到另一个自治系统中。这样的协议就是外部网关协议 EGP。在外部网关协议中目前使用最多的是 BGP-4。

22. **内部网关协议 RIP (Routing Information Protocol)**
路由信息协议 RIP 是内部网关协议 IGP中最先得到广泛使用的协议。
1. 工作原理
RIP 是一种分布式的基于**距离向量**的路由选择协议。
RIP 协议要求网络中的每一个路由器都要维护从它自己到其他每一个目的网络的距离记录。 
从一路由器到直接连接的网络的距离定义为 1。从一个路由器到非直接连接的网络的距离定义为所经过的路由器数加 1。
RIP 协议中的“距离”也称为“跳数”(hop count)，因为每经过一个路由器，跳数就加 1。RIP 允许一条路径最多只能包含 15 个路由器。
**“距离”的最大值为 16 时即相当于不可达。可见 RIP 只适用于小型互联网。RIP 不能在两个网络之间同时使用多条路由。RIP 选择一个具有最少路由器的路由(即最短路由)，哪怕还存在另一条高速(低时延)但路由器较多的路由。**

> RIP 协议的三个要点:
> 仅和相邻路由器交换信息。 
> 交换的信息是当前本路由器所知道的全部信息，即自己的路由表。 
> 按固定的时间间隔交换路由信息，例如，每隔 30 秒。 
>
> 路由表的建立 
> 路由器在刚刚开始工作时，只知道到直接连接的网络的距离(此距离定义为1)。以后，每一个路由器也只和数目非常有限的相邻路由器交换并更新路由信息。经过若干次更新后，所有的路由器最终都会知道到达本自治系统中任何一个网络的最短距离和下一跳路由器的地址。
> RIP 协议的**收敛(convergence)过程较(慢)快**，即在自治系统中所有的结点都得到正确的路由选择信息的过程。 
>
> **RIP协议让互联网中的所有路由器都和自己的相邻路由器不断交换路由信息，并不断更新其路由表，使得从每一个路由器到每一个目的网络的路由都是最短的(即跳数最少)。**
> **虽然所有的路由器最终都拥有了整个自治系统的全局路由信息，但由于每一个路由器的位置不同，它们的路由表当然也应当是不同的。**
>
>RIP 协议使用运输层的用户数据报 UDP进行传送(使用 UDP 的端口 520)。因此 RIP 协议的位置应当在应用层。但转发 IP 数据报的过程是在网络层完成的。  

> **RIP 协议的优缺点**
> RIP 存在的一个问题是当网络出现故障时，要经过比较长的时间才能将此信息传送到所有的路由器。
> RIP 协议最大的优点就是实现简单，开销较小。
> RIP 限制了网络的规模，它能使用的最大距离为 15(16 表示不可达)。
> 路由器之间交换的路由信息是路由器中的完整路由表，因而随着网络规模的扩大，开销也就增加。
> **好消息传播得快，而坏消息传播得慢。网络出故障的传播时间往往需要较长的时间(例如数分钟)。这是 RIP 的一个主要缺点。**这样不断更新下去，直到 R1 和 R2 到网 1 的距离都增大到 16 时，R1 和 R2 才知道网1是不可达的。

![](./cn/13.png)

23. **内部网关协议 OSPF  (Open Shortest Path First)**
OSPF 协议的基本特点:
- “开放”表明 OSPF 协议不是受某一家厂商控制，而是公开发表的。
- “最短路径优先”是因为使用了 Dijkstra 提出的最短路径算法SPF
- OSPF 只是一个协议的名字，它并不表示其他的路由选择协议不是“最短路径优先”
- 是**分布式的链路状态协议**
**三个要点**
- 向本自治系统中所有路由器发送信息，这里使用的方法是洪泛法。
- 发送的信息就是与本路由器相邻的所有路由器的链路状态，但这只是路由器所知道的部分信息。(“链路状态”就是说明本路由器都和哪些路由器相邻，以及该链路的“度量”(metric))
- 只有当链路状态发生变化时，路由器才用洪泛法向所有路由器发送此信息

> **链路状态数据库 (link-state database)**
> 由于各路由器之间频繁地交换链路状态信息，因此所有的路由器最终都能建立一个链路状态数据库。这个数据库实际上就是全网的拓扑结构图，它在全网范围内是一致的(这称为链路状态数据库的同步)。
> OSPF 的链路状态数据库能较快地进行更新，使各个路由器能及时更新其路由表。OSPF 的更新过程收敛得快是其重要优点。
>
> OSPF 的区域(area) 
> 为了使 OSPF 能够用于规模很大的网络，OSPF 将一个自治系统再划分为若干个更小的范围，叫作区域。每一个区域都有一个 32 bit 的区域标识符(用点分十进制表示)。
> 区域也不能太大，在一个区域内的路由器最好不超过 200 个。  

![](./cn/14.png)

> **划分区域** 
> 划分区域的好处就是将利用洪泛法交换链路状态信息的范围局限于每一个区域而不是整个的自治系统，这就减少了整个网络上的通信量。
> 在一个区域内部的路由器只知道本区域的完整网络拓扑，而不知道其他区域的网络拓扑的情况。
> OSPF 使用层次结构的区域划分。在上层的区域叫作**主干区域(backbone area)**。主干区域的标识符规定为0.0.0.0。主干区域的作用是用来连通其他在下层的区域。  
>
> OSPF 直接用 IP 数据报传送 
> OSPF 不用 UDP 而是直接用 IP 数据报传送，可见 OSPF 的位置在网络层。OSPF 构成的数据报很短。这样做可减少路由信息的通信量。
> 数据报很短的另一好处是可以不必将长的数据报分片传送。分片传送的数据报只要丢失一个，就无法组装成原来的数据报，而整个数据报就必须重传。 
>
> OSPF 的其他特点 
> OSPF 对不同的链路可根据 IP 分组的不同服务类型 TOS 而设置成不同的代价。因此，OSPF 对于不同类型的业务可计算出不同的路由。
> 如果到同一个目的网络有多条相同代价的路径，那么可以将通信量分配给这几条路径。这叫作多路径间的**负载平衡**。
> 所有在 OSPF 路由器之间交换的分组都具有鉴别的功能。
> 支持可变长度的子网划分和无分类编址 CIDR。
> 每一个链路状态都带上一个 32 bit 的序号，序号越大状态就越新。
>
> OSPF 的五种分组类型 
> 类型1，问候(Hello)分组。
> 类型2，数据库描述(Database Description)分组。
> 类型3，链路状态请求(Link State Request)分组。
> 类型4，链路状态更新(Link State Update)分组，用洪泛法对全网更新链路状态。
> 类型5，链路状态确认(Link State Acknowledgment)分组。 

![](./cn/15.png)
![](./cn/16.png)

> OSPF 的其他特点 
> OSPF 还规定每隔一段时间，如 30 分钟，要刷新一次数据库中的链路状态。 
> 由于一个路由器的链路状态只涉及到与相邻路由器的连通状态，因而与整个互联网的规模并无直接关系。因此当互联网规模很大时，OSPF 协议要比距离向量协议 RIP 好得多。 
> OSPF 没有“坏消息传播得慢”的问题，据统计，其响应网络变化的时间小于 100 ms。 
>
> OSPF 支持三种网络的连接 
> (1) 两个路由器之间的点对点连接
> (2) 具有广播功能的局域网
> (3) 无广播功能的广域网


24. **外部网关协议 BGP**
BGP 是**不同自治系统的路由器**之间交换路由信息的协议。 
因特网的规模太大，使得自治系统之间路由选择非常困难。 
对于自治系统之间的路由选择，要寻找最佳路由是很不现实的。 
自治系统之间的路由选择必须考虑有关策略。
因此，**边界网关协议 BGP 只能是力求寻找一条能够到达目的网络且比较好的路由(不能兜圈子)，而并非要寻找一条最佳路由**。  

> BGP 发言人 
> 每一个自治系统的管理员要选择至少一个路由器作为该自治系统的“BGP 发言人” 。
> 一般说来，两个 BGP 发言人都是通过一个共享网络连接在一起的，而 BGP 发言人往往就是 BGP 边界路由器，但也可以不是 BGP 边界路由器。 
>
> BGP 交换路由信息
> 一个 BGP 发言人与其他自治系统中的 BGP 发言人要交换路由信息，就要先建立 TCP 连接，然后在此连接上交换 BGP 报文以建立 BGP 会话(session)，利用 BGP 会话交换路由信息。
> 使用 TCP 连接能提供可靠的服务，也简化了路由选择协议。
> 使用 TCP 连接交换路由信息的两个 BGP 发言人，彼此成为对方的邻站或对等站。
>
> BGP 协议的特点
> BGP 协议交换路由信息的结点数量级是自治系统数的量级，这要比这些自治系统中的网络数少很多。
> 每一个自治系统中 BGP 发言人(或边界路由器)的数目是很少的。这样就使得自治系统之间的路由选择不致过分复杂。  
> BGP 支持 CIDR，因此 BGP 的路由表也就应当包括目的网络前缀、下一跳路由器，以及到达该目的网络所要经过的各个自治系统序列。
> 在BGP 刚刚运行时，BGP 的邻站是交换整个的 BGP 路由表。但以后只需要在发生变化时更新有变化的部分。这样做对节省网络带宽和减少路由器的处理开销方面都有好处。 

25. 因特网组管理协议 IGMP  (Internet Group Management Protocol) (了解即可)
IGMP 是在多播环境下使用的协议，它位于网际层。
IGMP 使用 IP 数据报传递其报文(即 IGMP 报文加上 IP 首部构成 IP 数据报)，但它也向 IP 提供服务。
不把 IGMP 看成是一个单独的协议，而是属于整个网际协议 IP 的一个组成部分。  

26. 虚拟专用网 VPN 和网络地址转换 NAT 
本地地址——仅在机构内部使用的 IP 地址，可以由本机构自行分配，而不需要向因特网的管理机构申请。
全球地址——全球惟一的IP地址，必须向因特网的管理机构申请。 

> [RFC 1918]指明的专用地址(private address) 
> 10.0.0.0 到 10.255.255.255
> 172.16.0.0 到 172.31.255.255
> 192.168.0.0 到 192.168.255.255
> 这些地址只能用于一个机构的内部通信，而不能用于和因特网上的主机通信。专用地址只能用作本地地址而不能用作全球地址。在因特网中的所有路由器对目的地址是专用地址的数据报一律不进行转发。 

> 网络地址转换 NAT 方法于1994年提出。
> **需要在专用网连接到因特网的路由器上安装 NAT 软件。**装有 NAT 软件的路由器叫做 NAT路由器，它至少有一个有效的外部全球地址 $IP_G$。
> 所有使用本地地址的主机在和外界通信时都要在 NAT 路由器上将其本地地址转换成 IPG 才能和因特网连接。


###运输层

1. 运输层向它上面的应用层提供通信服务，它属于面向通信部分的最高层，同时也是用户功能中的最低层。 
2. 运输层协议和网络层协议的主要区别
IP 协议的作用范围: (提供主机之间的逻辑通信)
TCP 和 UDP 协议的作用范围: (提供进程之间的逻辑通信)
3. TCP 与 UDP
两个对等运输实体在通信时传送的数据单位叫作运输协议数据单元 TPDU (Transport Protocol Data Unit)。
- TCP 传送的数据单位协议是 TCP 报文段(segment)。
- UDP 传送的数据单位协议是 UDP 报文或用户数据报。 

> UDP 在传送数据之前不需要先建立连接。对方的运输层在收到 UDP 报文后，不需要给出任何确认。虽然 UDP 不提供可靠交付，但在某些情况下 UDP 是一种最有效的工作方式。
> TCP 则提供面向连接的服务。TCP 不提供广播或多播服务。由于 TCP 要提供可靠的、面向连接的运输服务，因此不可避免地增加了许多的开销。这不仅使协议数据单元的首部增大很多，还要占用许多的处理机资源。  
> 运输层的 UDP 用户数据报与网际层的IP数据报有很大区别。**IP 数据报要经过互连网中许多路由器的存储转发，但 UDP 用户数据报是在运输层的端到端抽象的逻辑信道中传送的。**
> TCP 报文段是在运输层抽象的端到端逻辑信道中传送，这种信道是可靠的全双工信道。**但这样的信道却不知道究竟经过了哪些路由器，而这些路由器也根本不知道上面的运输层是否建立了 TCP 连接。**

4. UDP 概述 
UDP 只在 IP 的数据报服务之上增加了很少一点的功能，即端口的功能和差错检测的功能。
虽然 UDP 用户数据报只能提供不可靠的交付，但 UDP 在某些方面有其特殊的优点。
- 发送数据之前不需要建立连接
- UDP 的主机不需要维持复杂的连接状态表。
- UDP 用户数据报只有8个字节的首部开销。
- 网络出现的拥塞不会使源主机的发送速率降低。这对某些实时应用是很重要的。
![](./cn/udp.png)

> 用户数据报 UDP 有两个字段：数据字段和首部字段。首部字段有 8 个字节，由 4 个字段组成，每个字段都是两个字节。 
> 在计算检验和时，临时把“伪首部”和 UDP 用户数据报连接在一起。伪首部仅仅是为了计算检验和。
> 二进制反码求和: 对一个无符号的数，先求其反码，然后从低位到高位，按位相加，有溢出则向高位进1(跟一般的二进制加法规则一样)，若最高位有进位，则向最低位进1。
> 先取反后相加与先相加后取反，得到的结果是一样的！

![](./cn/tcp.png)

> 序号字段: 占 4 字节。TCP 连接中传送的数据流中的每一个字节都编上一个序号。**序号字段的值则指的是本报文段所发送的数据的第一个字节的序号。**
> 确认号字段: 占 4 字节，是期望收到对方的下一个报文段的数据的第一个字节的序号。(在响应报文中使用)
> 数据偏移: 占 4 bit，它指出 TCP 报文段的数据起始处距离 TCP 报文段的起始处有多远(标注了首部的长度)。“数据偏移”的单位不是字节而是 32 bit 字(4 字节为计算单位)。
> 保留字段: 占 6 bit，保留为今后使用，但目前应置为 0。 
> 紧急比特 URG: 当 URG = 1 时，表明紧急指针字段有效。它告诉系统此报文段中有紧急数据，应尽快传送(相当于高优先级的数据)。 
> 确认比特 ACK: 只有当 ACK = 1 时确认号字段才有效。当 ACK = 0 时，确认号无效。 
> 推送比特 PSH (PuSH): 接收 TCP 收到推送比特置 1 的报文段，就尽快地交付给接收应用进程，而不再等到整个缓存都填满了后再向上交付。  
> 复位比特 RST (ReSeT): 当 RST = 1 时，表明 TCP 连接中出现严重差错(如由于主机崩溃或其他原因)，必须释放连接，然后再重新建立运输连接。 
> 同步比特 SYN: 同步比特 SYN 置为 1，就表示这是一个连接请求或连接接受报文。 
> 终止比特 FIN (FINal): 用来释放一个连接。当FIN = 1 时，表明此报文段的发送端的数据已发送完毕，并要求释放运输连接。 
> 窗口字段: 占 2 字节。窗口字段用来控制对方发送的数据量，单位为字节。TCP 连接的一端根据设置的缓存空间大小确定自己的接收窗口大小，然后通知对方以确定对方的发送窗口的上限。
> 检验和: 占 2 字节。检验和字段检验的范围包括首部和数据这两部分。在计算检验和时，要在 TCP 报文段的前面加上 12 字节的伪首部。
> 紧急指针字段: 占 16 bit。紧急指针指出在本报文段中的紧急数据的最后一个字节的序号。 
> 选项字段: 长度可变。TCP 只规定了一种选项，即**最大报文段长度** MSS (Maximum Segment Size)。MSS 告诉对方 TCP：“我的缓存所能接收的报文段的数据字段的最大长度是 MSS 个字节。”MSS 是 TCP 报文段中的数据字段的最大长度。**数据字段加上 TCP 首部才等于整个的 TCP 报文段。**
> 填充字段: 这是为了使整个首部长度是 4 字节的整数倍。

1. TCP 协议是**面向字节**的。TCP 将所要传送的报文看成是字节组成的数据流，并使每一个字节对应于一个序号。
2. 在连接建立时，双方要商定初始序号。TCP 每次发送的报文段的首部中的序号字段数值表示该报文段中的数据部分的**第一个字节的序号**。
3. TCP 的确认是对接收到的数据的最高序号表示确认。接收端返回的确认号是已收到的数据的最高序号加 1。因此确认号表示**接收端期望下次收到的数据中的第一个数据字节的序号**。  
4. 运输连接就有三个阶段，即: **连接建立、数据传送和连接释放**。运输连接的管理就是使运输连接的建立和释放都能正常地进行。

> 连接建立过程中要解决以下三个问题：
> - 要使每一方能够确知对方的存在。
> - 要允许双方协商一些参数(如最大报文段长度，最大窗口大小，服务质量等)。
> - 能够对运输实体资源(如缓存大小，连接表中的项目等)进行分配。  

1. A 发送 FIN 给 B, 则从 A 到 B 的连接就释放了，连接处于**半关闭状态**。相当于 A 向 B 说: “我已经没有数据要发送了, 但你如果还发送数据，我仍接收。” 
2. TCP 采用大小可变的滑动窗口进行流量控制。窗口大小的单位是**字节**(实际上,可以使用一个名为“窗口缩放”的TCP协议选项。这个选项允许窗口尺寸乘以比例因子。如K字节)。
3. **慢开始和拥塞避免**: 发送端的主机在确定发送报文段的速率时，既要根据接收端的接收能力，又要从全局考虑不要使网络发生拥塞。(由**接收方控制流量，而拥塞控制可由发送方根据网络状态实现**)

> 每一个 TCP 连接需要有以下两个状态变量：
> **接收端窗口** rwnd (receiver window) 又称为通知窗口(advertised window)。
> **拥塞窗口** cwnd (congestion window)。
>
> (1) 接收端窗口 rwnd: 这是**接收端根据其目前的接收缓存大小所许诺的最新的窗口值，是来自接收端的流量控制。接收端将此窗口值放在 TCP 报文的首部中的窗口字段，传送给发送端。**
> (2) 拥塞窗口 cwnd (congestion window): 是**发送端根据自己估计的网络拥塞程度而设置的窗口值，是来自发送端的流量控制。**
> **发送端的发送窗口的上限值应当取为接收端窗口 rwnd 和拥塞窗口 cwnd 这两个变量中较小的一个**，即应按以下公式确定:
> **发送窗口的上限值 = Min [rwnd, cwnd]**
> 当 rwnd < cwnd 时，是接收端的接收能力限制发送窗口的最大值。
> 当 cwnd < rwnd 时，则是网络的拥塞限制发送窗口的最大值。 

1. **慢开始算法的原理**: 在主机刚刚开始发送报文段时可先将拥塞窗口 cwnd 设置为一个最大报文段 MSS 的数值。在每收到一个对新的报文段的确认后，将拥塞窗口增加至多一个 MSS 的数值。用这样的方法逐步增大发送端的拥塞窗口 cwnd，可以使分组注入到网络的速率更加合理。 

![](./cn/slow_start.png)

1. 乘法减小 (multiplicative decrease) 
“乘法减小“是指不论在慢开始阶段还是拥塞避免阶段，只要出现一次超时（即出现一次网络拥塞），就把慢开始门限值 ssthresh 设置为当前的拥塞窗口值乘以 0.5。当网络频繁出现拥塞时，ssthresh 值就下降得很快，以大大减少注入到网络中的分组数。 
2. 加法增大 (additive increase) 
“加法增大”是指执行拥塞避免算法后，当收到对所有报文段的确认就将拥塞窗口 cwnd增加一个 MSS 大小，使拥塞窗口缓慢增大，以防止网络过早出现拥塞。
3. 慢开始
慢启动一点也不慢，要达到每RTT发送W个数据包所需时间仅为$RTT×logW$。
由于在发生拥塞时，拥塞窗口会减半或降到1，因此**慢启动确保了源端的发送速率最多是链路带宽的两倍。**

> “拥塞避免”并非指完全能够避免了拥塞。利用以上的措施要完全避免网络拥塞还是不可能的。
> “拥塞避免”是说在拥塞避免阶段把拥塞窗口控制为按线性规律增长，使网络比较不容易出现拥塞。 

1. 快重传和快恢复
快重传算法规定，发送端只要一连收到三个重复的 ACK 即可断定有分组丢失了，就应立即重传丢失的报文段而不必继续等待为该报文段设置的重传计时器的超时。
不难看出，快重传并非取消重传计时器，而是在某些情况下可更早地重传丢失的报文段。 
2. TCP 的重传机制
重传机制是 TCP 中最重要和最复杂的问题之一。
TCP 每发送一个报文段，就对这个报文段设置一次计时器。只要计时器设置的重传时间到但还没有收到确认，就要重传这一报文段。
**超时重传时间应略大于运输层的往返时延。**
由于 TCP 的下层是一个互连网环境，IP 数据报所选择的路由变化很大。因而运输层的**往返时延的方差也很大**。
3. 往返时延的自适应算法
记录每一个报文段发出的时间，以及收到相应的确认报文段的时间。这两个时间之差就是报文段的往返时延。 
将各个报文段的往返时延样本加权平均，就得出报文段的平均往返时延 RTT。
每测量到一个新的往返时延样本，就按下式重新计算一次平均往返时延 RTT：
平均往返时延RTT = α × (旧的RTT) + (1 − α) × (新的往返时延样本) 

> 若 α 很接近于 1，表示新算出的平均往返时延 RTT 和原来的值相比变化不大，而新的往返时延样本的影响不大(RTT 值更新较慢)。
> 若选择 α 接近于零，则表示加权计算的平均往返时延 RTT 受新的往返时延样本的影响较大(RTT 值更新较快)。
> 典型的 α 值为 7/8。 

![](./cn/rtt.png)

> Karn 算法 
> 在计算平均往返时延 RTT 时，只要报文段重传了，就不采用其往返时延样本。这样得出的平均往返时延 RTT 和重传时间就较准确。 





















