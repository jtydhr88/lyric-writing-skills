---
name: lw-rap
description: Writing the words of a rap (说唱的词本身), not how the vocal sits in the beat. Rhyme density - how many rhymed syllables per bar and what it costs in intelligibility; multisyllable and compound rhymes, assonance, consonance, bent words, internal rhyme; rhyme schemes from couplet to whole-verse and where the rhyme lands; content forms (braggadocio, battle, concept, story, abstract, humorous) and line-level tools (punchline, wordplay, double meaning, simile, extended analogy); vocabulary, slang and its shelf life, rhyme-driven versus meaning-driven writing; the writing order MCs actually use (flow first or words first, freestyle, editing); and a transfer table for Mandarin rap, where one character is one syllable and every syllable carries a tone. Use when writing a rap verse or hook, turning an existing lyric into rap, when rhymes feel thin or predictable, when a verse rhymes well but says nothing, or when adapting English rap technique to Chinese. 说唱、rap、押韵密度、多音节韵、内韵、punchline、flow、中文说唱、改成说唱、韵脚、battle、叙事说唱。
---

# 说唱的词（Rap Lyrics）

> **本 skill 只管词本身。**
> 人声在编曲里怎么摆、delivery 怎么分配、flow 怎么记谱、beat 怎么做——**全在编曲库 `mc-style-hiphop`**。

两边共用同一批底本，分工是一刀切的：

```
编曲库 mc-style-hiphop  ──  音节落在哪一拍、哪一拍休止、用哪档声音说
本 skill  lw-rap        ──  那些音节是什么字、押几处韵、押的是什么、说的是什么
```

★ 交界处只有一件事要对齐：**押韵落点**。
编曲库从"落 4 拍还是落弱拍"这一侧写它，本 skill 从"这一行要押几个字"这一侧写它，
**记谱一律用编曲库 `mc-style-hiphop` reference §3.1 的 flow diagram，本 skill 不另造一套。**

## ★ 这个 skill 与本库其他 skill 最大的不同

> **rap 的词是按"每小节能塞多少音节"写的，不是按"一句好听的话"写的。**

《How to Rap》把这件事说得最直接：歌手可以拖着一个音唱很久，
"I love you" 三个词能撑起一整段 verse；**同样的词量在 rap 里连半小节都占不满**（p0125）。
所以 hip-hop 一首歌要写的字数远多于其他流派（《How to Rap》p0124）。

两个后果，贯穿全篇：
1. **密度是第一参数**——先定每小节几个音节、其中几个押韵，再谈写什么
2. ★ **押韵不是修饰，是结构**——韵把行与行连起来，韵式就是段落的骨架（§4）

## 按任务读哪几节

| 任务 | 读 |
|---|---|
| 第一次写 rap 词 | §1 → §2 → §8 |
| 韵听着单薄、太好猜 | ★ §2、§3 |
| 押得很密但听不懂 | ★ §2.4 可懂度的代价 |
| 韵押得漂亮但没说什么 | §5、§6 |
| 要写故事型 / battle / 概念曲 | §5 |
| 要 punchline | §6.3 |
| 不知道先写词还是先定 flow | ★ §8.1 |
| 把一段现成的词改成说唱 | ★ §8.4 |
| 中文说唱 | ★ §9（**必读**，英文那套有一半不能直接搬） |
| 要大表（韵式、内容形式、MC 并排说法、中文韵脚料） | `reference.md` |

## 边界

| 不归这里 | 归哪 |
|---|---|
| **人声在编曲里的位置、进退场、和伴奏的密度互让** | **编曲库 `mc-style-hiphop` §7.5** |
| **delivery 参数**（音高档、音量档、音色、staccato、气声、ad-lib） | **编曲库 `mc-style-hiphop` §7.3** 与其 reference §4 |
| **flow 怎么记谱、音节怎么落在 16 分网格上、休止与换气位置** | **编曲库 `mc-style-hiphop` §7.2** 与其 reference §3 |
| **beat 怎么做、采样、808、速度区间** | **编曲库 `mc-style-hiphop`** |
| 通用押韵原理：韵家族、韵的意外度、什么时候故意不押 | `lw-rhyme` |
| 十三辙、普通话韵表、平仄 | `lw-mandarin` |
| **中文字调与旋律/语调的冲突（倒字）** | `lw-tone-check`（★ 半唱型 hook 一定要过这一关，见 §9.4） |
| 这首歌要说什么（立意五问） | `lw-song-intent` |
| 具体名词、object writing | `lw-imagery` |
| 段落功能、hook 放哪、副歌变奏 | `lw-structure` |
| 粤语说唱的协音 | `lw-cantonese` |

---

## 1. 三个刻度：rap 的词和流行歌词差在哪

**动笔前先把这三个数定下来，它们决定后面一切。**

| 刻度 | 问什么 | 常见取值 | 定不下来时 |
|---|---|---|---|
| **音节密度** | 一小节放几个音节 | 8–16（16 分网格为主，见编曲库） | 先跟着 beat 哼无意义音节数出来（§8.2） |
| **押韵密度** | 这些音节里几个是韵 | 每小节 1 → 11（§2） | 从每小节 2 处起步 |
| **可懂度目标** | 听众第一遍要听懂多少 | 全懂 / 懂大意 / 只要好听 | 看内容形式（§5）——故事型必须全懂 |

★ **三者互相制约**：音节密度高 + 押韵密度高 → 可懂度必然下降。
**这不是缺陷，是选择**，但必须是**被选过**的（§2.4）。

**失效条件**：这三个数没定就开始写词 → 写出来的行长短随机、韵位随机，
到了 beat 上必然要大改。

---

## 2. 押韵密度

### 2.1 它从哪来：rap 的韵比流行歌词密一个量级

早期 hip-hop 的韵只出现在**乐句末尾的连接词**上——
《How to Rap》举的例子里，两小节只有 "mine" 和 "rhymes" 两个押韵音节（p0118）。
后来 MC 开始往每小节里填韵：

| 说法 | 是谁说的 | 出处 |
|---|---|---|
| Rakim 之前大家只押句尾词；Rakim 演示了**"put rhymes within a rhyme"**（韵里面还有韵）；Big Daddy Kane 扩到**每句 7–8 个押韵词** | Masta Ace | 《How to Rap》p0118 |
| 我试着**每小节押两个词**，普通 rapper 每小节押一次——这等于写作量翻倍，难度极大 | Termanology | 《How to Rap》p0119 |
| 我喜欢**整行押**，不是只押最后两个音节；押 4、5、6、7 个音节都行 | Rah Digga | 《How to Rap》p0119 |

**一个可以直接当尺子的实例**：Kool G Rap《Know Da Game》——
第一小节 4 个押韵音节（blown / home / zone / roam），
第二小节 7 个（flown / dome / blow / chrom- / -o- / -somes / bones），
**两小节共 11 个押韵音节**（《How to Rap》p0118–p0119）。

★ **拿它当上限刻度**：11/2 小节是高密度那一端；每小节 1 处是 1980 年代那一端。
**你要写的那首歌落在这条线的哪里，是一个必须做的决定。**

### 2.2 韵押在哪些位置

| 位置 | 效果 | 出处 |
|---|---|---|
| **行尾**（落 4 拍） | 最常见、最显眼 | 《How to Rap》p0120 |
| **行中（内韵）** | 落在非重拍音节上时不显眼，**更像对话** | 《How to Rap》p0120–p0121 |
| **跨拍、跨小节** | Nas《N.Y. State of Mind》的 "funky rhythm" 从 4 拍前开始延到下一个弱拍；"I be kicking" 从第一小节延进第二小节 | 《How to Rap》p0121 |
| **整行**（行内多处都押） | 极高密度，Rah Digga 的做法 | 《How to Rap》p0119 |
| **整段挪位** | Tajai：开头加几个词、结尾删几个词，把整段"挪过去"（scoot it over），韵就落到意想不到的位置 | 《How to Rap》p0122 |

★ **跨小节的韵怎么算归属**（《How to Rap》p0121–p0122 给了判定规则，写词时按它数韵）：
- 下一小节**继续同一个韵** → 两小节合并成一个 couplet（Nas 的例子：musician / inflicting / composition 接上）
- 下一小节**换了新韵** → 溢出的部分只算上一小节的（B.I.G.《Ready to Die》：material / imperial 溢出，但第二小节由 ripper / stripper / sipper 主导）

★★ **落点的记谱不在本 skill**：要把"这个韵压在第几拍"写下来，
用**编曲库 `mc-style-hiphop` reference §3.1 的 flow diagram**（四拍一行、重音加粗、空位即休止）。
本 skill 只负责决定**那一格填什么字**。

### 2.3 密度是可以变的，而且变化本身是信号

| 手法 | 说明 | 出处 |
|---|---|---|
| 段内递增 | Dray（Das EFX）开头平静，到第 6–8 行才上更复杂的 flow | 《How to Rap》p0119 |
| 跟着伴奏加倍 | El Da Sensei：鼓滚奏、额外军鼓会促使你在那里**把韵加倍**，以保持听众兴趣 | 《How to Rap》p0119–p0120 |
| 突变当段落标记 | 从每小节少韵切到多韵再切回，**本身就是段落信号** | 《How to Rap 2》p0203 |

★ **自检动作**：把整段每小节的押韵音节数写成一串数字（4, 7, 4, 3, 3, 6 …）。
**如果这串数字从头到尾一样，你写的是练习不是歌。**

### 2.4 ★ 密度的代价：可懂度

**密度不是越高越好，这是本节最重要的一条。**

| 你选的 | 得到 | 失去 | 什么时候选它 |
|---|---|---|---|
| **高密度**（每小节 5 处以上） | 技术冲击、"抓耳" | 听众第一遍抓不住意思 | battle、braggadocio、要展示 flow 的曲子 |
| **中密度**（每小节 2–3 处） | 既有韵感又跟得上 | 不会让人惊叹 | 大多数歌 |
| **低密度**（每小节 1 处或更少） | **内容听得清清楚楚** | 技术上不显眼 | ★ **故事型、conscious 型**（§5.2、§5.4） |

《How to Rap》p0122 把这条写成了一个直接的取舍：
**内容特别强的时候，用更简单一致的押韵技术（大部分韵落 4 拍）反而更能突出内容**；
**想展示 flow 的时候，才用多变的韵位和复杂韵式。**

R.A. the Rugged Man 建议**两种都做**：一首不断变换韵式的，一首保持同一个 flow 专门展示歌词能力——
他举 Redman：《Rated R》保持同一 flow 展示词，《Green Island》那类则展示多种 flow（《How to Rap》p0122–p0123）。

★ **自检动作（可懂度测试）**：把 verse 念给一个没看过词的人听一遍，
让他复述**这一段发生了什么**。复述不出来而这首歌是故事型 → **降密度**。
是 battle 型 → 不降，但确认 punchline 那一行是听得清的（§6.3）。

**失效条件**：hook 不适用高密度。hook 的词要比 verse 简单、密度低、拖长一点
（编曲库 `mc-style-hiphop` §7.4 给了结构数字）。

---

## 3. 韵的种类：多音节韵与近似韵

### 3.1 五种基本韵（这一层是通用押韵原理，`lw-rhyme` 讲原理，这里只列 rap 的用法）

| 种类 | 定义 | 例 | rap 里的地位 | 出处 |
|---|---|---|---|---|
| **完美韵** perfect rhyme | 两词结尾完全相同 | cat / hat，mug / plug | 早期主力；**重复同一个词现在也算完美韵**——过去被视为 corny，现已广泛接受 | 《How to Rap》p0095–p0096 |
| **元音韵** assonance | 元音相同、周围辅音可不同 | fit / hip，cat / back | ★ **当代 hip-hop 用得最多的一种**，因为它最灵活、可组合的词最多 | 《How to Rap》p0097 |
| **弯词** bending words | 元音只是接近，靠**改变发音**把它们弄成一样 | arms / Mom's（Eminem《Lose Yourself》"arms are heavy" / "Mom's spaghetti"）、three / Dre | 让本来不押的词押上 | 《How to Rap》p0098 |
| **头韵** alliteration | 词以相同的音开头 | jimmy / joke，mama / might | 最微妙，**不建立强链接**，只改善整体声音 | 《How to Rap》p0099 |
| **辅音韵** consonance | 辅音相同、元音不同 | sock / sack，cut / cot；"hip-hop" 本身就是 | 加一层流动感，不承担结构 | 《How to Rap》p0100 |

★ **头韵与辅音韵不能当韵式用**——它们不足以把两行连起来（p0099）。
**要连行，得用完美韵、元音韵或弯词。**

### 3.2 多音节韵（compound / multisyllable rhymes）

**定义**：长度超过一个音节的韵，也叫 multies（《How to Rap》p0100）。

★ **这是当代 rap 的默认**：单音节韵（cat / bat / hat）在现代 hip-hop 里已经少见（p0100）。

| 说法 | 是谁说的 | 出处 |
|---|---|---|
| 多音节押韵不是押 "fight / light / with all my might"，是 **"random luck" 对 "handsome fuck" 对 "we cop vans and trucks"**——基础韵**不抓耳** | Kool G Rap | 《How to Rap》p0101 |
| 我尽量找**还没被押过的**押韵词；办法是**把两个词组合起来**去押另一个多音节词 | Speech (Arrested Development) | 《How to Rap》p0101 |
| 一整张专辑都是 cat / bat / hat 就是无聊——**词汇量少，能写的就少** | Masta Ace | 《How to Rap》p0101 |

★ **多音节韵内部可以混用韵种**：Wu-Tang《Triumph》里 "dropping these" 押 "mockeries"——
"these" 和 "-ies" 是完美韵，而 "drop-" 和 "mock-" 是元音韵（《How to Rap》p0100–p0101）。
**这条很重要：整块不必都完美，只要有一处完美韵撑住，其余用元音韵就成立。**

先驱是 Big Daddy Kane 与 Kool G Rap，往下影响了 Eminem 与 Big Pun（《How to Rap》p0101）。

### 3.3 ★ 多音节韵怎么"连起来"：三种链接

**多音节韵块之间长度、重音位置常常不一样，靠什么让听众听出它们是一对？**
《How to Rap》p0102–p0104 给了三种，**这是本节最实用的一张表**：

| 链接方式 | 机制 | 实例 |
|---|---|---|
| **① 用韵连** | 节奏完全不同也没关系，只要押韵音节够强 | Lady of Rage《Unfucwitable》："mic brawler" / "night crawler" / "like I'm off that water"——重音位置完全不同、最后一句音节还更多，但**每块第一个音节押（mic / night / like），每块都以两个押韵音节收尾（brawler / crawler / water）** |
| **② 用节奏连** | 韵只是勉强相似，靠**音节数与重音位置完全一致**建立链接 | Snoop《Nuthin' but a G Thang》："One, two, three and to the four" / "Snoop Doggy Dogg and Dr. Dre is at the door"——开头只靠把 three 和 Dre 弯到一起，但两块**各 5 个音节、重音都在第 1 和第 4 个音节** |
| **③ 部分链接** | 一些零散的词搭在主韵块上，自己不构成完整的多音节韵 | Jay-Z《22 Twos》：主韵块是 "too late to come together" / "too much love equal forever"，另外 "too much" 只连到 "too"，**不完整但照样加韵** |

★★ **②是最被低估的一条**：**找不到合适的韵时，不要硬押，把节奏对齐。**
Nelly 的说法是——先把话说清楚，"you're not worried about if it rhymes"（《How to Rap》p0103–p0104）。

★ **③ 是提高押韵密度最便宜的办法**：不必造新的完整多音节韵，
**把零散的词挂到已有的韵块上**就能让一小节的韵数上去（p0104）。

### 3.4 怎么找到韵

| 方法 | 做法 | 是谁说的 | 出处 |
|---|---|---|---|
| **列表法** | 写词之前先把押韵的词和短语列出来 | Tash："我先想押韵的词，再想这一行" | 《How to Rap》p0105 |
| **字母表法** | 在每一页纸顶上写一遍 A–Z，边写边在脑子里过 at / bat / cat / dat… | Rah Digga | 《How to Rap》p0105 |
| **围着韵造句** | 把所有押韵的词写满一张纸，**再围着这些词造句** | Fredro Starr | 《How to Rap》p0105 |
| **卡住就降级到元音韵** | 押不上完美韵时，去找所有同元音的词 | El Da Sensei | 《How to Rap》p0105 |
| **押韵词典 / 词典** | 查同义词、反义词、词源 | Wildchild、Myka 9（推荐 Roget's Thesaurus） | 《How to Rap》p0105–p0106、p0068 |

★ **避免陈词滥调是主要成本**：Akil the MC——"每件事都有一个词或一种说法，
难的是**不做别人已经做过的**"；Termanology 说为了找一个没人押过的词，
**一段 verse 可能写六个小时**（《How to Rap》p0106）。

**失效条件（韵驱动写作的失效点）**：
Kool G Rap 的警告是最硬的一条——**押韵词不应该决定故事走向**：
"You can't just put whatever comes next that rhymes—the story gotta be right too"
（先决定接下来发生什么，再去找韵，《How to Rap》p0050）。
→ 这条与 §8.3 的"韵驱动 vs 意思驱动"是同一件事。

### 3.5 ★ 不押也是一个选项

**并非所有位置都必须押；有时不押比硬押好**（《How to Rap》p0106）。三个并排的说法：

- **David Banner**："It doesn't necessarily have to rhyme, if the feeling is there."（感觉到位就不必押）
- **Big Noyd**：有些话我就是想说，它可能和上一句不押，**但我为了把话说清楚照样说**（p0107）
- **Bootie Brown**：Prodigy 和 Nas 都不是一直押韵的——"你会觉得，这其实没押，但你不在乎，因为他那个说法太酷了"（p0107）

★ **自检动作**：段落里如果有一行是**整首歌最重要的那句话**，
检查它是不是为了押韵被改过。是 → **把它改回来，让它不押。**

→ "什么时候故意不押"的通用原理见 `lw-rhyme`；这里只写 rap 侧的三条实例。

---

## 4. 韵式：韵怎么变成段落骨架

**定义**：把押韵的词和短语按特定次序排布在整段里，这个模式就是韵式（《How to Rap》p0108）。
MURS 把它比作拼图：押韵的词是碎片，韵式是告诉你碎片该放哪的那张图（p0108）。

### 4.1 五种韵式（按"韵连起几行"分类，《How to Rap》p0112–p0117）

| 韵式 | 定义 | 实例 | 什么时候用 |
|---|---|---|---|
| **couplet** 对句 | 两行由同一个韵连起来 | Beastie Boys《Shadrach》：handle it / candle to it | ★ **最常用、最容易想**；**一整首歌常常就是从一个 couplet 起头的**（p0113） |
| **single-liner** 单行 | 这一行不和别的行押，**行内音节自己互押** | The Game《Put You on the Game》：行内 indo / Timbo | 增加 flow 的多样性（B.I.G. 常用） |
| **multi-liner** 多行 | 三行或更多行被同一个韵连起来 | Public Enemy《Bring the Noise》：one / numb / gun / spun 连四行 | 比 couplet 费时费力，但**flow 的可操作空间更大**；"能押四行就别只押两行" |
| **whole verse** 整段 | 整段所有行用同一个韵 | Busta Rhymes《Put Your Hands Where My Eyes Could See》：heard of us / murderous / curious，16 行同一韵式；Kool G Rap《The Anthem》 | 极难——**要在保持信息清楚的同时写这么多同韵** |
| **extra rhymes** 额外韵 | 在主韵式之外再加一组互押、但不与主韵押的词 | B-Real 在 OutKast《Xplosion》：主韵是 wine / mine 的 couplet，另加 pass / glass | 加密度而不动骨架 |

**组合**（p0114–p0115）：同一段里可以混用。一个被点名的常见配法是
**用 multi-liner 连奇数行、最后补一个 single-liner 凑成偶数行**；
更复杂的例子是"couplet → 8 小节 multi-liner → 5 小节 multi-liner → single-liner 收尾"，合成一段 16 小节。

★ **每行的韵不止一处**（p0117）：couplet 不是"第一行一个韵、第二行一个韵"——
每行都可以有多处互押的成分，**只要同一个韵连着两行，它们都算这个 couplet 的一部分**。
→ 这正是 §2 押韵密度的来源。

### 4.2 韵式怎么选

| 情况 | 选 | 理由 |
|---|---|---|
| 刚开始写这首歌 | couplet | 它常是整首歌的起点（p0113） |
| 想显技术 | multi-liner / whole verse | 需要更多时间和精力，回报是可操作空间 |
| 内容压倒一切 | couplet + 韵落 4 拍 | §2.4 的取舍 |
| 每首歌都一样 | ★ **换** | 《How to Rap》p0109：不同韵式让每首歌听起来独特；词汇量有限的 MC 的标志就是**押韵模式永远相同** |

★ **简单韵式没有错**——像 Melle Mel 那样有才华的话，不必每段都换 flow（p0113）。
**失效条件**：整张专辑只有一种韵式 → 那不是风格，是词汇量不够（p0109）。

### 4.3 与编曲库的交界

**韵落在第几拍是编曲侧的参数**，本 skill 决定的是"这一行有几个韵、押什么"。
两边在 `vocal.phrasing` 上对齐：

- 韵的**落点、休止、换气位置** → 编曲库 `mc-style-hiphop` reference §3.4–§3.5
- 韵的**数量、种类、内容** → 本 skill §2、§3

★ **一条必须知道的反向约束**：beat 若是 3 小节循环，词必须专门为它写——
用 3 行的 multi-liner，或"一对 couplet + 一个 single-liner"，
因为偶数小节的韵式会和音乐的重启点错开（《How to Rap 2》p0203–p0204）。
拍号不是 4/4 时 flow 要重写，韵改落 3 拍（《How to Rap 2》p0070）。

---

## 5. 内容：形式

内容与形式的完整对照（题材类型、battle/boast/storytelling 的惯例与写法）见 [reference.md](reference.md)。

## 6. 内容工具：逐行用的手法

**content form 是歌的骨架，content tools 是逐行使用的具体技巧**（《How to Rap》p0054）。
目标是让每一行都有力量：Guerilla Black——**每个词都要像子弹一样有目的**（p0055）。

### 6.1 比喻三件套

| 工具 | 定义 | 实例 | 出处 |
|---|---|---|---|
| **明喻** simile | 用 like / as 直接比较 | Chino XL《No Complex》："my clique is stoned like their eyes gazed upon Medusa"；Masta Ace："as fake as a tooth-fairy" | 《How to Rap》p0058 |
| **隐喻** metaphor | 不用 like / as，**直接拿被比的事物代替原事物** | Gift of Gab 说 "I'm an ancient Zen master" 而不是 "like an…"；"I'm a chef eating all you carnivores" | 《How to Rap》p0058–p0059 |
| **类比** analogy | **延长的隐喻**，可以覆盖整段、整首甚至整张专辑 | 2Pac《Me and My Girlfriend》表面写女朋友、实际写他的枪，整首构成一个类比 | 《How to Rap》p0059–p0060 |

★ **为什么值得**：一个巧妙的比较**用更少的词传达更多信息**，
而且听众可能要过一会儿才反应过来——这给词增加了深度（《How to Rap》p0057）。
MURS 的评价："隐喻很带劲——像一记扣篮"（p0059）。

**失效条件**：比喻堆到听众跟不上时，它就不是深度而是噪音。
**自检动作**：一小节里超过两个互不相干的比喻 → 删到两个以内，或把它们改成同一个类比的不同面（这正是 analogy 的做法）。

### 6.2 文字游戏（wordplay）

**定义**："玩弄词和它们的意思——用机巧的方式使用语言"（《How to Rap》p0069）。

| 手法 | 实例 | 出处 |
|---|---|---|
| **同一个词的多重语境** | R.A. the Rugged Man《Black and White》反复用 "white"：White House / White Sox / white cops in donut shops / white powder / Snow White / white knight / white lies…**同一个词每次意思都不同** | 《How to Rap》p0069 |
| **双关** | Pharoahe Monch 在 De La Soul《Ghost Weed #1》里用 "kill / killing" 的字面义（杀）与俚语义（表现炸裂）来回切 | 《How to Rap》p0070 |

★ **①那种"一个词贯穿全段、每次换一个意思"的做法，和 `lw-song-intent` 的 `anchor_object`
是同一个结构手段的两种形态**：物件靠再次出现产生意义，词靠再次出现产生意义。

### 6.3 punchline

**定义**：特别强的一句，能"击中"听众——可以是幽默、可以是妙喻、可以是文字游戏，
**只要产生冲击**（《How to Rap》p0071）。

**结构是 setup + punch**：
Canibus 在《Uni-4-Orm》——
"If you try to battle me face to face, / I'll bring your career to a stop quicker than anti-lock brakes."
（《How to Rap》p0072）

| 做法 | 说明 | 出处 |
|---|---|---|
| **先有 punchline 再造 verse** | 先把那句记下来，再围着它把整段建起来 | 《How to Rap》p0072 |
| **存料库** | Yukmouth 走路时想到 punchline 就记下来，存进 "data bank"，等遇到合适的歌再放进去 | 《How to Rap》p0072 |
| **位置** | 常放在 bar 的**结尾**，以拿到听众的反应 | 《How to Rap》p0072 |
| **配一个 1 拍休止** | couplet 的第二行放 punchline，两行之间用 1 拍休止隔开 | 《How to Rap 2》p0055–p0057 |

★ **落点与休止归编曲库**（`mc-style-hiphop` reference §3.4）；本 skill 只管**那句话是什么**。

**自检动作**：把 punchline 单独念出来。**离开上下文还成立** → 它是 punchline；
**必须解释才好笑** → 它是一个想法，还不是 punchline。

### 6.4 意象

**用生动的语言在听众脑子里造画面**——很多 MC 的说法是"用文字作画"（《How to Rap》p0055）。
Kool G Rap 自称是"作家型 rapper"，要让听众看到一部小短片（p0056）。
经典例：Geto Boys《Mind Playing Tricks on Me》用大量细节描写偏执，造出难忘的画面（p0057）。

→ **具体名词怎么找、object writing 的练法归 `lw-imagery`**，本 skill 不重复。
rap 侧唯一要加的一条：**密度高意味着你有更多音节可以用来堆细节**——
这是 rap 相对于流行歌词的优势，别浪费在形容词上。

---

## 7. 词汇与句法

### 7.1 词汇量

| 说法 | 是谁说的 | 出处 |
|---|---|---|
| **"你的词汇量越大，你的弹药就越多"** | 2Mex | 《How to Rap》p0063 |
| 在"文字战争"里，武器最多的人通常赢 | RBX | 《How to Rap》p0063 |
| 词汇量越大，能画的画面越多，能触达的听众越广 | — | 《How to Rap》p0064 |
| **词汇量少 → 押韵模式永远相同** | Masta Ace | 《How to Rap》p0101、p0109 |

**怎么扩**（《How to Rap》p0065–p0068）：
像吸尘器一样在阅读中记新词（MURS：尽量多读报纸、每周八本漫画、外加一本小说或传记）；
对某个学科的兴趣能扩大词域（用 amoeba、paramecium 这类词制造认知反差）；
填字游戏、拼字游戏、看新闻、和人聊天；用词典确认语境、查词源、查同义反义词。

★★ **但词汇量不是目的**，这是三条互相制衡的说法：

| 说法 | 是谁说的 | 出处 |
|---|---|---|
| 看你的目标听众：听众是别的 rapper 就可以用更晦涩的词，面向大众就得口语化——**"归根到底是让人听懂你在说什么。复杂或简单都行，只要他们懂"** | — | 《How to Rap》p0066 |
| **尽量用外行人的话，但别无聊** | Del the Funky Homosapien | 《How to Rap》p0067 |
| Biggie 的词汇量并不大，**"他只是把词组合得很顺滑，而这对他非常管用"** | Big Daddy Kane 评 Biggie | 《How to Rap》p0066 |
| 过度依赖词典会显得**做作（pretentious）** | K-Os | 《How to Rap》p0069 |

★ **自检动作**：一段里有几个词是你自己平时不会说的？
超过三个 → 逐个问"它在这里是因为意思对，还是因为它押上了/显得厉害"。

### 7.2 俚语与它的保质期

**俚语让内容有颜色，并把歌**钉在**一个特定的时间、地点或运动上**（《How to Rap》p0060）。

| 要点 | 内容 | 出处 |
|---|---|---|
| ★ **俚语随文化更替** | Q-Tip：1960 年代说 groovy，后来说 dope，现在说 hot——**同一种情绪，不同的词** | 《How to Rap》p0061 |
| **俚语是个人标识** | Omar Cruz：方言与俚语是把一个 MC 从千篇一律的声音里分出来的关键 | 《How to Rap》p0061 |
| **地域绑定** | E-40 在《Tell Me When to Go》结尾用了一串湾区 hyphy 俚语（ghost-ride the whip、thizz face、go stupid） | 《How to Rap》p0062 |
| **俚语能定主题** | N.O.R.E.《Oh No》就是从他街区的几个俚语来的 | 《How to Rap》p0062 |
| **团体私有俚语** | Wu-Tang Clan 以密集的、团体专属的俚语著称，让曲目有独特且一听就认出的质感 | 《How to Rap》p0063 |
| **可以自造** | Snoop《Drop It Like It's Hot》把词尾都换成 "-izzle" | 《How to Rap》p0062 |

★★ **失效条件（保质期）**：**俚语把歌钉在一个时间点上，这既是它的功能也是它的风险。**
Q-Tip 那条（p0061）反过来读就是：**用当下的俚语，等于选择让这首歌在几年后听起来属于某个年代。**
- 要**长效**（§5.4 的 substance） → 少用时效性俚语，或只用已经稳定下来的
- 要**地域身份/年代感** → 用，而且要用得准（用错比不用更糟）

**自检动作**：每个俚语问一句"**我自己在说话时用过它吗**"。
没有 → 删掉，它多半是从别人的歌里抄来的。

### 7.3 专有名词

**专有名词（人名、地名、品牌、作品名）是 rap 词汇里最有力也最脆的一类。**
底本里的用法都带着同一个机制：**它们把一个具体的世界一次性装进两三个音节**——
Masta Ace 的 "as fake as a tooth-fairy"、Chino XL 的 Medusa、Canibus 的 anti-lock brakes
（《How to Rap》p0058、p0072）都靠听众认得那个名字才成立。

| 收益 | 风险 |
|---|---|
| 一个名字等于一整段描写，**极省音节** | ★ **听众不认识它，那一行就等于空的** |
| 建立具体的时间地点（同 §7.2） | 与俚语一样有保质期 |
| 提供现成的多音节韵料 | ★ **为了押韵而拉进来的名字最容易露馅** |

**自检动作（两问）**：
1. 这个名字**去掉之后这一行还剩什么**？什么都不剩 → 它在替真正的内容占位
2. 它是先想到的，还是**为了押上前一行才想到的**？后者 → 换一个（或按 §3.3② 改成对齐节奏、不押）

---

## 8. 写作流程

写作流程的完整八节（先词还是先 flow、各 MC 的做法、freestyle 与书面写作、改词方法）见 [reference.md](reference.md)。

## 9. ★ 中文说唱的迁移表

> **英文 rap 的技术有一半可以原样搬，另一半必须改，原因只有两个：
> 中文一个字就是一个音节，而且每个音节带声调。**

### 9.1 ★ 迁移表（本节的主表）

| # | 英文那边的做法 | 中文 | 怎么改 / 为什么 |
|---|---|---|---|
| 1 | **押韵密度的概念**（一小节几处韵） | ✅ **直接可用** | 密度与可懂度的取舍（§2.4）与语言无关 |
| 2 | **韵式**（couplet / single-liner / multi-liner / whole verse / extra rhymes） | ✅ **直接可用** | 韵式是行与行的连接关系，不依赖语音结构 |
| 3 | **内韵**（行中押韵） | ✅ **直接可用**，而且**中文更容易** | 中文单音节，任意一个字都能当韵脚，不像英文要凑到词的重音音节上 |
| 4 | **元音韵 assonance** | ✅ 可用 → 对应**韵辙** | 中文的韵母系统本身就是元音韵的分类，十三辙表见 `lw-mandarin` |
| 5 | **辅音韵 consonance / 头韵** | ⚠ **弱化** | 中文声母系统小、音节结构是"声母+韵母"，头韵效果远不如英文明显；**当装饰用，不承担结构** |
| 6 | **多音节韵 multies** | ★★ **必须改做法**，见 §9.2 | 英文一个词里就有多个音节可押；**中文要押 n 个音节，就得连着押 n 个字** |
| 7 | **弯词 bending words** | ⚠ **受限** | 中文改元音会直接变成另一个字；能弯的只有**方言音**与**儿化/轻声**（见 §9.3） |
| 8 | **重音落拍** | ★★ **换判据** | 中文没有英文那样的词重音；落拍的锚点改用**语义重音**（句子里要强调的那个字）与**双音节词的首字** |
| 9 | **俚语的时效性** | ✅ 同样成立，风险更大 | 中文网络用语的更替比英文俚语更快 |
| 10 | **专有名词** | ✅ 同样成立 | 同 §7.3 |
| 11 | **punchline / wordplay / 双关** | ✅ **直接可用**，而且**中文更强** | 汉语同音字极多，双关材料远比英文丰富 |
| 12 | **比喻三件套** | ✅ 直接可用 | 与语言无关 |
| 13 | **内容形式**（battle / story / concept / abstract / humor） | ✅ 直接可用 | 与语言无关 |
| 14 | **不押也行**（§3.5） | ✅ 可用，但**听感代价更大** | 中文听众对"押上没押上"的感知比英文更二元——要么押要么不押，没有"接近押" |
| 15 | **声调** | ★★ **英文没有这一项** | 见 §9.4 |

### 9.2 ★★ 中文怎么做多音节韵

**这是迁移表里最需要展开的一条。**

英文的多音节韵靠**一个词内部就有多个音节**（mockeries / dropping these），
中文一个字一个音节，所以中文的"多音节韵"只有一条路：

> **连着押相邻的若干个字。**

| 做法 | 说明 | 对应英文的哪一条 |
|---|---|---|
| **双押**（连押两个字） | 最常用的一档。两行的最后两个字韵母都对上 | 对应 compound rhyme 的最小形态（《How to Rap》p0100） |
| **三押及以上** | 密度和技术感陡增，但对词汇的要求也陡增 | 对应 Kool G Rap 那类 multies（p0101） |
| **词组对词组** | 用两个词组合起来去押另一个多字词组——**Speech 那条在中文里一样成立** | 《How to Rap》p0101 |
| **不必全部完美** | ★ 借用 Wu-Tang 那条：**一块里只要有一处韵母完全相同撑住，其余可以只是同辙** | 《How to Rap》p0100–p0101 |
| **靠节奏连**（§3.3②） | 找不到多字韵时，让两块**字数相同、停顿位置相同** | 《How to Rap》p0103 |
| **部分链接**（§3.3③） | 把零散的同韵字挂在主韵块上，不必凑成完整的多字韵 | 《How to Rap》p0104 |

★★ **中文双押有一个英文没有的坑**：
**连押两个字时，第一个字往往被迫从一个很小的候选集里挑。**
后果是所有人都押同样那几组（"…的心 / …的人"这类）。
**破法**：把双押的位置从**行尾**挪到**行中**（§9.1 第 3 条：中文做内韵比英文容易），
或按 §3.3② 改成对齐节奏。

**自检动作**：写完一段，把所有韵脚**竖着抄成一列**。
出现两组以上完全相同的搭配 → 换掉其中一组。

### 9.3 中文能"弯"的只有三样

英文的 bending words 靠改元音发音（arms / Mom's）。中文改元音就变成别的字了，能动的只有：

| 可弯的 | 说明 | 失效条件 |
|---|---|---|
| **方言音** | 用方言读某个字，让它进入另一个韵辙 | ★ 听众不懂那个方言就只听到"念错了" |
| **儿化与轻声** | 儿化会改变韵母，轻声会削弱韵脚的存在感 | 儿化在非北方听众那里不一定读得出来 |
| **外来词与英文词** | 中英混押是中文说唱的常规手段 | 混得太多会让 §2.4 的可懂度直接塌掉 |

★ **失效条件（共同的）**：以上三样**每一样都在降低可懂度**，
和 §2.4 是同一笔账——用之前先确认这首歌可懂度的预算还剩多少。

### 9.4 ★★ 声调：英文完全没有的那一项

中文每个音节带声调，这带来两件英文里不存在的事：

**① rap 段：声调不影响押韵，但影响"顺不顺"。**
韵辙只看韵母，**不看声调**——所以"天 / 年 / 点 / 电"都同辙。
但连续几个韵脚**声调全同**会显得平，**声调全不同**会显得散。
**自检动作**：把一段的韵脚声调写成一串数字（1 2 4 1 3 …），
全同 → 换掉一两个；毫无重复 → 至少让 hook 前那两个同调。

**② 半唱型 hook：声调必须过倒字这一关。**
★★ **rap 段没有固定音高，倒字不适用**（编曲库 `mc-style-hiphop` §7.1 已经这样定）。
但 hip-hop 的 hook 常常是**旋律化的**（编曲库 §7.4：旋律化的 hook 比说唱 hook 更受欢迎），
**旋律化的 hook 一出现，倒字立刻适用**。

→ **hook 的每一个字都要过 `lw-tone-check`**；韵辙与平仄去 `lw-mandarin`。
**失效条件**：整首都是 rap、hook 也是说的 → 不必查倒字。
只要 hook 带上了确定的音高走向，**这一关就必须过**。

### 9.5 中文说唱的可懂度：比英文更吃紧

**三个叠加的原因**：
1. 同音字多 → 听错的概率高
2. 一字一音节 → 同样的信息量要占更多音节，密度一高就糊
3. 声调在快速念诵中会被削平 → 分辨率进一步下降

★ **所以 §2.4 的可懂度测试在中文里要做得更严**：
故事型与 conscious 型的中文说唱，押韵密度建议落在**每小节 2 处**一档，
把余下的音节让给内容。要飙密度，去写 battle 与 braggadocio——
那两类本来就不靠第一遍听懂（§5.1）。

---

## 10. 写完自检

**内容**
- [ ] 定了**内容形式**（§5），而不是只有一个题材
- [ ] 故事型：**逐行确认过没有一行是被韵拖出来的**（§5.2）
- [ ] 概念型：说得出这个概念的**三个不同侧面**（§5.3）
- [ ] 至少有一句经得起单独念出来的 **punchline**（§6.3）
- [ ] 一小节里互不相干的比喻**不超过两个**（§6.1）

**韵**
- [ ] 定了**目标押韵密度**，并把每小节的韵数写成了一串数字（§2.3）
- [ ] 那串数字**不是从头到尾一样**
- [ ] 韵脚竖着抄成一列检查过，**没有两组以上完全相同的搭配**（§9.2）
- [ ] 用到了**元音韵/同辙**，不是只有完美韵（§3.1）
- [ ] 整首歌**不止一种韵式**（§4.2）
- [ ] 全曲最重要的那一句**没有为了押韵被改过**（§3.5）

**词汇**
- [ ] 每个俚语都问过"**我自己说话用过它吗**"（§7.2）
- [ ] 每个专有名词都问过"**去掉之后这行还剩什么**"（§7.3）
- [ ] 平时不会说的词**不超过三个**（§7.1）

**流程**
- [ ] 先用无意义音节**把格子打出来了**，填完词回去对过节奏（§8.2）
- [ ] 逐行问过"**因为要说的事，还是因为押上了**"，后者不超过 4 行（§8.3）
- [ ] 做过**可懂度测试**：念给人听，让他复述发生了什么（§2.4）

**中文**
- [ ] 过了 **§9.1 迁移表**，知道哪几条改了、为什么
- [ ] 韵脚**声调串**看过（§9.4①）
- [ ] ★ hook 如果是旋律化的，**过了 `lw-tone-check`**（§9.4②）

**交界**
- [ ] flow 的落点与休止用的是**编曲库的 flow diagram**，没有另造记谱
- [ ] delivery（音高/音量/音色/长短）**没有写进词稿**，它归编曲库

---

## 附：来源

- **主干**：Paul Edwards《How to Rap: The Art and Science of the Hip-Hop MC》，
  与 Paul Edwards《How to Rap 2: Advanced Flow and Delivery》。
  两本都是对一百多位 MC 的访谈汇编，所以**书里本来就并排放着互相矛盾的说法**——
  本 skill 保留了这种并排，并标明是谁说的。
- **同一批底本的另一半在编曲库 `mc-style-hiphop`**：那边写人声在编曲里的位置、
  flow 与拍的关系、delivery 的八个维度、段落结构数字；本 skill 写词本身。
  ★ 两边都引同一本书，**引到的页是不同的页**——交界只在"押韵落点"，
  记谱法以编曲库 reference §3.1 为准。
- **中文说唱一节（§9）是把底本的英文结论按汉语的语音结构重新推的**，
  不是从书里抄的——书里没有中文材料。推的依据写在每一条的"怎么改 / 为什么"里，
  可以逐条反驳。韵辙与声调的材料在 `lw-mandarin` 与 `lw-tone-check`。
- 大表（韵式对照、内容形式清单、MC 说法并排、中文韵脚料）在 `reference.md`。
