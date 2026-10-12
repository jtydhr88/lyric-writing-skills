# lyric-writing-skills

English · [中文版](README_ZH.md) · [日本語](README_JA.md) · [한국어](README_KO.md)

17 agent skills (for [Claude Code](https://docs.anthropic.com/en/docs/claude-code/skills) and [OpenAI Codex](https://developers.openai.com/codex/)) for writing song lyrics, distilled from 29 books across four languages, covering English craft manuals, Chinese prosody and songwriting, Cantonese practice and Korean phonology, plus two volumes of Sondheim's collected lyrics with his own commentary.

Both agents share the same skill files: install once and it works in both.

**Along with the words, you get a spec sheet.** Ask for a lyric and the agent fills in a LYR-SPEC, the lyric spec sheet, which records the one thing this song says, who it is said to, at what moment, the object that runs through it, the syllable count and stress position of every line, the rhyme scheme, the deliberate asymmetries, and the language-layer checks. The same document is what you check the draft against.

**What it is for.** A lyric can be judged, and this library is the set of judgements: say one thing, anchor it to an object you could photograph, know who is speaking and when, let the line shape do work, take the rhyme that is not the first one anyone would reach for. Every gate in it exists to force an actual choice.

**Ask in your own language.** The skill bodies are written in Chinese, because most of the sources are Chinese originals or Chinese translations. The agent answers in whatever language you ask in.

**These skills trade time for quality.** A full pass through a professional music workflow often takes twenty minutes or more for a single song (the agent reads the criteria, fills in the spec, runs the checklists). What you get in return is a professional-grade spec.

**This library ships no musical works at all, neither the author's own nor any other artist's, no arrangements and no lyrics.** Whether a piece of music is good is a subjective call. Use it yourself and judge for yourself what it is worth, and what it costs you in time.

## The four libraries in this series

One audio line, cut into four independent libraries. Each one is usable on its own; the seams between them are written down, so they also combine.

| Library | What it does | State |
|---|---|---|
| **[music-composition-skills](https://github.com/jtydhr88/music-composition-skills)** | Composing and arranging. A brief becomes an ARR-SPEC (arrangement spec sheet): key, tempo, section map, harmony, who enters and leaves when, the energy curve, vocal and mix intent | Available |
| **[lyric-writing-skills](https://github.com/jtydhr88/lyric-writing-skills)** | Lyric writing. The intent gate becomes a LYR-SPEC: structure, imagery, rhyme, narrative, plus the language layer for Mandarin, Cantonese, English, Japanese and Korean | **This library** |
| **Film scoring** | Music written to picture: spotting, the relation to cuts, how a cue is written and named, how a theme develops across a film | Planned |
| **Mixing and sound design** | Turning mix intent into actual moves: EQ, compression, reverb, automation, mastering | Planned |

**Independent.** Filling words to an existing melody needs the lyric library only. Arranging an instrumental needs the composition library only.

**Combinable, through named handoffs.** ARR-SPEC and LYR-SPEC share six fields: section id, bar count, section name, tempo, key, and who is singing. Whoever works first sets them and whoever works second only reads them: music-first, composition and arrangement set them; lyrics-first, the lyricist sets them, and line lengths and stress positions then constrain the bar counts. If the second side needs one of the six changed, it sends a message to the first side and re-reads once that side has made the change. Lyrics-first, tempo and key may be left empty for composition and arrangement to set. The mix-intent section of an ARR-SPEC is what is handed to whoever does the mix; a cue sheet from whoever scores the picture is the brief handed to composition and arrangement.

**The seams are written into the spec sheets.** Each library is self-contained and works when installed on its own; no skill names another library or assumes you have installed one. Anything a library does not own is handed to the role that owns it, named by that role: EQ and compression practice belongs to mixing, spotting and cue writing belong to film scoring. Libraries meet only through the spec sheet: its external-interface section lists the fields handed out and the upstream fields read when present, and there is a message channel any side may write to.

## Why this exists

Lyric writing is a craft with a long written tradition: Pattison and Davis on the English side, 王力 on Chinese prosody, 黄志华 on Cantonese, Sondheim on writing for a character. **This library turns that tradition into the choices a professional lyricist would make.**

The agent writing the lyric is itself a language model. It will write you four verses in ten seconds. They will rhyme, they will scan, and they will be full of imagery. What is missing is the choosing. Whatever you leave undecided, it supplies from the average of everything it has read, and an average is the one thing no good song has ever been.

So this library makes it choose the way a professional lyricist would: the one thing this song says, who is being spoken to, the minute it is being said in, the object that recurs and changes meaning each time, which line breaks the pattern and why, which character may not sit on that note because the tone would turn it into a different word. **What it adds is the choosing.**

For Chinese lyrics there is a second reason, and it is not a matter of taste. A tone-melody mismatch in Mandarin makes a listener hear a different word; in Cantonese it simply is a different word. A model that writes beautiful lines with no tone checking produces lyrics that fall apart the moment they are sung. Those constraints are computable, and this library is where they are written down.

What it hands over is a lyric sheet for the singer and for composition and arrangement, with the reasons attached.

## Install

### Claude Code

#### Plugin marketplace (recommended)

```
/plugin marketplace add jtydhr88/lyric-writing-skills
/plugin install lyric-writing@lyric-writing-skills
```

Skills are then invoked as `/lyric-writing:<skill>`, e.g. `/lyric-writing:lw-workflow`.

#### Personal (all projects)

```bash
git clone https://github.com/jtydhr88/lyric-writing-skills.git
cp -r lyric-writing-skills/plugins/lyric-writing/skills/* ~/.claude/skills/
```

#### Project-specific

```bash
mkdir -p .claude/skills
cp -r lyric-writing-skills/plugins/lyric-writing/skills/* .claude/skills/
```

### Codex (CLI / ChatGPT desktop app / IDE extension)

```bash
codex plugin marketplace add jtydhr88/lyric-writing-skills
# Then: Plugins → select "Lyric Writing Skills" → Install
```

Or copy the same files to `~/.agents/skills/` (personal) or `.agents/skills/` (project).

#### Verify

Skills load automatically when the agent detects relevant context. To list them: `/skills`.

## Usage examples

```
# "Write a lyric for this melody. Here are the bars and the syllable counts"
# → lw-workflow (music-first track) → lw-song-intent → lw-structure → lw-mandarin

# "This draft reads fine but feels generic and I can't say why"
# → lw-ai-tell-audit: eight enumerated tells, then the skill that owns each one

# "Fill a Cantonese melody"
# → lw-cantonese: the pitch-class system, then choose characters. The writing
#   order is reversed for Cantonese and no other language layer substitutes

# "Turn this verse into rap"
# → lw-rap (rhyme density, multisyllable rhyme, the Mandarin transfer table)

# "Does this line sing as the words I wrote, or as different words?"
# → lw-tone-check: check the peak of each section, the first character of each
#   line, and the landing of every leap. That is about a fifth of the characters
```

## Common combinations

This is more involved than it looks. A one-sentence brief pulls in a dozen skills across composition, arrangement and lyrics, and what the agent reads and produces depends on whether that sentence names a few key things. Below are combinations that have actually been run end to end: how to say it, which skills it walks, what comes out. Anything with lyrics needs both the music library and the lyric library installed.

**1. A song with lyrics in the style of a named artist** (the most common case)

> Write a Mandarin pop song in the style of a named artist's song, female vocal, with lyrics.

Walks: lw-workflow → lw-song-intent → lw-structure → lw-mandarin → lw-tone-check; mc-workflow → mc-style-chinese-pop → mc-melody → mc-development → mc-arrangement-arch → mc-vocal-direction
Produces: a LYR-SPEC and an ARR-SPEC
Note: the reference artist lends instrumentation, tempo, vocal persona and section layout. Never words or melody.

**2. A Douyin-style earworm, no storytelling**

> Write a Douyin earworm, female, sweet, no storytelling, with lyrics.

Walks: lw-song-intent (attitudinal) → lw-structure (repetition budget, hook placement) → lw-rhyme → lw-mandarin; mc-style-chinese-pop → mc-rhythm-groove → mc-arrangement-arch
Note: "no storytelling" is what sets the lyric type. Leave it out and you get a situational lyric by default.

**3. A sad love song that says it straight, no scenery**

> Write a sad love song like a named artist's ballad, male vocal, with lyrics. The kind that says it directly, no scene description.

Walks: as in 1, but lw-song-intent takes the attitudinal route and the anchor is a sentence (the line that opens every chorus); mc-vocal-direction handles the close-mic male voice and the bare final line
Note: in the corpus, four in ten attitudinal songs contain nothing you could photograph. The chorus is one sentence said to "you", the verses state how I am, the opener is a monologue. To get that, say "say it directly, no scenes, no objects" in the brief.

**4. A feeling, with no story**

> Write a Mandarin pop song, three and a half minutes, female vocal. The subject: on moving day I left the charger cable in the wall socket, walked two blocks before remembering, and did not go back. Not a story. I want the feeling of remembering and letting it go.

Walks: lw-song-intent (situational, anchor object = the cable) → lw-imagery → lw-structure → lw-mandarin → lw-tone-check; music side as in 1
Note: this is the line between situational and narrative. There is an object; there is no plot advancing.

**5. An instrumental, composed from nothing**

> Write a two-minute-forty instrumental as a short-video bed. Lead is a nylon-string guitar, a little percussion and bass, one keyboard allowed. The feel is "three in the afternoon, waiting for someone, no hurry". No vocals.

Walks: mc-workflow → mc-development (motif, character, development devices) → mc-melody → mc-form → mc-harmony → mc-rhythm-section → mc-orchestration
Produces: an ARR-SPEC (the thematic material and each section's development filled in), a one-page note
Note: no lyrics, so the lyric library stays out. The criterion lives in mc-development: new material under half, and a return.

**6. Melody and words exist, arrangement only**

> Arrange a Mandarin love song whose melody and lyrics are already written. I want a salsa feel, with brass, medium-fast. Spec only.

Walks: mc-workflow (arrangement route) → mc-style-latin → mc-rhythm-section → mc-orchestration (brass) → mc-arrangement-arch → mc-texture-layering
Produces: an ARR-SPEC and a one-page note, nothing else

**7. Fusion: rap verses, Chinese-style chorus**

> Write a song like a named song, rap plus Chinese style, full Chinese lyrics.

Walks: mc-workflow §2.4 fusion → mc-style-hiphop (base) + mc-style-chinese-pop (overlay); lw-rap (verses) + lw-chinese-style (chorus) + lw-mandarin

**8. Cantonese lyric to a given melody**

> Fill this melody with Cantonese lyrics. Bars and syllables per line are attached.

Walks: lw-workflow (music-first) → lw-cantonese (compute by pitch class first, then choose characters) → lw-tone-check
Note: Cantonese writes in the reverse order, and the Mandarin layer cannot stand in for it.

The sentences in a brief that actually do something:

| What you say | What it decides |
|---|---|
| artist + song title | instrumentation, tempo, vocal persona, section layout are borrowed; words and melody never are |
| female / male, sweet / close-mic | persona and range in mc-vocal-direction |
| no storytelling / say it straight, no scenes / not a story | lyric type: attitudinal / attitudinal without objects / situational. Unsaid, situational is the default |
| duration | section count and bar count are derived from it |
| a list of deliverables | name the files you want and the agent produces exactly that list; one missing means not done |

Each of these takes twenty minutes or more to run in full, as described under "time for quality" above.

## No tooling required

The plugin is only text: install it and it works, with nothing else to install. The ten checks can all be judged by eye, and the tone-melody conflict check has a hand method that only looks at the three positions where the problem actually occurs.

**The rules are criteria:** a check that does not pass means you change the line or write one sentence saying why this song should be that way.

## Multilingual support

**One set of skills, answering in any language.** The skills are written once, in Chinese, and the agent answers in whatever language you asked in. No switch, no separate install, no per-language plugin.

This needs saying carefully here, because this library has a **language layer** and the two things are easily confused. The language layer is about the language a *lyric* is written in: Mandarin tones, Cantonese 協音, English stress, Japanese mora, Korean batchim. The policy below is about the language the *instructions* are written in. A Japanese lyricist asking in Japanese gets Japanese answers and the full `lw-japanese` layer; the instruction file behind it is still Chinese.

The skill bodies will not be forked into other languages. That is a decision. The sister project [screenwriting-skills](https://github.com/jtydhr88/screenwriting-skills) built a full English edition, merged it, then removed it, and the argument that killed it applies here unchanged: if a reader who cannot read Chinese deserves a translated edition, so does a reader who cannot read English, and the next request is Japanese, then Korean, then French. This pack is 31 files. Four languages makes 124 of them, drifting apart independently, with nothing to tell you which one is stale. Translating is the cheap part. The real cost is that forking once removes any principled ground for refusing the second fork.

How it is covered in use:

- **Output language follows your question.** Ask in Korean, get Korean.
- **Terminology is anchored to the original term.** *Object writing*, *prosody*, *family rhyme*, *hook*, モーラ, 符割り, 협음: the Chinese in the source books is itself a translation, so the original term travels with the concept.
- **Terms with no equivalent keep their original form plus a gloss.** 十三辙, 依字行腔, 類音階, 字余り come through as the original plus a short explanation.
- **Your lyric stays in its own language.** Discussing a Cantonese lyric in English is normal. Only the conversation switches language.

What this trades away is auditability: unless you read Chinese, you cannot read the instruction file itself, only the agent's account of it. That is a real cost, and it is the one thing a translated edition would genuinely buy. It is not worth a permanent four-way maintenance burden on a library whose value lies in every rule carrying a verifiable source and page.

**READMEs are a different matter** and are translated, because they are short, stable, and the first thing a newcomer meets.

## How the skills are organised

Six layers. The **language layer is the trunk** of this library, and that is the one design decision worth explaining.

Mandarin adds a whole tone-versus-melody constraint on top of everything else. Cantonese goes further and **reverses the writing order**: the melody is fixed first, and each pitch position leaves only a few tones usable, so you choose the tonal skeleton before you choose words. Japanese counts in mora (beats). English hangs on stress. These are different methods, so they are different skills, and each one says explicitly that the others must not be substituted for it.

```
L0 workflow    router, two process tracks (music-first / lyrics-first), the LYR-SPEC contract
L1 general     intent · structure · imagery · rhyme · narrative
L2 language    Mandarin · Cantonese · English · Japanese · Korean   ← the trunk
L3 tradition   Chinese-style · musical theatre · rap
L4 execution   tone-melody check · AI-tell audit
L5 corpus      taking finished lyrics apart
```

### L0 entry point

| Skill | What it covers |
|---|---|
| `lw-workflow` | Router, the fork you answer first (music-first or lyrics-first), the stage map for each, the whole-library boundary table, the LYR-SPEC schema and template, the ten checks, and the external interface (the fields handed out, the six fields shared with composition and arrangement, the message channel) |

### L1 general craft (language-independent)

| Skill | What it covers | Main sources |
|---|---|---|
| `lw-song-intent` | **The one hard gate: five questions before you write a line.** Which kind of song this is (attitudinal, situational, narrative, or expository; the default is not narrative); the one thing this song says; who it is said to; at what moment; one photographable object that runs through it. Each question catches a specific failure, and §7 is the test for telling a real answer from one filled in to pass the gate | the library's own architecture, cross-checked against Pattison and Davis |
| `lw-structure` | What each section is for and what it must not say, form templates, where the title and hook sit, how line shape makes a section feel finished or unfinished, and why perfect symmetry reads as a spreadsheet | Pattison *Essential Guide to Lyric Form*, Sheila Davis, 尤静波 |
| `lw-imagery` | Object writing and the seven senses, concrete versus abstract nouns, sense distribution, making images into a system, metaphor and dead metaphor | Pattison *Writing Better Lyrics*, *Without Boundaries*, *Songwriter's Playground* |
| `lw-rhyme` | Rhyme as a structural tool: perfect and family rhymes and what each does to closure, rhyme schemes, internal rhyme, surprise, and deliberate non-rhyme | Pattison *Essential Guide to Rhyming* |
| `lw-narrative` | Who is speaking, when, and how much they are allowed to know: person and point of view, tense anchor, withholding, and why a fully resolved emotional arc is a machine fingerprint | Sheila Davis ×2, *Popular Lyric Writing: 10 Steps* |

### L2 language layer (the trunk)

| Skill | What it covers | Main sources |
|---|---|---|
| `lw-mandarin` | Tone as phoneme: change the tone and you change the word. The thirteen rhyme classes (辙) with their characters, wide versus narrow rhyme, level-oblique tones and how much a lyric may relax them, the 顿 as the real rhythmic unit, singability (open versus closed finals, tongue-twisters), and the practice conventions of Mandarin pop | 王力《诗词格律》×2, 吴颂今, 李忠勇, 张藜, 洪源, 尤静波 |
| `lw-cantonese` | Nine tones and 協音 as a **hard** constraint: break it and the word is simply a different word. The pitch-class system that makes tone-to-melody matching computable, the elasticity of natural intervals, the six-tone test method, and the reversed writing order | 黄志华《文字声律与粤语歌创作》, 《词家有道》16 lyricist interviews, 黄霑 |
| `lw-english` | Stress against beat: word stress cannot be changed, sentence stress can; function words on strong beats; counting stresses; prosody; phrasing, breath and enjambment; the six mistakes Chinese speakers make writing English lyrics | Sheila Davis *Craft of Lyric Writing*, Pattison, *Lyrics: Writing Better Words* |
| `lw-japanese` | Counted in mora (beats): the small tsu, the moraic n and long vowels each take a beat. Pitch accent against melody, 符割り (mapping mora to notes), 分節, deliberate 字余り and 字足らず, the four ways to fix a syllable-count mismatch, 七五調 and the "sounds too Japanese" alarm, and the iron rule for English words in a Japanese lyric | Japanese lyric-and-vocal production practice, 旋律法, pro songmaking |
| `lw-korean` | One hangul block is one syllable is one note by default. Unlike Japanese, a final consonant takes no beat of its own. The batchim (받침): single and double, the seven representative finals, and why a syllable closing on a stop is the wrong place for a long note, a phrase-end hold or a section peak. Liaison (연음) moves a batchim onto the next block, so the sung syllable boundary is not the written one, which moves every breath, caesura and rhyme landing. Plus the sound changes that rewrite a line between paper and voice (nasalization, tensification, aspiration, palatalization, elision, insertion, vowel harmony); why Korean has no tone and no word stress; how Korean rhyme differs from the Mandarin che | Korean phonology (4 titles) |

### L3 tradition layers

| Skill | What it covers | Main sources |
|---|---|---|
| `lw-chinese-style` | What makes a lyric Chinese-style: the vocabulary families, sixteen named wordplay devices with their failure conditions, why the images must form one consistent world, and how deep an allusion may go | 方文山《中国风：歌词里的文字游戏》 |
| `lw-musical-theatre` | A song must be an action; the words must sound like something this character would say; Sondheim's three principles, all in the service of clarity; his catalogue of his own faults; and a transfer table for which of these a pop lyric should also obey | Sondheim *Finishing the Hat*, *Look, I Made a Hat* |
| `lw-rap` | The words themselves: rhyme density and what it costs in intelligibility, multisyllable and bent rhymes, content forms and line-level tools, rhyme-driven versus meaning-driven writing, and a transfer table for Mandarin rap | Paul Edwards *How to Rap* 1 & 2 |

### L4 execution and verification

| Skill | What it covers |
|---|---|
| `lw-tone-check` | The tone-melody conflict check and how to read it. Its output is a **risk**. A long note, a stressed beat or clear articulation can all rescue a flagged character |
| `lw-ai-tell-audit` | Eight enumerable tells of machine-written lyrics, counted individually, each routed to the skill that owns it. Plus the harder test: strip the title and proper nouns, hand it to someone who knows nothing, and ask what specific thing this song is about |

### L5 corpus

| Skill | What it covers |
|---|---|
| `lw-case-studies` | How to take a finished lyric apart: a twelve-row analysis table tied to the library's own fields, three working lyricists' self-reported methods and where they disagree, worked examples, and before-and-after revisions | 姚谦, 张藜, 洪源 |

## The interface with composition and arrangement

This is the lyric half of an audio line. The other half is composition and arrangement: in this series that is [music-composition-skills](https://github.com/jtydhr88/music-composition-skills), but it can be any person or tool that reads the spec sheet. The two sides meet only through the spec sheet, and which one goes first depends on the process:

- **Music first**: composition and arrangement hand over the section map, bar counts and emotional arc; the lyric is written into that grid.
- **Lyrics first**: the lyric hands over its line lengths and stress positions, and composition and arrangement derive bar counts from them.

The two sides share six fields: section id, bar count, section name, tempo, key, and who is singing. **Whoever works first sets them; whoever works second only reads them.** If the second side needs one of them changed, it writes an entry in the spec sheet's message channel to the first side saying which field and why; once the first side accepts and changes its own spec sheet, the second side reads it again. Lyrics-first, tempo and key may be left empty for composition and arrangement to set.

## What is not in this package

Folk-narrative song. It has no source base yet, and this library does not write a skill without one. Inventing prosodic rules for a form produces confident, wrong answers. For that, use the general layer and say plainly that it is not covered.

## Source books

**English craft (10):** Pat Pattison *Writing Better Lyrics*, *Songwriting Without Boundaries*, *Essential Guide to Lyric Form and Structure*, *Essential Guide to Rhyming*, *Songwriting Essential Guide*; Sheila Davis *The Craft of Lyric Writing* and *Successful Lyric Writing*; *Lyrics: Writing Better Words for Your Songs*; *Popular Lyric Writing: 10 Steps to Effective Storytelling*; *Songwriter's Playground*

**Chinese prosody and lyric writing (7):** 王力《诗词格律·诗词格律概要》and《王力谈诗词格律》; 吴颂今《歌词写作十八讲》; 李忠勇、何福琼《歌词写作常识》; 张藜《歌诗之路》; 洪源《春消息》; 尤静波《流行歌词写作教程》

**Cantonese (3):** 黄志华《文字声律与粤语歌创作》; 黄志华、朱耀伟、梁伟诗《词家有道：香港16词人访谈录》; 黄霑《粤语流行曲的发展与兴衰》

**Chinese style (1):** 方文山《中国风：歌词里的文字游戏》

**Musical theatre (2):** Stephen Sondheim *Finishing the Hat* and *Look, I Made a Hat*, collected lyrics with the author's own commentary and self-criticism

**Rap (2):** Paul Edwards *How to Rap* and *How to Rap 2*

**Korean phonology (4):** 郑政德《韩国语语音入门》; 李翊燮、李相亿、蔡琬《韩国语概论》; 刘小瑛《韩语发音快速入门》; 《新魅力韩国语发音入门》

**Corpus:** 姚谦《我们都是有歌的人》and the worked analyses inside the Chinese lyric-writing books

## Conventions

- Each skill opens with a long English description with Chinese keywords appended, so it can be found whether you ask in English or Chinese.
- Skill bodies are Chinese; numbered principles, tables and checklists. Output language follows the user's question.
- **Every rule carries a failure condition or a self-check action.**
- Where the sources disagree, both positions are kept side by side with a note on when each applies.
- **Nothing is written without a source.** Where a skill's examples are the library's own, it says so.
- Citations carry the source and page.
- Long tables and worked examples sit in a separate reference file, so the main file stays short.
- Agent-neutral by design: the skill files name no agent and use no agent-specific syntax.

## Technical notes

- **Skill files**: the `SKILL.md` files follow the open [agentskills.io](https://agentskills.io) standard. The frontmatter has `name` (kebab-case, matching the folder) and a long English `description` ending in "Use when …", with Chinese keywords appended so routing works in both languages. Long tables and worked examples live in `reference.md`, so `SKILL.md` stays under 40 KB.
- **Nothing to run**: the plugin is plain text files. There is no script to run, no Python, no Node and no lint step. The ten checks are called LYR-LINT in the schema, and a person judges all of them.
- **The spec sheet is a YAML file**: the use cases produce `LYR-SPEC.yaml` and `ARR-SPEC.yaml`. The LYR-SPEC template, schema and examples are in the `lw-workflow` folder (`LYR-SPEC.template.yaml`, `LYR-SPEC.schema.md`, `example-*.yaml`).
- **Fields the text above names in plain words**: the spec sheet's message channel is the top-level `messages`; tempo and key left empty in lyrics-first work are written as `null` (see `lw-workflow/LYR-SPEC.schema.md` §3). In an ARR-SPEC, the mix intent is `mix_intent`, and the thematic material and per-section development in use case 5 are the `material` block and each section's `development` field.

## License

MIT for the skills themselves, see [LICENSE](LICENSE). Quotations from the source books remain the property of their authors and translators, see [NOTICE](NOTICE). Song lyrics quoted for analysis are quoted only as far as the analysis requires.

---

Sister project, same idea applied to screenwriting: [screenwriting-skills](https://github.com/jtydhr88/screenwriting-skills), whose Chinese-opera layer shares the 依字行腔 and thirteen-rhyme-class material with the Mandarin layer here.
