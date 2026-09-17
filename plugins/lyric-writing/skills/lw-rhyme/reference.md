# 押韵检索参照表（lw-rhyme reference）

> 本表只服务英文（及其他重音语言）的韵脚检索。
> **中文的辙口与韵部不在这里** → `lw-mandarin`；粤语 → `lw-cantonese`。
> 主文见 [SKILL.md](SKILL.md)。**读本表之前先读 SKILL.md §2 的稳定度尺度。**

---

## 1. 为什么辅音可以互换：语音亲属关系

**元音是发声体（tone generators），辅音是围着它的过滤器。**

两个辅音只要共享下面任意一条，就算**语音相关（phonetically related）**：

1. **同一种发声技巧**（都是爆破音／都是摩擦音／都是鼻音）
2. **同一个发声位置**
3. **声带用不用**（浊 / 清）

**把元音之后的辅音换成它的语音亲属 → 得到家族韵。**

★ **判据**：两个辅音**既同家族、又额外是 Partner 或 Companion 的**，
才是更好的完美韵替身。

| 关系名 | 含义 |
|---|---|
| **Partners（伙伴）** | **发声位置相同**，只差声带用不用 |
| **Companions（同伴）** | **清浊相同**，位置不同 |

---

## 2. 三类辅音与它们的横向家族

### 2.1 爆破音 Plosives

> 气流被堵住、压力积起来、炸开。

| | 唇 | 舌尖抵硬腭 | 舌中抵软腭 |
|---|---|---|---|
| **Voiced 浊** | b | d | g |
| **Unvoiced 清** | p | t | k |

- **Partners**（上下同列）：`b = p`、`d = t`、`g = k`
- **Companions**（左右同行）：浊组 `b, d, g`；清组 `p, t, k`
- ★ **搜索顺序：先 Partners，再 Companions，最后剩下的爆破音**

**演示（`rut`，短元音 ＋ 清爆破音 t）**：

| 步骤 | 查什么 | 结果 |
|---|---|---|
| 0 完美韵 | 短音 + t | rut, cut, glut, gut, hut, shut |
| 1 **Partner** | 短音 + d | blood, flood, mud, stud, thud |
| 2 **Companions** | 短音 + k / + p | buck, duck, luck, muck, stuck, truck；up, hard-up, make-up |
| 3 剩下的爆破音 | 短音 + b / + g | club, hub, pub, scrub, tub；bug, jug, lug, plug, shrug, snug, tug |

★ **家族韵大约给出 5 倍于完美韵的候选。**

#### ★ g 的脾气

g 在口腔后部发音，会改变多数**短元音**的听感，**短元音 + g 不能当完美韵替身**：

| 不成立 |
|---|
| hag ≠ hat（短 a） |
| egg ≠ ebb（短 e） |
| big ≠ bid（短 i） |
| log ≠ lob（短 o） |

**可用的**：长 a（vague）、长 e（league）、长 o（vogue）、长 u（fugue）、短 u（rug）。
**例外**：`fraud` / `hawk` / `fought` 那个 o 音可以用来扩 `log`。

> **口诀：Long — yes. Short — no.**

### 2.2 摩擦音 Fricatives

> 把气流出口收窄，磨出摩擦声，像漏气的管子。

| | | | | | |
|---|---|---|---|---|---|
| **Voiced 浊** | v | TH（baTHe） | z | zh（beige） | j（judge） |
| **Unvoiced 清** | f | th（faith） | s | sh | ch |

- **Partners**（上下同列）：`f = v`、`th = TH`、`s = z`、`sh = zh`、`ch = j`
- ★ **搜索顺序与爆破音相反：先 Companions（同清浊那一行），再 Partner，再 Partner 的 Companions**
- **为什么反过来**：摩擦音发音时间长，清浊差别听得更清楚；
  而它们在口腔里的位置比爆破音集中得多

**演示（`safe`，长 a ＋ 清摩擦音 f）**：

| 步骤 | 查什么 | 结果 |
|---|---|---|
| 0 完美韵 | 长 a + f | safe, waif（很少） |
| 1 **Companion** | 长 a + th | faith |
| 2 **Companion** | 长 a + s | case, ace, chase, commonplace, disgrace, embrace, face, grace, lace, race, space, breathing-space |
| 3 **Partner** | 长 a + v | behave, brave, cave, grave, shave, slave, wave |
| 4 **Partner 的 Companions** | 长 a + TH / z / j | bathe；blaze, craze, daze, haze, maze, phrase, paraphrase, praise；age, cage, page, rage, stage |

★ 摩擦音家族韵**至少把候选翻四倍**。
★ 注意它带来的意外：`daze` 一旦离开惯常搭配 `haze`，立刻新鲜。

**这一步要剔掉的**：`erase`、`trace`、`crave`、`forgave`（及物动词，放韵脚位置句子会瘸）、
`gave`（太平淡）、`lineage`（次重音改变了声音）。

### 2.3 鼻音 Nasals

> 声音全部从鼻子出来。**鼻音全是浊音，所以只有 Companions。**

| m | n | ng |
|---|---|---|
| 双唇闭合，口腔当共鸣腔 | 舌尖抵硬腭，半个口腔当共鸣腔 | 舌中抵软腭，口腔完全不参与 |

- **Companions**：`m`、`n`、`ng` 互为同伴
- 它们的口型对应爆破音（m↔b、n↔d、ng↔g），只是气流走鼻腔

**演示（`home`，长 o ＋ m）**：

| 步骤 | 结果 |
|---|---|
| 0 完美韵 | home, catacomb, comb, hippodrome, honey-comb, Nome（避开 `roam`：陈词滥调） |
| 1 **Companion（m → n）** | blown, bone, chaperone, cornerstone, gramophone, grown, throne, undertone, zone |

★ `alone` 对 `home` 是陈词滥调，**即使严格派也这么认为**。

#### ★ ng 的限制

- **ng 从不跟长元音**（Pattison《Essential Guide to Rhyming》p0004）
- 只跟两个短元音：短 o（gone / wrong）、短 u（fun / rung）
- 这条限制决定值不值得去查：目标词落在短 o、短 u 之外，ng 家族韵直接跳过，查了也是白查（p0004）
- **鼻塞测试**：捏住鼻子念 "I sing songs that ring wrong"，ng 会被挤成 g，听起来像 "I sig sogs that rig wrog"。
  这只用来验证 ng 和 g 同属软腭发音位置，不代表 ng 可以直接当 g 的韵脚替身用（p0004）
- 多数时候帮不上忙，**但一旦用得上，效果显著**

### 2.4 l 和 r

- ★ **l 和 r 本身没有有用的家族替身**
- 但它们与别的辅音组合时，**搜索反而更容易**——因为 l、r 的声音很强，
  后面再挂的辅音几乎听不出来

**演示（`hurt` = r + t）**：

| 换 | 结果 |
|---|---|
| t → d（Partner） | absurd, gallows-bird, stirred, word；blurred, deterred, preferred, purred, slurred |
| t → p（Companion） | burp, twerp |
| t → k（Companion） | jerk, quirk, smirk, dirty-work |
| t → b / g | curb, iceberg, suburb |

**演示（`help` = l + p）**：

| 换 | 结果 |
|---|---|
| p → d | unparalleled, weld；compelled, propelled, quelled, rebelled, shelled |
| p → t | felt, heart-felt, melt |

★ `help` 本来几乎无韵可押，扩到这个程度已经很值。

### 2.5 音节末尾不止一个辅音

**方法**：逐个辅音找家族韵，或者同时换。

★ **规则：第一个辅音若是清音，后面跟的辅音通常也清。**
所以换到浊摩擦音那一侧时，末尾的 `t` 音会变成 `d` 音。

**演示（`fast`）**：保持 s，动 t → `clasp, gasp, grasp, rasp`；`ask, flask, mask, task`；
进到浊摩擦音 → `jazzed, razzed`。

★ **音节末尾有两个以上辅音时，候选量增长得最快。**

---

## 3. 纵向家族（同一舌位）——给头韵用

**横向家族按气流方式分（上面第 2 节），纵向家族按舌位分。**
纵向家族用来扩展**头韵（alliteration）**，不是用来押尾韵的。

| M 家族（唇／舌平） | N 家族（舌尖抵硬腭） | NG 家族（舌中抵软腭） |
|---|---|---|
| b | d | g |
| p | t | k |
| v | j | x |
| f | ch | y |
| w | l | |
| | z | |
| | s | |

*（表内从紧密到较远排列。）*

**例外**：`TH` / `th`（舌触上齿）不属于 M 也不属于 N；`r` 不属于任何纵向家族。

★ **隐蔽头韵（concealed alliteration）**：头韵不限于词首，
**词中（medial）与词尾（terminal）的同家族辅音一样在连**。

---

## 4. 开元音与加音／减音

### 4.1 开元音 Open Vowels

**重读元音后面没有辅音的词。** 除 `papa` 的 ä 外都是长元音：

| 长 a | ä | 长 e | 长 i | 长 o | 长 u |
|---|---|---|---|---|---|
| play | papa | free | die | go | few / shampoo |

- 阳性韵里，开元音排在每个元音段的**开头**
- 阴性韵里，按**非重读音节开头的辅音**排序：
  `data` = 长a + ta；`viva` = 长e + va；`riot` = 长i + ot；`heroic` = 长o + ik；`stupid` = 长u + pid
- ★ **开元音韵被用得太多，大半已成陈词滥调**——这正是需要完美韵替身的地方

### 4.2 加音韵 Additive：加什么最不显

**加得越少，越像完美韵。** 按"越往下越明显"排：

| 顺序 | 加什么 | 说明 |
|---|---|---|
| 1 | **浊爆破音** b, d, g | 发音时间最短，最不显 |
| 2 | **清爆破音** p, t, k | |
| 3 | **清摩擦音** f, th, s, sh, ch | 摩擦音比爆破音持续时间长 |
| 4 | **浊摩擦音** v, TH, z, zh, j | |
| 5 | ★ **鼻音** m, n, ng | **除 l、r 外最明显，尽量别加** |
| 6 | 多个辅音一起加 | 最远（`free` / `dreams`） |

**补充规律**：**发音位置越靠口腔前面，越不明显。**

**演示（`free`）**：+d → bleed, greed, speed, seed；+p → deep, asleep, cheap, weep；
+t → bittersweet, deceit, defeat（名词）, elite；+k → bleak, speak, weak；
+f → belief, relief, thief；+s → peace, police, release。

★ **判断一个加音韵够不够稳，看两件事**：
**多出来的辅音有多显眼**，以及**那个音节的音符有多长**。
音符长 → 元音被拉满 → 多出来的辅音就藏得住。

#### r 和 l 结尾的特权

这两个音本身很强，和元音结合之后，**再加的辅音几乎察觉不到**：

| 基准 | 可以押 |
|---|---|
| scar | heart, dark, tarred, guard, charge, hearth |
| Jezebel | unparalleled, help, knelt, svelte, wealth |
| star | arms |
| war | endorsed |

#### 及物动词的解法

`erase` / `trace` 需要宾语，直接放韵脚位置会瘸：

> ❌ As if my heart you could **erase**
> ✅ As if my heart could be **erased**

★ 加 `-ed` 变被动就顺了，**代价是主动语态比被动有力**。
（读音细节：前面的清音 s 会把最后的 d 读成 t。）

### 4.3 减音韵 Subtractive

**加音韵反着做**：从一个带两个辅音的音节里**减掉一个**，再查剩下部分的完美韵。

**演示（`fast`）**：

| 做法 | 结果 |
|---|---|
| 减掉最不显的 t | 查 `as` → class, mass, lass, pass |
| 保留 s、在 t 的家族里找 | clasp, ask |
| 在 s 的摩擦音家族里加 t | draft |
| 直接找 `as` 的家族韵 | dash, wrath, laugh |

★ `fast` / `dash` 是个漂亮的连接：不是陈词滥调，**又当得起完美韵替身**。

**长元音 + 单个辅音**可以直接削到开元音：`treat` / `free`。

### 4.4 家族加音 Family Additives

找家族韵的时候**顺手留意加音韵**：`condemn` / `defend`；`love` / `bluffs`；
`trip` / `risk`；`ache` / `saint`。

★ **陷阱**：有时多出来的辅音**位于家族辅音之前**（`ache` / `saint`），
按字母顺序在韵典里翻不到，**只能靠自己留神**。

---

## 5. 最远的几类：怎么找

| 韵型 | 怎么找 |
|---|---|
| **元音韵 Assonance** | ★ **最宽的一次搜索**：凡是以目标元音打头的列全看一遍。`tide` → life, isle, climb, brine, life-line, rise, survive, revive |
| **阴性元音韵** | 在阴性长元音段里找非重读音节以 i／li／ing 收的词。`lonely` → approaching, probing, foreboding, coldly, imposing, consoling, ghostly, voting |
| **辅音韵 Consonance** | 韵典里每个元音段都按尾辅音字母排——**把这个尾辅音下面所有元音段都看一遍**。`love` → grave, have, leave, thrive, forgive, rove, groove |
| **部分韵 Partial** | 先定一个阴性词，去阳性段找能押它**重读音节**的词，**弱音节不管** |

### ★ 辅音韵的可用度排序（从最能听见到最难听见）

| # | 类型 | 例 |
|---|---|---|
| 1 | **阴性辅音韵** | cramming / rubber；teeming / fibber |
| 2 | **含 r 或 l 的阳性辅音韵** | scare / pull / snarl；fear / fall / curl |
| 3 | **多辅音收尾的阳性辅音韵** | ranch / fast / crypt；lynch / rest / slept |
| 4 | **鼻音收尾的** | stun / came / song；ran / scream / ring |
| 5 | **浊摩擦音收尾的** | grave / rage / cause；reprieve / badge / whiz |

★ 排序的道理：**能拖长的、浊的、声音大的辅音，在唱的时候才听得见。**
辅音韵在诗里常见，因为诗是念的；**在歌里，辅音的连接必须非常强才听得到**。

★ **Pattison 的手背规则（back of the hand rule）**：
当你说的话允许你喊一声 "Alas!"、用**手背**拍额头表示悲伤时，**可以用辅音韵**。

---

## 6. 元音三角形（给可唱性用）

**元音按嘴的做法排成三角**：

```
                 ä (papa)  ← 顶点，最开放
            /              \
   舌元音（左腿）           唇元音（右腿）
   舌向硬腭抬起              嘴唇收圆、渐闭
```

- **测试**：说一声 "Yeow!"，从极端唇元音扫到极端舌元音
- **双元音**不在三角上，是三角上两个（或更多）声音的组合：
  长 a = 短 e + 长 e；长 i = ä + 长 e；长 o = 短 o + 长 u；oi = 短 o + 长 e；ou = ä + 长 u

### 用法

| 场合 | 怎么选 |
|---|---|
| **音域极高／极低处，或跨换声点** | ★ **用越靠近顶点的元音越好唱**，喉咙更放松 |
| **长 i 这类双元音** | 唱的时候保持**第一个**声音（ä）——所以它是过换声点最好用的元音之一 |
| **长 u（few）** | 唱的时候保持**第二个**声音（oo） |
| **情绪色彩** | 唇元音整体更温暖（"Hold me close"）；舌元音更硬更冲（"Hold me tight"） |

★ 这一节直接连到 `lw-english` 的可唱性，以及库一 `mc-melody` 的最高音落点。

---

## 7. 声部进行（voice leading）与连接点（juncture）

**这两项不影响韵式结构，但决定一行词唱起来顺不顺。**

### 7.1 Assonance 的两种身份 —— ★ 别搞混

| 用在哪 | 是什么 | 效果 |
|---|---|---|
| **连接乐句末尾** | **元音韵（Assonance Rhyme）** | ★ **影响结构**，见 SKILL.md §2 |
| **短语内部的词与词之间** | **声部进行技巧（Voice Leading）** | ★ **不造结构、不造加速**，只把词黏顺（`lazy days away`、`free and easy`） |

★ **一句话**：**内韵是激活器，元音声部进行是抹平器。**

### 7.2 三种元音连接

| 名称 | 说明 |
|---|---|
| **Simple assonance** | 直接重复同一个元音 |
| **Hidden assonance** | ★ 重复的元音藏在**双元音内部**或被邻近的 l／r 盖住（`Play head games` 里三个词都有短 e） |
| **Family assonance** | 在元音三角上**移动一步**——对应和声里"非共同音走最小音程" |

### 7.3 头韵（Alliteration）

- **传统定义**：相邻或紧密相连的词开头出现相同的辅音（Pattison《Essential Guide to Rhyming》p0007）
- **不限词首**：词中（medial）、词尾（terminal）出现同一个辅音，一样算头韵在连；能不能连得上看的是第 3 节的纵向家族表，不是死记词首字母（p0007）
- **例证**（Eliot，《The Love Song of J. Alfred Prufrock》）：
  > I have seen them riding seaward on the waves / Combing the white hair of the waves blown back / When the wind blows the water white and black
  三行里 s、w、r 三个音轮流出现在词首、词中、词尾，互相接力，没有一处是孤立的重复（p0007）
- **隐藏头韵（Concealed Alliteration）**：借纵向家族表把头韵的范围从"同一个辅音"扩到"同一个舌位"，扩法和第 3 节用横向家族扩韵脚是同一个道理（p0007）
- **例证**（Tennyson，《Ulysses》）：`The long day wanes: the slow moon climbs: the deep / Moans round with many voices.`
  b 和 d 的头韵把几个词粘出"循环"的暗示，d 又给 n 挂上一层隐藏头韵；最后一行的重读音节全部落在鼻音上，像风笛的持续低音，把别的声音焊在同一个音色上（p0008）
- ★ **警告**：过度铺排的头韵很快变得陈旧、抢戏。**内部头韵通常最有效**

### 7.4 连接点 Juncture

**一个词的收尾怎么流进下一个词的开头。**

| 类型 | 说明 |
|---|---|
| **Legato 平滑** | `an apple`、`a pickle`——英语有 a / an 两个不定冠词就是为了这个 |
| **Staccato 粗糙** | ★ 前一个词的尾音与后一个词的头音**相同**时产生，必须停顿 |

**代价示例**：

> She can't take your rent.

`can't → take`、`your → rent` 两处都卡。硬要唱顺，听成 "She can take your ent."——**意思反了**。
只能停：`She can't (停) take your (停) rent.`

`old dog` 要么读成方言 `ol' dog`，要么强行停顿；**换成 `old hound` 就绕过去了**。
其他会出事的：`save victory`（听成 `say victory`）、`stun none`、`free ether`。

★ **Staccato juncture 也能当效果用**——需要"卡住"的地方故意让它卡。

★ **总原则**：**让句子平滑、可唱。歌手会感谢你。**

### 7.5 断裂本身也是表达

Matthew Arnold "Dover Beach" 的那一行：

> Begin, and **cease**, and then again begin …

意思是"浪停一下再继续"，声音却因为鼻音连成一片而不肯停。
`cease` 的价值在于**它把声部进行打断了**——
"It is the break in the Voice Leading that is expressive."
（比 `end`、`stop`、`pause` 都好，而且 `cease` 听起来就像浪打在滩上。）

★ **原则**：**Reasons for choosing. Choosing for reasons.**
把自己放到"有好几个备选"的处境里，再说清楚为什么挑这个。

---

## 附：来源

- **语音家族表、逐类搜索顺序、g 与 ng 的限制、l/r 的特权、及物动词解法、开元音、
  加音／减音／家族加音、辅音韵可用度排序、手背规则、元音三角形、声部进行与连接点**：
  Pattison《Essential Guide to Rhyming》（、pattison-eg）
- **纵向家族表与隐蔽头韵**：同上
- ⚠ 本表只适用于英语。中文见 `lw-mandarin`，粤语见 `lw-cantonese`
