---
name: lw-workflow
description: Entry point and router for the lyric writing library (作词工作流与路由). The two workflows that fork at the very first question - music-first versus lyrics-first - and their different stage tables, which skill to load for which task, the full-library boundary table, the LYR-SPEC gate rules, the bidirectional interface with the arrangement library, and the three testing devices. Load this FIRST for any lyric writing request, before deciding which other skill to read. Use when starting a lyric, when fitting words to an existing melody or a melody to existing words, when unsure which skill owns a question, when a draft fails lint, or when handing work to another library. 作词、歌词、填词、工作流、路由、该读哪个 skill、LYR-SPEC、先曲后词、先词后曲。
---

# 作词工作流与路由（Workflow & Routing）

**任何作词请求先读这个 skill，再决定读哪个别的。**

这个库的产出**不是歌词文本，是一份 LYR-SPEC**（词稿规格单）——
词是它的一部分，但规格单还带着"为什么这么写"和"怎么验它"。

## ★ 这个库与另外两个库最大的不同

> **作词是整条音频线里唯一产出纯文本的环节。**

两个后果：

1. **不用绕"先算再听"那三步** —— 剧本那套 AB 方法可以原样搬：
   评判表在看结果前定稿、A/B 标签打乱、成对比较、同一对判两三次看结论稳不稳
2. ★ **倒字与协音可以用程序判定** ——
   普通话的倒字（声调走向与旋律走向相反 → 唱成别的字）、粤语的协音，
   **都不需要耳朵**。这让中文歌词第一次有了客观判据，
   **地位相当于音频线里的 tempo**（而 tempo 恰好是库一唯一校准成功的那一项）

---

## 0. 三十秒定位

| 你现在要做的事 | 去 |
|---|---|
| 从零写一首词 | ★ **先答 §1 那个岔路口**，再走对应的阶段表 |
| 给现成旋律填词 | §2 先曲后词 |
| 先写词再谱曲 | §3 先词后曲 |
| 不知道某个问题归哪个 skill | §4 全库边界表 |
| lint 不过 | §5.2 |
| 要交给别的库 | §6 |
| 要跑测试 | §7 |
| 想知道这个库现在能用到什么程度 | ★ §8 |

---

## 1. ★ 第一个岔路口：哪种流程

**这是本库唯一一个必须先答的问题，因为两条路的阶段表完全不同。**

```
先曲后词：ARR-SPEC.form ＋ 旋律符割り  ──→  LYR-SPEC 的 prosody 约束
先词后曲：LYR-SPEC 的字数句式         ──→  反向约束 ARR-SPEC.form[].bars
```

★ **库一对下游是单向的，这里是双向的**——这是本库的结构特点。

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
| **S1 接规格** | 从 ARR-SPEC 取段落、小节数、情绪弧 | `prosody.sections` 的框 | 段落 id 与 `ARR-SPEC.form[].id` **一一对应** |
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
| **S3 量句** | ★ **反过来**：数出每句字数，**交给库一去定 `form[].bars`** | 这是双向接口的另一半 |
| **S4 语言层检查** | ★ **此时还没有旋律，倒字查不了** | ⚠ **倒字检查要等旋律出来再补做** |
| **S5 交接** | 把字数句式送给库一 | |
| **S6 回检** | ★ **旋律回来之后，必须重跑倒字/协音检查** | **这一步最常被漏** |

★★ **先词后曲的最大陷阱**：
**词定稿了，旋律配上去才发现倒字。** 那时改词代价很大。
**对策**：S2 写词时就把每句的"字调轮廓"标出来，交给库一当旋律约束的一部分。

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
| 词稿怎么变成 Suno 的输入 | `lw-suno-interface` |
| 交稿前的 AI 味终检 | `lw-ai-tell-audit` |
| 找一个真实例子 | `lw-case-studies` |

### 4.2 ★ 最容易混的几组分界

★ **`lw-japanese` ⇄ `lw-korean`**：日文按モーラ数，促音・撥音・長音各占一拍；韩文按谚文字块数，收音不另占拍。拿日文那套去数韩文，每个闭音节都会多数一拍。

| A ⇄ B | 分界线 |
|---|---|
| `lw-rhyme` ⇄ `lw-mandarin` | **rhyme 管押韵这件事本身（韵式、意外度、故意不押）；mandarin 管中文的韵表（十三辙）与字调** |
| `lw-mandarin` ⇄ `lw-cantonese` | ★ **不是"换张韵表"**。粤语的协音是**硬约束且写作顺序反转**——旋律定了，每个位置只剩几个字可选 |
| `lw-imagery` ⇄ `lw-narrative` | **imagery 管"用什么东西说"；narrative 管"谁在说、什么时候说、哪些不说"** |
| `lw-structure` ⇄ 库一的 `mc-form` | ★ **词的段落功能归这里；曲式的小节数归库一。** 两边共享 `form[].id` |
| 本库 ⇄ 库一的 `mc-vocal-direction` | ★ **字怎么安到音上（符割り）归本库；那些字该怎么唱（气声/力度/修音）归库一** |

### 4.3 一律出库

| 内容 | 去哪 |
|---|---|
| 旋律、和声、编曲 | **库一** 作曲编曲库 |
| 人声录音、修音、演唱指导 | **库三** 声音设计与混音库 |
| 为画面写音乐 | **库二** 配乐库 |
| 不入乐的诗歌 | 不在音频线内 |
| 戏曲唱词的**曲牌格律** | **编剧库**的戏曲层 |

---

## 5. LYR-SPEC

**完整规范在本 skill 目录下的 [LYR-SPEC.schema.md](LYR-SPEC.schema.md)，空模板 [LYR-SPEC.template.yaml](LYR-SPEC.template.yaml)，填好的例子 [example-01-jacket.yaml](example-01-jacket.yaml)（正）与 [example-00-ai-default.yaml](example-00-ai-default.yaml)（反）。**

★ **写规格单前先 Read 模板，照它的字段名填。** **写完 `prosody.syllables` 之后对着词逐行点一遍字数再交**，这一项是最稳定的差一个字的地方。 不看模板的话字段名会自己长出来（实测写成过 `said_to`、`moment`，而规范里是 `to_whom`、`at_what_moment`），对面的库就接不上了。

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

★ **九条里七条可算。** 比库一的比例更硬，**因为文本不需要检测**。

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

## 6. 跨库接口

| 对方 | 进来 | 出去 |
|---|---|---|
| **库一（作曲编曲）** | `ARR-SPEC.form`（段落/小节数/情绪值）＋ 符割り规格（每句音节数、重音位置、**最高音落在哪个字**） | 先词后曲时，字数句式**反向约束** `form[].bars` |
| **编剧库** | ✅ **戏曲层的十三辙表、「唱词三好」、依字行腔** —— ★ **倒字在戏曲里就是这个名字，同一个问题的老版本，直接跨库引用** | — |
| 配乐库 / 声音设计库 | — | 有歌词的 cue / 词稿给录音参考 |

### 6.1 ★ 与库一必须一致的六个字段

`form[].id` / `form[].bars` / `form[].name` / `meta.tempo` / `meta.key` / `vocal.persona`

**任何一边改了这六项，另一边必须同步。** 这是双向耦合唯一的代价。

---

## 7. 三个测试装置

### 7.1 路由／污染测试

本库用 20 条典型请求做路由回归（仓库内，不随包发布），含陷阱：
- 「帮我写段旋律」→ **出库**到库一
- 「这个混音人声太糊」→ **出库**到库三
- 「什么是十三辙」→ 只读 `lw-mandarin`，**不开全流程**
- 「给这首粤语歌填词」→ **必须读 `lw-cantonese`**，不许只用普通话那套
- 「把这段词改成说唱」→ `lw-rap`，不该惊动语言层以外的东西

### 7.2 ★ AB 实验：本库最便宜的那个

> **同一首曲子，三组词：AI 直写 / skill 引导 / 手写，都过 Suno，盲听打乱。**
>
> - skill 组被听成"人写的" → **作词库的价值立住**
> - 听众仍能把它和手写组分开 → **差的那一截就是接下来要补的规则**

★ **这是整条音频线最便宜的对照实验**——全在文本层，不需要生成音频就能做前半段。
**副产品**：一份 AI 味清单，直接当 `lw-ai-tell-audit` 的骨架。

★ **评判表必须在看结果之前定稿。**

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
- [ ] 段落 id 与 `ARR-SPEC.form[].id` 对齐
- [ ] 语言选定了，且读了对应的 L2 skill（**粤语不许用普通话那套顶替**）
- [ ] 先词后曲的话，**记得旋律回来后重跑倒字检查**（§3 的 S6）
- [ ] 写完跑 LYR-LINT 与 `lw-ai-tell-audit`

---

## 附：目录地图

```
随包发布（用户拿到的就是这些，全是文本）：
  skills/<19 个 skill>/SKILL.md, reference.md
  skills/lw-workflow/LYR-SPEC.schema.md      ★ 规格单定义（v1.0）
  skills/lw-workflow/LYR-SPEC.template.yaml  空模板
  skills/lw-workflow/example-*.yaml          填好的示例（外套 / 反面样本）

仓库内、不随包发布（skill 里提到它们只是标注来源）：
  本库架构文档、读书笔记、实验记录、lint 与倒字检测器
```
