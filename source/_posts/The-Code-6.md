---
title: 幽灵代码-6
date: 2025-04-03 22:01:34
tags: [幽灵代码]
---

Cindy父亲的病情幸无大碍。在Cindy回国探望的时间里，父亲病情随着心情一起好转。这小棉袄长年不在身边，思念总是难免，加上逐渐年迈，本来就有轻微冠心病的父亲时不时总来医院报道，医生交代了不要太早起床运动，注意饮食，也就出院了。Cindy长舒一口气。

国内的日子稀疏平常，Cindy过了高压的日子之后也终于有段短暂的放松，和父母的近距离接触虽有矛盾，但太久未见面的亲切还是压住了很多冲突。

一天中午，Cindy正坐在家里吃着妈妈做的饭，屋内静悄悄的。阳光在不经意间透过窗户洒在桌角，让Cindy看的入神。她突然收到了Angela发来的Slack消息，语气一如既往温柔而礼貌：“Cindy姐，现在方便打个电话吗？我卡在一个技术点上，特别想请教您一下！”

Cindy看了眼时间，按时差，Angela在美国那边应该还是晚上9点多了。她不禁心里泛起一丝好感，觉得这个小姑娘真是够拼够上进，便放下了筷子，点了视频通话。电话那头的Angela声音极为谦虚，“Cindy姐，我最近在看您之前写的那个数据处理的prototype，真的太厉害了呀，我想问问，要是我想把它 productionize，该怎么走流程呀？是不是要进deploy channel？”

Cindy一怔，那段prototype代码是她前阵子辛辛苦苦搞出来的初版，还在自己内部测试，尚未正式提报上线流程。但她没有多想，只觉得Angela认真肯学，于是便耐心的讲了将近两个多小时：从模块封装到dependency管理，从测试oneBox到逐步上线流程，尤其是weblab的使用，如何逐步上线，是这次deploy的关键，她每一个细节都毫无保留的分享了出来。

Angela在那头边听边认真记笔记，时不时发出几声“哇”“太厉害了”“Cindy姐您真的好细心”的感叹，像一只温顺的小猫，Cindy讲完时还有点感慨，心想这个姑娘真是肯学，帮一把也无妨。

但她并不知道，就在她挂断电话被妈妈问道“午饭都凉了，要不要热一热”的时候，Angela那边的电脑窗口已经悄悄的打开了Git分支，熟练的开始将那段prototype代码merge进她自己的branch，开始准备向整组发出上线code review请求。

万里赴戎机，关山度若飞。不闻爷娘唤女声，但闻大海流水鸣溅溅。
起飞降落，西雅图的阴绵像一杯冷彻的冰咖，Cindy却已苦中作乐。

米色风衣下的Cindy挺拔高挑，步步走进office还提着几包家里的小特产，几个同事抬头，“Cindy回来啦！旅途还顺利不？你父亲怎么样了呀！”

“嗯嗯！我爸的病好多了，这也是老毛病了，就是轻度冠心病，时不时就需要静养，这也得多吃些我带的鱼油，舒缓心肌就好一些。” 一边Cindy还把带来的小特产分给大家，“这个核桃糕是我家门口的老字号的，我从小就喜欢吃，来大家尝尝！”

大家一边接过Cindy的核桃糕，一边却用异样的目光互相交流着，Cindy倍感奇怪，莫非有什么事情大家都在瞒着她么。

打开电脑，一封outlook邮件映入眼帘，发信人是L8部门大领导Sanjay。
    Subject: [Team Update] Network Infra Team Realignment

    Hi team,

    As part of our broader effort to streamline leadership and improve execution across the Network Infra organization, I’m pleased to share the following updates:
    
    Hao Wang, the senior manager who has been leading the Network Infra domain, will be moving on from the company. Please join me in wishing Hao all the best in his next chapter.

    Prood will take over leadership of the Network Infra domain moving forward.
    
    Varun, who has been leading our Network Infra Security initiatives, will now report to Prood, who is stepping into a Senior Manager role. Varun will continue to own the Network Infra Security domain.

    David will remain the manager for Network Insight, and will also report to Prood.

    The Wolf migration project under Network Infra Security will be directly sponsored and managed by Prood, with Angela Wang taking on the role of Tech Lead for this effort. Angela will report directly to Prood.

    Prood will continue to report to me in his capacity as a Senior Manager for Network Infra.
    This realignment is intended to strengthen cross-domain coordination and ensure tighter ownership around our most strategic infrastructure investments. Please reach out to me or Prood directly with any questions.

    Thanks for your continued focus on ownership and commitment to the highest standard!

    Best,
    Sanjay

Cindy慢慢把鼠标从邮件正文移到左边，“Mark as unread”。停顿了一下，又点了回来，重新又读了一遍。她不敢相信，她不知道来来回回读了多少遍，仍然不敢相信这次巨大的reorg就如同针对自己一样把自己的亲生骨肉残忍剥离。

她想笑，可怎么都笑不出来。原本想着，回来之后继续完善那套Wolf的Auth pipeline，把prototype推进上线，让组里看到自己的能力，这是她回国前夜以继日在做的东西，是她调研、构架、设计、验证一整套下来亲手写出来的，是她期待promotion希望的关键项目。她点开Slack，果然，在她离开的这些日子里，各种project channel已经悄悄被加了‘deprecated’字眼，而进去新的项目channel里，看到Angela每天的status update就如同钢针一般刺伤自己的眼睛。她忽然觉得自己很可笑，离开前还那么信任Angela，还在饭桌前把半碗饭撂下，掏出几个小时细细讲流程、讲设计、讲上线的方法，讲到嗓子干，讲到饭菜都凉了。她以为是在扶持一个后辈，没想到是把让别人把自己当梯子给爬了上去。

“不对，Prood为什么会突然变成这个项目的owner呢？他原本是下游的dashboard负责人呢。” Cindy冷静的想到，

“Cindy姐，刚刚开完会，Prood说Wolf推进要快一些，我准备这几天就上1%的traffic了，你当时给我的信息特别有用，真的很感谢呀！” Angela短裙光着腿踩着一双小白鞋飘了过来，大眼睛无辜的看着Cindy。

Cindy只是一笑，“Good Luck！”

与Varun的1:1，Varun皱着眉，叹了口气，苦笑着对Cindy说，自己也是临时被通知要改reporting，根本没有任何前兆，没有人和自己沟通过这件事情。

“昨天晚上才知道要report给Prood，而且Hao怎么走的这么突然，然后Prood他怎么就直接上位了。”他声音压得很低，带着一丝疲惫，“连我自己都觉得莫名其妙。”

说到Wolf项目时，Varun的手指在杯沿敲了敲，神情诡异。他说，这本来是他负责推进的核心项目，可现在突然TL被换成了Angela。

“而且...TL直接跳过我，直接跟Prood汇报。”Varun顿了顿，“老实说，真不知道这是怎么安排的。也许Prood和上层Sanjay的关系更好吧。但是Angela我实在不知道怎么回事。”

“Cindy，我理解你的心情，建议你继续PTO休息几天，调整心情，接下来毕竟还有新的机会不是？” Varun还是一如既往的鼓励她。

但是Cindy彻夜未眠，这样的变动实在难以承受。不仅仅是好的project损失，更多的是对人心和trust的彻底失望。

随手写了一些小的project，Cindy这些日子就如同行尸走肉一样看着身旁的人在有条不紊的推进Wolf项目。

却说Angela，加班加点，干劲十足，因为Prood说了，只要这个project能干好，就保证她下一轮能promo。她模仿着Cindy的rollout计划，准备开始1%的switch，这意味着马上1%的流量将进入新的模块变为快速auth，beta测试显示比原有的authN/Z节省了45%的时间！

时间马上到了 1% dial up的日子，Angela大清早就浓妆艳抹出现在office十分显眼，这明显是为了下午的launch party能够一搏眼球。那蓝色风铃的香水味弥漫在整个office似乎预示着party即将到来。

一切按部就班，随着一个switch=on用control plane写入，1%的prod流量准确进入预设的新auth path，全组紧张的看着latency metrics的dashboard，一道直线滑了下来，P90从590ms的延时突然跳到了290ms！这比预想的还要好，因为prod的机器比起beta计算能力更高一些。Angela高兴的几乎跳了起来，metrics极其稳定，在新的水平线上铺展开来。同时，Availability以及Error log并无异常，这意味着1%的launch非常成功！

一个小时，两个小时过去了，新系统非常稳定，各项metrics像约定好了一样平稳前行。

Prood笑的合不拢嘴，正在给大领导写一封launch email，要让所有领导都知道这么完美的launch。只是他走过Cindy的桌子的时候，Cindy却敏锐的闻到了他身上同样的蓝色风铃香水味。

一个sev2 ticket刺破了宁静。Cindy打开看了一下，看到Angela已经在ticket里面开始研究，但是还是好奇，就看了这个ticket的内容。ticket开始显示，新的auth pipeline的几个cache server某一个运行模块内存使用率飙到100%，若干auth的request开始出现失败，然后自动retry开始引发整个latency逐步增加。刚才喜悦无比的metrics开始出现各种浮动，随着traffic的failure，不同的sev2 ticket开始进入，pager的响声在office此起彼伏。1%的流量里面现在failure rate已经高达5%。

“rollback！” 虽然Angela还想看看有什么bug可以尽快修复，但是Prood等不及了，下达了rollback的指令。

按照原计划，rollback只需要将config=off写入control plane即可。Angela无奈，只好做出操作，心想着这次launch party肯定没了。她盯着metrics，期待写入之后的config能够将metrics重新带回去，虽然回到590ms，但是至少failure rate会大幅度下降。

一分钟，五分钟，十分钟。

“Angela，你到底有没有rollback！”Prood急了！

”Yes I did！but not sure why traffic is not back to the original path!“ Angela焦急的说道，

Launch party变成了oncall war room，天堂地狱，一念之间。

Cindy坐在边上看着这一堆热锅上的蚂蚁，不禁好奇为啥rollback没有生效，她点开层层代码，很快便一声冷笑，她发现rollback的feature根本没有被实测过，Angela过于自信也过于着急，根本没有把rollback feature测试过，这里面rollback的config写入有一些bug没有被抓到。

但是，虽然config写不进去，rollback还是可以手动调整各项fleet的预设初始值，并且重启fleet来达到的。Angela完全没有这方面的经验，不知道如何快速手动的调整prod的各项switch数值，焦急的手脚冰凉。Sanjay开始了责问，要求尽快解决问题，不一会儿，VP也在ticket上询问什么时候能缓解问题。

Angela机械的打开prod host的server log，一行行熟悉又陌生的log，各种issue和压力下她几乎丧失了思考能力，她听不到任何人说话，也不知道现在怎么才能把traffic修复到old path上，哭爹喊娘都没用的时候，突然一条log让她眼球一颤：

    [US-prod-1][fatal] 00:01:07.239 - aGUgaXMgd2F0Y2hpbmcgeW91


