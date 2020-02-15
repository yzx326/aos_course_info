<h2>– Summary of major innovations</h2>

<p>   
PF-Miner是第一个在正常执行路径和错误执行路径间挖掘对函数的工具。并且利用挖掘的结果而函数的定义检测程序的违例情况。
</p>

<h2>– What the problems the paper mentioned?</h2>

<p>
驱动程序对于OS特别重要，运行在内核模式中。一般情况下，驱动程序需要处理很多错误，在正常路径下调用的函数和在错误情况下调用的函数都是成对出现的。但是一些程序员由于忘记或不清楚需要释放获取的资源而并没有完全处理异常情况，这样就非常容易导致内存泄漏和其他可能的问题出现。
</p>

<h2>– How about the important related works/papers?</h2>

<p>
1、Engler等人提出一种ECC方法，即利用“&lt;a&gt;必须和&lt;b&gt;成对”的模版提取对函数。ECC也利用挖掘程序从源码中检测相关信息并且从正常的执行路径提取潜在的规则。PR-Miner利用数据挖掘工具从大型软件源码中提取模糊的程序规则，而且可以利用为数不多的函数和变量提取最长的执行路径模式。但他们所挖掘的对函数主要是基于相同的函数和正常的执行路径。而PF-Miner处理的是在一个函数中只有在错误出现时才会成对地执行，从而检测到对函数。<br>

2、另一些方法会对异常处理进行标记，但主要处理错误的容错机制。CAR-Miner通过研究来自网络的开源项目并基于序列相关的规则来挖掘异常情况，并利用这些得到的规则检测程序的违例情况。<br>

3、也有提出的异常处理模型来自动处理异常运行时异常。但是所有这些方法仅仅应用到C++或java程序中而没有应用到C作为源码的内核中。
</p>

<h2>– What are some intriguing aspects of the paper?</h2>

<p>
判定函数的原理，需要满足的限制条件：<br>
（1）在任意两个函数间基于函数的语义评估可能是对函数的概率。判定函数的输入是两个函数，输出是介于Smin和Smax的一个整数值。<br>
（2）对函数需要在相同的情况下执行相反的操作。判定函数利用潜在的对函数集合PP评估对函数的可能性。<br>

选择函数的原理，需要满足的限制条件：<br>
（1）找出通常以对的形式出现的函数；<br>
（2）保存那些语义方面成对可能性更大的函数；<br>
（3）过滤掉不相关的函数；
</p>

<h2>– How to test/compare/analyze the results?</h2>

<p>
在一个PC上进行评估（ABUS CM6331-C12C, Intel core i3-3220, 3.30 GHz, 4GB memory, 7200rpm SATA drive），利用Android内核3.10.0的源码作为PF-Miner的输入。<br>

对不同版本的源码测试进行比较<br>

为了评估PF-Miner检测程序的违例能力，将PF-Miner运行在Android内核2.6.39和3.10.0上进行对比。其中内核为2.6.39的版本是从Linux的内核中分离出来，内核3.10.0是Android的最新版本。测试结果的详细情况如下：<br>
（1）在内核2.6.39上运行PF-Miner并从对函数检测违例情况。<br>
（2）在内核3.10.0上运行PF-Miner并执行相同的操作，与内核2.6.39上的操作进行对比。
PF-Miner总共从对函数中检测到81个使用违例情况。PF-Miner在内核2.6.39中将这些检测到bug作为潜在的bug，并且在3.10.0版本之前就已经修复。<br>

PF-Miner在正常执行路径和异常执行路径中，共从4225个驱动程序中检测到546个对函数。
</p>

<h2>– If you write this paper, then how would you do?</h2>

<p>
不仅从程序中函数间的语义进行分析，也从函数功能、输入、输出等的相关性检测潜在的对函数。
</p>