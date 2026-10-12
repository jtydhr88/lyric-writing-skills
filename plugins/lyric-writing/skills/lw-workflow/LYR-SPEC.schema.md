# LYR-SPEC v1.0 —《词稿规格单》规范

> 本库唯一的交接物。一物四用：对外交接、AB 测试对象、导出源（→领奏谱／ChordPro／ABC 歌词行，§3.1）、验收基准。
> 对外只经这一份：交出去的字段、有就读的上游字段、消息通道，见 §3。先曲后词时本库读曲这一侧的段落与旋律；先词后曲时本库先定段落与字数句式，曲这一侧来读。
>
> 配套：`LYR-SPEC.template.yaml`、`example-*.yaml`。写完按 §2 十条自查；中文按 `lw-tone-check` §2.3 手判倒字。

---

## 0. 使用纪律

1. ★ **`intent` 五项不填齐，不许写第一句词。** 这是本库唯一的硬门禁。
2. 写完**逐条过十条自查**（§2），不过的条目改掉或写明理由再交。这些是判据不是铁律。
3. 中文词**按 `lw-tone-check` §2.3 手判倒字**，并**人工念一遍高风险处**。
4. ★ **先词后曲时，旋律回来之后必须重跑倒字/协音检查**——这一步最常被漏。
5. 交稿前过 `lw-ai-tell-audit` 的八条。
6. 开工时与每次改词前，读写给本库的消息（`messages` 里 `to: lyrics` 的条目，§3.4）。

---

## 1. 字段规范

### 1.1 `meta`

| 字段 | 必填 | 说明 |
|---|---|---|
| `spec_version` | ✅ | `"1.0"` |
| `title` | ✅ | |
| `language` | ✅ | `普通话` / `粤语` / `英文` / `日文` / `韩文`。★ **决定读哪个 L2 skill** |
| `flow` | ✅ | `先曲后词` / `先词后曲`。★ **本库的第一个岔路口**，两条路的阶段表完全不同 |
| `style_layer` | ○ | L3 skill id，如 `lw-chinese-style`；无则 `none` |
| `tempo`、`key` | ○ | 与歌曲另一侧共享的字段，谁先做谁定，见 §3.3 |
| `upstream` | ○ | 有就读的上游字段（段落表、速度、调、人声设定、旋律、委托、所在的戏或画面），见 §3.2。没有就按本库自己的分析走 |

### 1.2 `intent` —— 动笔前必填（★ 门禁）

| 字段 | 必填 | 说明 |
|---|---|---|
| `plot_type` | ✅ | ★ **先答**。这首歌是哪一类，封闭集合：`attitudinal` 态度型 / `situational` 情境型 / `narrative` 叙事型 / `expository` 说理型。**默认不是 narrative**，大多数流行歌是前两类。它定人称、声音与重复预算，见 `lw-song-intent` §1.1–1.3 |
| `one_thing` | ✅ | **这首歌只说一件事**。一句话，不许两句，**不许"既…又…"**。★ 念出来要像一句人话，不是主题词 |
| `to_whom` | ✅ | **对谁说**。★ **"抒情"和"听众"不是对象**——要一个能想象出脸的对象 |
| `at_what_moment` | ✅ | **在哪个时刻说**。★ **时间点，不是时间段** |
| `anchor_object` | ✅ | **一个贯穿全曲的、能拍照的物件**。★ 判据：**说得出它的颜色、大小、新旧** |
| `anchor_phrase` | ○ | **锚也可以是一句话**：态度型／说理型常常没有物件，贯穿全曲的是一句直接对「你」说的话（请求、决定、质问、宣言），副歌反复它。填了它，态度型／说理型的 `anchor_object` 可以写「无」。语料：国语态度型四成没有贯穿物件，这一组破题句 41% 是独白、口语占 82% |

> **为什么设门禁**：AI 写的词不是"用词不好"，是**没有人做过选择**——
> 它写出来的四段可以属于任何一首歌。这四项就是强迫做选择的地方。
> 详见 `lw-song-intent`。

### 1.3 `prosody` —— 词与旋律的咬合

先曲后词时**照曲这一侧给的段落表与旋律量出来**（`meta.upstream`，§3.2）；先词后曲时**由本表输出**，交出去约束小节数（§3.1）。

★ **`syllables` 的填法**：词写完之后，对着 `lyrics[].lines` **逐行数汉字**再填，不要先定字数再凑词。只数汉字，标点与整行括号的 ad-lib 不算。这一项是照模板写规格单时最常差一个字的地方，所以顺序要反过来：**先有词，后有数**。

```yaml
prosody:
  sections:
    - id: C1                      # ★ 段落 id，与 form[].id 一一对应（§3.3）
      syllables: [9, 9, 7, 11]    # 每句音节/字数。★ 一个元素 = 词稿里的一行
      stress_positions:           # 英文：重音位置；中文：旋律强拍落在第几字
      peak_syllable:              # ★ 全段最高音落在哪个字——这个字必须经得起唱
      melody_contour: "5→3 下行"  # 先曲后词：量到的旋律走向；先词后曲：词对旋律走向的要求（字调轮廓）
      notes: [67, 69, 67, 64]     # ○ MIDI 音高序列，给 倒字判定 用
```

★ **与歌曲另一侧共享的六个字段**：
`form[].id` / `form[].bars` / `form[].name` / `meta.tempo` / `meta.key` / `vocal.persona`
**谁先做谁定，后做的一方只读；想改，走消息**（§3.3）。

### 1.4 `rhyme`

| 字段 | 必填 | 说明 |
|---|---|---|
| `scheme` | ✅ | 韵式，如 `AABA` |
| `che` | ✅ | 辙口（普通话十三辙 / 粤语韵部）。写成列表；**推荐逐段写**，每项 `{section, 辙, 宽窄, 韵脚}`，也接受只写辙名的字符串列表。**受第 8 条自查约束**：不许全曲只用一两个宽辙 |
| `deliberate_breaks` | ✅ | ★ **哪几处故意不押**——全押到底是 AI 味。**空数组视为未填** |
| `surprise_notes` | ○ | 哪个韵脚是"意外又觉得对"的。**受 lint 第 9 条约束** |

### 1.5 `imagery`

| 字段 | 必填 | 说明 |
|---|---|---|
| `concrete_nouns` | ✅ | ★ **能拍照的具体物件清单**。**受 lint 第 2 条约束** |
| `system` | ✅ | ★ **这些物件构成什么系统**——不是随机堆意象。空着意味着它们只是装饰 |
| `forbidden` | ✅ | **本首禁用的抽象词**（时光/远方/梦/自由/青春/思念…）。**受 lint 第 2 条约束：零出现** |

### 1.6 `narrative`

| 字段 | 必填 | 说明 |
|---|---|---|
| `pov` | ✅ | 人称与视角。**受 lint 第 6 条约束** |
| `tense_anchor` | ✅ | 时间锚点。★ 由 `intent.at_what_moment` 决定 |
| `withholding` | ✅ | ★ **该说的地方不说的那一处在哪**。**受 lint 第 5 条约束**。AI 会把情绪走完整，真人经常停在难受里 |

### 1.7 `asymmetry` —— ★ 专门一节：刻意的不对称

| 字段 | 说明 |
|---|---|
| `short_line` | 哪一行故意短 |
| `unrhymed` | 哪一段故意不押 |
| `chorus_variation` | 末遍副歌改了哪一到三个字，落在热点位。★ 前两遍逐字相同是常态，不是缺陷 |
| `repetition_budget` | ★ 副歌重复几遍、主歌靠什么推进（新事件 / 再看一眼 / 拉远镜头）。**副歌占全曲三到六成（人工分段 72 首中位 0.44）**，先定副歌几行几遍再算主歌剩几行；主歌之间也要有复用。不同行占比超过 0.85 先怀疑这一项没花。见 `lw-structure` §6.0 |

**受 lint 第 3、4、10 条约束**：三项**至少填两项**；各段字数不许完全相同；副歌各遍文本不许完全相同。

★ **每一处不对称都要说得出理由。** 为了破坏而破坏，和整齐一样机械。

### 1.8 `lyrics` —— 词本身

```yaml
lyrics:
  - section: C1
    lines:
      - "第一行"
      - "第二行"
```

★ **分行不是排版，是指令**——唱的人会把换行当成乐句边界读。
分行必须与 `prosody.sections[].syllables` 一致。

★ **`section` 必须等于段落 id `form[].id`**（§3.3；`C1`、`A2` 这种 id，不是 `Chorus` 这种名字）。词与曲靠这一列咬合：MusicXML 领奏谱、ChordPro 和 ABC 的 `w:` 行都从这里取词，按段落 id 找到该段的小节，再按"每个音符一个音节"逐字贴上去，中文一字一音节。

★★ **词里不许有任何注释/创作说明**——照着词唱的人会把它唱出来。注释写 `note` 字段。

### 1.9 `checks`

```yaml
checks:
  computed: {}      # 倒字率、协音违例、韵脚意外度…（手判后填）
  self_audit: []    # 人工逐条打勾
  exemptions: []    # ★ 豁免必须写理由，不许静默跳过
```

**人工项固定这几条**：
- [ ] `one_thing` 念出来是一句人话，不是主题词
- [ ] `anchor_object` 说得出颜色、大小、新旧
- [ ] 去掉标题和专名，别人能说出这首歌讲的是哪一件具体的事
- [ ] 每一处不对称说得出理由
- [ ] 中文：倒字高风险处**实际唱/念过**，确认无误

---

## 2. LYR-LINT 十条

人工逐条过。**不过 = 改或写理由**，不是禁止交付。

| # | 检查 | 对抗的 AI 味 | 可算 |
|---|---|---|---|
| 1 | `intent` 五项非空，`anchor_object` 是能拍照的实物，或态度型／说理型用 `anchor_phrase` 代替 | 没做过选择 | 半 |
| 2 | 每段至少 N 个具体名词；`forbidden` 抽象词**零出现** | 名词全是抽象的 | ✅ |
| 3 | 各段字数**不许完全相同** | 结构对称到死 | ✅ |
| 4 | `asymmetry` 三项**至少填两项** | 同上 | ✅ |
| 5 | `narrative.withholding` 非空 | 什么都解决了 | 半 |
| 6 | `pov` ＋ `tense_anchor` 非空 | 没有视角和时间 | ✅ |
| 7 | **倒字率 ≤ 阈值（普通话）／协音违例 = 0（粤语）** | 倒字不管 | ✅ |
| 8 | 辙口不许全曲只用一两个宽辙 | 只挑最顺的辙 | ✅ |
| 9 | 韵脚意外度：不许全是最高频韵字 | 押韵选第一个想到的 | ✅ |
| 10 | 副歌各遍文本**不许完全相同** | 原样重复三遍 | ✅ |

### 2.1 ⚠ 哪些条能判过/不过

第 2、7、8、9 条只报数，不判过/不过：

| 条 | 状态 |
|---|---|
| 1、3、4、5、6、10 | ✅ **可判过/不过**（结构性检查，不需要阈值） |
| 2 | ⚠ `forbidden` 零出现**可判**；"每段至少 N 个具体名词"的 **N 待定** |
| 7 | ⚠ **只能给数值**（详见 `lw-tone-check` §5） |
| 8、9 | ⚠ **只能给数值**，需要辙口表与韵脚词频表 |

---

## 3. 对外接口

这份规格单记的是**一首歌的词**：说什么、对谁说、每一句几个字、押什么、哪里故意不押，以及为什么。本节写给规格单之外的读者——写曲的、录音的、配乐的、写戏的，另一套工具、另一个 agent 都一样：不假设谁在读、用什么工具，只约定数据。四件事：交出去哪些字段、每个字段怎么理解（§3.1）；有就读的上游字段（§3.2）；与歌曲另一侧共享的六个字段（§3.3）；按职能记名的消息通道 `messages`（§3.4）。本库的 skill 之间也只经这些字段交换，对内对外是同一份规格单。

```
先曲后词：meta.upstream（段落表 ＋ 旋律）       ──→  本库的 prosody 照它量
先词后曲：本库的字数句式 ＋ 本库定的六个共享字段  ──→  交出去约束小节数与旋律
```

### 3.1 交出去的字段（按职能）

**先读这几条约定**，下表每一行都照它们理解：

- **段落 id**：`lyrics[].section`、`prosody.sections[].id`、`form[].id` 是同一个 id（`C1`、`A2`），不是段落名；段落名在 `form[].name`。
- **一行＝一个乐句**：`lyrics[].lines` 的换行是乐句边界，不是排版；一行对应 `prosody.sections[].syllables` 的一个元素。中文只数汉字；整行括号的是 ad-lib 或和声应答。
- **词里没有注释**：说明一律写在字段或 `note` 里（§1.8），词里的每个字都是要唱的。
- **量到的与要求的**：先曲后词时，`prosody` 是照旋律量出来的；先词后曲时，`prosody` 是本库的提议，`melody_contour` 写的是词对旋律走向的要求（字调轮廓）。`checks.computed` 是本库的自查记录（倒字手判）；`checks.exemptions` 里写了理由的偏离是有意的选择，不是错误。

| 职能 | 读哪些字段 | 字段怎么理解 |
|---|---|---|
| **作曲编曲**（旋律、和声、编曲、曲式小节数） | `lyrics[]`；`prosody.sections[]`（`syllables` `stress_positions` `peak_syllable` `melody_contour` `notes`）；先词后曲时本库定的六个共享字段（§3.3）；`checks.computed`；`intent`；`asymmetry.chorus_variation`；`rhyme.deliberate_breaks` | **`peak_syllable` 是全段最高音落在哪个字**，本库已按字调与开口音挑过，改旋律时这个位置要守住。先词后曲时，各段句数与 `syllables` 是 `form[].bars` 的依据，`melody_contour` 是字调对旋律的要求（阳平字别配下行、去声字别配上行，`lw-tone-check` §2.2）。`checks.computed` 标出的倒字风险，写曲时换个走向就能避开；避不开的写 `messages`。`chorus_variation` 是末遍副歌改了哪几个字，旋律跟不跟着变由写曲的定 |
| **声音**（录音与演唱指导） | `lyrics[]`；`vocal.persona`、`narrative.pov`；`checks.computed`；`checks.self_audit` | **词稿只给字与分行**：那些字怎么唱（气声、力度、咬字、修音）由演唱指导定。`checks` 里标出的倒字风险字与要装饰音才救得回来的字（`lw-cantonese` §3.9），是**录音时要特别咬清的地方**——长音、重音、清晰咬字都能救（`lw-tone-check` §5.3）。整行括号的是 ad-lib 或和声应答，不是主唱的词 |
| **配乐**（为画面写音乐；有歌词的 cue） | `intent`（`one_thing` `to_whom` `at_what_moment`）；`narrative`（`pov` `tense_anchor` `withholding`）；`lyrics[]`；`meta.upstream.scene` | **词只写这一刻说什么、对谁说、哪里不说**。`withholding` 是词有意不说的那一处。cue 从哪进、到哪停、怎么和画面对位由配乐定 |
| **剧作**（戏里的唱段） | `intent`；`narrative`；`lyrics[]`；`meta.upstream.scene` | 唱段在戏里的位置与这场戏的转折由剧作定，本库从 `meta.upstream.scene` 读；本库交出去的是这一段唱词，以及唱完之后处境变了什么（`intent.one_thing`） |
| **制片与现场**（许可） | `meta.upstream.melody`；`meta.flow` | 给现成的曲子填词时，曲子的授权由制片确认；本库只在 `meta.upstream.melody` 写明旋律出处 |

★ **与导出格式的接口**：

| 去向 | 从 LYR-SPEC 取什么 | 怎么落 |
|---|---|---|
| MusicXML 领奏谱 | `lyrics[].lines`、`meta` 里的词作者 | 每个音符一个 lyric，syllabic=single；creator lyricist |
| ChordPro | `lyrics[].lines` | 歌词行，和弦由曲这一侧给 |
| ABC | `lyrics[].lines` | `w:` 行，字数与该行音符数相等 |
| LRC 等时间戳歌词 | 不从这里出 | 有了录音或 MIDI 之后，按它们的时间推 |
| 倒字校验 | `lyrics[].lines` + `prosody` | ★ 输入是旋律的实际音高（ABC 或 MusicXML）加歌词文本；只有文字描述的轮廓时按 `lw-tone-check` §2.3 手判，有谱时按谱判 |

`intent`、`imagery`、`narrative`、`rhyme`、`asymmetry` 是仅意图的块，行业里没有格式存它们，导出时整块作为文本随文件走。

### 3.2 有就读的上游字段

| 字段 | 装什么 | 本库怎么用 |
|---|---|---|
| `meta.upstream.form` | 段落表 `[{id, name, bars, energy}]`：段落 id、段落名、小节数、情绪值（0–10） | 先曲后词时是 S1 的框：`prosody.sections[].id` 与 `lyrics[].section` 照它的 id 写；`id`／`name`／`bars` 是锁死项（§3.3）；`energy` 是情绪弧，段落是推还是停参考它（`lw-structure` §1.1） |
| `meta.upstream.tempo`、`meta.upstream.key` | 速度（BPM）、调（如 `D major`） | 锁死项。速度决定一小节放得下几个字；调与音域决定最高音落在哪、哪些字要开口音（`lw-mandarin` §5.1） |
| `meta.upstream.vocal_persona` | 谁在唱：性别、年纪、人设 | 锁死项。`narrative.pov` 与用词照它写（`lw-narrative`、`lw-musical-theatre` §2） |
| `meta.upstream.melody` | 旋律出处：demo、谱、MIDI 的文件或说明；没有写 `none` | 先曲后词时，`prosody`（每句字数、重音位置、最高音、`notes`）从这里量出来 |
| `meta.upstream.brief` | 委托的要求：命题、用途、演唱者、交稿形式；没有写 `none` | `intent` 从这里读起，但五项仍由本库自己答（`lw-song-intent`） |
| `meta.upstream.scene` | 这首歌在戏或画面里的位置：剧本场次与页、cue 号与时长、前后发生了什么；不在戏里、不在画面里写 `none` | 角色唱段与有歌词的 cue 从这里拿处境与转折（`lw-musical-theatre`） |

- **来自谁不重要**：作曲编曲、配乐、剧作、委托方本人、别的工具都可以预先填。**有就读，没有就按本库自己的分析走**：没有段落表就对着旋律自己分段、数小节；没有旋律就走先词后曲；空着的项由本库补上自己读到的，注明是自拟。
- 已经填好的上游字段本库不改写。上游与本库的判断冲突（例如锁死的小节数放不下这句词），照实写进本库的字段，再往 `messages` 写一条给来源的职能。

### 3.3 与歌曲另一侧共享的六个字段

> **与歌曲另一侧共享的六个字段**：`form[].id`、`form[].bars`、`form[].name`、`meta.tempo`、`meta.key`、`vocal.persona`。两边用同一套段落 id。
> - **先做的一方定这六项**，后做的一方原样读进来，当锁死项用（`meta.upstream`）。先曲后词：作曲编曲定、作词读；先词后曲：作词定、作曲编曲读，这时词的字数和句式会反过来约束 `form[].bars`。
> - **后做的一方不改这六项。** 真要改（比如词放不进这几小节），就写一条 `messages` 给先做的一方，说清改哪一项、为什么。对方接受后改自己的规格单，后做的一方再重新读。
> - 只有一侧、另一侧的规格单不存在时，这六项由本包自己定。

本库这一侧，这六项放在：

| 共享字段 | 先曲后词（本库后做，只读） | 先词后曲，或只有词这一侧（本库定） |
|---|---|---|
| `form[].id` | `meta.upstream.form[].id`；本库的 `prosody.sections[].id`、`lyrics[].section` 照抄 | `form[].id`，与 `prosody.sections[].id`、`lyrics[].section` 相同 |
| `form[].bars` | `meta.upstream.form[].bars` | `form[].bars`：按各段句数与每句字数定（`lw-structure` §7.2） |
| `form[].name` | `meta.upstream.form[].name` | `form[].name`：`Verse`、`Pre-Chorus`、`Chorus`、`Bridge` 这类段落名 |
| `meta.tempo` | `meta.upstream.tempo` | `meta.tempo`：由每小节要放下的字数推 |
| `meta.key` | `meta.upstream.key` | `meta.key` |
| `vocal.persona` | `meta.upstream.vocal_persona` | `vocal.persona`：谁在唱，与 `narrative.pov` 一致 |

- 先曲后词时，顶层的 `form`、`vocal.persona` 与 `meta.tempo`、`meta.key` 留空，以 `meta.upstream` 为准。
- 先词后曲时 `meta.tempo`、`meta.key` 本库定不出（写词这一侧常常没有依据）：写 `null`，再写一条 `messages` 请 `music` 定；对方填了之后，本库照读。
- 段落 id 与段落名不是一回事：**id 是 `C1`、`A2`，名字是 `Chorus`、`Verse`**；refrain 是主歌的最后一两句，不单独占 id（`lw-structure` §7.3）。
- 无词的段（前奏、间奏、尾奏）在段落表里有 id，在 `prosody` 与 `lyrics` 里没有；"一一对应"指有词的段。

### 3.4 消息通道 `messages`

顶层字段，列表，每条一件事。它和 `checks.exemptions` 一样是公共区：**任何一方都可以写**。

| 字段 | 类型 | 必填 | 谁写 | 说明 |
|---|---|---|---|---|
| `messages` | list | ○ | 任何一方 | 空列表＝没有消息 |
| `messages[].from` | enum | ✅ | 发的一方 | 职能封闭集合：`lyrics`（本库）`music`（作曲编曲、配乐）`sound`（声音：录音与演唱指导、混音）`writing`（剧作）`production`（制片与现场） |
| `messages[].to` | enum | ✅ | 发的一方 | 同上，不与 `from` 相同 |
| `messages[].about` | str 或 list | ✅ | 发的一方 | 说的是哪里：字段路径（`form[C2].bars`、`prosody.sections[B1].peak_syllable`、`lyrics[C1]`）或段落 id（`"C1"`）；可写列表 |
| `messages[].says` | str | ✅ | 发的一方 | 要对方做什么、为什么；一件事一条 |
| `messages[].status` | enum | ✅ | 发的一方写 `open`，收的一方改 | `open`（发出，未回）`answered`（回了话，字段没改或还在商量）`accepted`（接受，已照它改了字段）`rejected`（不接受，`reply` 写理由） |
| `messages[].reply` | str | ○ | 收的一方 | 回话；`accepted` 时写改了哪个字段 |

1. **怎么发**：新加一条，填 `from／to／about／says`，`status: open`。本库写给别人的也放这里，`from: lyrics`，例如"C2 第 3 句十一个字放不进 4 小节，请把 C2 改成 6 小节"（`to: music`，`about: form[C2].bars`）；"B1 的最高音落在去声字上，旋律是上行进去的，请改成同音或下行进入"（`to: music`，`about: prosody.sections[B1].peak_syllable`）；"C1 末句单独成行，前面要空半拍，录音时请保留这句前的换气"（`to: sound`，`about: lyrics[C1]`）。
2. **怎么回**：收的一方只改写给自己的那条的 `status` 与 `reply`；不删别人的条目，不改 `says`。
3. **读不到对方回话就当没有，本库不等待。** `open` 的消息不挡任何门禁、不暂停任何阶段；本库按自己的判断把词写完，交付时 `open` 的消息原样交出去。下一次读到这份规格单时回话到了，再按回话处理。
4. **回话落到字段**：消息本身不改任何字段。被要求改的本库字段由本库改，改完把那条标 `accepted` 并在 `reply` 写改了什么；不改就标 `rejected` 并写理由。共享的六项只由先做的一方改（§3.3）。
5. **数据写在字段里**：字数、韵、最高音都写在各自的字段；消息只说哪里、为什么、要对方做什么。
6. 写给本库的消息（`to: lyrics`）在开工时与每次改词前读（§0 第 6 条）。

---

## 4. 为什么是这些字段

**直接对着「AI 直接写的词为什么一耳朵能听出来」清单来的：**

| AI 味症状 | 对抗项 | 可算 |
|---|---|---|
| 名词全是抽象的 | `imagery.concrete_nouns` ＋ `forbidden` | ✅ |
| 结构对称到死 | `asymmetry` 三项 | ✅ |
| 什么都解决了 | `narrative.withholding` | ⚠ |
| 没有视角和时间 | `narrative.pov` ＋ `tense_anchor` | ⚠ |
| **倒字不管** | `prosody` ＋ 检测器 | ✅ **完全可算** |
| 辙口只挑最顺的 | `rhyme.che` | ✅ |
| 押韵选第一个想到的 | `rhyme.surprise_notes` | ✅ |
| 副歌三遍全同且末遍没有一处改动 | `asymmetry.chorus_variation` | ✅ |

★ **八条里六条可算。** 比音频的同类检查更硬，**因为文本不需要检测**。
