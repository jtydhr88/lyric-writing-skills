---
name: lw-imagery
description: The imagery layer - how to find concrete nouns and make them a system (意象与具体名词). Object writing and the seven senses, the ten-minute timed practice, why abstract nouns are the most direct AI fingerprint and how to build the forbidden list, how to check that a lyric is not all sight, why a set of images must belong to one physical world instead of being piled up at random, simile versus metaphor and how to spot and replace a dead one, and how one object recurs with a shifting meaning. Use when a lyric feels vague or generic but the words look fine, when every noun in a draft is a concept, when you cannot find images, when images are pretty but unrelated, when a metaphor sounds borrowed, or when LYR-LINT check 2 fails. 意象、具体名词、抽象词、object writing、物体写作、五感、七感、比喻、明喻、暗喻、通感、陈词、死喻、词太泛、找不到意象。
---

# 意象与具体名词（Imagery）

**这个 skill 管一件事：词里出现的东西是不是真东西，以及这些东西是不是同一个世界里的。**

> ★ **AI 味八条里的第 1 条「名词全是抽象的」归这里。**
> 它是最直接的机器指纹——因为抽象名词是所有可能的具体物件的平均值，
> **而平均值不属于任何人。**

## 按任务读哪几节

| 任务 | 读 |
|---|---|
| 不知道从哪找意象 | §1 object writing |
| 词写出来了但很泛 | §2 具体 vs 抽象 |
| 意象有了但读着单薄 | §3 感官分布 |
| 意象很多但互不相干 | ★ §4 意象成系统 |
| 比喻读着像别人的 | §5 比喻与死喻 |
| 一个物件怎么用满全曲 | §6 物件的贯穿 |
| 交稿前查这一层 | §7 自检 |

练习清单与抽象词/死喻词表在 [reference.md](reference.md)。

## 边界

| 不归这里 | 归哪 |
|---|---|
| 立意五问、`anchor_object` **选哪一个** | `lw-song-intent`（★ 它管"挑哪个物件"，本 skill 管"怎么找、怎么把它写成系统"） |
| 段落功能、句式、盒子结构、不对称 | `lw-structure` |
| 押韵、韵式、韵脚意外度 | `lw-rhyme` |
| 人称、视角、时间锚点、留白 | `lw-narrative` |
| 倒字、协音 | `lw-tone-check` |
| 交稿前的八条终检 | `lw-ai-tell-audit` |

> ★ **与 `lw-song-intent` 最容易混的一刀**：
> 它的 §5 只问"这个物件能不能拍照、说不说得出颜色新旧"；
> **本 skill 不重复那五问**，只接着做两件事：**怎么把物件挖出来**（§1）、
> **怎么让它和别的东西长在同一个世界里**（§4、§6）。

---

## 1. Object Writing（物体写作）

### 1.1 它是什么

**随机选一个真实物体，把感官对准它，限时十分钟往下写。**
（Pattison《Writing Better Lyrics》p0001；《Songwriting Without Boundaries》p0001）
物体可以是回形针、咖啡杯、一辆车——**只要是真东西**。

书里把物体叫**跳板**（diving board）——
它不是要你描写这个物体，**是要你借它跳进自己的感官记忆库**
（vaults of your senses）。目标是找到**独属于你的写作声音**，
因为每个人的感官记忆库都是独一无二的。（同上 p0001）

★ **它的定位一句话说死**：
> 「Object writing prepares you for whatever other writing you do. It is not a substitute.」
> （物体写作为你所做的其他任何写作做准备。**它不是替代品**。）
> —— Pattison《Writing Better Lyrics》p0001

**这句要当规则读**：object writing 写出来的东西**不是词**。
它是素材堆，词是从里面挑出来的。直接把 object writing 段落当歌词交，是误用。

★ **它要达到的效果，书里有一句最短的说法**：
> 「Sense-bound writing turns observers into participants. It is one of the most powerful tools a writer has.」
> （**感官性的写作把旁观者变成参与者。**它是写作的人手里最有力的工具之一。）
> —— Pattison《Songwriting Without Boundaries》p0001

**为什么它能做到**：你写出来的是感官刺激，
**听的人是用自己的感官档案把画面补出来的**——
所以那个世界**装的是他自己的东西**，这首歌于是变成了关于他的
（同上 p0006）。

### 1.2 ★ 七种感官（不是五种）

书里把感官分成**七种**，多出来的两种正是最少被想到、也最难被机器仿的：

| # | 感官 | 内容 | 例（书中 Back Porch 段落，p0001） |
|---|---|---|---|
| 1 | **视觉** sight | 看见的。★ 书里把它再拆成**颜色、形状、质地**三维（《Without Boundaries》p0001） | 透明翅膀的大熊蜂；缠在蛛网里的电线；生锈的钉子；阳光里的金色斑点 |
| 2 | **听觉** hearing | 听见的 | 嗡嗡响的旧剃须刀；高跟鞋哒哒的声音 |
| 3 | **嗅觉** smell | 闻到的 | 潮湿夏天泥土的气味 |
| 4 | **味觉** taste | 尝到的 | 空气里淡淡的霉味和蜀葵味 |
| 5 | **触觉** touch | 碰到的 | 又厚又脆的电线；手底下凉的湿土 |
| 6 | ★ **体觉** organic | **身体内部的感觉**：心跳、脉搏、肌肉紧张、胃痛、呼吸 | 缩紧肩膀；蹲着；猛地站起；后背和脖子发麻 |
| 7 | ★ **动觉** kinesthetic | **你与周围世界的空间关系** | 「避开上方那些耐心等着我后背或脑袋忘掉它们的生锈钉子」；「我能感觉到妈妈在我上方」 |

**书里对这两种的说明**（p0001）：
- **体觉**：「Athletes are most keenly focused on this sense, but you use it constantly, especially in responsive situations.」
  （运动员最敏锐地关注这种感官，但你一直在用它，尤其是在有反应的情境里。）
- **动觉**：「When you get seasick or drunk, the world around you blurs... When the train you're on is standing still and the one next to it moves, your kinesthetic sense goes crazy.」
  （晕船或喝醉时，周围的世界会模糊……你坐的火车没动而旁边那列动了，你的动觉会发疯。）
  舞者和潜水员把它发展得最充分——他们看向舞台或水面，看到的是身体的空间可能性。

★ **总原则**：
> 「The more senses you incorporate into your writing, the better it breathes and dances.」
> （你在写作里放进的感官越多，它就越能呼吸、越能舞动。）
> —— Pattison《Writing Better Lyrics》p0001

**失效条件**：
七感写全了但每一条都是"美的"——那是在填表。
书里那段 Back Porch 里有霉味、有生锈的钉子、有蹲着发麻的后背，
**不体面的感觉比好看的感觉有用**。

### 1.3 十分钟，就十分钟

**方法**（Pattison《Writing Better Lyrics》p0001）：

1. **早上第一件事**，限时十分钟。
2. > 「Guarantee yourself ten minutes and only ten minutes. Set a timer, and stop the second it goes off.」
   （保证自己只有十分钟，就十分钟。设个计时器，**响铃那一秒就停**。）
3. ★ **不许多写**。书里给的理由很实际：某天写了三十分钟，第二天就容易因为累而放弃。
   > 「Any good coach will tell you that more is gained practicing a short time each day than doing it all at once.」
   （任何好教练都会告诉你，每天练一小会儿比一次练完收获更多。）
4. ★ **中断效应**（书里叫 *writus interruptus*）：**在第六分钟状态最好的时候停**。
   > 「Guaranteed, when you sit down the next morning, you will dive deeper faster. The bottom in three minutes flat. Next time, one minute. Finally, instantly. That is your goal: immediate access — speed and depth.」
   （保证第二天早上坐下时，你会潜得更深更快。三分钟到底。下次一分钟。最后是瞬间。**这就是目标：即时抵达——速度与深度**。）
5. ★ **停得比你想的更彻底**（Pattison《Songwriting Without Boundaries》p0001）：
   > 「Be sure you always stop right at the buzzer. Don't finish the sentence. Don't even finish the word you're in the middle of.」
   > （务必在铃响那一刻停。**别写完句子，连正在写的那个词都别写完**。）
   > 「The ten-minute absolute limit is the key to building both.」
   > （十分钟的绝对上限，是同时建立速度与深度的关键。）

**一天三个，时长不同**（同上 p0001、p0002）：**10 分钟 / 5 分钟 / 90 秒**。
90 秒那个短冲刺是专门**练速度、快速潜进感官**用的。
提示词清单与十四天的编排见 [reference.md](reference.md) §2。

**为什么是早上**：书里说这是为了**把你身体里那个"写作的人"叫醒**，
让它一整天都在嗅、在尝、在找比喻——
> 「It's like writing all day without moving your fingers.」
> （这就像整天都在写作，却不用动手指。）
> —— 同上 p0001

**周期**：每天十分钟，**至少坚持六周**（Pattison《Writing Better Lyrics》p0002）。

### 1.4 写的时候的限制

（Pattison《Writing Better Lyrics》p0001、p0002）

| 限制 | 原文 |
|---|---|
| **不押韵、不讲节奏** | 「No rhythm, no rhyme. No need for complete sentences.」（不要韵律，不要押韵。不需要完整句子。） |
| **不需要故事线** | 不必解释"真实是怎么发生的"（how it really happened） |
| **不必守住起始物** | ★ 允许**急转弯**（full right turns）和跳跃：**让每个新的感官意象当枢轴**（pivot），把你带到下一个意象 |
| **待在感官里** | stay inside your senses——一想解释、一想议论，就回到感官 |
| **不许下判断、评论、引语** | ★ 《Without Boundaries》p0002 把这条列成明文规则：**只用那七种感官** |

**书里那句话最能说明这条**（《Without Boundaries》p0001）：
> 「There's no reason to stay loyal to the subject that sets you on your path. Your senses are driving the bus — you can go wherever they take you.」
> （没有理由忠于那个让你上路的题目。**是你的感官在开车**——它们带你去哪都行。）

★ **"不必守住起始物"这条容易被误读**：
它不是"想到哪写到哪"，是**只允许从感官跳到感官**。
从"雨伞"跳到"外婆家的铁皮屋顶"合法（听觉带过去的）；
从"雨伞"跳到"人生的庇护"不合法（那是概念跳的，不是感官跳的）。

**中文语境示范**（自拟，非书中例）：
> 起始词「暖水瓶」——软木塞拔出来那一下的闷响／瓶胆内壁的银锈／
> 塞子上一圈被烫黄的印子／倒水时先出来的那口白气／
> 手腕往回收的角度（动觉）／喉咙里烫到缩了一下（体觉）……

### 1.5 不只从"物"起头：who / when / where

物体只是最常用的起点。书里把提示词分成四类，并按这个顺序练
（Pattison《Songwriting Without Boundaries》p0002）：

| 类 | 写什么 | 它管的事 |
|---|---|---|
| ★ **what** | 物、事 | 打底。**先纯写这一类**，它是物体写作多年的主食 |
| **who** | 从一个具体的人的眼睛里看 | 角色。核心问题：**谁在说话？她在对谁说？**（→ 对象与视角归 `lw-narrative`） |
| **when** | 一个时刻 | |
| **where** | 一个地点 | ★ 「"Where" organizes action.」（**地点组织动作**，同上 p0006） |

★ **"where" 和 "when" 合起来最有用**（同上 p0005）：
> 「"Where" and "when" are a powerful combination, working together to create a scene and situation — a context for "who" and "what" to operate from.」
> （地点和时间是很强的组合，它们一起造出场景与情境——**给"谁"和"什么"一个可以运作的语境**。）
> 「The better you are at imagining a place, the more activity is possible for your characters because they'll have something to react to.」
> （你越会想象一个地方，你的人物就越有事可做，因为**他们有东西可以做出反应**。）

⚠ **这一条直通 §4**：**场景是意象合法性的来源**。
先把地点和时刻写实，后面的意象才有地方站。

### 1.6 素材怎么存

书里建议**专门开一个存"宝石"的地方**——
一个叫 `frag.` 的文件，或者笔记本前五页留白，
专门放 object writing 里跳出来的漂亮意象。
目的是**刺激灵感、加深你所游泳的那个世界**。
（Pattison《Writing Better Lyrics》p0003）

★ **挑的时候多问一句**（Pattison《Songwriting Without Boundaries》p0002）：
> 「Why do you like those best?」（你为什么最喜欢那几个？）
>
> 书里给的理由：**这会帮你发现你自己写作的工具。**

**自检动作**：
写完一段 object writing，**当场圈出两三个你自己都没预料到的词**，
只把这几个抄进存放处。全段都觉得好 = 一个都没挑出来。

### 1.7 object writing 与写日记不是一回事

（Pattison《Writing Better Lyrics》p0003）

| | 驱动力 | 目的 |
|---|---|---|
| **写日记** | 事件、情绪、"我真正的感受" | 自我探索 |
| **object writing** | **感官** | **为写歌做准备**，有特定用途 |

★ 这条是判据：**写着写着变成在写自己的心情，就已经不是 object writing 了。**

### 1.8 允许加"说"：destination writing

纯感官练几周之后，可以在 object writing 里掺进**评论/告知**（tell），
这个变体叫 **destination writing**（目的地写作），
由 Andrea Stolpe 在《Popular Lyric Writing: 10 Steps to Effective Storytelling》里提出。
理由是：**好的歌曲想法、尤其是标题，同样容易从"说"那一侧冒出来**，
不是只有"展示"那一侧才出东西。
（Pattison《Writing Better Lyrics》p0002）

⚠ **顺序不能反**：书里明说先练几周纯 sense-bound 的，再掺 tell。

---

## 2. 具体 vs 抽象

### 2.1 为什么抽象名词是最直接的 AI 指纹

一个抽象名词（时光、远方、梦、自由、青春、思念、温柔）**本身没有错**——
它错在**它是一堆具体物的平均值**：
说"思念"，听的人调不出任何画面；说"总是多煮的那半碗饭"，画面自己就来了。

书里把这件事说成 **universal 与 generic 的区别**
（Pattison《Writing Better Lyrics》p0005）：
- 歌要有**普遍性**（universal），**但不要把它和"通用"（generic）搞混**。
- 做法是 **sense-bound**：刺激听众的感官，**让他们从自己的感官档案里调出画面**。

**书里的对照**（同上 p0005）：

| | 例 | 结果 |
|---|---|---|
| **通用** | 「Noise and confusion, there's no peace / In the hustle and bustle of city streets…」 | 只能指向"意义的领域"，你没到那儿 |
| **感官** | Yeats：「I will arise and go now… I hear lake water lapping…」 | ★ **它把你带到了那里** |

★ **另一本书把病因说得更直接**：
**抽象、通用的写作缺的是"落地的力量"**（grounding power）
（Pattison《Songwriting Without Boundaries》p0006）。
"泛"不是风格问题，**是这句话没有着地点**。

### 2.2 ★ 重力法则：先展示，后告知

这是本节最可操作的一条，书里叫**玛丽·伊丽莎白修女规则**
（The Sister Mary Elizabeth Rule of Songwriting，Pattison《Writing Better Lyrics》p0003）：

> 「YOU CAN'T TELL UNLESS YOU SHOW FIRST」
> （**除非你先展示，否则你没资格告知**。）

书里的比喻是**染料袋**（bag of dye）：
把具体的感官意象当成一袋染料**挂在段落顶上**，颜色会往下滴，
给后面的句子染上兴趣和深度。
★ **重力法则：颜色只能往下滴，不能往上。**
具体意象放在后面，前面那些抽象句就是没颜色的。

**书中对照（同一段，只换顺序）**（p0003）：

| 顺序 | 词 | 结果 |
|---|---|---|
| ✅ 先展示 | Hot rod hearts and high school rings ／ Those dreamy teenage nights ／ Nothing matters like it did ／ Back when you were mine | "teenage nights" 变梦幻了，情绪更强 |
| ❌ 后展示 | Nothing matters like it did ／ Those dreamy teenage nights ／ Hot rod hearts and high school rings ／ Back when you were mine | 前两行没颜色——**染料滴不上去** |

**自检动作**：把一段词的**第一行**单独拿出来看。
它如果是个判断句／概括句，这一段后面所有具体的东西都**白写了**。

### 2.3 抽象词黑名单怎么建

`imagery.forbidden` 不是一张通用词表，**是这一首歌的禁用表**。三步：

1. **搬 `lw-song-intent` §5.1 排掉的那些**——
   为了选出 `anchor_object` 而被判掉的抽象词，**原样写进 `forbidden`**。
2. **抄一遍自己的**。书里 Exercise 10 就是这个：
   **列一份你自己的陈词清单，长度不少于书里那份**（Pattison《Writing Better Lyrics》p0005）。
   ★ **自己写的黑名单才有用**，因为每个人偷懒时伸手够的是不同的词。
3. **从初稿里反向抓**：把初稿所有名词圈出来，
   **凡是拍不了照的，全部进表**，然后一个一个换。

⚠ **黑名单的失效条件**：
表里的词不出现，但**换成了同一层级的近义词**（"思念"改"牵挂"），
那就只是躲过了字符串检查。**判据是能不能拍照，不是有没有命中词表。**

常见抽象词与死喻的起手清单见 [reference.md](reference.md)。

### 2.4 ★ 把抽象改成具体的操作步骤

**一句话一句话地做，不要整段重写：**

| 步 | 动作 |
|---|---|
| **1** | 圈出这句里**拍不了照的那个词** |
| **2** | 问：**我是在哪一次、哪个房间里知道这件事的？**（回到 `intent.at_what_moment`） |
| **3** | 问书里那三问的物件版：**那时候手里拿着什么？那屋里有什么别人不会注意？什么东西现在还在你那儿？**（→ `lw-song-intent` §6.1） |
| **4** | 用 §1 的七感把那个场景刷一遍，**不要只刷视觉** |
| **5** | 挑一个**能拍照、且带一点不体面**的东西，换掉第 1 步圈出的词 |
| **6** | ★ 回读整段：**那句原本的抽象话还需要说吗？** 多半不需要了 |

**书中最有说服力的一组反向演示**（Gillian Welch《One More Dollar》，Pattison《Writing Better Lyrics》p0003）——
把具体换成陈词，一首好词当场垮掉：

| 原版（具体） | 改坏（抽象／陈词） |
|---|---|
| For a job in the **fruit trees** | For a job in the **city** |
| But I missed those **hills with the windy pines** | But I miss **that place** and the things I did |
| When I reach **those hills**, boys | When I reach **that place**, boys |

书里引 David Rawlings 的判断：用 city/pretty 这种陈词韵替掉具体意象，
整首歌立刻变得 **"Instant bland"**（瞬间平淡）、**"beige"**（一片米色）。
Pattison 的原话：
> 「Look how completely it destroys a perfectly good work.」
> （看看它把一个完好的作品毁得多彻底。）

★ **这一组要反过来用**：拿自己的词做一次"改坏"实验——
把你最得意的那行的具体名词换成上位词，**如果换完读着差别不大，说明它本来就不够具体。**

### 2.5 客观对应物

书里把要找的东西叫 **objective correlative**（客观对应物，T.S. Eliot 的术语）：
**任何人都能摸到、闻到、看到的物体，而它与你要表达的那种情绪相关联。**
（Pattison《Writing Better Lyrics》p0004）

书中举的例：写"无家可归"，找到的是**购物车上那只坏掉的轮子**、**父母吵架的场景**。
★ 注意它给的策略：**就算已经找到一个好想法，也要继续找——好想法后面通常还有更多。**

---

## 3. 感官的分布

### 3.1 为什么一首词不能只有视觉

**视觉是最省力的感官**，所以它是默认值——
写作的人（和模型）不特意管的时候，出来的东西几乎全是"看见"。
而书里那条总原则是**感官越多越好**（§1.2，p0001），
七感里另外六种一个都不出现的词，**就是只用了七分之一的材料**。

★ **嗅觉与味觉是回忆的入口**，体觉与动觉是"身体在场"的证据——
**这两对恰好是抽象化最先丢掉的东西。**

### 3.2 怎么检查感官分布

**一个动作**：把词稿打一遍，**给每一个感官性的词标上它属于哪一感**，然后数。

| 检查 | 判据 |
|---|---|
| 七感出现了几种 | ★ 只有视觉 → 回 §1 重做 object writing |
| 视觉占比 | 视觉占到绝大多数 → 挑 2–3 处改写成别的感官 |
| **体觉/动觉有没有** | 一处都没有 → 词里**没有身体**，只有眼睛 |
| 副歌有没有感官 | 副歌全是议论也可能是对的（见 §3.3），但主歌不能也是 |

★ **写的时候随身带这三问**（Pattison《Songwriting Without Boundaries》p0002）：
1. 「What's that like?」（那像什么？）
2. 「Can I get more specific?」（我能更具体吗？）
3. ★ 「Is there another sense I could be using?」（**我还能用上别的感官吗？**）

**第 3 问就是这一节的日常形态**——它在写的当下就把分布补了，
不必等到检查时再回头改。

**改写不是加形容词**，是**换事件**：
"我很紧张" → 体觉：「指甲掐进掌心那一下」；
"房间很安静" → 听觉：「冰箱的嗡声突然显得很大」。（自拟示范）

### 3.3 ⚠ 主歌与副歌的分工

书里有一句现成的分工：
> 「verses show, chorus tells.」（主歌展示，副歌陈述。）
> —— Pattison《Writing Better Lyrics》p0009

★ **所以"感官分布"不是要求每段均匀。**
它要求的是：**具体的东西必须在前面出现过**（§2.2 的重力法则），
副歌才有资格说那句概括的话。
**副歌抽象 + 主歌也抽象 = 没有染料袋。**

---

## 4. ★ 意象成系统

**这一节是本 skill 与"多写几个具体名词"的分界，也是 `imagery.system` 这个字段存在的理由。**

### 4.1 随机堆意象 ≠ 意象系统

具体名词凑够了，词仍然可能是散的：
每一句都有画面，但这些画面**不在同一个世界里**。
`lw-ai-tell-audit` §4.1 把这条列为"全过了还是像 AI"的四个征兆之一。

**判据来自书里最硬的一句**（Pattison《Writing Better Lyrics》p0021）：
> 「A metaphor has to be grounded in something real. If they were on the beach, sea spray on his face would be just fine. It could be both what it actually is, plus more. Remember to ground your metaphors in reality. They must have a legitimate place in the context.」
> （比喻必须扎根在某件真实的东西上。如果他们在海滩上，他脸上的浪花就完全没问题。它既可以是它实际的样子，又可以不止于此。**记住把你的比喻扎根在现实里。它们在语境中必须有合法的位置。**）

**书里的具体情形**：那首词的场景在室内，写到 "sea spray on his face"（脸上的浪花）——
**浪花没有来源**，所以它只是个漂亮的说法，让人困惑。
书里同时提醒：**不能假设听众脑子里的画面和你一样**，
场景必须在词里立起来，成为**"每个人的心理图像"**。

★ **一句话的判据**：
> **意象的合法性来自场景，不来自它本身好不好看。**
> 问每一个意象：**它凭什么在这里？谁带它进来的？**

### 4.2 系统怎么长出来：一个物件的"同调词"

书里给的生成法是拿音乐的**调性**打比方
（diatonic relationship，Pattison《Writing Better Lyrics》p0003）：
选一个词当**基音**，围着它列出属于同一个"调"的词。

**书中例**：以 **tide**（潮汐）为基音，同调的有
ocean、moon、recede、power、beach。

**两个生成问题**（同上 p0003）：
1. **我这个东西有什么特征？**
2. ★ **还有什么东西也有这些特征？**
   （书里说，回答第二问通常会一次放出一大把可能的比喻。）

**中文语境示范**（自拟）：基音取「暖水瓶」——
同调词：软木塞、白气、烫、铁皮壳、瓶胆、开水房、暖、凉透了、倒空。
★ 注意这一串的共同点：**它们能出现在同一间屋子里**。
"星辰"、"远方"不在这个调上——它们进来就是转调。

### 4.3 连接特质：把一整套词汇搬过来

★ **系统之所以能成系统，是因为它带着一整套词，不是一个词。**

书里的四步（Pattison《Songwriting Without Boundaries》p0009、p0010）：

| 步 | 动作 |
|---|---|
| 1 | 给要写的东西列**至少三个特征** |
| 2 | 对每个特征问 ★ 「What else has that quality?」（还有什么有这个特征？） |
| 3 | 把新找到的那个东西的**名词、动词、形容词全都列出来** |
| 4 | **把这一整套词用到原来那个东西身上** |

**书中演示**（p0009，写警察）：

| 特征 | 接到 | 搬过来的词 | 写出来 |
|---|---|---|---|
| 他调查 | X 光 | black and white、broken bones、revealing | 「The police are an x-ray, investigating the broken bones of the neighborhood, revealing every fracture in black and white.」 |
| 他调查 | 机械师 | engine、oil、pistons、wrench、hood | 「Policemen are the mechanics of mystery… pop open the hood of a criminal case… Every piston that misfires… is a fingerprint.」 |

★ **看这两行的差别**：同一个特征接到不同的东西上，
**整段的词汇库就换了一整套**——这就是"成系统"在写作时的实际操作。
书里管这个叫**家族**（family）：
> 「subtle members of the river and guitar families sharing "bending."」
> （河与吉他这两个家族里，微妙地共享着"弯折"这个成员。）
> —— 同上 p0012

更长的清单、双向做法与"透镜"见 [reference.md](reference.md) §4。

### 4.4 书中一个成系统的实例

《She Sells Seashells》的定稿主歌（Pattison《Writing Better Lyrics》p0020）：

> Daddy's voice is thunder
> Mommy's voice is rain
> She's too scared not to watch
> The hurricane

★ **雷、雨、飓风是同一个气象系统**——不是三个漂亮比喻并列，
是**同一场天气**，所以第三句的"飓风"不需要解释：前两句已经把它造出来了。
而全曲的核心物件（贝壳／海岸／潮汐）与这场天气**共用一个物质世界：水**。

书里还留下了挑选的过程（同上 p0020）：
围绕 "Seashells" 做 object writing 之后，作者**逐条判去留**——
"前端装载机"（来自童年，但可能不合这个场景）被搁置；
"贝壳上的螺旋纹"留下（对应父母分开在女孩身上刻下的东西）；
"潮汐当作父母声音的比喻"留下。
★ **留下的理由全都是"它属不属于这个场景／这个人"，不是"它好不好看"。**

### 4.5 怎么检查系统

| # | 检查动作 | 不过的表现 |
|---|---|---|
| **1** | 把全词的具体名词**列成一张单子**（就是 `imagery.concrete_nouns`） | 列不出十个 → 先回 §1 |
| **2** | ★ 问：**这些东西能同时出现在一个场景里吗？** | 出现了两个以上互不相干的物质世界 |
| **3** | 每个意象问一遍：**谁把它带进来的？**（人物、场景、时刻） | 答"因为它好听" → 删 |
| **4** | 把 `imagery.system` 用**一句话**写出来 | ★ **写不出来 = 没有系统**，它们只是装饰 |
| **5** | 试删：任取一个意象删掉，看别的意象**会不会跟着塌** | 全都删得掉、互不影响 → 是并列的装饰，不是系统 |

★ **第 5 条最狠**：系统里的东西互相支撑，装饰互不相干。

---

## 5. 比喻与死喻

比喻的完整分类、死喻清单与替换方法见 [reference.md](reference.md)。
**提喻与转喻**这两个比隐喻更少人用的格、各自的操作指令、以及象征性歌词，见 [reference.md](reference.md) §7；聚类法生标题见 §8；旅程型歌词的九点清单见 §9。

## 6. 物件的贯穿

**语料实测**（国语非说唱 n=487；有无物件两模型盲判一致 75%）：有贯穿物件的歌 67%，出现次数中位 4 次、P90 9 次；★ **物件每次意义有偏移的只占 21%**，八成的物件只是复现，靠位置与句式换意思。
情境型有物件的 86%，态度型 60%（→ `lw-song-intent` §1.2）。样本里最常见的物件是风、雨、酒、太阳、梦、手、列车、海、星星、电话，全是通用词，
说明**物件本身不需要新奇，需要的是它在段落里的位置**。说唱 54%、粤语 61%（n=100／36）。

### 6.1 它已经在别处定过了

`intent.anchor_object` 的选取判据（能拍照、说得出颜色大小新旧）
以及"出现三次、每次含义不同"的原则，**归 `lw-song-intent` §5**。
**本节不重复那五问**，只接着讲**怎么让含义递进**。

### 6.2 含义递进靠段落发展，不靠换形容词

书里讲重复的那条规则叫 **productive repetition（有效重复）**
（Pattison《Writing Better Lyrics》p0007）：
> **重复的那句话再说一次时依然有趣，甚至因为重复而得到了更多东西。**

★ **关键在于：变的不是那个物件，是它周围的信息。**

**书中实例：《Strawberry Wine》里的月亮**（Pattison《Writing Better Lyrics》p0006）——
同一句 "The hot July moon saw everything"，含义随段落推进：

| 位置 | 月亮是什么 |
|---|---|
| 第一段 | 见证了河边那次初次 |
| 第二段 | 知道这场爱不会长久 |
| 第三段 | ★ 知道往后再也回不到初恋的那种纯与烈——"the fields have grown over now" |

书里的判断：**月亮从"观察者"变成了"预言者"**，
而且**每一行都有责任让自己能够"增重"（gain weight）**。

### 6.3 怎么让它递进（操作）

| 步 | 动作 |
|---|---|
| **1** | 物件在**每段各是什么**，一段一句写出来（→ `lw-song-intent` §5.3 的那张表） |
| **2** | ★ 检查**变的是不是物件本身**——换形容词（"那件旧卫衣"→"那件破卫衣"）不算递进 |
| **3** | 让**它周围的事实**发生变化：谁还在／谁不在了、它在谁手里、它还能不能用 |
| **4** | 最后一次出现时，**读者对它的了解必须比第一次多**——否则它只是重复 |

**失效条件**：
物件每段都出现，但**每段说的是同一件事**。
这时候它不是结构，是口头禅。

### 6.4 ⚠ 物件不等于比喻

一个贯穿的物件**可以**同时是比喻，但**不必是**。
书里那条"扎根"的说法正好给了最舒服的状态（p0021）：
> **它既可以是它实际的样子，又可以不止于此。**

★ **顺序是：先让它是个真东西，再让它有意思。**
反过来做（先想要一个象征，再找个东西来当它）
就是 `lw-song-intent` §7 那面照妖镜照出来的东西——
**倒推出来的物件说不出颜色和新旧**。

---

## 7. 与 LYR-SPEC 的字段对应

| 字段 | 本 skill |
|---|---|
| `imagery.concrete_nouns` | §1（怎么挖）、§2（怎么把抽象换掉）、§4.5 第 1 条（怎么列） |
| `imagery.system` | ★ §4——**这个字段就是本 skill 的核心**，一句话写不出来就是没有 |
| `imagery.forbidden` | §2.3 建表、§2.4 换词 |
| `intent.anchor_object` | 选取在 `lw-song-intent` §5；**本 skill 管它的贯穿与递进**（§6） |
| `narrative.tense_anchor` | 借它定"哪个时刻"（§2.4 第 2 步），字段本身归 `lw-narrative` |

★ **LYR-LINT 第 2 条查这一层**：每段具体名词的数量、`forbidden` 是否零出现。
⚠ 该条**只报数不判过/不过**——数字之外还要人判 §4.5 的第 4、5 条。

---

## 8. 写完自检

- [ ] **每段的具体名词都列出来了**（`concrete_nouns` 不是事后补的）
- [ ] 抽象词黑名单**零命中**，且**不是靠换近义词躲过去的**（§2.3）
- [ ] ★ 每一段的**第一行**不是概括句（重力法则，§2.2）
- [ ] 七感**至少出现三种**，且**体觉或动觉至少有一处**（§3.2）
- [ ] ★ `imagery.system` **一句话写得出来**（§4.5 第 4 条）
- [ ] 做过**试删**：删掉一个意象，别的会跟着塌（§4.5 第 5 条）
- [ ] 每个比喻**在场景里有来源**——没有凭空出现的浪花（§4.1）
- [ ] 全词的比喻**只有一套喻体**，或换套的地方有真实过渡（§5.5）
- [ ] 用了暗喻的地方**兑现了**（§5.3）
- [ ] 死喻家族里的词如果出现，**是被扎进了场景或被拆开了**，不是顺手拿的（§5.4）
- [ ] 贯穿物件**每段含义不同**，且变的是它周围的事实（§6.3）
- [ ] ★ 做过"改坏"实验：把最得意那行的具体名词换成上位词，**读着明显变差**（§2.4）

---

## 附：来源

- **主干**：Pat Pattison《Writing Better Lyrics》——
  object writing 与七种感官、十分钟计时法（p0001）、感官自由联想与练习周期（p0002）、
  先展示后告知与染料袋、比喻的定义与三种形式、同调词（p0003）、
  名词配动词、明喻与暗喻的焦点转移、客观对应物（p0004）、
  陈词清单与死喻家族、universal 与 generic（p0005）、
  物件的增重（p0006、p0007）、主歌展示副歌陈述（p0009）、
  object writing 作为探索工具与意象的筛选（p0020）、比喻必须扎根现实（p0021）。
- **destination writing** 的出处是 Andrea Stolpe《Popular Lyric Writing: 10 Steps to Effective Storytelling》，
  经 Pattison《Writing Better Lyrics》p0002 转述。
- **与 `lw-song-intent` 的分工**：那边定 `anchor_object` 的判据，这边定找法与系统。
- ⚠ §1.4、§2.4、§3.2、§4.2 里标注"自拟"的中文示范不是书里的例子，
  是为中文写词做的演示。
