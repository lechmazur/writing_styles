# Mapping LLM Style and Range in Flash Fiction

This writeup documents the **style** side of the short-story Creative Writing LLM benchmark: we generated many short stories (≥400 per model; some models have more due to multiple runs) with a range of LLMs, then analyzed those stories for stylistic fingerprints and **within-model diversity**. This study focuses on how models write, how their outputs differ, and how varied each model is across its own stories.

---

## What we measured

* **Diversity per model.** For each LLM, we quantify how dissimilar its own stories are from one another in the measured style space.
* **Style fingerprints per story.** Each story is scored along a curated set of axes (mix of numeric 0–10 scales and enums such as register, POV, closure form, genre family).
---
## How the data was gathered
We asked models to write **flash-fiction pieces of 600–800 words** from the same pool of prompts so comparisons are fair. Prompts include required elements to keep content varied across runs. For style analysis, those elements are treated as context rather than something to reward on their own. Each story was then read by a separate reviewing model that answered a fixed set of style questions. Results are aggregated at the story level and then rolled up by model. (Dec 2025 update: 29 models; 15,347 total stories; min 400/model, max 947/model.)

## What the style axes cover

We score what’s visible on the page. The axes summarize choices in:

* **Voice and diction:** distinctiveness, concreteness, register.
* **Rhythm and syntax:** sentence cadence, complexity, paragraphing, linkage style.
* **Point of view and discourse:** POV person and distance, scope, tense, reliability, use of free indirect style.
* **Structure and pacing:** scene vs. summary balance, chronology handling, narrative modality, how background is delivered, what drives the read.
* **Tone and mood:** intensity and range, rhetorical stance.
* **Imagery:** density of sensory detail, sensory bias, motif strategy.
* **Dialogue:** amount, subtext, tagging style.
* **Experimentation:** degree of formal play, associative gaps, metafictional devices.
* **Closure:** cadence and ending type.
* **Content choices:** genre family, topic domain, time and place band, conflict frame, stakes level, cast size, realism vs. fabulism, ending valence, and how dependent the piece feels on the prompt.

All results reflect models under a neutral, minimally directive prompt; targeted prompting can shift register, structure, and voice substantially, so read these style patterns as tendencies rather than fixed traits.


---

## Stylistic diversity by model (Weighted Gower)

![Stylistic Diversity by LLM (Weighted Gower Mean Pairwise Distance)](images/diversity_leaderboard_dot.png)

* **Clear leader:** GPT-5 (medium reasoning) shows the widest within-model range (0.218). The other GPT-5 variants follow closely (GPT-5.2 at 0.215; GPT-5.1 and GPT-5 Pro at 0.213). Kimi K2 Thinking (0.210) and GLM-4.5 (0.206) anchor the next tier, with several frontier models clustered tightly behind.&#x20;
* **Low-range models:** GPT-OSS-120B (0.171) and Cohere Command A (0.178) show the narrowest spread of styles, with Llama 4 Maverick and Qwen 3 Max Preview both at 0.183.&#x20;
* **Tight field overall:** the spread from lowest to highest is \~0.047, so most models vary by a similar amount; GPT-5 (medium reasoning) is the notable outlier for range.
* **Consistency with fingerprints:** lower-diversity models align with earlier fingerprints that showed more uniform paragraphing, stance, and dialogue choices, while high-diversity models also tended to vary tense, POV person, and experimentation.


---
## LLM Diversity Leaderboard (Weighted Gower mean pairwise distance)
| Rank | LLM                    | Diversity Score |
|-----:|------------------------|----------------:|
| 1 | GPT-5 (medium reasoning) | 0.218 |
| 2 | GPT-5.2 (medium reasoning) | 0.215 |
| 3 | GPT-5.1 (medium reasoning) | 0.213 |
| 4 | GPT-5 Pro | 0.213 |
| 5 | Kimi K2 Thinking | 0.210 |
| 6 | GLM-4.5 | 0.206 |
| 7 | Grok 4.1 Fast Reasoning | 0.204 |
| 8 | Deepseek V3.2 Exp | 0.203 |
| 9 | Claude Opus 4.1 (no reasoning) | 0.202 |
| 10 | Kimi K2-0905 | 0.201 |
| 11 | Kimi K2 | 0.201 |
| 12 | GLM-4.6 | 0.200 |
| 13 | Qwen 3 235B A22B 25-07 Think | 0.199 |
| 14 | Claude Sonnet 4.5 Thinking 16K | 0.197 |
| 15 | Mistral Large 3 | 0.195 |
| 16 | Claude Sonnet 4.5 (no reasoning) | 0.195 |
| 17 | o3-pro (medium reasoning) | 0.195 |
| 18 | Grok 4 | 0.194 |
| 19 | Baidu Ernie 4.5 300B A47B | 0.194 |
| 20 | Gemini 2.5 Pro | 0.193 |
| 21 | Gemini 3 Pro Preview | 0.193 |
| 22 | Mistral Medium 3.1 | 0.191 |
| 23 | DeepSeek V3.1 Reasoner | 0.191 |
| 24 | DeepSeek V3.1 Non-Think | 0.191 |
| 25 | Claude Opus 4.5 (no reasoning) | 0.189 |
| 26 | Llama 4 Maverick | 0.183 |
| 27 | Qwen 3 Max Preview | 0.183 |
| 28 | Cohere Command A | 0.178 |
| 29 | GPT-OSS-120B | 0.171 |


### How diversity is computed

Diversity is a **style-range** number for each model. We compare that model’s stories to each other along all axes, combine the differences, and average them. The score sits between 0 and 1.

* **Higher** means the model explores a wider span of styles across its outputs.
* **Lower** means the model tends to stay in a narrow lane.

This is **not** a quality grade. It complements quality by showing range.

---
## Style Results

### Numeric style means (0–10)

![Style Fingerprints • Per-LLM Means for Numeric Style Axes (0–10)](images/style_numeric_axes_heatmap.png)

* **High-style cluster.** Kimi K2 sits at the top of the craft cluster (voice, imagery, rhythm, tone, concreteness), with the latest GPT-5 variants (GPT-5 Pro, GPT-5.1, GPT-5.2) and o3-pro close behind. Kimi K2-0905 and Qwen 3 Max Preview also score strongly across the same “surface craft” bundle.
* **Paragraphing split.** GPT-OSS-120B remains a clear outlier with extremely low paragraphing/lineation (blocky pages). Mistral Medium 3.1 leads this axis, with o3-pro and GPT-5 Pro also using notably varied paragraphing; GLM-4.6 and Deepseek V3.2 Exp are the next-lowest after GPT-OSS-120B.
* **Dialogue fingerprint.** Claude Sonnet 4.5 (no reasoning) and Mistral Large 3 use the most dialogue by volume (with Baidu Ernie 4.5 close behind). On *dialogue subtext*, Mistral Medium 3.1 leads, followed by GPT-5 Pro and GPT-5.2 (medium reasoning). Llama 4 Maverick and GPT-OSS-120B are sparse on both.
* **Experimentation.** GPT-5 Pro shows the highest experimentation and associative gaps in the latest GPT-5 line, with Kimi K2-0905 the next tier. Most other models remain comparatively conservative on formal play.
* **Endings.** Kimi K2-0905 and Qwen 3 Max Preview post the strongest closure cadence, with GPT-5 Pro close behind. Kimi K2’s endings are comparatively softer given its high craft scores elsewhere.
* **World feel.** Several models lean away from strict realism: Kimi K2-0905, GPT-OSS-120B, and Kimi K2 are the most fabulist on the realism spectrum. Worldbuilding intensity is highest for GPT-5.2 (medium reasoning), Kimi K2-0905, and Gemini 3 Pro Preview.
* **Structure and pace.** Kimi K2, o3-pro, and Mistral Medium 3.1 lead structure/pacing, while Llama 4 Maverick sits at the bottom across most structure/craft axes.
* **Internal vs external pressure.** GPT-5.2 (medium reasoning), Gemini 3 Pro Preview, and Grok 4.1 Fast Reasoning push the farthest toward external action, while Llama 4 Maverick and GPT-OSS-120B skew most internal.
* **Model snapshots.**

  * **GPT-5.2 (medium reasoning):** high worldbuilding intensity and the strongest external-action tilt (internal–external ratio), with high syntax complexity and strong dialogue subtext; diversity near the top of the leaderboard.
  * **GPT-5 Pro:** near-max voice/imagery with the strongest dialogue subtext in the GPT-5 line and top-tier closure cadence; very high first-person share.
  * **Kimi K2:** top craft cluster with the strongest structure/pacing; high concreteness and a fabulist tilt; comparatively soft closure cadence.
  * **Kimi K2-0905:** highest syntax complexity and closure cadence; high concreteness and worldbuilding intensity; strong “crafted” endings.
  * **Mistral Medium 3.1:** best paragraphing/lineation and highest dialogue subtext; strong pacing with a balanced overall profile.
  * **GPT-OSS-120B:** lush voice/imagery with extremely low paragraphing and minimal dialogue; among the lowest diversity scores.
  * **Llama 4 Maverick:** lowest on most numeric craft axes, very solo-cast and internally focused, minimal dialogue; low diversity.

---
### Topic domain

![Style Fingerprints • Topic Domain — Choice Proportions by LLM](images/style_enum_topic_domain_stacked.png)

* **Existential dominates** across models; **Memory** is the clear second and **Social** is third. **War** and **Crime** remain negligible.
* **Most existential:** Cohere Command A, Llama 4 Maverick, and GLM-4.6. **Most memory-tilted:** Kimi K2 (by a wide margin), with DeepSeek V3.1 Reasoner next.
* **Niche tilts:** GPT-5.2 (medium reasoning) shows the strongest **Social** share, while Qwen 3 235B (25-07 Think) and Grok 4 show the highest **Nature** share.


---
### Tense

![Style Fingerprints • Tense — Choice Proportions by LLM](images/style_enum_tense_stacked.png)

* **Past tense dominates** almost universally; most models are ≈100% past.
* **A couple GPT-5 variants (including GPT-5 Pro) are the exceptions,** with substantial **present** tense and a small **mixed** slice.
* **Minor variation:** Kimi K2 and o3-pro show small present usage; most other models are essentially all past.


---
### Temporal handling

![Style Fingerprints • Temporal Handling — Choice Proportions by LLM](images/style_enum_temporal_handling_stacked.png)

* **Linear dominates** across the board (≈82–99%).
* **Selective nonlinearity:** GPT-5.1 (medium reasoning) and Claude Opus 4.5 use the most **flashback**, with Claude Sonnet 4.5 Thinking 16K also above-average.
* **Braided/fragmented timelines are rare,** with only small (but visible) shares in a handful of models.
* **Near-all linear:** Llama 4 Maverick and GPT-OSS-120B are effectively straight-chronology by default.


---
### Stakes level

![Style Fingerprints • Stakes Level — Choice Proportions by LLM](images/style_enum_stakes_level_stacked.png)

* **Existential stakes dominate** for every model; most bars are two-thirds or more existential.
* **Most existential:** Llama 4 Maverick, Mistral Medium 3.1, and Cohere Command A.
* **Moral stands out** most for GPT-5.2 (medium reasoning) (largest moral band), with GPT-5 Pro next and a small cluster of other frontier models behind.
* **Relational stakes** remain a small slice overall, but peak for Grok 4 and Grok 4.1 Fast Reasoning (with Claude Opus 4.5 also higher than peers).

---
### Setting time

![Style Fingerprints • Setting Time — Choice Proportions by LLM](images/style_enum_setting_time_stacked.png)

* **Timeless dominates** across models; **Future** is the main alternative and **Contemporary** is third.
* **Future-heavy outliers:** Gemini 3 Pro Preview leads by a wide margin, with Claude Sonnet 4.5 (both variants) and Gemini 2.5 Pro also leaning futureward.
* **Timeless-heavy outliers:** GPT-OSS-120B, Llama 4 Maverick, and Cohere Command A.
* **Near-past/historical** remain almost absent; the highest **Contemporary** shares appear for Claude Sonnet 4.5 Thinking 16K and Claude Opus 4.1.


---
### Setting space

![Style Fingerprints • Setting Space — Choice Proportions by LLM](images/style_enum_setting_space_stacked.png)

* **Abstract is the modal setting** overall, with **Rural** and **Workplace** close behind (a three-way split rather than a single winner).
* **Most abstract:** Qwen 3 Max Preview and Deepseek V3.2 Exp, with GPT-OSS-120B also strongly abstract.
* **Rural tilt:** Qwen 3 235B (25-07 Think) and both DeepSeek V3.1 variants.
* **Workplace tilt:** Claude Opus 4.1 and both Claude Sonnet 4.5 variants.


---
### Sentence form preference

![Style Fingerprints • Sentence Form Preference — Choice Proportions by LLM](images/style_enum_sentence_form_preference_stacked.png)

* **Balanced dominates** for most models; several are effectively 100% balanced (notably GPT-5 Pro and the Claude Opus/Sonnet 4.5 variants).
* **Hypotaxis outliers:** Qwen 3 235B (25-07 Think) and Grok 4 are the strongest subordinators, with GPT-OSS-120B also notably hypotactic.
* **Parataxis is rare,** appearing only as thin slivers.
* **Note:** Kimi K2 stays mostly balanced despite high syntax complexity, showing complexity doesn’t require heavy hypotaxis.


---
### Sensory bias

![Style Fingerprints • Sensory Bias — Choice Proportions by LLM](images/style_enum_sensory_bias_stacked.png)

* **Visual leads** for nearly every model; Deepseek V3.2 Exp, Claude Sonnet 4.5 (no reasoning), and Grok 4.1 Fast Reasoning are the most sight-driven.
* **Mixed palettes** stand out for Kimi K2 and o3-pro, which rely less on a single sensory channel (with GPT-5 Pro also above average on mixed sensory usage).
* **Auditory is secondary** and stays modest overall; it peaks most for DeepSeek V3.1 (both variants), with GPT-5 Pro also elevated. **Tactile** cues remain minimal everywhere.


---
### Rhetorical stance

![Style Fingerprints • Rhetorical Stance — Choice Proportions by LLM](images/style_enum_rhetorical_stance_stacked.png)

* **Near-uniformly Earnest.** All models default to an earnest narrative posture (≈99.8% on average).
* **Other stances are negligible.** Ambiguous and ironic appear only as trace slices (largest for GPT-5.1 (medium reasoning)).
* **Implication:** stance is not a differentiator here; to elicit irony or detachment you need explicit prompting or constraints.


---
### Register level

![Style Fingerprints • Register Level — Choice Proportions by LLM](images/style_enum_register_level_stacked.png)

* **High register dominates** across all models, effectively the default narrative voice.
* **Neutral is the main alternative** and is most visible for Mistral Large 3 and the Claude Sonnet 4.5 variants; **Mixed** appears mainly for Mistral Medium 3.1.
* **Colloquial is essentially absent,** aligning with the near-uniform earnest stance.


---
### Prompt dependency

![Style Fingerprints • Prompt Dependency — Choice Proportions by LLM](images/style_enum_prompt_dependency_stacked.png)

* **Medium dependency dominates** overall, with most models landing in a Medium/High split rather than “all High.”
* **Most prompt-independent (highest Medium):** the GPT-5 family (especially GPT-5.2, GPT-5.1, and GPT-5 Pro) adds the most beyond the required elements.
* **Most prompt-dependent (highest High):** Llama 4 Maverick (≈all High), followed by Grok 4 and Cohere Command A.
* **Low is essentially absent** across the board, as expected under element-constrained prompts.


---
### POV scope

![Style Fingerprints • Pov Scope — Choice Proportions by LLM](images/style_enum_pov_scope_stacked.png)

* **Single-POV is the default** for essentially every model (≈93–100%).
* **Alternating and ensemble** are rare, but o3-pro shows the largest (still small) multi-POV usage.
* **Implication:** viewpoint scope isn’t a differentiator under these prompts; to test multi-POV behavior, prompts must ask for it explicitly.


---
### POV person

![Style Fingerprints • Pov Person — Choice Proportions by LLM](images/style_enum_pov_person_stacked.png)

* **Close third dominates** for nearly every model.
* **First-person outliers:** GPT-5 Pro is overwhelmingly first-person, with GPT-5.1 and GPT-5.2 also notably above baseline; o3-pro shows a smaller but visible first-person share.
* **Second person is essentially absent** across the board.
* **Omniscient** remains a thin slice, peaking most for o3-pro.


---
### Narrator reliability

![Style Fingerprints • Narrator Reliability — Choice Proportions by LLM](images/style_enum_narrator_reliability_stacked.png)

* **Reliable dominates** almost entirely for every model; *unreliable* narration is effectively absent.
* **Ambiguity is concentrated** in the GPT-5 family: GPT-5 Pro and GPT-5.1 show the largest ambiguous slices, with GPT-5.2 also above baseline.
* **Implication:** unreliable narrators don’t emerge by default—prompts must call for them explicitly.


---
### Narrative modality

![Style Fingerprints • Narrative Modality — Choice Proportions by LLM](images/style_enum_narrative_modality_stacked.png)

* **Balanced is the default** for most models, with smaller reflective/scenic slices.
* **Reflective-heavy outlier:** Llama 4 Maverick is by far the most reflective. A secondary reflective cluster includes GPT-5 Pro, GPT-5.1 (medium reasoning), Deepseek V3.2 Exp, and Qwen 3 Max Preview.
* **Scene-forward cohort:** Gemini 3 Pro Preview is the most scenic, followed by Grok 4.1 Fast Reasoning and Mistral Large 3 (with Kimi K2-0905 also above baseline).
* **Mosaic/reportage are negligible**, indicating little collage/documentary mode under these prompts.


---
### Narrative drive

![Style Fingerprints • Narrative Drive — Choice Proportions by LLM](images/style_enum_narrative_drive_stacked.png)

* **Idea-driven is the baseline** across models; plot and situation are minor contributors.
* **Voice-led outliers:** GPT-5 Pro shows the largest voice-driven slice among the latest GPT-5 variants, with Kimi K2 also elevated.
* **Character-forward cohort:** Claude Opus 4.5 leads character-driven stories, with GPT-5.2 (medium reasoning) and Mistral Large 3 also strongly character-tilted.
* **Situation remains negligible,** confirming momentum usually comes from idea, voice, or character rather than set-ups.


---
### Motif strategy

![Style Fingerprints • Motif Strategy — Choice Proportions by LLM](images/style_enum_motif_strategy_stacked.png)

* **Two-strategy world:** models almost always use **Threaded** or **Transforming** motifs; **Reprise** is negligible.
* **Threaded-leaning:** Gemini 3 Pro Preview, Mistral Large 3, and Claude Sonnet 4.5 (no reasoning) show the strongest threaded share.
* **Transforming-heavy:** Kimi K2 is the clear transforming outlier, with o3-pro and DeepSeek V3.1 Reasoner also strongly transforming-tilted.
* **Mixed craft:** most remaining models sit in a threaded-dominant blend, with transforming as a substantial minority.


---
### Metafictional devices

![Style Fingerprints • Metafictional Devices — Choice Proportions by LLM](images/style_enum_metafictional_devices_stacked.png)

* **Absent dominates** for most models, but incidental metafiction is a real (still minority) slice in this set.
* **Incidental outliers:** Kimi K2-0905 and GPT-5.2 (medium reasoning) show the most cameo-level self-reference, with GPT-5 Pro also above baseline.
* **Sustained use remains rare** (single-digit percentages at most).
* **Takeaway:** metafiction rarely emerges by default; you generally must ask for it.


---
### Language mix

![Style Fingerprints • Language Mix — Choice Proportions by LLM](images/style_enum_language_mix_stacked.png)

* **Monolingual dominates** across the board; most models are ≥95% single-language, though GLM-4.5/GLM-4.6 dip closer to ~90%.
* **Occasional code-switches** are concentrated in GLM-4.6 and GLM-4.5, with small traces elsewhere.
* **Integrated multilingual style is essentially absent.** If you want sustained bilingual voice, the prompt must require it.


---
### Genre family

![Style Fingerprints • Genre Family — Choice Proportions by LLM](images/style_enum_genre_family_stacked.png)

* **Fabulist is the plurality** across models, with **Literary** second and **Speculative** third.
* **Most fabulist:** GPT-OSS-120B, Kimi K2, and o3-pro (medium reasoning).
* **Most literary:** DeepSeek V3.1 (both variants) and Qwen 3 235B (25-07 Think).
* **Most speculative:** Gemini 3 Pro Preview, with the Claude Sonnet 4.5 variants also notably speculative-tilted.


---
### Free indirect presence

![Style Fingerprints • Free Indirect Presence — Choice Proportions by LLM](images/style_enum_free_indirect_presence_stacked.png)

* **Incidental dominates.** Most models touch free indirect style briefly; **sustained** use is rare (largest for Mistral Medium 3.1, still a small slice).
* **GPT-5 Pro largely avoids FID** (mostly **Absent**), matching its strong first-person preference.
* **Takeaway:** persistent free-indirect narration isn’t a default behavior; it needs explicit prompting.


---
### Exposition strategy

![Style Fingerprints • Exposition Strategy — Choice Proportions by LLM](images/style_enum_exposition_strategy_stacked.png)

* **Distributed exposition is near-universal**—virtually every model parcels context through the scene rather than front-loading.
* **Minimal exposition** is most visible for GPT-OSS-120B and Llama 4 Maverick (with GLM-4.6 also elevated). **Front-loaded** remains a small band, led by Deepseek V3.2 Exp.
* **Takeaway:** exposition strategy is not a strong differentiator here; under 600–800 words, models converge on weaving background into the action.


---
### Ending valence

![Style Fingerprints • Ending Valence — Choice Proportions by LLM](images/style_enum_ending_valence_stacked.png)

* **Positive dominates** for every model; GPT-OSS-120B and Cohere Command A are almost entirely positive, with Llama 4 Maverick also strongly positive.
* **Ambiguous endings** concentrate in a few models: GPT-5.1 (medium reasoning) is the clear leader, followed by Gemini 3 Pro Preview and Mistral Large 3.
* **Negative endings** are rare to vanishing (highest for Gemini 3 Pro Preview, still only a small slice).
* **Takeaway:** without explicit prompting, models resolve toward optimistic or gently open finales.


---
### Dialogue markup

![Style Fingerprints • Dialogue Markup — Choice Proportions by LLM](images/style_enum_dialogue_markup_stacked.png)

* **Minimal attribution dominates** for nearly all models; tag-heavy dialogue is rare.
* **Beat-heavy users (still rare overall):** GPT-5.1 (medium reasoning) is the strongest beat-heavy outlier, with Mistral Medium 3.1 next (and smaller beat-heavy slices for GPT-5.2 and the Mistral Large 3).
* **Mixed styles:** Baidu Ernie 4.5 and Claude Sonnet 4.5 (no reasoning) keep the largest mixed markup, alternating beats and tags (with Claude Sonnet 4.5 Thinking 16K also elevated).
* **Extremes:** GPT-OSS-120B and Llama 4 Maverick are almost entirely minimal, with Kimi K2 Thinking and Deepseek V3.2 Exp also very minimal.


---
### Conflict type

![Style Fingerprints • Conflict Type — Choice Proportions by LLM](images/style_enum_conflict_type_stacked.png)

* **Internal conflict dominates** for every model; Llama 4 Maverick and Cohere Command A are the most internal, with Kimi K2 also very internal-heavy.
* **Societal is the main secondary band** and peaks most for GPT-5.2 (medium reasoning), followed by GPT-5 Pro and several Claude/Gemini/o3-pro variants.
* **Supernatural is the #3 band** and is most visible for Mistral Large 3 (with Grok 4.1 Fast Reasoning also elevated); environmental and interpersonal remain small.
* Overall pattern matches the earlier **internal–external ratio** results: stories skew inward unless the prompt pushes otherwise.


---
### Closure form

![Style Fingerprints • Closure Form — Choice Proportions by LLM](images/style_enum_closure_form_stacked.png)

* **Resonant is the default** across all models; most endings resolve by reweighting meaning rather than a decisive act.
* **Decisive outliers:** Deepseek V3.2 Exp leads by a wide margin, with Grok 4.1 Fast Reasoning and Grok 4 next.
* **Circular is the main alternative** to resonant and is especially visible for Kimi K2 Thinking, with Llama 4 Maverick and Deepseek V3.2 Exp also elevated.
* **Suspended/open are rare,** but suspended peaks for Kimi K2; open peaks for Llama 4 Maverick.


---
### Cast size

![Style Fingerprints • Cast Size — Choice Proportions by LLM](images/style_enum_cast_size_stacked.png)

* **Solo dominates** for most models. It’s highest for Llama 4 Maverick and GPT-OSS-120B (with Qwen 3 235B also very solo-heavy).
* **Duo** is the main secondary option and peaks for Mistral Large 3, with GPT-5.1 (medium reasoning) and o3-pro also duo-forward.
* **Small casts** are most common for GPT-5.2 (medium reasoning) and the other GPT-5 variants; **ensemble** is almost nonexistent.


---
### Style numeric axes — correlations (per-LLM means)

![Style Numeric Axes • Pearson Correlations (Per-LLM Means)](images/style_numeric_axis_correlation.png)

* **Craft cluster moves together.** *Voice style*, *imagery density*, *rhythm*, *tone*, and *concreteness* are tightly linked (e.g., voice–imagery ≈ 0.99; voice–rhythm ≈ 0.96). Models that elevate one of these usually elevate the others.
* **Paragraphing is stagecraft more than grammar.** *Paragraphing/lineation* has a modest tie to *syntax complexity* (≈0.28) but tracks *dialogue subtext* (≈0.67) and *tonal span* (≈0.68).
* **POV depth shapes nuance.** *POV distance* correlates with *tonal span* (≈0.79) and *dialogue subtext* (≈0.83), suggesting deeper interior access coexists with tonal modulation and implied meaning.
* **Experimentation comes with ellipsis.** *Experimentation degree* aligns strongly with *associative gaps* (≈0.96) and also with *imagery* (≈0.86) and *voice* (≈0.85); its tie to *closure cadence* is modest (≈0.36).
* **Closures stand somewhat apart.** *Closure cadence* is weakly connected to most craft axes, and only mildly related to *realism spectrum* (≈0.17).
* **Worldbuilding and externality go together.** *Worldbuilding intensity* rises with *internal–external ratio* (≈0.79) and *concreteness* (≈0.70), but only moderately with *structure/pacing* (≈0.45).
* **Dialogue volume vs. nuance.** *Dialogue density* correlates with *internal–external ratio* (≈0.57), but the richer signal is *dialogue subtext*, which tracks *tonal span* (≈0.90) and the craft cluster (rhythm ≈0.77, voice ≈0.65).
* **Realism is moderately tied to craft and experimentation.** It correlates with *voice* (≈0.62), *imagery* (≈0.67), and *experimentation* (≈0.68), but only weakly with *paragraphing* (≈0.14).

**Implication:** many surface-craft axes are collinear, while **endings, paragraphing strategy, and realism** behave more independently—useful when selecting a smaller set of levers to compare models.


---
## Head-to-head comparisons

Below are A‑vs‑B analyses for stories written to the same required elements. Each report separates rubric‑aligned differences (Q1–Q8 craft + 9A–9J element integration) from beyond‑rubric insights (e.g., risk appetite, humor timing, cultural specificity).

- [Grok 4 (A) vs GPT-5 Medium (B)](inter_llm_comparison_summaries/grok-4-0709__vs__gpt-5-medium.txt)
- [Kimi K2-0905 (A) vs Qwen 3 Max Preview (B)](inter_llm_comparison_summaries/kimi-k2-0905__vs__qwen3-max-preview.txt)
- [Kimi K2-0905 (A) vs DeepSeek V3.1 Reasoner (B)](inter_llm_comparison_summaries/kimi-k2-0905__vs__deepseek-reasoner.txt)
- [Claude Opus 4.1 (no reasoning) (A) vs GPT-5 (medium reasoning) (B)](inter_llm_comparison_summaries/claude-opus-4-1-20250805-0K__vs__gpt-5-medium.txt)
- [Mistral Medium 3.1 (A) vs GPT-5 (medium reasoning) (B)](inter_llm_comparison_summaries/mistral-medium-2508__vs__gpt-5-medium.txt)
- [Kimi K2-0905 (A) vs GLM-4.5 (B)](inter_llm_comparison_summaries/kimi-k2-0905__vs__glm-4-5.txt)
- [Gemini 2.5 Pro (A) vs GPT-5 (medium reasoning) (B)](inter_llm_comparison_summaries/gemini-2.5-pro__vs__gpt-5-medium.txt)
- [Kimi K2-0905 (A) vs GPT-5 (medium reasoning) (B)](inter_llm_comparison_summaries/kimi-k2-0905__vs__gpt-5-medium.txt)


Rubric‑Aligned: Directly maps to our grading rubric (Q1–Q8 craft; 9A–J element integration), with concrete, falsifiable observations tied to on‑page evidence.

Beyond‑Rubric: Additional, non‑graded distinctions (e.g., metaphor layering, syntactic rhythm, idiomatic freshness, genre fluency). These contextualize differences that the rubric doesn’t fully capture.

---


## Poor‑writing samples (what goes wrong)  
The folder `poor_writing/` collects short excerpts where top LLMs trip on continuity, physics, or basic logic. Each file lists the offending lines with a one‑line diagnosis. A few representative snippets:

- GPT‑5.2 (medium reasoning) — see `poor_writing/gpt-5.2-medium.txt`
  - "\"The harp waited in a cave… | She followed the sound out of the cave… | …laid the crocodile tooth in Elowen's palm… | Mara kept playing…\"" (state/prop contradiction)
  - "\"the last strip of sun clung to the horizon\" | \"a few stars survived the pale morning\" | \"first true light…\"" (time-of-day inconsistency)
  - "\"I turned my back on the cheers… ladder dropped to the black water… | …breathing silt…\"" (physics/affordances ignored)

- Gemini 2.5 Pro — see `poor_writing/gemini-2.5-pro.txt`
  - "…lunar observatory above the clouds… sunrise over the distant Earth" (no clouds on the Moon; no Earth “sunrise” there)
  - "He inhaled the thin air that smelled of burnt helium" (helium is odorless and doesn’t burn)

- Claude Opus 4.1 (no reasoning) — see `poor_writing/claude-opus-4-1-20250805-0K.txt`
  - "She opened it, revealing not ink but ashes—… before beginning the embalming." (ashes don’t precede cremation)
  - "The gondola swayed gently at thirty thousand feet… rescue helicopters." (helos don’t operate at 30k ft)

Browse the rest in `poor_writing/` for a compact catalog of common failure modes across models.


---

## Poor‑writing theme summaries (why it goes wrong)
The folder `poor_writing_theme_summaries/` distills recurring failure patterns by model—short narratives explaining not just the errors, but the mechanisms behind them. Highlights:

- GLM‑4.5 — see `poor_writing_theme_summaries/glm-4-5.txt`
  - Sentence‑over‑scene bias: local vividness overwrites prior state (time of day, identities, object states) after soft resets.
  - Resolution templates over causality: endgame emits outcomes and jargon without bridges; figurative language gets literalized.
  - Surface rubble under strain: mixed‑script/token leaks and half‑edits at transition points.

- Kimi K2‑0905 — see `poor_writing_theme_summaries/kimi-k2-0905.txt`
  - Short planning horizon: props teleport/duplicate and tenses flip for cadence; aphorisms override chronology.
  - Physics optional under lyric pressure: environment/affordances ignored unless rules are restated explicitly.
  - Numbers/rules used decoratively; occasional truncated lines reveal cadence‑first decoding.

- Qwen 3 Max Preview — see `poor_writing_theme_summaries/qwen3-max-preview.txt`
  - Absolutes as style, not rules: stated constraints are contradicted by the next striking image (negations, “twin,” “only”).
  - Local state tracking: objects exist in two places; persona/vehicle traits blend; paragraph breaks act as soft resets.
  - Expertise veneer without mechanism: precise nouns/numbers and hybrid devices that don’t work in any coherent world.

These writeups pair with `poor_writing/` examples: one shows the symptoms; the other explains the disease.

---

## Multi-agent benchmarks
- [PACT - Benchmarking LLM negotiation skill in multi-round buyer-seller bargaining](https://github.com/lechmazur/pact)
- [BAZAAR - Evaluating LLMs in Economic Decision-Making within a Competitive Simulated Market](https://github.com/lechmazur/bazaar)
- [Public Goods Game (PGG) Benchmark: Contribute & Punish](https://github.com/lechmazur/pgg_bench/)
- [Elimination Game: Social Reasoning and Deception in Multi-Agent LLMs](https://github.com/lechmazur/elimination_game/)
- [Step Race: Collaboration vs. Misdirection Under Pressure](https://github.com/lechmazur/step_game/)

## Other benchmarks
- [Extended NYT Connections](https://github.com/lechmazur/nyt-connections/)
- [LLM Thematic Generalization Benchmark](https://github.com/lechmazur/generalization/)
- [LLM Creative Story-Writing Benchmark](https://github.com/lechmazur/writing/)
- [LLM Confabulation/Hallucination Benchmark](https://github.com/lechmazur/confabulations/)
- [LLM Deceptiveness and Gullibility](https://github.com/lechmazur/deception/)
- [LLM Divergent Thinking Creativity Benchmark](https://github.com/lechmazur/divergent/)

## Updates
- Dec 18, 2025: Expanded to 29 models (added GPT-5 variants, Claude 4.5/Sonnet 4.5 variants, Gemini 3, Grok 4.1, Deepseek V3.2 Exp, GLM-4.6, Qwen 3 Max Preview, Mistral Large 3, and multiple Kimi K2 variants)
- Sep 8, 2025: Head-to-head comparisons added

## More
- Follow [@lechmazur](https://x.com/LechMazur) on X (Twitter) for other upcoming benchmarks and more.
