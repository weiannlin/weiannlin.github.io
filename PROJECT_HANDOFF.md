# Project Handoff

This file is the operational handoff for future Codex sessions working on `weiannlin.github.io`. It records the project goals, user preferences, style rules, mathematical conventions, site workflow, current teaching sequence, and next likely steps.

Before editing this project, read this file together with `CODEX_PROJECT_MEMORY.md`.

## Primary Files To Read First

- `CODEX_PROJECT_MEMORY.md` is the hard-rule memory file. It records mandatory style, terminology, citation, LaTeX, cross-reference, and source-checking rules. It must be read after every context compression and before any Teaching Topics edit.
- `PROJECT_HANDOFF.md` is this handoff file. It records the broader project direction, current status, editorial rationale, and accumulated user preferences.
- `README.md` is the public repository overview. It is intentionally shorter and should not be treated as a complete workflow or writing specification.
- `/Users/sagalin/Dropbox/.claude/用詞文風對照檔.md` is an external style reference requested by the user. When working on prose, consult it together with the user's MathStat source files.
- `/Users/sagalin/Dropbox/MathStat/chapters/` contains the user's source lecture/book material. This is the primary mathematical, notational, graphical, and stylistic source for Teaching Topics. For probability and mathematical statistics topics, inspect the relevant `mathstat*.tex` files before writing.
- `/Users/sagalin/Dropbox/黃文璋數統/` contains Huang Wen-Jang's materials. These are the secondary but still essential benchmark for Chinese textbook rigor, terminology, and exposition.

## Project Identity

This repository is Wei-Ann Lin's academic website at `weiannlin.github.io`. It began from the Academic Pages template but has been reshaped into a personal academic site with a journal-like visual identity and a major teaching component.

The site is not just a CV page. It is becoming a bilingual academic profile, research record, talk archive, notes area, and a long-term web textbook for probability and statistics.

The user wants the teaching part to become a rigorous but readable set of topic-based webpages. The intended audience includes motivated undergraduate students, graduate students, and students preparing for probability or statistical inference courses.

## Main Long-Term Teaching Goal

The central teaching project is a topic-based probability/statistics web curriculum.

The user wants to start from probability theory and random variables, then proceed toward mathematical statistics, statistical inference, and later descriptive statistics and interactive demos. The web articles should be shorter than lecture notes but more polished than casual blog posts.

The guiding metaphor from the user is that the same "mountain" can be climbed by different paths. A topic may serve undergraduate probability, graduate statistical inference, or self-study students. The web pages should therefore be generally useful and not mention course-specific routing inside the article body unless it genuinely helps the reader.

## Course-Level Direction

The user expects the site to support at least two future teaching tracks.

- Undergraduate probability theory should emphasize measure-related foundations, event probability, random variables, distribution theory, and limiting distributions. It should include enough measure language to prepare students for rigorous probability.
- Graduate Statistical Inference I should be more selective about measure theory, move efficiently from events to random variables, and emphasize common distribution models and limiting distributions in preparation for Statistical Inference II.
- The first five chapters of the user's source material are intended to be broadly implemented, with later course-specific emphasis handled in class rather than hard-coded into the webpage text.

## Teaching Topics Sequence

The current public Teaching Topics sequence is organized by chapter.

Chapter 1, probability foundations:

- Topic 1: `random-experiments-sample-space-events`, random experiments, sample space, sample points, events.
- Topic 2: `event-families-sigma-fields`, event families, sigma-fields, measurable spaces, Borel sigma-field.
- Topic 3: `probability-assignment-classical-geometric`, probability assignment, classical probability, counting measure, geometric probability.
- Topic 4: `probability-rules-from-axioms`, probability rules from Kolmogorov axioms, complement, monotonicity, addition principle, inclusion-exclusion, Boole and Bonferroni.
- Topic 5: `conditional-probability-information`, conditional probability, information, multiplication rule, conditional probability as a probability measure, filtering interpretation.
- Topic 6: `independence-and-conditional-independence`, independence, pairwise independence, conditional independence.
- Topic 7: `total-probability-bayes-rule`, partitions and the law of total probability. Bayes' rule has been split out and should not be presented as the next topic from this article.
- Topic 8: `group-mixing-simpsons-paradox`, grouping, mixing, and Simpson's paradox. This web-only bridge may keep its current relative weight because it connects to a dedicated demo.
- Topic 9: `bayes-rule-posterior-probability`, Bayes' rule, posterior probability, information as updating, rapid-test demo, then bridge to random variables.

Chapter 2, random variables and distributional summaries:

- Topic 1: `random-variables-from-sample-space-to-real-line`, random variables as maps from sample space to the real line.
- Topic 2: `probability-accumulates`, cumulative distribution functions and how probability accumulates.
- Topic 3: `discrete-random-variables-pmf`, discrete random variables and PMF.
- Topic 4: `continuous-random-variables-pdf`, continuous random variables and PDF.
- Topic 5: `mixed-random-variables`, mixed random variables, CDF/PDF decomposition, and combined discrete-continuous probability calculation.
- Topic 6: `expected-value-random-variables`, expected value as average position.
- Topic 7: `variance-standard-deviation`, variance and standard deviation.
- Topic 8: `linear-transformations-standardization`, linear transformations and standardization.
- Topic 9: `quantiles-and-median`, quantiles, percentiles, and median.
- Topic 10: `mode-and-distribution-shape`, mode and distribution shape.
- Topic 11: `skewness-and-kurtosis`, skewness, Pearson skewness, kurtosis, and the moment-system bridge.

The next likely article after Topic 11 is moment-generating functions. The user has repeatedly said that each new topic must begin by checking the original MathStat manuscript before drafting.

## Demos And Interactive Material

Interactive demos are teaching companions, not standalone games. They should be linked from teaching articles only when they deepen the concept.

Current demos include:

- PMF to CDF.
- PDF to CDF.
- Mixed distributions.
- Monty Hall problem.
- Bayesian updating through rapid-test interpretation.
- Simpson's paradox mixing lab.

Important demo-related rules:

- Do not add a demo simply because it is possible.
- A demo should clarify a concept that is otherwise difficult to see.
- The demo link usually belongs after the relevant concept or in a note, not at the top of an article.
- For Bayesian updating, the rapid-test context is preferred. It should mention sensitivity and specificity, and clarify that repeated independent observations connect to the spirit of Naive Bayes only after independence is introduced.
- Simpson's paradox works well as a demo because students can adjust group composition and see reversal.

## Source Hierarchy For Mathematical Content

Do not write Teaching Topics from general model knowledge alone.

The highest authority is the user's book draft. Huang Wen-Jang's教材 is the next authority and should be used to calibrate Chinese mathematical-statistics exposition. General textbook knowledge and model memory are not acceptable substitutes.

The user's MathStat source files are also the highest reference for topic sequencing and first-pass prose scaffolding. Past Codex sessions drifted away from the book draft after context compression; this must not recur. After every context compression, new handoff, or new Teaching Topics writing task, return to the relevant `mathstat*.tex` file before deciding the article order, paragraph skeleton, examples, formulas, notation, or figure logic. Web readability may justify compression or local reordering, but not a different conceptual spine.

For mathematical content, check sources in this order:

- First, the user's MathStat source files in `/Users/sagalin/Dropbox/MathStat/chapters/`, especially the relevant `mathstat*.tex` file. This source controls the main concept, notation, figure logic, and writing direction.
- Second, Huang Wen-Jang materials in `/Users/sagalin/Dropbox/黃文璋數統/`. This source is used to check rigor, standard Chinese mathematical wording, and textbook-level presentation.
- Third, published textbooks such as Casella and Berger, Ross, Wackerly et al., DeGroot and Schervish, Billingsley, and Durrett, only as supplementary checks.

If the user's source and Huang's source differ, begin from the user's source. Adjust only when Huang's version, or another standard reference, is clearly more rigorous or avoids a genuine mathematical ambiguity. In such cases, preserve the user's notation and teaching intent whenever possible.

The user accepts reordering for web readability but does not accept mathematical content that contradicts the source material.

## Writing Tone

The target voice is the user's lecture-note voice made web-readable.

Preferred style:

- Use direct mathematical prose such as `令`, `若`, `則稱`, `由此可得`, `因此`, `故`.
- Keep Chinese professional terminology close to the user's lecture notes.
- Use concise but complete explanations.
- Let definitions, examples, and figures carry the exposition.
- Use "直覺校準" for reflective interludes that invite the reader to think.

Avoid:

- Obvious AI phrases like `第一步不是...而是...`, `核心想法`, `語言`, `物件`, `入口`, `承載`, `讀出`, `讀回`, `考察`.
- Broad template sentences that sound like they explain the writing plan rather than the mathematics.
- Phrases that belong in a private course-planning note, such as `原書`, `我的講義`, `使用者講義`, `依照使用者要求`, or `沿用原書的寫法`.
- Machine-learning-circle language unless the topic genuinely requires it. The user strongly dislikes importing such vocabulary into mathematical statistics teaching.
- Chinese full-width colons in visible prose.
- The two-character phrase formed by `語` plus `感`.

## Terminology Rules

Key terminology decisions:

- Use `分配` for general distribution terminology. The user explicitly overrode the older `分佈` convention on 2026-06-21. Across Teaching Topics as a whole, the first visible mention may say that some materials also write `分佈`; after that, public prose should use `分配`.
- Use `累積分配函數 (cumulative distribution function, CDF)` and `分配函數 (distribution function, DF)` for CDF-related language, following the user's MathStat source.
- Use `電腦實驗`, not `電腦試驗`.
- Use `均等可能性 (equally likely)`, not `等可能性`.
- Use `$\sigma$-域 ($\sigma$-field)`, not `sigma-algebra`, unless directly comparing terms.
- Use `成對獨立`, not `兩兩獨立`.
- Use `中央趨勢量數` for expected value, median, and mode. Do not call all of them "position measures".
- Quantiles are position measures. Median is a special quantile and also a central tendency measure.
- Use `母體眾數 (population mode)` and `樣本眾數 (sample mode)` carefully.
- For continuous mode, the user source treats mode in connection with local maxima in distribution-shape discussion. Be careful not to force a global-only interpretation when discussing unimodal, bimodal, and multimodal shapes.
- Use `統計標準化 (statistical standardization)` where appropriate. Standardization means centering and scaling by standard deviation in the scalar setting. Whitening is different and belongs to multivariate settings where covariance structure is removed.
- For inverse standardization, the user considered `inverse standardization`; use it if the topic appears.

## User-Specific Wording Preferences

The following wording preferences have been stated repeatedly or with strong emphasis. Treat them as project rules, not casual suggestions.

Avoid or use with extreme care:

- `語言`, when used vaguely to package a concept. Prefer `定義`, `概念`, `符號`, `內容`, `架構`, or the actual mathematical term.
- `物件`, especially in summaries such as "機率論的第一層物件". Prefer `定義`, `角色`, `概念`, or the named mathematical entity.
- `入口`, especially in templated phrases like "第一個入口". Prefer `敲門磚` if a metaphor is needed.
- `服務`, especially in course-routing prose. Prefer wording such as `同一篇文章可能出現在不同課程中`.
- `問`, `詢問`, and `考察` when used as generic exposition. Prefer `討論`, `計算`, `求取`, `處理`, `回頭審視`, or directly state the event/probability.
- `讀出` and `讀回`. Prefer `由圖可見`, `由表可得`, `由公式可得`, `計算`, `求得`, or `呈現`.
- `承載` for probability mass. Prefer `具有正機率`, `機率集中在單點上`, or `該點具有多少機率質量`.
- `支撐` when merely saying one sample space can correspond to random variables. Prefer `對應`.
- `不是同一句話`. Prefer `不是同一件事情`.
- `第一步不是...而是...`, because the user finds this AI-like.
- `核心想法`, `這件事很重要`, `可以理解為`, `本文要說明` when used as filler.
- Chinese full-width colons in visible prose.
- The two-character phrase formed by `語` and `感`.
- `似然` and `證據機率` in introductory Bayes-rule prose. If likelihood must appear later, define it carefully and only where mathematically needed.
- Machine-learning-flavored terms imported unnecessarily into classical probability or mathematical statistics.

Preferred or established replacements:

- Use `直覺校準`, not `思想實驗`, for reflective interludes.
- Use `$\sigma$-域 ($\sigma$-field)`, not `sigma-algebra` in running prose.
- Use `均等可能性 (equally likely)`.
- Use `電腦實驗`.
- Use `成對獨立`.
- Use `中央趨勢量數` for expectation, median, and mode.
- Use `位置量數` for quantiles and percentiles.
- Use `期望值是依機率或機率密度權重計算出來的平均位置` where the expected-value comparison with median is needed.
- Use `分配中心`, `聚集中心`, `重心位置`, or `質心` where this reflects the user's source material.
- Use `資訊帶來更新` for Bayes' rule, but avoid making it sound like a slogan.

Examples of accepted user wording:

- `本篇建立的是機率論的入門基礎，為讀者釐清每一個定義在機率論的角色。`
- `機率論 (probability theory) 對很多人而言就是計算機率的過程，但事實上機率論要比這個還廣泛與嚴謹不少。`
- `隨機變數定義後，便可固定門檻 x，回頭審視並計算 X <= x 此一事件的機率。`
- `不可能發生的事件機率必為零，但機率為零的事件未必不可能發生。`
- `由此可再次印證，分位數與中位數都可能面臨不唯一的情況，透過分位函數 x_{0.5} 所找到的中位數只不過是「其中一個」而已。`

## Mathematical Notation

General notation:

- Probability is `\mathbb{P}`.
- Expectation is `\mathbb{E}`.
- Variance is `\mathrm{Var}`.
- Use `$...$` and `$$...$$` only. Do not use `\(...\)` or `\[...\]`.
- Display math should not end with punctuation inside the display.
- If a sentence introduces a displayed equation, use a complete bridge such as `則`, `可寫為`, `此即`, `由此可得`.
- Avoid ending a line before display math with an awkward comma.
- Use `\mid` rather than `:` in set-builder notation.
- Use `\mathcal{R}_X` for the range of random variable `X`.
- For cases-like formulas, align numeric values centrally and conditions left, with commas retained.
- Use `\eta_X` for median.
- Use `x_p = F_X^{-1}(p)` or related notation for quantile function, not an invented `Q_X(p)`.
- Use `Q_1,Q_2,Q_3` for quartiles and `P_r` for percentiles when those appear.

## Equation And Layout Rules

- Display math must remain centered and large. If MathJax renders it inline or small, inspect Markdown spacing around HTML blocks.
- In `markdown="1"` HTML blocks, leave a blank line between closing `$$` and `</div>`.
- Multi-line displayed equations should use extra row spacing such as `\\[0.35em]` or `\\[0.45em]`.
- If a formula produces only one final number, it often does not need a separate line break.
- Avoid punctuation alone on a line.
- Avoid "head punctuation" and "tail punctuation" in default desktop width. If necessary, rewrite the sentence length.
- Do not leave a single Chinese character, punctuation mark, or isolated English word on its own line.

## Article Structure Rules

Each Teaching Topics article should typically include:

- A concise lead that links from the previous topic.
- Definitions with stable anchors when likely to be referenced later.
- Examples with numbering and optional titles, such as `Example 2.16 (Two Modes)`.
- Example blocks must use `topic-box--example`; do not convert examples into `## Example ...` headings. If an example needs a cross-reference anchor, put the `id` before `class`, as in `<div id="example-..." class="topic-box topic-box--example" markdown="1">`.
- Propositions or theorems only when appropriate; do not overload every article.
- "直覺校準" blocks where a reflective pause materially helps.
- Figures when they clarify the concept.
- A "本篇小結".
- "參考文獻與延伸閱讀".
- A clear bridge to the next article.

Reference rules:

- Teaching Topics references use pure bibliography format. Do not add Markdown external links or bare URLs in public reference entries, even for web sources such as encyclopedia articles, unless the user explicitly asks for a link.
- Use external URLs for verification work, not as visible tails in public Teaching Topics references.

Cross-reference rules:

- Link to specific definitions, examples, figures, or interludes when the reference is specific.
- Do not link vaguely to an entire article when a stable anchor can be used.
- If future use is intended but should not appear in public prose, add an internal HTML comment rather than a visible note.
- The Uniform Distribution example in `quantiles-and-median` currently displays as Example 2.14 and must retain the stable anchor `example-214` for future probability integral transform.

## Figure Rules

Figures should resemble the user's source material when the source contains a diagram.

General rules:

- Do not produce generic "AI slop" illustrations.
- Prefer simple mathematical diagrams with clean strokes, restrained colors, and clear labels.
- Use SVGs for teaching figures.
- If a figure comes from the user's TikZ logic, preserve its mathematical structure rather than redrawing it as a vague smooth cartoon.
- Captions should use `Fig. x.y.`.
- Captions should be formal but not stiff.
- Avoid introducing notation in figures before the article defines it.
- If a symbol like `\alpha_3` has not yet been introduced, do not put it in a conceptual preview figure.
- For CDF/PMF diagrams, points, dashed lines, and arrows must align exactly with the intended mathematical value.
- For multi-line formulas in figures, label placement matters. The user cares about pixel-level alignment.

Recent figure lessons:

- The skewness preview figure in `mode-and-distribution-shape` should follow the user's book draft: right-skewed, left-skewed, and symmetric curves; dashed lines to the x-axis; labels under the axis; no `\alpha_3` yet.
- The peak-count figure should not imply all local peaks are equal height. It should emphasize peak count as local maxima, not global maximum.
- The user dislikes overly rounded, cartoon-like curves when the source has a more mathematical TikZ-style curve.

## References And Citation Rules

Every Teaching Topics article should have references.

Strict rules:

- Do not show DOI in public reference lists.
- Do not show ISBN in public reference lists.
- Do not show publication city.
- Do not append database labels such as EUDML, JSTOR, Project Euclid, or Rényi Institute to complete journal references.
- If using journal papers, include journal name, volume, issue, and pages.
- Use standard bibliography style consistently.
- Chinese book format may be `黃文璋，2003，《數理統計》，初版，華泰文化。`
- English book format may be `Author. Year. *Title*. Edition. Publisher.`
- Journal format may be `Author. Year. “Title.” *Journal* volume (issue): pages.`
- Verify publication data from reliable sources. Do not infer from a local lecture PDF.

User frustrations that must not recur:

- Do not write Huang Wen-Jang's publisher as a university department.
- Do not insert `臺北市` or `台北市` into references.
- Do not list DOI even if it was used for verification.
- Do not add only one ISBN while leaving other references without ISBN.
- Do not use `[EUDML](...)` or similar database labels at the end of a scholarly reference.

After editing references, scan `_pages` and `_teaching_topics` for `doi:`, `DOI`, `https://doi.org`, `ISBN`, `臺北市`, `台北市`, `EUDML`, `JSTOR`, `Project Euclid`, and similar residue.

## Local Preview And Build Workflow

Use Homebrew Ruby's Bundler, not system Ruby.

Recommended command:

```bash
/opt/homebrew/lib/ruby/gems/3.4.0/bin/bundle exec jekyll serve --host 127.0.0.1 --port 3000
```

For build verification:

```bash
/opt/homebrew/lib/ruby/gems/3.4.0/bin/bundle exec jekyll build
```

Notes:

- In this environment, sandbox may block writes to `_site`. If so, rerun build with escalated permissions.
- When checking localhost with tools, sandbox may block localhost. Request escalation if needed.
- The user expects preview links every time a visible page is changed.
- Preview links should stay local, e.g. `http://127.0.0.1:3000/teaching-topics/.../?v=...`.
- Use cache-busting query strings after changing SVGs or CSS.
- If local preview links redirect to production, inspect `site.url`, `baseurl`, and page links. Internal Teaching Topics links should be local-relative where possible.

## Git Workflow

The user has authorized this project to be edited and pushed. Still:

- Never revert user changes without explicit instruction.
- Use `git status --short` before staging.
- Stage only related files.
- Commit with a clear message.
- Push to `origin/master` when the user asks `push`.
- Do not commit generated `_site/`.
- After push, confirm working tree is clean.

Recent push:

- `15ffafd Add mode and distribution shape topic` added the mode article and associated figures.

## Non-Teaching Site Work Already Done

Talks:

- SRC 2026 contributed talk was added: `Multi-Fidelity Category-Tree Gaussian Process Modeling with Many Categorical Combinations`.
- Southern Region Statistics Conference was added with invited talk title `Multi-Objective Bayesian Optimization of CPU Cooling Design with Mixed Variables using Category Tree Gaussian Process`.
- 115年統計學術研討會 was treated as Republic of China year 115, not "115th"; invited talk title `Objective-Wise Category Tree Gaussian Processes for Mean-Dispersion Bayesian Optimization`.
- Scheduled talks have been moved according to dates when requested.

News:

- Upcoming talks were added to News after user asked whether they should appear there.

Home/About:

- Industrial Collaboration section was added to the home/about presentation.
- Tone must match other site sections. The user prefers third-person-like or site-descriptive tone rather than a sudden self-promotional first-person voice.
- Industrial work can be mentioned only generally because of confidentiality. Acceptable areas include military/industrial design, chemical formulation optimization, mixed-variable design, Bayesian optimization, Gaussian process modeling, and confidential consulting contexts.

Notes:

- Blog was reframed as Notes.
- A note about ctGP tool progress was added.
- ctGP began in R and moved toward C++.
- ctmGP is for multi-objective development, not specifically mean-dispersion.
- ctmfGP is a multi-fidelity sister version.
- The desired public framing is that these tools are moving toward a comprehensive GP modeling and Bayesian optimization toolkit, to be released after theoretical development and package polish.

## Chapter 1 Content Intent

Chapter 1 is now public and should be treated as the completed probability-foundation arc, though it can still be polished.

Important conceptual decisions:

- Topic 1 starts from random experiment, sample space, sample point, event.
- Continuous sample spaces require early attention to probability-zero versus impossible events.
- The "dart at a point" thought experiment became a "直覺校準" style example.
- Topic 2 introduces event families and sigma-fields. The preferred term is `$\sigma$-域 ($\sigma$-field)`.
- Borel sigma-field should be cross-referenced when random variables are introduced.
- Topic 3 clarifies "how to assign probability" after Kolmogorov axioms. It includes classical probability, counting measure, and geometric probability.
- Topic 4 derives probability rules from axioms and includes visual set diagrams. Difference notation should be consistent. The user has adjusted many figure details and cares about exact labels.
- Topic 5 begins from information and conditional probability, not just formula manipulation. It includes the idea that changing the condition changes the reference world.
- Topic 6 centers on partition and law of total probability. Bayes' rule was split out.
- Monty Hall appears under total probability and may link to demos. It should include history and intuitive surprise, but examples should not become oversized.
- Simpson's paradox was inserted before Bayes' rule as a side branch about grouping and mixing. It connects naturally to base-rate reasoning later but should not over-preview Bayes before it appears.
- Bayes' rule emphasizes information bringing updating. Avoid terms the user dislikes such as `似然` or `證據機率` in introductory language unless carefully defined later.
- Independence closes Chapter 1 and bridges to random variables.

## Chapter 2 Content Intent

Chapter 2 starts from the need to move from event probabilities to real-valued random variables so calculus and numerical tools can be used.

Important decisions:

- Start with random variables as functions from sample space to real line.
- CDF is introduced early because it provides a unified treatment of discrete and continuous cases.
- PMF and PDF are then developed as different ways to compute or interpret the CDF.
- Mixed random variables are introduced after PMF/PDF and before expectation, following the user's MathStat manuscript order. Keep expectation and variance treatment in this article minimal or clearly framed as later preview.
- Standardization is introduced after expectation and standard deviation, as comparing individual positions relative to a group's center and variability.
- Quantiles and median come after standardization. Quantiles describe positions throughout a distribution; z-scores describe a single individual's standardized distance from the center.
- Mode comes after quantiles and median as another central tendency measure and a bridge to distribution shape.
- Skewness and kurtosis come after quantiles/median and mode, as formal shape measures connected to moments.

## Current Topic 9 To 11 Notes

`quantiles-and-median.md`, `mode-and-distribution-shape.md`, and `skewness-and-kurtosis.md` are the current end of Chapter 2.

Important rules for this article:

- Do not call mode merely a position measure. It is a central tendency measure.
- Definition 2.13 uses PMF/PDF maximum to define mode.
- Sample mode and population mode are different definitions but have the same underlying idea.
- Continuous mode does not mean positive point probability. It means the density is highest at that point.
- The phrase requested by the user: "所以眾數未必永遠是用機率去選擇，但意義上，它確實是「最有可能」出現的一個點。"
- Split peak count from symmetry/skewness. Do not mix them.
- Do not use `\alpha_3` in this article's conceptual skewness figure because skewness coefficient has not yet been introduced.
- Peak count should be explained through local maximum. Peak heights need not be equal.
- The skewness preview figure should follow the user's book draft and not look like a rounded generic illustration.

## Future Work Suggestions

Likely next Teaching Topics:

- Moment-generating functions, using the user's MathStat source immediately after the skewness/kurtosis material.
- Do not start a new topic from memory. Reopen the relevant original manuscript section first, then draft from that order and wording skeleton.
- When later teaching machine learning or classification topics, hidden Naive Bayes notes in the Bayes and independence articles may be revived as cross-references.

Other future directions:

- Probability integral transform should later refer back to the Uniform Distribution example in quantiles. Its visible label is currently Example 2.14, while the stable anchor remains `example-214`.
- Descriptive statistics topics such as IQR and boxplots can branch from quantiles, but the user wants that as a later descriptive-statistics section, not necessarily in probability theory.
- Interactive demos for independence are deferred; avoid duplicating the rapid-test demo unless a genuinely new concept is clarified.

## Site Design And UX Rules

- Preserve the cream-paper background, brick-red accent, serif typography, restrained borders, and journal-like atmosphere.
- Teaching Topics index uses chapter blocks and should default to collapsed chapters.
- Demos index ordering should place random events and random variables in the intended conceptual order.
- Top-right Teaching Topics site header should link back appropriately.
- Preview links should be supplied for page edits.

## Common Failure Modes To Avoid

- Writing something that sounds like a note to the user rather than a paragraph for students.
- Introducing a later notation in a figure before the article defines it.
- Using broad AI-ish wording when the user's lecture-note style has a precise phrase available.
- Treating the web article as a direct paste of lecture notes. The content should be compressed and web-readable, not copied.
- Treating the web article as a casual blog post. The content should remain mathematically precise.
- Forgetting to check earlier topics when a global style or notation rule changes.
- Forgetting that the user cares deeply about figure labels, line positions, and mathematical alignment.
- Using publication information without verification.
- Leaving old production links in a local preview context.

## Minimal Checklist Before Returning A Teaching Topics Change

- Read `CODEX_PROJECT_MEMORY.md` and this handoff file.
- Check the relevant MathStat source and Huang source when mathematical content is involved.
- Confirm no visible prose contains forbidden AI-ish terms or internal workflow language.
- Confirm display math uses `$$...$$` and has no punctuation inside.
- Confirm cross references point to specific anchors when possible.
- Confirm figure labels do not introduce undefined notation.
- Confirm references follow the no-DOI, no-ISBN, no-city, no-database-tail rule.
- Run `bundle exec jekyll build` with Homebrew Ruby.
- Provide a local preview URL with cache-busting query string.
- If user asks to push, stage only related files, commit, push, and verify clean status.
