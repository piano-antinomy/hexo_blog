---
title: 幽灵代码-7
date: 2025-04-26 22:23:40
tags: [幽灵代码]
---

Angela从未见过这样的fatal log，但是它还在继续，

   [US-prod-1][fatal] 00:01:07.239 - aGUgaXMgd2F0Y2hpbmcgeW91
   [US-prod-1][fatal] 00:01:08.131 - aGUgaXMgd2F0Y2hpbmcgeW91
   [US-prod-1][fatal] 00:01:09.338 - aGUgaXMgd2F0Y2hpbmcgeW91

在prod的log terminal里反反复复的打出，淹没了Angela的屏幕，Prood在一旁踱着步子走来走去，当rollback无法顺利进行的时候，Angela和其他组员束手无策。面对着从未见过的fatal log，二人更是看不出任何头绪，就仿佛看着已经起飞的飞机，毫无办法让其停下来。

Sanjay走了过来，再次询问什么时候能解决，现在全公司都受到影响，sev1的impact已经被高频客户察觉，几个VP已经开始给客户频频道歉了。这虽已到午饭时间但是没人敢去吃饭，当Sanjay听到负责的TL连root cause都没搞清楚的时候，几乎震怒，转身对着Prood大骂了几句就转身离开。而Angela面容如死人一样的苍白，看着所有metrics飘红和领导无数催促的sev1，自己即将晕过去。

Cindy也在一旁看着，全程她都很清楚这个incident的原因，rollback属于核心模块但是Angela和Prood都太着急立功了，没有把这个模块测试好就上线了，现在rollback无法顺利进行的时候，Cindy心里居然从失落和不甘里滑过一丝冷笑，她好像突然觉得坏人在被惩罚一样。

“你的机会来了”，一条Slack消息从Tiago大哥那里发来，Cindy顿感一阵凉意，心里琢磨，“Tiago大哥从来都是晚上才出现，怎么今天白天还slack跟我联系了呢？”

“所以，要我帮忙解决么？他们那么坏，搞出事故真是罪有应得！” Cindy忿忿道，

“傻孩子，是仇恨重要还是在领导面前当一次救世主更重要？这么好的机会，你要大显身手才能力挽狂澜，小人的伎俩自然就不攻自破呀！” Tiago写道，

“大哥，快教我怎么做吧！”，Cindy一知半解，

“你自己最明白这个流程，你先不要着急修，要记住我的话，让领导看见的impact才是真的credit！” Tiago细细的说道，“现在的情况对你最有利，他们已经把自己当成了项目负责人，但是捅了这么大的篓子，负责人几个小时还解决不了，这个低下的技术能力肯定已经被领导看在眼里了。” 

“但是这个时候，你觉得领导心里最重要的是什么？” 

“是 - 不惜一切代价，先解决这个问题，让客户影响变到最小？” Cindy半信半疑，

“你答对了一半！mitigation的确是最重要的，现在一堆级联事故都指向了我们network auth的事故，全公司都等着看大的COE呢，领导自然很着急先修复好。”， Tiago顿了一下，接着打字，

“但是，还有另一半，你要知道领导谁也不愿意自己承担责任，如果这个事故出现之后，TL连root cause几个小时都搞不出来，TL自己被开也就算了，估计上下两级领导都有不少连带责任，因为TL是他们安排的，prod change是他们审核批准的。” 

Tiago坚定的在slack写道，“你现在不仅要修复，更要帮着大领导Sanjay撇清责任，这样你就饶过了Prood，你把credit拿走并且重新带领project，同时玩死Angela和Prood吧！” 

Cindy顿悟，这果然是自己绝佳的机会。

她正要动手修复，准备开始重启fleet重新读取flip之后的config，“等等”，Tiago打断了她，

“你忘了，先说再做，才是最好的？” Tiago问道，

“对呀！我要把话说清楚！” Cindy眼神一凛，猛地坐直了身子。
就在整个SEV1陷入一片混乱，众人一筹莫展的时候，Cindy一条冷静坚定的回复跳进了ticket，像一道利箭：

"Hi team — no need to panic. I'm actively working on mitigation now.
Root cause identified: memory leak caused by excessive temporary state retention per request.
We should not attempt to patch this on-the-fly — it's too risky under live traffic. Instead, the immediate focus should be on rollback.
I understand the rollback Angela attempted earlier encountered issues.
Next step: I am preparing a manual fleet config revert. My script will be ready within 10 minutes.
ETA for full fleet rollback: approximately 30 minutes."

一个组的人看到这条回复，仿佛拨云见日一般。几个entry level的SDE都围了过来，看着Cindy在慢条斯理的整理script逻辑，这个script很关键，其实是手动做了control plane应该做的事情，但是强制了所有被impact的fleet重启并读取revert之后的config，这样所有1%的流量继续使用老的路子，而不是新的auth路径。

Prood正想来Cindy的desk看看，被Sanjay拽了过去，“you'd better stay at your desk, and don't disturb her, dude!”

在被围观中，Cindy“键”步如飞，script出来之后，她熟练的先拿beta测试了一次，才开始对prod开始运行，并且把自己的操作全程update在ticket里面。

一分钟，5分钟过去，failure metrics开始回归正轨，10分钟过去，有效的流量全部退回了老的auth路径，开始继续正常工作。30min，所有alarm都被清掉了。sev1也降级成了sev4用以追寻之后的root cause。

Cindy长舒一口气，看着不远处坐着的Angela，还是面如死灰，但是Cindy却喜上眉梢。包括VP在内的大领导均在ticket里赞不绝口，指名道姓的感谢Cindy的巨大帮助。

“别忘了，总结陈词，但是有些话可以公开，而有些话只能够私信”，Tiago再次提醒到，

Cindy秒懂，她在ticket里面把这次事故的impact，原因，mitigation方法概括总结了一遍，并且严明的指出，该项目负责人Angela必须事后写出COE，解决流程问题，已经回答为什么rollback模块没有被实测的原因。

同时，她简要的向Sanjay发了email并且cc给了他下面所有manager：

Hi Sanjay,

Following up on today's SEV1 incident: The root cause was memory exhaustion at the API gateway due to improper request handling, plus the problematic rollback tool.
Additionally, I noticed that the recent production rollout did not fully follow the established deployment best practices, which contributed to the incident.

If the team needs support, I am happy to offer some help to stabilize and improve the system.

Best regards,
Cindy

言简意赅，却充满了自信和力量。Cindy再次成了组里的英雄，Varun激动的要哭了出来，Cindy的力挽狂澜也给Varun在领导心中增加了太多的分量和信任。

当然，还有一条的email，是Cindy建议了之后让自己的manager Varun单独发Sanjay的：

“
Hi Sanjay,

I wanted to briefly follow up regarding the SEV1 today and the ongoing project work.
While I fully respect the recent team adjustments, I do have some concerns about the current structure, particularly given the complexity of the work ahead and the experience level required for TL roles.

I remain committed to the success of the project and would be happy to step in and provide support wherever needed.
”

Angela被空调冻的瑟瑟，抖着腿走过Cindy，“Cindy姐，谢谢你”，少气无力，羞愧难当。

Cindy微微一笑，“下周COE写出来记得给我看，一切prod rollout都等COE review之后再推进，别乱了套。” 从容淡定。

Prood心跳久久没平静，现在虽然解决了，但是这次立功不成反遭殃的事故让他心里对Angela厌恶至极，也怪自己太过信任。

“哎，下午没心工作了” Prood心想，“我还是想想怎么能快速扭转Sanjay对我的印象吧，这下可好，credit都被Cindy拿回去了，我这处心积虑最后反噬了自己，哎！而且Cindy这小姑娘怎么这么机灵，我还没反应过来她就email给了Sanjay，前因后果都解释了，而且切切实实的解决了问题，这下我怎么伪装都没用了，有了这些铺垫，Sanjay就可以事后问责的时候把所有责任都给我Prood，是我建议了reorg，是我临阵换了TL。。。”，他不想接着想了，自己离职的想法都有了。

Prood颓着步子走进电梯，准备下楼，实在没有工作的状态，Sanjay对他的眼神并不适合现在去沟通，Sanjay毕竟正忙着感谢Cindy和Varun。

banana这个network部门在这栋楼的25层，电梯缓缓的打开，Prood走进去的一刻，发现Angela也垂头丧气的走了进来，吃瘪的二人好像难兄难弟但又各怀鬼胎，落寞的心情让Prood无心在Angela光着的大长腿上停留半点目光，呆滞着看着电梯门。电梯门关了，里面只有这二人，电梯屏幕上的广告就像一个无聊的背景，闪闪烁烁却无所事事。

“Prood，这个事情是我不对，我太着急了，就。。。” 

“别说了，现在都晚了。” Prood打断了Angela，也并没有继续交流的意思。他注意到Angela手里拎着蛋糕和红酒，这明显是给launch party准备的，奈何launch party变成了oncall war room之后，谁也没心情歆享这份美食和美酒。

电梯的屏幕上，广告还在无聊的闪烁着，突然间，电梯猛的一颤，二人都踉跄了一下，电梯突然悬停了！二人在突如其来的急停下，都随着惯性摔坐到了电梯冰冷的地板上，蛋糕伴着手机和钥匙摔了一地，而电梯屏幕上显示电梯刚到17层，电梯门紧锁。

高空悬停，二人开始按紧急按钮，想呼叫外界救援，但是按钮仿佛坏了一样，根本就没半点反应。二人本能的按尽了所有按钮，皆如损坏一般。Prood试图打开门，但是门如同铸铁了一样，死死的锁住了。

“这下怎么办！” Angela哭到，打开手机准备打911求助，发现手机这个时候完全没有任何的信号，什么电话都打不出来！

“我能怎么办？” 本就烦恼的Prood更加恼火，二人吵了几句，又开始了不听的摆放手机的姿态，妄图吸取一丁点信号。但是手机的信号格毫无动静，二人在电梯里反反复复的按按钮，变手机方位，但皆于事无补。

“HELP！！” 二人开始大喊！

两个人的声音此起彼伏，哭声喊声汇成一片，但是这个世界犹如静音了一般，安静的让人可怕。

突然，电梯里的灯和屏幕猛的闪过一道白光，接着瞬间都熄灭了，电梯本身就像死去了一样。Angela打开手机的灯光，照着自己苍白的面孔，想想自己最近的所作所为，心里恐惧到了极点。

10分钟，20分钟，30分钟过去了，除了手机的光亮，电梯依旧一片死寂，但二人情绪逐渐稳定了下来，从最初的惊恐变成了沉默。

“别担心，这只是意外。以后机会还多着呢，你的路还长着。” Prood安慰到，“现在只有耐心等待救援了，一会儿电梯工作人员就会发现我们的。”

Angela蜷缩在一角，听着Prood的话，焦躁和寒意开始蔓延，但短裙下裸着的双腿在冰冷的地板上微微发抖，她下意识的靠近了Prood，试图寻求一丝温暖。

“反正和Prood也不是第一次了” Angela心想到，

两人之间的距离越来越近。

Prood感受到Angela靠了过来，下意识的伸手扶住了她。手掌触及她光滑冰凉的大腿的一瞬间，空气仿佛凝滞了。一阵轻微的颤抖后，Prood炙热急切的吻了上去。并且一路扩散，从唇到耳垂，再到她细腻的肩颈，带着不容抗拒的侵略性。Angela闭上眼睛，任由自己在黑暗中沉沦。

窒息般的黑暗里，二人身体的本能战胜了一切。粗重的呼吸交叠，在封闭的电梯里弥漫。姿势变换之间，地板晃动，偶尔撞击到电梯墙壁，发出声声的闷响。

良久，皆瘫坐在电梯地板，穿起了衣服并且彼此依靠喘息着，四周是不变的死寂，心跳声还在余烬一样燃烧。

黑暗溢满了整个空间的时候，任何光亮都能让人惊悚，突然，电梯里的灯光开始忽明忽暗，全屏幕开始不停的闪烁一行字幕，

Angela惊恐万分，但定睛望去，电梯屏幕上尽是 “aGUgaXMgd2F0Y2hpbmcgeW91” ！！！ 

一行一行，反反复复。


