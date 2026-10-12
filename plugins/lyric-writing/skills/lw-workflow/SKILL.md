---
name: lw-workflow
description: Entry point and router for the lyric writing library (作词工作流与路由). The two workflows that fork at the very first question - music-first versus lyrics-first - and their different stage tables, which skill to load for which task, the full-library boundary table, the LYR-SPEC gate rules, the external interface (what the spec hands out, what it reads if present, the six fields shared with the music side, the messages channel), and three checks (requests that are easy to misroute, whether a draft can be told apart from human-written lyrics, the tone check). Load this FIRST for any lyric writing request, before deciding which other skill to read. Use when starting a lyric, when fitting words to an existing melody or a melody to existing words, when unsure which skill owns a question, when a draft fails lint, or when handing the lyric on to composition, recording or scoring. 作词、歌词、填词、工作流、路由、该读哪个 skill、LYR-SPEC、先曲后词、先词后曲。
---

# 作词工作流与路由（Workflow & Routing）

**任何作词请求先读这个 skill，再决定读哪个别的。**

这个库的产出**不是歌词文本，是一份 LYR-SPEC**（词稿规格单）——
词是它的一部分，但规格单还带着"为什么这么写"和"怎么验它"。

## ★ 作词这一环最大的不同

> **作词是一首歌的制作里唯一产出纯文本的环节。**

两个后果：

1. **不用绕"先算再听"那三步** —— 文本的 AB 方法可以原样用：
   评判表在看结果前定稿、A/B 标签打乱、成对比较、同一对判两三次看结论稳不稳
2. ★ **倒字与协音可以用程序判定** ——
   普通话的倒字（声调走向与旋律走向相反 → 唱成别的字）、粤语的协音，
   **都不需要耳朵**。这让中文歌词第一次有了客观判据，
   **地位相当于音频里的速度（tempo）**：少数能直接量准、拿来对照的量

---

## 0. 三十秒定位

| 你现在要做的事 | 去 |
|---|---|
| 从零写一首词 | ★ **先答 §1 那个岔路口**，再走对应的阶段表 |
| 给现成旋律填词 | §2 先曲后词 |
| 先写词再谱曲 | §3 先词后曲 |
| 不知道某个问题归哪个 skill | §4 全库边界表 |
| lint 不过 | §5.2 |
| 要把词交出去（作曲编曲、录音、配乐、戏） | §6 |
| 要检验：请求归哪、词像不像人写的、倒字 | §7 |
| 想知道这个库现在能用到什么程度 | ★ §8 |

---

## 1. ★ 第一个岔路口：哪种流程

**这是本库唯一一个必须先答的问题，因为两条路的阶段表完全不同。**

```
先曲后词：meta.upstream（段落表 ＋ 旋律）  ──→  LYR-SPEC 的 prosody 约束
先词后曲：LYR-SPEC 的字数句式             ──→  交出去约束小节数 form[].bars
```

★ **两条路里数据的方向相反，规则只有一条：谁先做谁定，后做的一方只读**（§6.1）。

| 问 | 答 |
|---|---|
| 已经有旋律/demo 了吗 | 有 → **先曲后词**（§2） |
| 是命题作文、有既定曲子吗 | 是 → 先曲后词 |
| 词的内容比曲更重要吗 | 是 → 考虑**先词后曲**（§3） |
| 是粤语吗 | ★ **粤语几乎必然是先曲后词**——协音让旋律直接决定每个位置能用什么字（见 `lw-cantonese`） |

---

## 2. 阶段表：先曲后词

| 阶段 | 做什么 | 产出 | 门禁 |
|---|---|---|---|
| **S0 立意** | 把 brief 变成"只说一件事" | `intent` 五项 | ★ **五项齐全**，`plot_type` 先答且不默认叙事型，`anchor_object` 必须是**能拍照的实物** |
| **S1 接规格** | 从 `meta.upstream` 读段落、小节数、情绪弧与旋律；没有段落表就对着旋律或 demo 自己分段、数小节，填进 `meta.upstream.form` 并注明自拟 | `prosody.sections` 的框 | 段落 id 与 `meta.upstream.form[].id` **一一对应** |
| **S2 量句** | 逐句数音节/字数、标重音位置、标**最高音落在哪个字** | `prosody` 填满 | ★ **`peak_syllable` 必填**——那个字要经得起唱 |
| **S3 找物件与意象** | object writing，凑出具体名词清单 | `imagery` | 抽象词黑名单清零 |
| **S4 写词** | 按 prosody 的格子填 | 词稿 | |
| **S5 语言层检查** | 倒字/协音/辙口/重音 | `checks.computed` | ★ 普通话查倒字率，粤语**协音违例必须为 0**。★★ **手判的结果必须写进 `checks.computed`**（倒字率、查了哪些位置、哪几个字倒了、怎么处理），只读了 `lw-tone-check` 不写记录等于没查，lint 第 7 条直接不过 |
| **S6 反对称** | 刻意破坏整齐 | `asymmetry` 三项 | 至少填两项 |
| **S7 验收** | LYR-LINT + AI 味清单 | | 10 条全过 |

---

## 3. 阶段表：先词后曲

| 阶段 | 做什么 | 与先曲后词的差别 |
|---|---|---|
| **S0 立意** | 同上 | 一样 |
| **S1 定形** | 先定段落与句式 | ★ **没有外来约束，自己定**——所以更容易写得整齐划一，**§6 的反对称要更用力** |
| **S2 写词** | 按自己的句式写 | |
| **S3 量句** | ★ **反过来**：数出每句字数，**按字数句式定 `form[].bars`** | 本包先做，六个共享字段由本包定（§6.1） |
| **S4 语言层检查** | ★ **此时还没有旋律，倒字查不了** | ⚠ **倒字检查要等旋律出来再补做** |
| **S5 交接** | 交出规格单：字数句式、六个共享字段、字调轮廓（§6） | |
| **S6 回检** | ★ **旋律回来之后，必须重跑倒字/协音检查** | **这一步最常被漏** |

★★ **先词后曲的最大陷阱**：
**词定稿了，旋律配上去才发现倒字。** 那时改词代价很大。
**对策**：S2 写词时就把每句的"字调轮廓"标出来，写进 `prosody.sections[].melody_contour`，交出去当旋律约束的一部分。

---

## 4. 全库边界表

### 4.1 按问题查

| 问题 | Owner |
|---|---|
| 这首歌要说什么 | `lw-song-intent` |
| 段落功能、hook 与标题放哪、句式稳不稳 | `lw-structure` |
| 意象、具体名词、object writing | `lw-imagery` |
| 押韵、韵式、什么时候故意不押 | `lw-rhyme` |
| 人称、视角、时间锚点、留白 | `lw-narrative` |
| **倒字、十三辙、平仄** | `lw-mandarin` |
| **协音**（粤语） | ★ `lw-cantonese`（**不许用普通话那套顶替**） |
| 英文的重音与节拍对齐 | `lw-english` |
| **日文按モーラ填词、符割り、字余り** | `lw-japanese` |
| **韩文按音节填词、받침（收音）、连音与音变** | `lw-korean` |
| 中国风 | `lw-chinese-style` |
| 音乐剧、角色唱词 | `lw-musical-theatre` |
| 说唱的押韵密度与 flow | `lw-rap` |
| **倒字检测器怎么用、结果怎么读** | `lw-tone-check` |
| 交稿前的 AI 味终检 | `lw-ai-tell-audit` |
| 找一个真实例子 | `lw-case-studies` |

### 4.2 ★ 最容易混的几组分界

★ **`lw-japanese` ⇄ `lw-korean`**：日文按モーラ数，促音・撥音・長音各占一拍；韩文按谚文字块数，收音不另占拍。拿日文那套去数韩文，每个闭音节都会多数一拍。

| A ⇄ B | 分界线 |
|---|---|
| `lw-rhyme` ⇄ `lw-mandarin` | **rhyme 管押韵这件事本身（韵式、意外度、故意不押）；mandarin 管中文的韵表（十三辙）与字调** |
| `lw-mandarin` ⇄ `lw-cantonese` | ★ **不是"换张韵表"**。粤语的协音是**硬约束且写作顺序反转**——旋律定了，每个位置只剩几个字可选 |
| `lw-imagery` ⇄ `lw-narrative` | **imagery 管"用什么东西说"；narrative 管"谁在说、什么时候说、哪些不说"** |
| `lw-structure` ⇄ 作曲编曲 | ★ **词的段落功能归这里；曲式的小节数归作曲编曲。** 段落 id 两边共用（§6.1） |
| 本库 ⇄ 演唱指导 | ★ **字怎么安到音上（符割り）归本库；那些字该怎么唱（气声/力度/修音）归演唱指导（声音）** |

### 4.3 一律出库

| 内容 | 归哪个职能 |
|---|---|
| 旋律、和声、编曲、曲式小节数 | **作曲编曲** |
| 人声录音、修音、演唱指导 | **声音**（录音与演唱指导） |
| 为画面写音乐 | **配乐** |
| 不入乐的诗歌 | 不是歌词，不在本包 |
| 戏曲唱词的**曲牌格律**、板式句格 | **剧作**（戏曲编剧）。本库只借韵与字调：十三辙在 `lw-mandarin`（戏曲读法见其 reference §1.5），唱词选韵的三好在 `lw-mandarin` reference §7，依字行腔在 `lw-tone-check` §1 |

出库的东西只经 LYR-SPEC 交出去（§6）。

---

## 5. LYR-SPEC

**完整规范在本 skill 目录下的 [LYR-SPEC.schema.md](LYR-SPEC.schema.md)，空模板 [LYR-SPEC.template.yaml](LYR-SPEC.template.yaml)，填好的例子 [example-01-jacket.yaml](example-01-jacket.yaml)（正）与 [example-00-ai-default.yaml](example-00-ai-default.yaml)（反）。**

★ **写规格单前先 Read 模板，照它的字段名填。** **写完 `prosody.syllables` 之后对着词逐行点一遍字数再交**，这一项是最稳定的差一个字的地方。 不看模板的话字段名会自己长出来（实测写成过 `said_to`、`moment`，而规范里是 `to_whom`、`at_what_moment`），读这份规格单的人就接不上了。

★ **YAML 自查**（最常写坏的两处）：
- 值里用了引号就整句都在引号里，**不要引号外再续写**（`peak_syllable: "价"（第二杯半价）—— 去声` 这样整份文件都解析不了）
- 列表项 `- {…}` 下面**不能再挂 `note:` 键**，要注释用同级 `xxx_note:` 或 `#` 行注释

### 5.1 ★ 为什么是这些字段

**每一个字段都对着一条"AI 直接写的词为什么一耳朵能听出来"：**

| AI 味症状 | 对抗字段 | 可算 |
|---|---|---|
| 名词全是抽象的 | `imagery.concrete_nouns` 必填、`forbidden` 黑名单 | ✅ |
| 结构对称到死 | `asymmetry` 三项必填 | ✅ |
| 什么都解决了，没有悬着的 | `narrative.withholding` 必填 | ⚠ 半自动 |
| 没有视角和时间 | `narrative.pov` ＋ `tense_anchor` | ⚠ 半自动 |
| **倒字不管** | `prosody` ＋ 倒字检测器 | ✅ **完全可算** |
| 辙口只挑最顺的 | `rhyme.che` ＋ 辙口分布 | ✅ |
| 押韵永远选第一个想到的字 | `rhyme.surprise_notes` | ✅ |
| 副歌原样重复三遍 | `asymmetry.chorus_variation` | ✅ |

★ **九条里七条可算。** 比音频的同类检查更硬，**因为文本不需要检测**。

### 5.1b ★ 十条怎么过：用眼睛，不用工具

本库不需要用户机器上有任何工具——没有脚本、不预设 Python 或 Node。
- LYR-LINT 十条全部**手工逐条过**（下表每条都是能用眼睛判的），结果写进 `checks.self_audit`
- 倒字：用 `lw-tone-check` §2.2 的五个调型表**手判**——只对每段最高音、每句首字、大跳落点这三类位置查（约占全部字的 1/5），不必全查；★ 判完把结果写进 `checks.computed`（例：`倒字: {查了: 18 字, 倒: ["暖", "口"], 率: 0.11, 处理: "暖 改 温"}`），这一步漏掉是最常见的失分点
- ★ **十条是判据不是铁律**：不过的条目改掉，或写一句为什么这首词就该这样。写了理由的偏离是合法选择，不是"没过"
- **不要为了检查去写脚本**

### 5.2 LYR-LINT 十条

| # | 检查 | 不过时去看 |
|---|---|---|
| 1 | `intent` 五项非空，`plot_type` 在封闭集合里，`anchor_object` 是能拍照的实物 | `lw-song-intent` |
| 2 | 每段至少 N 个具体名词；`forbidden` 抽象词零出现 | `lw-imagery` |
| 3 | 各段字数不许完全相同 | `lw-structure` |
| 4 | `asymmetry` 三项至少填两项 | `lw-structure` |
| 5 | `narrative.withholding` 非空 | `lw-narrative` |
| 6 | `pov` ＋ `tense_anchor` 非空 | `lw-narrative` |
| 7 | **倒字率 ≤ 阈值（普通话）／协音违例 = 0（粤语）** | `lw-tone-check` |
| 8 | 辙口不许全曲只用一两个宽辙 | `lw-mandarin` |
| 9 | 韵脚意外度：不许全是最高频韵字 | `lw-rhyme` |
| 10 | 副歌各遍文本不许完全相同 | `lw-structure` |

⚠ **第 2、7、8、9 条只报数，不判过/不过。**
★ 这意味着**第 7、8、9 条只能给出数值，不能给出"过/不过"**。

---

## 6. 对外接口

本库对外只经 LYR-SPEC：交出去什么、读什么、有事怎么说，都写在规格单里；不假设读的人是谁、用什么工具。每个字段怎么理解见 [LYR-SPEC.schema.md](LYR-SPEC.schema.md) §3。

| 交给哪个职能 | 交出去 | 有就读（`meta.upstream`） |
|---|---|---|
| **作曲编曲**（旋律、和声、编曲、曲式小节数） | `lyrics[]`；`prosody.sections[]`（每句字数、重音位置、**最高音落在哪个字**；先词后曲时还有字调轮廓）；先词后曲时本库定的六个共享字段（§6.1）；`checks.computed` 的倒字记录 | 段落表 `form`（段落 id、名、小节数、情绪值）、速度、调、谁在唱、旋律出处——先曲后词时就是 S1 的输入 |
| **声音**（录音与演唱指导） | `lyrics[]`（录音与修音的参考）；`vocal.persona`、`narrative.pov`；倒字高风险字与要装饰音才救得回来的字（`checks`） | — |
| **配乐**（有歌词的 cue） | `intent`、`narrative`、`lyrics[]` | 这首歌在画面里的位置（`scene`：cue、时长、前后发生了什么） |
| **剧作**（戏里的唱段） | `intent`、`narrative`、`lyrics[]` | 这场戏的出处与转折（`scene`） |

- **有就读，没有就按本库自己的分析走**：没有段落表就对着旋律自己分段；没有旋律就走 §3 先词后曲；不在戏里、不在画面里的歌，`scene` 写 `none`。
- 读进来的上游字段本库不改写。上游与本库的判断冲突时，本库照实写自己的字段，再写一条消息（§6.2）。

### 6.1 ★ 与歌曲另一侧共享的六个字段

`form[].id` / `form[].bars` / `form[].name` / `meta.tempo` / `meta.key` / `vocal.persona`

- **谁先做谁定，后做的一方只读**：先曲后词时，这六项在 `meta.upstream` 里，本库当锁死项用；先词后曲时由本库定、交出去——词的字数和句式就是 `form[].bars` 的依据。
- **后做的一方不改这六项**：词放不进这几小节，就写一条消息给 `music`，说清改哪一项、为什么；对方接受后改了，本库再重新读。
- 只有词这一侧时，这六项由本库自己定。规则原文与每一项放在哪，见 schema §3.3。

### 6.2 消息怎么写

`messages` 是规格单顶层的公共区，每条 `{from, to, about, says, status, reply}`，本库写 `from: lyrics`；`to` 取 `music`（作曲编曲、配乐）、`sound`（声音）、`writing`（剧作）、`production`（制片）。
- 例：`to: music`，`about: form[C2].bars`，`says`："C2 第 3 句十一个字放不进 4 小节，请把 C2 改成 6 小节"。
- 读不到回话就当没有，**本库不等待**：`open` 的消息不挡任何门禁，词照自己的判断写完，交付时原样交出去。
- 写给本库的消息（`to: lyrics`）在 S0 开工时与每次改词前读。

---

## 7. 三样检验

### 7.1 最容易走错的几类请求

- 「帮我写段旋律」→ **出库**：作曲编曲
- 「这个混音人声太糊」→ **出库**：声音（混音）
- 「什么是十三辙」→ 只读 `lw-mandarin`，**不开全流程**
- 「给这首粤语歌填词」→ **必须读 `lw-cantonese`**，不许只用普通话那套
- 「把这段词改成说唱」→ `lw-rap`，不该惊动语言层以外的东西

### 7.2 ★ 一稿词拿什么判

> **判据只有一条：这一稿能不能和人手写的词分开。**
>
> - 被当成"人写的" → **这一稿立住了**
> - 仍能和手写的分开 → **差的那一截就是还要改的地方**

做法就是开头说的文本 AB：评判表在看结果之前定稿（用 `lw-ai-tell-audit` §2 的八条），把这一稿和人手写的词打乱 A/B 标签，请不知情的人成对比较，同一对判两三次看结论稳不稳。差的那一截按 `lw-ai-tell-audit` §5 找归哪个 skill 改。

### 7.3 倒字检测

判据、五调约束、三条边界（一字多音、语境消歧、风险≠错）与五种改法见 `lw-tone-check` §2~§6。
★ **这是本库唯一一个不需要任何教材就能建、且立刻产生客观判据的东西**，所以这里只放路由，不重复正文。

---

## 8. ★ 本包的覆盖范围

| | 本包有 | 本包没有 |
|---|---|---|
| **语言层** | 普通话（十三辙、平仄、倒字）、粤语（协音）、英文（重音与节拍）、日文（モーラ、符割り）、韩文（音节与 받침、连音、音变） | 无 |
| **体裁层** | 中国风、音乐剧唱词、说唱 | 民谣叙事 |

★ **五套语言约束不可互相顶替**：中文靠字调、粤语靠协音、英文靠重音、日文靠拍数、韩文靠音节与收音。
拿其中一套去查另一套，得到的是自信的错误答案。对照见 `lw-korean` §7 与 §4.2。
体裁层缺民谣叙事，遇到这类请求用 L1 通用层，并说明体裁惯例没有覆盖。

每个 skill 的「附」列出它依据的书。

---

## 9. 开工前自检

- [ ] 答了 §1 的岔路口：**先曲后词还是先词后曲**
- [ ] `intent` 五项**想出来的**，不是为了过 lint 填的
- [ ] `prosody.syllables` 是**词写完后对着每一行数出来的**（只数汉字），不是先填再写词
- [ ] `anchor_object` 是**能拍照的实物**
- [ ] 段落 id 与 `form[].id`（先曲后词时是 `meta.upstream.form[].id`）对齐
- [ ] 读过写给本库的消息（`messages` 里 `to: lyrics` 的条目）
- [ ] 语言选定了，且读了对应的 L2 skill（**粤语不许用普通话那套顶替**）
- [ ] 先词后曲的话，**记得旋律回来后重跑倒字检查**（§3 的 S6）
- [ ] 写完跑 LYR-LINT 与 `lw-ai-tell-audit`

---

## 附：目录地图

```
本包的文件（全是文本）：
  skills/<17 个 skill>/SKILL.md, reference.md
  skills/lw-workflow/LYR-SPEC.schema.md      ★ 规格单定义（v1.0）
  skills/lw-workflow/LYR-SPEC.template.yaml  空模板
  skills/lw-workflow/example-*.yaml          填好的示例（外套 / 反面样本）
```
