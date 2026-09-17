# lyric-writing-skills（作词技能集）

[English](README.md) · 中文版 · [日本語](README_JA.md) · [한국어](README_KO.md)

18 个 agent skill（用于 [Claude Code](https://docs.anthropic.com/en/docs/claude-code/skills) 与 [OpenAI Codex](https://developers.openai.com/codex/)），写歌词。底本是四种语言的 29 本书，涵盖英文作词教程、中文诗律与歌词写作、粤语实务、韩语语音学，另有桑德海姆两卷带自评的歌词全集。

`SKILL.md` 遵循开放的 [agentskills.io](https://agentskills.io) 规范，两个 agent 共用同一套文件：装一次，两边都能用。

**产出的是一份规格单，不止是词。** 你要一首词，agent 填的是一份 LYR-SPEC，内容是这首歌只说一件事、对谁说、在哪个时刻、什么物件贯穿全曲、每一句的字数与重音位置、韵式、刻意的不对称、语言层的检查结果，然后编译成生成后端的输入。改稿时对照的还是它。

**这个库要做什么。** 一首词的好坏是有判据的，这个库就是那套判据：只说一件事，落在一个能拍照的物件上，知道谁在说、说在哪一刻，让句式本身干活，韵脚不取第一个想得到的那个。库里每一道门禁的存在，都是为了逼出一个真实的选择，而不是一个默认值。

**用你自己的语言问。** skill 正文是中文写的，因为大部分底本是中文原著或中译本。你用什么语言问，agent 就用什么语言答。

**这套 skill 不会让生成模型跑得更快，它是在用时间换质量。** 完整走一遍专业的音乐工作流程，一首歌常常要二十分钟以上（agent 要读判据、填规格单、过自检），换来的是专业级的规格，不是几句提示词。

**本库不提供任何作品，作者自己的或别的歌手的都没有，编曲和歌词都没有。** 音乐作品的好坏是很主观的判断，请自己用、自己判断这套东西的价值，以及它在耗时上的代价。

## 这一套的四个库

一条音频线，切成四个各自独立的库。每一个单独就能用；库与库之间的接缝是写下来的，所以也能搭配着用。

| 库 | 干什么 | 状态 |
|---|---|---|
| **[music-composition-skills](https://github.com/jtydhr88/music-composition-skills)** | 作曲与编曲。一句 brief 变成一份 ARR-SPEC：调、速度、段落表、和声、谁什么时候进退、能量曲线、演唱与混音意图，再编译成 Suno、YuE2 或 MIDI 的输入 | 已发布 |
| **[lyric-writing-skills](https://github.com/jtydhr88/lyric-writing-skills)** | 作词。动笔前的门禁变成一份 LYR-SPEC：结构、意象、押韵、叙事，加上普通话、粤语、英文、日文、韩文的语言层 | **本库** |
| **配乐库** | 为画面写音乐：spotting（哪里该有音乐、从哪一帧进）、与剪辑点的关系、cue 怎么写怎么命名、主题在全片怎么发展 | 待建 |
| **混音与声音设计库** | 把混音意图变成实际操作：EQ、压缩、混响、自动化、母带 | 待建 |

**各自独立。** 给现成旋律填词，只要作词库。编一首器乐曲，只要编曲库。

**能组合，靠的是有名字的交接物。** ARR-SPEC 与 LYR-SPEC 是双向的：先曲后词时交过来段落表与小节数，先词后曲时交回去每句字数与重音位置，有六个字段必须两边一致。ARR-SPEC 里的 `mix_intent` 就是将来递给混音库的简报。配乐库出的 cue 表就是递给编曲库的 brief。

**接缝已经写好了。** 每个 skill 都带一张边界表，不归自己的问题按名字指到对应的库，而不是在原地勉强作答。所以那两个待建的库现在已经被处处引用：EQ 与压缩的实操出库到混音库，spotting 与 cue 的写法出库到配乐库。

## 为什么有了生成模型还要这套 skill

作词是一门有长久文字传统的手艺：英文这边有 Pattison 与 Sheila Davis，中文这边有王力的诗律、黄志华的粤语声律，剧场这边有桑德海姆的角色唱词。**这套 skill 把这个传统整理成一个专业词人会做的选择，并写成生成模型能被告知的形态。**

语言模型十秒钟就能给你四段词，押韵、字数齐整、意象丰富，缺的正是"选择"这一步。你没决定的地方，模型用它读过的一切的平均值补上，而平均值恰恰是任何一首好歌都不是的东西。

所以这套 skill 交出去的是选择本身：这首歌只说哪一件事，说给谁听，说在哪一分钟，哪个物件反复出现且每次含义不同，哪一句打破了句式以及为什么，哪个字不能落在那个音上因为声调会把它变成另一个字。**它做的是用专家级的规则去指导生成模型，不去重做一个生成模型。**

中文词还有第二个理由，而且与品味无关。普通话里字调与旋律冲突，听众会听成别的字；粤语里它就是别的字。一个不查声调、只管把句子写漂亮的模型，产出的词一唱就散。这些约束是可算的，这个库就是把它们写下来的地方。

模型仍然是歌手和录音棚。这份东西是递给它的词稿，附着每一处的理由。

## 安装

### Claude Code

#### 插件市场（推荐）

```
/plugin marketplace add jtydhr88/lyric-writing-skills
/plugin install lyric-writing@lyric-writing-skills
```

之后用 `/lyric-writing:<skill>` 调用，例如 `/lyric-writing:lw-workflow`。

#### 个人级（所有项目）

```bash
git clone https://github.com/jtydhr88/lyric-writing-skills.git
cp -r lyric-writing-skills/plugins/lyric-writing/skills/* ~/.claude/skills/
```

#### 项目级

```bash
mkdir -p .claude/skills
cp -r lyric-writing-skills/plugins/lyric-writing/skills/* .claude/skills/
```

### Codex（CLI / ChatGPT 桌面端 / IDE 扩展）

```bash
codex plugin marketplace add jtydhr88/lyric-writing-skills
# 然后：Plugins → 选 "Lyric Writing Skills" → Install
```

或者把同一批文件复制到 `~/.agents/skills/`（个人级）或 `.agents/skills/`（项目级）。

#### 确认装上了

agent 判断到相关上下文时会自动加载。列出全部：`/skills`。

## 用法示例

```
# "给这条旋律填词，小节数和每句字数在这里"
# → lw-workflow（先曲后词）→ lw-song-intent → lw-structure → lw-mandarin

# "这稿读着没毛病，但就是泛，我说不出哪里不对"
# → lw-ai-tell-audit：八条可枚举的机器指纹，每条指向管它的那个 skill

# "给一首粤语歌填词"
# → lw-cantonese：先用音高类别体系算，再选字。粤语的写作顺序是反的，
#   别的语言层顶替不了

# "把这段主歌改成说唱"
# → lw-rap（押韵密度、多音节韵、中文说唱迁移表）

# "这句唱出来还是我写的那几个字吗？"
# → lw-tone-check：只查每段最高音、每句首字、大跳落点，约占全部字的五分之一
```

## 常见用例

这套东西比看上去复杂。一句话的 brief 会牵动作曲、编曲、作词三边十几个 skill，agent 读什么、出什么，取决于你那句话里有没有把几个关键项说到。下面是实际跑过的几种常见组合，每条写清楚怎么说、会走哪些 skill、出什么。带歌词的用例要同时装作曲编曲库和作词库。

**1. 参照某位歌手的风格写一首带词的歌**（最常见）

> 写一首某位歌手某首歌那种风格的华语流行歌，女声，要在 Suno 上生成，带歌词。

走：lw-workflow → lw-song-intent → lw-structure → lw-mandarin → lw-tone-check → lw-suno-interface；mc-workflow → mc-style-chinese-pop → mc-melody → mc-development → mc-arrangement-arch → mc-vocal-direction → mc-render-compile
出：LYR-SPEC.yaml、ARR-SPEC.yaml、suno-pack.md（标题、风格描述、带段落标签的歌词、排除词）
说明：参照歌手只借编制、速度、人声人设、段落走法，不借词曲。

**2. 抖音口水歌，不要叙事**

> 写一首抖音口水歌，女生，甜美，不要叙事。Suno 生成，带歌词。

走：lw-song-intent（态度型）→ lw-structure（重复预算、hook 位置）→ lw-rhyme → lw-mandarin；mc-style-chinese-pop → mc-rhythm-groove → mc-arrangement-arch → mc-render-compile
说明："不要叙事"四个字决定歌词类型。不说的话，默认会写成情境。

**3. 伤感情歌，要直接说的，不要场景**

> 写一首某位歌手某首歌那种的伤感情歌，男声，Suno 生成，带歌词。要直接说的那种，不要场景描述。

走：同 1，但 lw-song-intent 走态度型，锚是一句话（副歌段首反复的那句）而非物件；mc-vocal-direction 管贴麦男声与末句留白
说明：语料里四成的态度型歌没有任何可拍照的物件，副歌就是对"你"说的一句话，主歌说我的状态，开头是独白。想要这种，就在 brief 里说"直接说，不要场景不要物件"。

**4. 一种心情，不写成故事**

> 写一首国语流行歌，三分半，女声，主题是搬家那天把充电线留在了墙上的插座里，走了两条街才想起来，没回去拿。不要写成故事，我要的是想起来又算了的心情。

走：lw-song-intent（情境型，锚物件是充电线）→ lw-imagery → lw-structure → lw-mandarin → lw-tone-check；曲侧同 1
说明：情境型与叙事型的分界在这里：有物件，没有情节推进。

**5. 器乐曲，从零作曲**

> 写一首两分四十秒的器乐曲，给短视频当背景，主奏是一把尼龙弦吉他，配一点打击和贝斯，可以有一件键盘。感觉是"下午三点，在等一个人，不着急"。不要人声。

走：mc-workflow → mc-development（动机、性格、发展手法）→ mc-melody → mc-form → mc-harmony → mc-rhythm-section → mc-orchestration → mc-render-compile
出：ARR-SPEC.yaml（material 块与每段的 development 字段填满）、suno-pack.md、一页说明
说明：不带词，作词库不参与。判据在 mc-development：新材料不过半，有再现。

**6. 已有词曲，只做编曲**

> 给一首已经写好旋律和歌词的国语情歌做编曲，要 salsa 的感觉，有铜管，速度中快。只要规格单，不用 Suno prompt。

走：mc-workflow（编曲路线）→ mc-style-latin → mc-rhythm-section → mc-orchestration（铜管）→ mc-arrangement-arch → mc-texture-layering
出：只有 ARR-SPEC.yaml 和一页说明

**7. 风格融合：主歌 rap，副歌中国风**

> 写一首像某首歌那样 rap 加中国风的歌，要完整的中文歌词，用在 Suno 上。

走：mc-workflow §2.4 风格混合 → mc-style-hiphop（基底）+ mc-style-chinese-pop（叠加）；lw-rap（主歌）+ lw-chinese-style（副歌）+ lw-mandarin

**8. 粤语填词**

> 给这条旋律填粤语词，小节数和每句字数在这里。

走：lw-workflow（先曲后词）→ lw-cantonese（先按音高类别算，再选字）→ lw-tone-check
说明：粤语的写作顺序是反的，普通话那层顶替不了。

**9. 不用 Suno，用本地开源模型（YuE2）**

> 同一首歌，不走 Suno，用本地 YuE2 生成，把规格单编译成 ABC 谱给我。

走：同 1，再加 mc-symbolic-score（把 ARR-SPEC 编译成 ABC，人声线写在小写音名区、带 w: 歌词行）
说明：实验性。词唱出来的比例目前低于直接给 style 与歌词的方式，细则见 mc-symbolic-score §6b。

brief 里真正起作用的几句话：

| 你说的 | 它决定什么 |
|---|---|
| 歌手名＋歌名 | 只借编制、速度、人声人设、段落走法；不借词曲 |
| 女声／男声，甜美／贴麦 | mc-vocal-direction 的人设与音域 |
| Suno ／ 本地 YuE2 ／ 只要规格单 | 出口：suno-pack、ABC 谱、只出 ARR-SPEC |
| 不要叙事 ／ 直接说不要场景 ／ 不写成故事 | 歌词类型：态度型 ／ 态度型无物件 ／ 情境型。不说，默认情境 |
| 时长 | 段落数与小节数从这里反推 |
| 产物清单 | 写明要哪些文件，agent 就按清单出，少一份都算没做完 |

以上每条完整走完通常二十分钟以上，见上文"用时间换质量"。

## 不需要装任何工具

插件是纯文本。没有脚本要跑，不需要 Python，不需要 Node，没有 lint 这一步。LYR-LINT 十条全部用眼睛就能判，倒字检查也有手判方法，只看问题真正发生的那三类位置。

**规则是判据，不是铁律。** 某条不过，要么改那一句，要么写一句为什么这首歌就该这样。

## 多语言支持

**一套源文件，运行时出任何语言。** skill 只写一遍，用中文写，你用什么语言问，agent 就用什么语言答。不需要开关，不需要另装，也没有分语言的插件。

这一点在本库要说仔细，因为本库有**语言层**，两件事很容易混。语言层管的是**词**用哪种语言写：普通话的字调、粤语的协音、英文的重音、日文的拍数。下面这条政策管的是**指令文件**用哪种语言写。一位日本词人用日语提问，得到的是日语回答和完整的 `lw-japanese` 层，而它背后的指令文件仍然是中文。

skill 正文不会再做其他语言的版本，这是一个决定，不是疏漏。姊妹项目 [screenwriting-skills](https://github.com/jtydhr88/screenwriting-skills) 做过完整的英文版，合进去过，后来删掉了，当时说服大家的理由在这里同样成立：如果一个读不了中文的人该有一套译本，那读不了英文的人也该有，接下来就是日语、韩语、法语。本包 31 份文件，四种语言就是 124 份，各自独立漂移，而且没有任何东西告诉你哪一份已经过期。翻译本身是便宜的，真正的代价是分叉一次之后，再拒绝第二次分叉就没有站得住的理由了。

运行时是这样覆盖的：

- **输出语言跟随提问语言。** 用韩语问就得到韩语。
- **术语锚定原词。** object writing、prosody、family rhyme、hook、モーラ、符割り、협음：中文书里的说法本身也是译名，所以原词跟着概念一起走。
- **没有对应译法的术语保留原形加注解。** 十三辙、依字行腔、類音階、字余り 都是原词加一句简短解释。
- **你的词保持它自己的语言。** 用英语讨论一首粤语词是正常的。换的是对话的语言，词稿不换。

这样放弃掉的是可审计性：除非你读中文，否则你读不到指令文件本身，只能读到 agent 对它的转述。这是真实的代价，也正是一套译本唯一能换来的东西。对一个价值建立在"每条规则都带可核对的出处与页码"之上的库来说，它不值四套永久维护负担。

**README 是另一回事**，它们做了翻译，因为篇幅短、内容稳定，而且是新来的人最先看到的东西。

## 分层

六层。**语言层是这个库的主干**，这是唯一值得专门解释的设计决定。

换一种语言不是在同一套方法上换一张表。普通话在别的约束之上**再加一整套字调约束**；粤语更进一步，把**写作顺序整个反过来**：旋律先定，每个音高位置只剩少数几个声调可用，所以要先定字调骨架再选字；日文按モーラ（拍）数，不是按音节；英文挂在重音上。这是方法级的差别，所以各占一个 skill，而且每一个都写明：别的语言层顶替不了它。

```
L0 工作流   路由、两条流程（先曲后词／先词后曲）、LYR-SPEC 契约
L1 通用层   立意 · 结构 · 意象 · 押韵 · 叙事
L2 语言层   普通话 · 粤语 · 英文 · 日文          ← 主干
L3 传统层   中国风 · 音乐剧 · 说唱
L4 执行层   倒字检查 · 编译到后端 · AI 味诊断
L5 语料层   把成品词拆开看
```

### L0 入口

| Skill | 管什么 |
|---|---|
| `lw-workflow` | 路由、开头那个必须先答的岔路口（先曲后词还是先词后曲）、两条流程各自的阶段表、全库边界表、LYR-SPEC 规范与模板、十条检查，以及与编曲库的双向接口 |

### L1 通用层（与语言无关）

| Skill | 管什么 | 主要来源 |
|---|---|---|
| `lw-song-intent` | **本库唯一的硬门禁：动笔前的五个问题。** 这首歌是哪一类（态度、情境、叙事、说理，默认不是叙事）、这首歌只说一件事、对谁说、在哪个时刻、一个能拍照的贯穿物件。每个问题抓一种特定的失败，§7 是照妖镜，分辨"真答了"还是"为了过门禁填了" | 本库架构，并与 Pattison、Davis 交叉核对 |
| `lw-structure` | 各段该说什么不该说什么、曲式模板、标题与 hook 放在哪、句式怎么让一段听起来"说完了"或"还没说完"，以及整齐对称为什么读起来像表格 | Pattison《歌词形式》、Sheila Davis、尤静波 |
| `lw-imagery` | object writing 与七种感官、具体名词对抽象名词、感官分布、让意象成系统而不是堆意象、比喻与死喻 | Pattison《Writing Better Lyrics》《Without Boundaries》《Songwriter's Playground》 |
| `lw-rhyme` | 押韵是结构手段不是装饰：完美韵与各类家族韵各自的收束力、韵式、内韵、意外度、故意不押 | Pattison《Essential Guide to Rhyming》 |
| `lw-narrative` | 谁在说、什么时候说、允许他知道多少：人称与视角、时间锚点、留白与不解决，以及"情绪走完整"为什么是机器指纹 | Sheila Davis ×2、《十步叙事》 |

### L2 语言层（主干）

| Skill | 管什么 | 主要来源 |
|---|---|---|
| `lw-mandarin` | 字调是音位，换调等于换字。十三辙及其代表字、宽辙与窄辙、平仄以及歌词能松到什么程度、顿才是中文句子真实的节奏单位、易唱性（开口闭口音、绕口）、中文流行歌词的实务惯例 | 王力《诗词格律》×2、吴颂今、李忠勇、张藜、洪源、尤静波 |
| `lw-cantonese` | 九声与协音是**硬**约束：违了就唱成另一个字，不只是听着别扭。让字调与旋律的匹配变得可算的音高类别体系、自然音距的弹性、六调试音法，以及反过来的写作顺序 | 黄志华《文字声律与粤语歌创作》、《词家有道》16 位词人访谈、黄霑 |
| `lw-english` | 重音对节拍：词重音不可改、句重音可调；功能词不该落强拍；数重音而不是数音节；prosody；分行、气口与跨行；中文母语者写英文词最常犯的六个错 | Sheila Davis《Craft of Lyric Writing》、Pattison、《Lyrics: Writing Better Words》 |
| `lw-japanese` | 按モーラ（拍）不按音节，促音、撥音、長音各占一拍。音高重音与旋律的冲突、符割り（拍对音符）、分節、故意的字余り与字足らず、音节数不合时的四种修正法、七五調与"听起来太日本"的警报、英文词混进日文歌的铁律 | 日式作词与人声制作实务、旋律法、pro songmaking |

### L3 传统层

| Skill | 管什么 | 主要来源 |
|---|---|---|
| `lw-chinese-style` | 什么让一首词是中国风而不只是"听着古"：词汇家族、十六种文字游戏手法及各自的失效条件、意象为什么必须成套、用典能用多深 | 方文山《中国风：歌词里的文字游戏》 |
| `lw-musical-theatre` | 一首歌必须是动作不是停顿；词要像这个角色会说的话，不像作词人；桑德海姆的三条原则，全都服务于清晰；他对自己毛病的清单；以及一张迁移表说明哪几条流行歌词也该守 | 桑德海姆《Finishing the Hat》《Look, I Made a Hat》 |
| `lw-rap` | 词本身，不是人声在 beat 里的位置：押韵密度与可懂度的权衡、多音节韵与近似韵、内容形式与逐行手法、押韵驱动与意思驱动的取舍，以及中文说唱迁移表 | Paul Edwards《How to Rap》1&2 |

### L4 执行与检验

| Skill | 管什么 |
|---|---|
| `lw-tone-check` | 倒字检查怎么做、结果怎么读。它输出的是**风险**，不是判决。长音、重音、清晰咬字都能救回一个被标红的字 |
| `lw-suno-interface` | 成品词编译成后端输入：段落标签、格式、已知行为与陷阱 |
| `lw-ai-tell-audit` | 八条可枚举的机器指纹，逐条数，每条指向管它的 skill。外加一个更狠的测试：去掉标题和专有名词，给一个不知情的人看，他能说出这首歌在讲哪一件具体的事吗 |

### L5 语料层

| Skill | 管什么 |
|---|---|
| `lw-case-studies` | 怎么把一首成品词拆开：一张十二行的拆解表，对应本库自己的字段；三位在职词人各自的写作习惯与判断标准，以及他们之间的分歧；成篇案例；改稿前后对照 | 姚谦、张藜、洪源 |

## 与编曲库的接口

这是一条音频线的作词半边。另一半是 [music-composition-skills](https://github.com/jtydhr88/music-composition-skills)，两者是**双向**耦合，不是谁喂谁：

- **先曲后词**：ARR-SPEC 交过来段落表、小节数、情绪弧，词写进那个格子里。
- **先词后曲**：词把每句字数与重音位置交回去，编曲库据此定小节数。

有六个字段必须两边一致。任何一边改了其中一个，另一边必须跟着改。

## 这个包里没有什么

韩文（받침 及其对演唱的影响）与民谣叙事。这两块目前没有底本，而本库不写没有底本的 skill。给一门语言编造韵律规则，产出的是自信的错误答案。遇到这类请求，用通用层，并明说语言层没有覆盖。

## 底本书目

**英文作词教程（10）**：Pat Pattison《Writing Better Lyrics》《Songwriting Without Boundaries》《Essential Guide to Lyric Form and Structure》《Essential Guide to Rhyming》《Songwriting Essential Guide》；Sheila Davis《The Craft of Lyric Writing》《Successful Lyric Writing》；《Lyrics: Writing Better Words for Your Songs》；《Popular Lyric Writing: 10 Steps to Effective Storytelling》；《Songwriter's Playground》

**中文诗律与歌词写作（7）**：王力《诗词格律·诗词格律概要》《王力谈诗词格律》；吴颂今《歌词写作十八讲》；李忠勇、何福琼《歌词写作常识》；张藜《歌诗之路》；洪源《春消息》；尤静波《流行歌词写作教程》

**粤语（3）**：黄志华《文字声律与粤语歌创作》；黄志华、朱耀伟、梁伟诗《词家有道：香港16词人访谈录》；黄霑《粤语流行曲的发展与兴衰》

**中国风（1）**：方文山《中国风：歌词里的文字游戏》

**音乐剧（2）**：桑德海姆《Finishing the Hat》《Look, I Made a Hat》，歌词全集，带作者本人的评注与自我批评

**说唱（2）**：Paul Edwards《How to Rap》《How to Rap 2》

**韩语语音学（4）**：郑政德《韩国语语音入门》；李翊燮、李相亿、蔡琬《韩国语概论》；刘小瑛《韩语发音快速入门》；《新魅力韩国语发音入门》

**语料**：姚谦《我们都是有歌的人》，以及中文歌词写作书里的成篇分析

## 体例

- `SKILL.md` frontmatter：`name`（短横线小写，与目录名一致）＋一段较长的英文 `description`，以 "Use when …" 收尾，并附中文关键词，两种语言都能路由。
- 正文中文；带编号的原则、表格、清单。输出语言跟随提问语言。
- **每条规则都带失效条件或自检动作。**
- 两家说法不一致时并排保留，并注明各自适用场合。
- **没有底本的不写。** 某个 skill 的例子若是本库自拟而非书里的，会写明。
- 引用标出处与页码。
- `reference.md` 放长表与详例，让 `SKILL.md` 保持在 40 KB 以内。
- 设计上与 agent 无关：skill 文件不提任何 agent 的名字，不用任何 agent 专有语法。

## 授权

skill 本身是 MIT，见 [LICENSE](LICENSE)。底本引文版权仍属原作者与译者，见 [NOTICE](NOTICE)。为分析而引用的歌词，只引到分析所必需的长度。

---

姊妹项目，同一套做法用在编剧上：[screenwriting-skills](https://github.com/jtydhr88/screenwriting-skills)，它的戏曲层与这里的普通话层共享依字行腔与十三辙的材料。
