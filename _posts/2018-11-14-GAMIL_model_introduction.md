---
layout: post
title: LASG GAMIL模式介绍报告
categories: 讲座笔记
tags: model
author: renql
---

* content
{:toc}

2018年11月16日，托数值老师的福，终于有机会回南校区，并有幸了解到大气物理研究所**LASG**研发的气候系统模模式，去年暑假参加大气所暑期夏令营时就听说LASG有自己研发的模式，但一直不知道叫什么，这次算是知道全名了   
![](http://wx4.sinaimg.cn/mw690/006fa9Xlgy1fxe8vl5k4jj30rp0jm0wy.jpg)  
![](http://wx2.sinaimg.cn/mw690/006fa9Xlgy1fxe8vtxbhoj30rs0kqgs7.jpg)




**李立娟**，研究员，博士生导师，研究模式发展，听说刚刚二胎，真是厉害  
**刘鸿波**，副研究员，硕士生导师，研究极端天气气候事件，她好像与前一位是同一年本科毕业  
**董理**，副研究员，硕士生导师，研究模式发展，12年博士毕业后留所工作至今

通过此次讲座，了解到了我国模式的发展情况，动力框架存在的问题，以及ENSO模拟中存在的问题。  
发现听报告的时候，如果强迫自己要问问题，就会听得比较认真，并且也会强迫自己去思考，it's good, So let's ask questions every time.

# 李立娟 气候系统模式FGOLAS-g简介 #
气候系统主要分为**大气模式**、**海洋模式**、**海冰模式**、**陆面模式**，当然后面又加入了**大气化学模式**、**海洋生物模式**、**陆面生物模式**、**空间天气模式**，各模块之间主要通过**耦合器**实现水通量、热通量、动量通量的交换，因此耦合器也是相当重要的。

其中，大气模式主要分为  
- **动力框架**：主要指大气运动方程组的离散、差分、积分，第三个报告有着重介绍这一部分  
- **物理过程**：包括辐射方案、积云对流参数化方案、层云过程（云宏观/微观物理过程）、边界层方案、重力波拖曳、陆面过程等

随后围绕两类**模拟偏差**（ENSO模拟偏差、预测的初始冲击）展开论述，说明FGOLAS-g的优越性。  
结合第三个报告，得知目前GAMIL还只是静力模式，不支持非静力，当然这对于大尺度的气候模拟的影响或许不大。  

## ENSO模拟偏差修正 ##
ENSO的模拟是衡量模式性能的重要指标之一，但很多模式都对ENSO振幅的模拟存在偏差，有偏强也有偏弱的 

ENSO模拟中重要的挑战————**云短波辐射强迫对EINino的负反馈**————当海温增加时，对流增强云增加，使到达海表的短波减少，从而抑制海温增加。  
> 之前了解到的四种ENSO负反馈中，似乎没有看到从云短波辐射角度出发的，虽然这样解释似乎也是合理的

大部分CMIP模式模拟的云短波辐射负反馈偏弱甚至模拟出正反馈  
> 如果是这样的话，那么模拟出的ENSO振幅不应该普遍偏强吗？为什么前面看到的振幅模拟偏差中有强有弱呢?且感觉弱的更多？

国际上关于云短波负反馈模拟偏差成因存在争议，主要有以下三种声音：  
1. 海洋模式模拟的海温偏差————但当给定观测海温时，单独的大气模式也存在类似偏差    
2. 对流过程————大量的对流方案改进研究  
3. 分辨率————不同分辨率CMIP模式普遍问题  

而他们的团队认为是层云过程，于是他们通过**降低大尺度凝结条件，增加其云水雨水转化率等**以及**改进闭合假设、增加对流触发条件等**来协调改进层云和对流过程，并在耦合框架下同时改进大气模式和耦合模式以减少耦合放大偏差。（2014，2015的工作）  
而以往的大部分模式只改进对流过程中的一个或几个子过程，如触发条件等。

改进后的FGOLAS-g2对ENSO的模拟确实得以提升。  

此外，他们还通过CESM的交叉耦合模式来验证其大气耦合模式GAMIL2对ENSO振幅模拟的准确性（Tang，Li et al. 2018 Clim.Dyn)。  
> 但此处有一个耦合器的问题，即把CAM、POP、GAMIL、LICOM重新组合后，耦合器如何选择？感觉耦合器的选择会影响模式的表现能力

## 年代际预测中的初始冲击 ##
![](http://wx3.sinaimg.cn/mw690/006fa9Xlgy1fxe8vxvc2yj30u10l8q9u.jpg)
![](http://wx3.sinaimg.cn/mw690/006fa9Xlgy1fxe8w2qze9j30rw0k4tcz.jpg)

采用两种方法来解决该问题，  
- 一是使用Nudging，  
- 二是采用四维集合-变分混合同化方法4DEnVar，**Dimension-Reduced Projection 4DVar (DRP-4DVar)**，是国际上最早将该方法用于年代际预测的模式，使用该方法后的效果也很好

![](http://wx1.sinaimg.cn/large/006fa9Xlgy1fxe9h96mgkj30t10lan1n.jpg)

# 刘鸿波 云贵高原东侧一次典型低空急流事件的数值模拟研究 #
其实没怎么听懂，提取到的有效信息如下：  
- 低空急流**low-level jet(LLJ)**分为两种，**SLLJ**(1-4km), **BLLJ**(<1km)边界层低空急流  
- 利用WRF模拟，两层嵌套，分辨率36/12km，且只模拟了30h  
- LLJ存在明显的日变化，夜间爆发  

![](http://wx1.sinaimg.cn/mw690/006fa9Xlgy1fxea3bwdx8j30ps0eozmw.jpg)

# 董理 GAMIL动力框架简介 #
天哪，这个就更没怎么听懂了，太难了  
- GAMIL的开发始于2003年，目前还只是一个基于**经纬网格**的全球**静力**大气环流模式，变量布置采用**C网格**  
- 采用**平方守恒**和**专门的时间积分方案**保持能量守恒，而国外的其他模式则是采用**通量**的方式来使能量守恒  
- 随后讲了一堆关于平方守恒的计算原理、时间积分方案、预估-矫正方案，完全没听懂  
- **C网格**下，科式力无法直接计算，需采用平均或插值。除C网格外，还有A网格，B网格  
- **快慢分离方案**，将空间算子分为快过程、慢过程两类算子，**慢过程**包括非线性动量平流，**快过程**包括惯性重力波  
- 经纬网格在极区计算存在不稳定  
- 随后用Rossby-Haurwitz波、急流、地形波进行正压测试，这里就真的完全不懂

![](https://image.slidesharecdn.com/cm2015-ch03-agcm-160120144349/95/cm2015-chapter-3-agcm-57-638.jpg?cb=1453301438)