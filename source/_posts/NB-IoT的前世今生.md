---
title: NB-IoT的前世今生
date: 2018-11-30 20:37:12
tags: 
	- 其他
---
   
根据《爱立信2018移动报告》（Ericsson Mobility Report,June 2018）预测，蜂窝物联网设备连接数将在2023年达到35亿——年增长率达到百分之三十。
![](https://raw.githubusercontent.com/KL3Answer/sdgzzgsd/master/pics/Screenshot%20from%202018-11-28%2016-24-18.png)
该文中尤其还提到了我国对IoT产业的推动对上述数据产生的巨大影响：

![](https://raw.githubusercontent.com/KL3Answer/sdgzzgsd/master/pics/Screenshot%20from%202018-11-30%2020-53-12.png)





IoT(Internet of Things,即所谓的物联网)可能早已为大家耳熟，上到别人家孩子手上那个不能打电话看视频的小天才手表，下到天天格子衫双肩包的高中同学的家里的那台树莓派，都算是IoT设备。而在诸多IoT技术之中，NB-IoT 无疑是目前国内最受关注的一个，前有三大运营商积极建设基站、狂砸补贴，后有ofo、摩拜拥抱NB-IoT智能锁。那么问题来了，被众星高捧的这轮明月到底是何方神圣呢？

NB-IoT全称是 NarrowBand IoT，也称窄带物联网，是由3GPP组织开发的为大范围蜂窝网服务与设备而服务的低功耗广域网络（LPWAN）广播技术，其规范在3GPP Release 13中完全定型，并在Rel-14中做了部分增强（Rel-13 主要是对LTE的改进与一些物联网规范）。
问题又来了，既然在NB-IoT之前已经有了其他IoT技术的存在，为什么还要发明一个新的技术呢，这就说来话长了。曾几何时，我们也使用2/3G网络连接物联网设备，虽然现在看来2/3G网络频谱效率、吞吐率等不高，但是对于数据量极小（相对PC、智能手机以及可以发短信放音乐的大天才手表来说）的物联网设备来说已经足够了。
但是随着时间的推移，人们对物联网设备的需求与落后的技术之间的矛盾开始变大：一方面考虑到IoT设备的数量，大量使用GPRS模块在成本上不够划算，另一方面低电池容量的IoT设备也与GPRS的相对复杂的通信协议天生不相容。另外也考虑到GPRS即将被退群，人民群众对新的物联网通信解决方案的需求也日渐高涨。

发现这一空白的各通信大厂，自然也不会放过这一盈利点，各种标准不断被推出。2014年5月华为、Vodafone提出了NB M2M技术，而后又进化成NB-CIoT，2015年7月Nokia、Ericsson、Intel提出了NB-LTE技术，随后3GPP在上述两者之上着手制定标准，并在2016年7月确定标准（在上文所说的Release 13中），至此NB-IoT算是正式诞生。	出生于4G时代的NB-IoT复用了一系列LTE的设计，并与GSM、GPRS、LTE等技术良好兼容，它上下行共同使用180 kHz 的最小系统带宽，因此GSM运营商可以将NB-IoT放在一个的GSM载波上（带宽200 kHz，可以放一个NB-IoT总带宽加两个10 kHz的保护带），而LTE运营商则可以划分一个PRB（Physical Resource Blocks）给NB-IoT（具体部署方式有stand-alone、in-band、guard-band三种）。
    ![](https://raw.githubusercontent.com/KL3Answer/sdgzzgsd/master/pics/1.bmp)
	         NB-IoT与LTE的关系，该图来自《A Primer on 3GPP Narrowband Internet of Things (NB-IoT)》

为了降低NB-IoT模块的成本与能耗，NB-IoT在复用的同时也对LTE物理信道、UE （User Equipment，终端）处理流程、模块结构做了许多精简，减轻了设备制造复杂度，在降低成本的同时也减少了能耗。此外，NB-IoT的PSM（power saving mode）和eDRX（echanced Discontinuous Reception）模式也是减低能耗的大杀器，在PSM模式下，设备进入休眠状态不进行通信活动，该模式一般适用与通信频率低的设备;而在eDRX模式下，UE可以更快进入接收模式，而不需要从休眠模式转换到激活模式，而且相比DRX模式接受间隔更长，在较高频率通信的设备上可以减少信令，更加省电。

为了增强覆盖率，NB-IoT增加重传减低数据速率，引入单个子载波NPUSCH（Narrowband Physical Uplink Shared Channel，窄带物理上行链路共享信道）传输和π/2-BPSK调制来维持接近0dB PAPR（Peak to Average Power Ratio，峰值平均比例）来减小PA（power amplifier，功率放大器）功率回退造成对覆盖的影响，一般性的来说，NB-IoT的MCL（maximum coupling loss，最大耦合损耗）比LTE （Rel-12）高20db。

当然，上述这些也意味着NB-IoT的传输速率不会很高。但是正是基于这种通信模型，NB-IoT才可以得以在低成本的情况下做到单个小区仅使用一个PRB支持上万台设备，而且NB-IoT本就不是为高频高实时需求的设备设计的，它的主要用途正是在于低功耗、低成本、高覆盖、低移动性的设备上（关于低移动性这一点上，Rel-13中不支持漫游，Rel-14对移动性进行了增强，目前已经有厂商在进行漫游试验了，期待未来在这方面有所发展）。
虽然有各通信大厂的背书，NB-IoT在国内的发展却并不是一路绿灯。从目前来看，模组成本并没有下降到预期的成本。智慧农业、智慧城市等方面对NB-IoT似乎并没有那么感兴趣，使得模组出货量并没有达到预期，没有形成规模效应。另一方面，NB-IoT作为一个刚出现不久的技术，其相关的基础设施、产业链、甚至人才储备缺少积累，也使得制造成本无法快速下降。

此外，作为一种蜂窝网络技术，NB-IoT的发展无疑需要运营商的支持。在国内三大运营商之中，中国电信无疑是目前表现最好的选手，据称中国电信在国内NB-IoT基站已达40万，已经实现“城乡全覆盖”，并且还有对外开放的Wing中国电信物联网开放平台，帮助开发者管理终端。中国联通虽然相较而言声音较小，但也称到2018年5月将建成30万NB-IoT基站，并与阿里、腾讯、百度等三十多家战略合作伙伴成立了中国联通物联网产业联盟。与前两者相比，中国移动的位置则略显尴尬。 说它尴尬，是因为移动之前并没有LTE FDD牌照，这就意味着它要么在已分配的GSM频段上部署NB-IoT，要么等待NB-IoT支持TDD，要么等待FDD-LTE的牌照，不管从时间还是从成本上来说，中国移动都不占优势。不过好消息是，移动在2018年4月份获得了FDD-LTE牌照，并计划到今年（2018）年底建成14.6万个NB-IoT基站 （毕竟从“零”开始，这速度也不慢了），而且中国移动也对外开放OneNET -中国移动物联网开放平台。
	
虽然三大运营商的动作如此迅速，但是考虑到部分NB-IoT终端的工作环境，目前的NB-IoT网络覆盖率仍然不够，而相对较低基站的数量与覆盖率也使终端必须抬高发射功率，这也使得所谓的超长电池寿命大打折扣。
运营商的角力对于消费者和厂家来说是一件好事，既能降低资费，又能多一些选择，增加消费体验，但是对于开发者来说就是另外一件事情了：多个管理平台就意味这与必须考虑多种设备多种SDK的情况，甚至同一种设备同一种协议上层的API却是不一样的。当发生这种情况时，开发人员无疑就需要付出额外的精力和时间了。
除了需要面对“内忧”，NB-IoT 的“外患”也不少。当姗姗来迟的NB-IoT到来之时，LoRa和Sigfox等技术已经攻占下大片城池： 已经有一百多个国家被LoRa网络覆盖，其中法国电信Orange已经宣布实现全法覆盖LoRa。而我国的北京、上海、广州、深圳、南京、苏州、杭州等地也有LoRa网络的覆盖，其中北京市六环以内已经实现了全覆盖，京杭大运河江苏段也实现全段覆盖；Sigfox在欧美地区同样兵强马壮，其在法国的覆盖率已达92%（是的还是法国），在美国也已经覆盖一百多个城市。

抛开这些，NB-IoT也并不是物联网的唯一选择，有时候甚至不是最好的选择。比如说能打电话看视频的大天才手表就更适用于使用LTE Cat M1 甚至 LTE Cat 1，格子衫同学的树莓派也未必会上NB-IoT，而更可能选择LoRa（毕竟自己组网更geek，还不用操心网络覆盖与资费的问题）。

那么刚出襁褓的NB-IoT怎么该如何应对呢？其实不同的技术有不同的适用场景，比如对于水表电表行业来说，NB-IoT简直就是量身打造的：通过NB-IoT模组，设备仅需在每天汇报数据时唤醒并与基站进行通信，其他大部分时间几乎没有电能消耗，这种场景中，在保证电池寿命的前提下，NB-IoT能够恰如其分的完成监控电量水量的任务，而对于烟雾传感器、火警报警器来说也是相同的场景，同样的好用；对于水文、空气监控来说，NB-IoT模组可以大部分时间休眠，当需要进行较实时的汇报与反馈时，eDRX与DRX模式的作用就显现了，工作在此模式时可以即时反馈变化情况，当不需要实时监控时，又可以切换回PSM，省电工作两不误。

除了上面的这些场景，智慧停车、智能门锁、路灯故障监控、二轮车标识定位、农牧业监控、资产管理等等领域，NB-IoT也是大有作为。市场之外，工信部也在去年发布了关于推进移动物联网（NB-IoT）建设发展的通知，要求加快推进移动物联网部署，构建NB-IoT网络基础设施。可以说，在市场与政策的扶持之下的NB-IoT毫无疑问是一颗闪亮的新星。

在目前各种IoT技术百花齐放的形势下，NB-IoT似乎已经找到了自己的发展领域，那之后的发展道路会是怎么样呢，让我们拭目以待吧。






参考文献：

[1]Y.-P. Eric Wang, Xingqin Lin, Ansuman Adhikary, Asbjörn Grövlen, Yutao Sui, Yufei Blankenship, Johan Bergman, and Hazhir S. Razaghi，Ericsson Research, Ericsson AB,”A Primer on 3GPP Narrowband Internet of Things (NB-IoT)”

[2]Ericsson,”Ericsson Mobility Report”,June 2016.
[Online]. Available:
https://www.ericsson.com/assets/local/mobility-report/documents/2018/ericsson-mobility-report-june-2018.pdf
[12] A. Adhikary, X. Lin and Y.-P. E. Wang, “Performance evaluation of
NB-IoT coverage,” Submitted to IEEE Veh. Technol. Conf. (VTC),
September 2016, Montréal, Canada.

[3] TR 36.888 v12.0.0, “Study on provision of low-cost machine-type
communications (MTC) user equipments (UEs) based on LTE,” Jun.
2013. [Online]. Available:
http://www.3gpp.org/ftp/Specs/archive/36_series/36.888/36888-c00.zip

[4] Ericsson, “New WI proposal for L1/L2 eMTC and NB-IoT
enhancements,” RP-160878, 3GPP TSG RAN Meeting #72, June 2016.
[Online]. Available:
http://www.3gpp.org/ftp/tsg_ran/TSG_RAN/TSGR_72/Docs/RP-
160878.zip

[5] Vodafone, Huawei, and HiSilicon, “NB-IoT enhancements Work Item
proposal,” RP-160813, 3GPP TSG RAN Meeting #72, June 2016.
[Online]. Available:
http://www.3gpp.org/ftp/tsg_ran/TSG_RAN/TSGR_72/Docs/RP-
160813.zip