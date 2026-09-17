# 英文重音与音步参照表（lw-english reference）

> 本表只服务英文（及其他重音语言）的落位检查。
> **中文的字调与十三辙不在这里** → `lw-mandarin` / `lw-tone-check`；粤语 → `lw-cantonese`。
> **押韵的语音家族表、元音三角形、连接点** 在 `lw-rhyme` 的
> [reference.md](../lw-rhyme/reference.md)，**本表不重复**。
> 主文见 [SKILL.md](SKILL.md)。**读本表之前先读 SKILL.md §1 与 §3。**

---

## 1. 标记法

### 1.1 逐音节标记

| 记号 | 含义 |
|---|---|
| `/` 或大写 | **重读音节（stressed）** |
| `x` 或小写 | 非重读音节（unstressed） |
| ★ `//` | **次重音（secondary stress）**——不是主重音，但比周围的音节强 |
| `DUM` / `TUM` | 重读音节的拟声写法 |
| `da` / `ta` | 非重读音节的拟声写法 |
| `(hold)` | 延音 |
| `(pause)` | 休止、气口 |

**两套拟声写法并存**：Pattison 系用 `DUM da`，Davis 系用 `TUM ta`。
★ **同一份稿子里只用一套，不要混。**

### 1.2 行长标记

| 记号 | 含义 |
|---|---|
| `4` | 四个重音 |
| ★ `3+` | **三个重音，末尾再挂一个弱音节收尾**（`Sátan rídes the fréeway`）。★ **它比纯 `3` 长** |
| `2+` | 同理 |
| `A` / `B` / `C` | ★ **行长相同、押韵相同、基本节奏相同**的行才共用一个大写字母 |
| `x` | 不押韵的行 |

（大写字母的三条件见 Pattison《Writing Better Lyrics》"Notation and Stability" 一节：
必须同时满足**互相押韵、重音音节数相同、基本节奏相同**。）

### 1.3 排查用的对照写法

```
行文本   The  SUN  comes  UP   on a  BRIGHT  new  DAY
重音     x    /    x      /    x x   /       x    /
拍位     &    1    &      2    & &   3       &    4
判       ✔ 四个重音全落在 1/2/3/4 拍上，the 在弱起位
```

---

## 2. ★ 音步表（Feet）

**希腊人把语言里常见的节奏按二音节组、三音节组命名；
诗以音步（foot）、行（line）、节（stanza）为单位度量。**
（Davis《Craft of Lyric Writing》p0243）

| 音步 | 重音模式 | 例 | 性格 |
|---|---|---|---|
| **iamb 抑扬格** | `ta TUM` | to-DAY, the SNOW | ★ **最接近日常口语的起伏**（p0244） |
| **trochee 扬抑格** | `TUM ta` | AL-ways, TRY and | 落在强拍上起句，铿锵 |
| ★ **spondee 扬扬格** | `TUM TUM` | QUICK-SAND, TIN CUP | ★ **拉伸时间、迫使放慢**（p0245） |
| **dactyl 扬抑抑格** | `TUM ta ta` | HEAV-en-ly, RAIN on the | 戏剧性、宏大（p0247） |
| **anapest 抑抑扬格** | `ta ta TUM` | in-ter-JECT, on a TRAIN | ★ 轻快、欢快、甚至肤浅（p0246） |
| **paean 四音节格** | `TUM ta ta ta` | — | 喜悦、赞美、胜利；像货运列车一样脉动（p0249–p0250） |

- **二音节音步**（iamb、trochee）合称 **double meters**；
  **三音节音步**（dactyl、anapest）合称 **triple meters**（p0244）
- ★ **少于五个音步的行比长行更"songlike"（更像歌）**（p0244）
- **iambic pentameter（五步抑扬格）** 是英语诗歌里最重要的格，因为它最接近日常口语（p0244）

### 2.1 音步与情绪的对应（Davis）

| 音步 | 适合 | 实例（Davis 所举） |
|---|---|---|
| **spondee** | 严肃、疲惫、悲伤、庄严 | `SOME-WHERE … SOME-HOW …`（p0245）；《Memory》开头的慢 spondee 造出庄严感（p0245）；《Climb Every Mountain》结尾的 terminal spondee `TUM/(hold)/TUM(hold)`（p0246） |
| **anapest / dactyl** | 轻快、喜剧 | ★ 在以 iamb / trochee 为主的段落里插三音节音步 → **加速、增加 breeziness**（p0246）；五行打油诗的 anapestic trimeter 自带轻浮联想（p0246） |
| **dactyl** | 宏大、戏剧性（尤其慢歌） | 《The Impossible Dream》、《Somewhere》、《She's Leaving Home》（p0247） |
| **三音步行（iambic trimeter）** | 轻快的抱怨、街头口吻 | 《Gee Officer Krupke》——★ 末行把上行的 iamb 反转成 trochee 来加强收尾（p0246–p0247） |
| **长行（5–7 音步）** | 叙事、哲思、孤独、存在困境 | p0244 |
| **短促行（2–3 音步）** | 尖锐的社会评论、切分感强的都市口吻 | Cole Porter 的 clipped cadence、Sondheim 的二三音步行（p0244–p0245） |

### 2.2 ★ 音步与意思打架的两个反例（Davis p0247–p0248）

| 反例 | 出了什么事 |
|---|---|
| 写"垃圾食品"却用了 spondee（`Junk/food`） | ★ **给琐碎的词灌了情感重量**，产生不协调（incongruity） |
| 写无家可归者的严肃题材却通篇 anapest（`dadaDUM`） | ★ **整首变成童谣（sing-song）**，严肃性被抽掉 |

> ★ **Davis 的经验判据**：**连着三个 anapest，往往就把这个想法变琐碎了（trivialize）。**

**反过来也成立（p0248–p0249）**：想法本来就轻，anapest 会把这份轻**强化**。

### 2.3 行中重音碰撞（midline stress collision）

★ **两个重读音节在行中间挤在一起，会把语速压下来、把意义压重。**
Davis 分析《The Gambler》（p0251）：三音步行、节奏 `one, two THREE [silent four]`，
行中的 `warm/summer`、`train/bound for` 两处重音碰撞**有效放慢了语速**；
主导的下行节奏 `DUM/DUM da/DUM da` 与《葬礼进行曲》的庄严节奏同形。

★ **另一例（p0249–p0250）**：《Gentle on My Mind》主体是 paean 格，
**靠 midline spondee 去强调特定词（`ink stains`、`back roads`），打破 paean 的规律性。**

---

## 3. 词重音的几类边界情形

### 3.1 ★ 词性变了，重音就变

**这不是自由，是另一条约束——用错等于用错词性。**

| 名词 / 形容词（重音在前） | 动词（重音在后） |
|---|---|
| `REC-ord` | `re-CORD` |
| `PRES-ent` | `pre-SENT` |
| `CON-tract` | `con-TRACT` |
| `CON-flict` | `con-FLICT` |
| `PER-mit` | `per-MIT` |
| `REB-el` | `re-BEL` |
| `OB-ject` | `ob-JECT` |
| `PRO-duce` | `pro-DUCE` |
| `IN-crease` | `in-CREASE` |
| `DES-ert`（沙漠） | `de-SERT`（抛弃） |

**自检动作**：这类词落位前，**先确认这一句里它是哪个词性**，再定重音。

### 3.2 英美读音不同的词

`ad-VER-tise-ment`（英）/ `AD-ver-tise-ment`（美）、
`CON-tro-ver-sy`（美）/ `con-TRO-ver-sy`（英常见）、
`gar-AGE`（美）/ `GAR-age`（英）、
`AD-ult` / `a-DULT`、`RE-search` / `re-SEARCH`。

★ **先定歌手的口音，再定落位。** 同一首歌里不要两种口音混着来。

### 3.3 次重音会翻车的词

**次重音（`//`）是"不是主重音、但比周围强"的音节。**
当一个词的**最后一个音节带次重音**时，它在听感上不是弱收尾：

- `appreciate` —— 最后一个音节比前一个强
- `celebrate`、`decorate`、`demonstrate` 一类 `-ate` 动词同理

★ **后果有两层**：
1. **押韵上**它不能当阴性韵（详见 `lw-rhyme` §2.1）
2. ★ **落位上**它的收尾音节**不能挂在最弱的那个音符上**——那里撑不住

---

## 4. 缩写与口语省音：音节数与重量

| 全写 | 省音 | 音节 | 重量变化 | 语域 |
|---|---|---|---|---|
| going to | gonna | 3 → 2 | 收尾变弱音节 | 口语 |
| want to | wanna | 2 → 2 | ★ `-na` 比 `to` 更弱 | 口语 |
| got to | gotta | 2 → 2 | 同上 | 口语 |
| them | 'em | 1 → 1 | ★ **几乎不能承重** | 口语 |
| because | 'cause / cos | 2 → 1 | — | 口语 |
| and | 'n' | 1 → 0~1 | ★ 可以完全并进相邻词 | 口语 |
| about | 'bout | 2 → 1 | — | 口语 |
| them / him / her | 'em / 'im / 'er | 1 → 1 | 只能上弱拍 | 方言色彩强 |
| -ing | -in' | 不变 | ★ **改韵不改拍** | 乡村、蓝调、嘻哈 |
| I am / do not / will not | I'm / don't / won't | 2 → 1 | — | ★ **几乎所有语域通用** |
| let us | let's | 2 → 1 | — | 通用 |
| ever | e'er；over → o'er | 2 → 1 | — | ★ **古语，慎用**（见下） |

★★ **古语式省音（`e'er`、`o'er`、`'tis`、`thee`）是明确的警告信号**：
《Lyrics: Writing Better Words for Your Songs》p0055 把"为了凑韵改用 `thee` 代替 `you`"
列进要避开的清单，同页也警告不要为押韵扭曲时态
（Bob Dylan 用 `knowed` 代 `knew`、Neil Diamond 用 `brang` 代 `brought` 去押 `sang`，p0056）。
**为落位扭曲语言，和为押韵扭曲语言是同一种毛病。**

★ **省音能开出新的韵**（同书 p0057，详见 `lw-rhyme` §5.2）：
`museum` / `see em`、`tell 'em` / `cerebellum`、`warn yer` / `corner`、`do yer` / `hallelujah`。
**本表只负责它改了几个音节；那些韵成不成立归 `lw-rhyme`。**

---

## 5. 行长的长短关系（重音这一侧）

★ **本节只给与重音数直接相关的运动法则。用行长做段落结构在 `lw-structure`。**

> **Longer followed by shorter is less stable than shorter followed by longer.**
> **长行后接短行，比短行后接长行，向前倾斜得厉害得多。**
> **原因**：长行在经过时**已经把短行的长度"匹配掉了"**
> （The longer line has matched the shorter line on its way by），
> 所以短行到来时没有解决感，只剩缺口；反过来不存在这个匹配效应。
> （Pattison《Writing Better Lyrics》"Stability vs. Instability: Two-Line Sections" 一节）

**四种两行组合的稳定度（同节）**：

| 排序 | 行长 | 押韵 | 听感 |
|---|---|---|---|
| **1 最稳** | 匹配 | 押 | **停住，解决** |
| **2** | 匹配 | 不押 | **平衡**——比押韵弱，但足以阻止前冲 |
| **3** | 不匹配 | 押 | 较不稳——★ **韵落在不同的拍位上**，推力反而更强 |
| **4 最不稳** | 不匹配 | 不押 | **重重向前倒** |

★ **行长与押韵是两个独立的工具**：本 skill 只负责"行长"那一维，
"押韵"那一维在 `lw-rhyme`，**两维的组合怎么做段落**在 `lw-structure`。

---

## 6. 段内破除机械感的三种手法

**Davis《Craft of Lyric Writing》p0230 给的三条，按代价从低到高**：

| # | 手法 | 说明 |
|---|---|---|
| **1** | **改变重音（vary the accents）** | ★ 最便宜。换一个音步（见第 2 节），底盘不动 |
| **2** | **改变行内的自然停顿** | 把气口从行中挪一挪，见 SKILL.md §5.3 |
| **3** | **改变标点** | 逗号、破折号、句号带来的停顿长度不同 |

★ **加码手段：run-on line（跨行）**——"把一个想法绕过转角"，软化格律的严格性（p0230）。
★★ **但必须省着用**：听众要费力跟，连着用会令人疲惫（p0231）。

**再往上一层**（Davis p0245）：改行长（三拍变四拍）、或在行内打破均匀，
用来解 **meter fatigue（格律疲劳）**——"Everything sounds the same!"

### 6.1 ★ 用弱起做段落对比

Davis 分析《Over the Rainbow》（p0231–p0232）：

| 段 | 起法 | 词面表现 |
|---|---|---|
| **A 段** | 以 **downbeat（强拍）** 起 | ★ **以重音词开头** |
| **Bridge** | 每小节以 **pickup note（弱起）** 起 | ★ **以非重音词开头** |

> ★ **这是一个只靠"第一个音节是重是轻"就做出来的段落对比**，
> 不动旋律、不动韵式、不动行长。**最便宜的对比手段。**

---

## 7. 平行短语（Anaphora）

**定义**：写一个短语，保住它的结构，用变体重复它。
（《Lyrics: Writing Better Words for Your Songs》p0057；诗学名称 **Anaphora**）

| | |
|---|---|
| **优点** | ★ **不变的那半推着下一个想法往前走**；配上隔行押韵后，找韵脚常常会提示下一行 |
| ★ **对本 skill 的意义** | **重复的那半把节奏格子固定住了**——后半句可以自由变重音数，整段仍然听得出是一个系统 |
| **缺点** | ★ **越铺越显眼**。想象三段八行的主歌共 24 行都以 `some days` 开头——太重复 |
| **怎么收** | **限制在隔行使用**，或**四次陈述之后打破模式** |
| **最适合的位置** | ★ **副歌**——那里正需要张力与焦点的累积 |

**同页示例**：
`Some days are full of promise, / Some days never leave the ground; /
Some days are like an echo chamber, / Some days don't have a sound.`

★ **另一种极端**（同书 p0061）：Gilbert O'Sullivan《Nothing Rhymed》副歌里
`nothing` 出现 **13 次**——**靠纯重复累积出节奏力量。**

---

## 8. 节奏大纲：先写节奏，后填词

**Davis《Craft of Lyric Writing》p0236–p0239 的做法**：
**先写一份 rhythmic outline（节奏大纲），再往格子里填词。**

**大纲长这样**（p0237）：

```
Verse    TUMtata / TUMta / TUM (pause) …        —— 混合，密
Climb    TUM / TUM / TUM …                      —— 比 Verse 短促
Chorus   TUM / TUM / (hold) …                   —— 最强调重音，最慢
```

★ **各段的节奏模式要形成鲜明对比——这一步本身就把段落结构定义出来了。**

**Davis 说它解决三个问题（p0236–p0237）**：

| # | 效果 |
|---|---|
| **1** | ★ **写得更紧凑**——业余词里常见的松垮形容词与多余连接词自动被挤掉 |
| **2** | ★ **打破 personal meter 的紧身衣**——每个人都有自己不自觉重复的节奏惯性；有了外来格子，就会本能地去增减非重读音节 |
| **3** | 词在节奏上更 "musical" |

★ **实操口径（p0238）**：格式**松散地**用，允许改节奏、允许增删弱起的过门词。

★★ **对中文母语作者，这条尤其值钱**：
**先定格子再填词，能绕开"先想中文句子再译成英文"那条死路**（见 SKILL.md §6 第 6 条）。

---

## 9. 先曲后词时：怎么从旋律里把词"拉"出来

**Davis《Craft of Lyric Writing》p0258–p0259 的四步**：

| 步 | 做什么 |
|---|---|
| **1 当旋律侦探（tune sleuth）** | ★ **词必须是从旋律内部"拉出来（pull from within）"的，不是从外面叠上去（superimposed）的** |
| **2 内化旋律** | 反复播放到背熟，让旋律开始"对你说话" |
| **3 试哑元音（dummy vowels）** | ★ 用 `-ay-`、`-ee-`、`-i-`、`-o-`、`-oo-` 去唱旋律，**声音会把意义引出来** |
| **4 找标题位** | 标题通常落在**最主导、最好记的那个乐句**上 |

★ **第 3 步直接接到 SKILL.md §4.4**：哑元音试出来最顺的那个元音，
**就是这个位置该用的元音**——再回头去找带这个元音、且重音位置对的词。

★ **Davis 同处引 Irving Berlin**：标题与旋律绑在一起，听众才记得住这首歌（p0259）。

---

## 附：来源

- **音步表、音步与情绪、行中重音碰撞、meter fatigue、段内三种变化法、run-on line 的限制、
  弱起做段落对比、节奏大纲、旋律侦探四步、拍数必须相同**：
  Davis《Craft of Lyric Writing》p0227–p0260
- **`3+` 记法、大写字母的三条件、两行组合的稳定度、Longer-followed-by-shorter 法则**：
  Pattison《Writing Better Lyrics》
- **次重音与 `appreciate`**：Pattison《Essential Guide to Rhyming》
- **缩写与省音、古语式省音的警告、平行短语（Anaphora）、长元音好唱**：
  《Lyrics: Writing Better Words for Your Songs》p0055–p0057、p0061、p0100
- **词性决定重音的词表、英美读音差异词表**：英语词典通例，不属某一家的说法
- ⚠ **本表只适用于英语。** 中文见 `lw-mandarin` 与 `lw-tone-check`，粤语见 `lw-cantonese`

---

## 2. ★ 英文的重音不是你能选的

**这是中文作者最容易低估的一节。** 中文没有词重音体系，
所以中文母语者的直觉是"重音＝唱响一点"，可以自由安排。**英文不是这样。**

### 2.1 词重音（lexical stress）——词典决定，不可改

**每个多音节英文词的重音位置是词自带的属性**，和拼写一样固定；改了它，那就不是这个词了。

Pattison 在讲阴性韵时给了一条旁证：`appreciate` 的**最后一个音节比前一个强**（次重音，标 `//`），
所以它**不能**当阴性韵用——只能按单音节阳性韵处理（押 `fate`），
或当三音节韵（押 `the quiche he ate`，★ 而这只适合写喜剧）。
（Pattison《Essential Guide to Rhyming》"Mosaic Rhymes 与次重音" 一节）
★ **用法**：**连"这个词算阳性还是阴性"都由重音位置单方面决定，
那你更没有权力为了塞进小节去挪它。**

**自检动作**：**把每个三音节以上的词单独圈出来，逐个念一遍，确认重音在哪。**
若旋律要求的强拍不在那个音节上——**换词，不要换读音。**

**失效条件**（★ 完整词表见 [reference.md](reference.md) §3）：
- 少数词**随词性换重音**：`REC-ord`（名）/ `re-CORD`（动）、`PRES-ent` / `pre-SENT`。
  ★ **这不是自由，是另一条约束**——用错等于用错词性
- **英美读音不同**的词（`ad-VER-tise-ment` / `AD-ver-tise-ment`）：**先定歌手的口音，再定落位**

### 2.2 句重音——实词重，功能词轻

在词重音之上还有一层：**一句话里哪些词整体被强调。**

- ★ **实词（content words）重**：名词、动词、形容词、副词、疑问词、指示词
- ★ **功能词（function words）轻**：冠词 a/an/the、介词 of/to/in/on、连词 and/but、
  助动词 is/have/will、人称代词、关系词 that/which

★ **Common meter 的定义正建立在这一层上**：它**"基于强重音（strong stresses），
弱音节的位置是可变的"**（Pattison《Writing Better Lyrics》"Common Meter" 一节）——
**英文格律数的是强重音，中间夹几个弱音节相对自由**，
这是英文与中文最结构性的差别（中文一字一音节，数的是字）。

**失效条件**：**对比强调**会临时把功能词变重（`I said **A** ring, not **THE** ring.`）；
代词在句尾或情感中心上可以重。★ **这时功能词落强拍是对的，但你必须说得出它在对比什么。**

### 2.3 ★ 功能词落强拍：为什么是硬伤，四种改法

**强拍是聚光灯。** `lw-rhyme` §1 已论证韵脚位置是 HOT SPOT；
**强拍是同一件事的节奏版本——被强拍照到的词，必须值得照。**

**自检动作（强拍列测试）**：★ **把每个强拍位置上的词单独抄成一列，只读这一列。**
读下来是一串实词、大致读得出这首歌在讲什么 → 节奏骨架对了；
读出来是 `the / of / and / that / to` → **骨架全浪费了。**
> ★ 这和 `lw-rhyme` §1 的"韵脚列测试"是**同一个动作的两条轴**：
> 一条查韵落在哪，一条查拍落在哪。**两条都要做，不能互相顶替。**

★ **《Lyrics: Writing Better Words for Your Songs》p0101 把这条写成了可直接照抄的规则**：

> **如果发现 `the` / `of` / `a` / `at` / `to` 落在强拍上，说明词与旋律的匹配需要调整。**

**同页的演示**（`The sun comes up on a bright new day`）：
`the` 落小节第一拍 → ❌；`The sun` 落三四拍、把 `comes` 顶进下一小节强拍 → ❌ 一样错；
★ **`sun` 落第一拍、旋律从前一小节最后一拍唱 `the`** → ✅ **这就是弱起（pickup）**。
★ **这就是英文作词里弱起到处都是的原因——英文句子的开头常常是功能词。**

**四种改法（从便宜到贵，优先级永远是 1 → 4：先动词的落位，最后才动旋律）**：

1. ★ **加弱起（pickup）**——把整句往前挪，让功能词落在弱拍、实词顶上强拍
2. **换一个同义实词，音节数对得上**：`the sound of rain` → `the rain came down`
3. **删掉那个功能词**（英文歌词允许比散文更省）：`I was walking down the road` → `Walking down the road`
4. ★ **改旋律**：挪那个音符的位置或时值（先曲后词时最贵）→ **库一** `mc-melody`

**失效条件（故意错位是一种手法）**：
★ **错位通常显得笨拙，但在特定语境下能产生 playful / comic / endearing 的效果**
（同书 p0101；实例：把 `badminton` 唱成移位的 `bad-min-ton`，
把三音节的 `endlessly` 唱成四音节的 `en-der-less-ly`）。
★ **前提是听众能听出你是故意的**——偶一为之、且和歌的口吻一致。

### 2.4 单音节词连用：不是"敲击感"，是"慢下来"

英文的默认步子是**二拍子 `da DUM`** 或**三拍子 `da da DUM`**
（Pattison《Writing Better Lyrics》Exercise 16 把这两种步子并列作为练习）。
**一串单音节实词会让相邻音节全变成重音**——诗学里叫**扬扬格（spondee，`TUM TUM`）**。

★★ **中文作者最容易在这里误判**：
直觉以为"全是重音 → 密 → 快"。**恰恰相反。**

> **spondee 是两个同等重音的音节，它比扬抑格或抑扬格发音更慢，起"拉伸时间"的作用。**
> 处理严肃主题（疲惫、悲伤）时，**spondee 迫使歌手放慢速度，提醒听众严肃回应。**
> （Davis《Craft of Lyric Writing》p0245；例：`SOME-WHERE … SOME-HOW …`）

★ **同书 p0242 的呼应观察**：
**快乐时节奏加速、用多音节词（`sensational`）；悲伤时节奏放缓、用单音节词（`too bad`）。**

★ **完整的音步表与"音步和意思打架"的两个反例见 [reference.md](reference.md) §2。**

**是优点时**：严肃、疲惫、悲伤、决断、庄严的位置。
**是毛病时**：轻快飞奔的段落里连出四五个单音节实词——**情绪和节奏打架**。

**自检动作**：把这一行**按拍子念**（不唱）；速度感和情绪对不上 → **改音步，不要改速度**。

**失效条件**：★ **说唱、口号型副歌、行进感强的曲风里，密集单音节正是要的东西** → `lw-rap`。

### 2.5 缩写与口语省音：它们怎么改变音节数

- `going to` → `gonna`：**3 → 2** ★ 省一个音节，**并且把剩下的收尾变成弱音节**
- `want to` → `wanna`：**2 → 2** 音节数不变，**但 `-na` 比 `to` 更弱**，更容易挂在弱拍上
- `them` → `'em`：**1 → 1** ★ 音节数不变，**重量变了**——`'em` 几乎不能承重，只能上弱拍
- `-ing` → `-in'`：**不变** ★ **改的是韵不是拍**（→ `lw-rhyme` §5.2）
- `I am` → `I'm`、`do not` → `don't`：**2 → 1** 标准缩写，几乎所有语域都成立

★ **完整省音表（含古语式省音的警告）见 [reference.md](reference.md) §4。**

★★ **关键判断：省音是"降一个音节并把它降成弱音节"，不是"随便少算一个字"。**
`gonna` 之所以好用，是因为它**恰好把一个功能词从强拍上拿走了**。
★ 它同时是一种**语域变化（change of register）**，
在合适的语境里"俏皮而富有表现力"（《Lyrics: Writing Better Words for Your Songs》p0057）。

**失效条件（语域）**：
- ★★ **语域跳错是灾难性的**。同书 p0055 举 Des'ree《Life》为例：
  歌手说宁愿吃一片吐司也不愿见鬼——**从严肃突然跌进滑稽（bathetic）**。
  **口语省音把语域往下拉，用在庄重、古典、宗教、正式叙事的词里会出同样的事**
- **同一首歌里要一致**：前一段 `going to` 后一段 `gonna`，听众会以为你在凑音节（事实也是）

**自检动作**：把省音处**改回全写**再念一遍。
全写版本更像这个角色会说的话 → **你是在凑音节，不是在写口语。**

### 2.6 ★ 多音节词本身就是个坑

《Lyrics: Writing Better Words for Your Songs》p0062 列了两条纯发音层面的理由：
★ **多音节词唱起来笨拙**（占掉好几个音符、重音又不能动，**落位自由度接近零**）；
★ **难听清，现场尤其**。同书 p0056 补了更硬的一条：
**歌手普遍咬字不清，一个词的最后一个音节往往听不清，元音比词尾重要。**

> ★★ **合起来一条实用纪律**：**一行里最要紧的那个意思，不要放在这行最后一个弱音节上**——
> 放在**重读音节上**，最好还在**长音符上**。

**失效条件**：**音乐剧、喜剧、讽刺、说唱**里，长多音节词与炫技咬字本身就是卖点
（→ `lw-musical-theatre` / `lw-rap`）。

---

