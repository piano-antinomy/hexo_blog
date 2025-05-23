---
title: 幽灵代码-3
date: 2024-11-17 16:27:19
tags: [幽灵代码]
---

Cindy很快投入到新的项目中，心情复杂却满怀动力。而与此同时，Raj也开始了他为期一周的 oncall 值班生活。这个刚刚投入生产的系统运行得极其稳定，在过去一个月几乎没出过大的纰漏，让团队感到些许自豪，也稍稍放松了警惕。

所谓 oncall，是每位工程师都既熟悉又敬畏的任务。值班期间，工程师要随时待命，24小时不离身的手机和笔记本电脑成了生活的中心。一旦系统出现异常，报警（alarm）会通过pager的急促呼叫他们起床，以及时修复问题。Raj经验丰富，对这种生活习以为常，但他也希望这周能和之前一样平静。

直到这天深夜。凌晨两点，Raj正睡得迷迷糊糊时，手机的报警声刺破寂静，把他从梦中惊醒。他迅速翻身坐起，打开电脑上的log和metrics界面，发现一条异常的内存使用警告触发了报警。系统显示内存使用率突然飙升到99%，这是一个极其危险的信号，看上去带着一丝神秘和莫名的紧迫感。

他揉着惺忪的眼睛，登上系统检查，可系统运行一切正常，没有任何异常的征兆。出于谨慎，他连夜深入排查，却始终没找到问题源头。这折腾了他两个小时，最终确认系统无碍，他才不得不无奈的回到床上继续睡，却始终无法安眠。

第二天，Raj顶着通红的眼睛出现在早晨的standup上，把这个诡异的记录告诉大家："昨晚两点，系统内存突然爆表，可我检查了半天，系统根本没事。问题是，现在想复现系统metrics，却发现根本没有任何内存异常的痕迹。"

他边说边试图在会议室的屏幕上演示，结果翻遍了系统dashboard，也没能找到那条所谓的内存异常记录。队友们一个接一个的笑了起来："Raj，这不是系统的问题，可能是你pager 出了问题吧！"有人还半开玩笑的补充："是不是太久没被叫醒，pager都在想办法提醒你存在感了？"

Cindy坐在一旁，目光复杂的盯着屏幕上的日志。她低头若有所思，却没有参与玩笑，只是轻声说了一句："可能只是一次意外吧，别太放在心上。"

接下来的两个晚上，Raj的噩梦持续上演。第二晚，他再次在凌晨2点被刺耳的报警声惊醒，打开手机一看，还是那条神秘的内存警告。系统显示内存占用再次达到99%，但当他登录系统查看时，内存使用却完全正常。

第三晚，当警报再次刺破黑夜时，Raj已经崩溃了。他疲惫不堪，却无从忽视，拖着沉重的身体爬起来再一次检查系统。一切如常，毫无头绪。他愤愤的掐灭电脑，仰靠在椅子上，盯着屏幕，喃喃自语："到底是谁在耍我？这不可能是巧合。" 仔细检查了prod host的内存使用明细，发现并无异常，只是一条条打出的fatal error log还和以往见过的一样，只是频率高了很多。

白天，Raj满脸憔悴的出现在办公室，他几乎是扑到团队会议桌前，挥舞着手里的手机，对大家喊道："这不是我的幻觉！是真的有一条内存警告在凌晨2点报警，我亲眼看到了三次！"他瞪着众人，急切的希望得到哪怕一点点支持。他急切的打开了prod的的dashboard，想让大家看到那条曲线的峰值，但是不管他怎么刷新，内存使用曲线平稳的在屏幕上徜徉着，而prod log，一条一条的检查，可不管怎么用命令行filter，他看到的频繁的fatal log也确实是根本没有。

Varun皱着眉，半是同情半是调侃的说："Raj，冷静点。你查过两天了，系统一点问题都没有。连 IT 部门都确认你的 pager 正常，可能……你只是压力太大，出现了幻觉。也许 oncall 结束后，你该去看看心理医生或者神经科吧dude。"

其他人也窃窃笑着附和："是啊，Raj，这么多夜班oncall pages，你确实该休息了。"

Cindy坐在会议桌的一角，始终没有说话，只是盯着Raj紧握手机的手，表情比平时更严肃。Raj听着同事们的议论，脸涨得通红，他猛的站起身，咬着牙说："你们不信我？好啊，今晚我录下来！我要让你们看看内存监控面板，到底是不是我的幻觉！"说罢，他气冲冲的甩开椅子，拎着包离开了会议室。

走廊里，Cindy低声喊了他一声："Raj……" 但他头也不回的离开了。

Raj的 oncall 周很快结束了。他迫不及待的卸任这个令他崩溃的oncall rotation，试图通过心理医生寻求帮助，但几次咨询后，他得到的答复却是："精神状态没有问题，可能只是工作压力导致的错觉。"医生的言辞让Raj倍感孤立。每当他回想起深夜里响起的警报声、无法解释的内存异常，以及过于频繁的fatal log，一种挥之不去的阴影便紧紧笼罩着他。

此后的一个普通的早晨，Cindy和往常一样到办公室准备开始一天的工作，却发现公司气氛异常沉重。几位同事低声交谈，眼中透着难以置信的震惊。她刚坐下，就收到了一个噩耗：Raj前一天夜里在I-5高速上遭遇严重车祸，当场丧生。

大家都在讨论事故的细节。据警方的初步调查，Raj的车当时正以超过每小时90英里的速度飞驰，远超限速。而根据高速路监控视频，在事故发生的几秒钟前，他的车突然失控，径直撞上一辆停靠在路边的重型货车，车辆瞬间被撞得粉碎。

更让人毛骨悚然的是，警方报告中提到一个车内记录仪给出的诡异细节：事故发生前，Raj车内的 pager 疯狂鸣叫，声音刺耳且持续不止。调查人员推测，这可能分散了他的注意力，导致他在高速行驶中无法保持专注，最终酿成悲剧。然而，事故现场的 pager 被找到时，却已经完全损坏，无法复原当时的报警记录。

消息传来，公司里的人无不震惊。有几位同事私下议论："会不会是他一直说的那个内存异常又出现了？如果是真的，那也太……"话没说完，便被其他人制止。公司整个IT部门配合调查，但是系统显示，在Raj开车出事故的时间段内，并没有任何issue和任何通信手段主动page了他。

Cindy没有加入讨论，她的脸色比任何人都要难看。她回想起会议室里Raj气急败坏的模样，还有他反复强调的“午夜的诡异内存警报”，心里不禁泛起一丝寒意。她打开自己的电脑，试图查看系统日志，却发现什么异常也没有。可当她合上笔记本时，背后似乎吹来一阵冷风，脊背一阵发凉。

午后，雨点继续敲打办公室的玻璃，Cindy感到一阵莫名的不安。仿佛那份“fatal log”仍在某个地方，静静的等待着再次出现。

