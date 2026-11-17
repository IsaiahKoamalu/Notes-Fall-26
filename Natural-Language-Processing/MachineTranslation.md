
#### IBM Models
- Start with lexical translation model
- Goal: learn the word translation probabilities for each word

#### Phrase-Based MT
- Phrases as the unit of translation (rather than words)
	- more context
	- non-compositional phrases (idioms)
		- ex: "Kick the bucket."
- Three submodels
	- phrase translation
	- reordering model
	- language model
- Final model is a weighted combination of the three submodels.

#### Generation
- Called decoding
- **Greedy sampling**: pick the most likely next word
	- not so good
- **Beam search:** keep $k$ best choices at each timestep.

#### Neural Models
- Encoder-Decoder
- Decoder only
- Beam search works too

#### Evaluation
- **Adequacy:** does the output convey the original meaning.
	- is part of the message lost or distorted?
- **Fluency:** is the output natural in the target language.
- Get humans to rate adequacy and fluency on a scale of 1-5
	- humans are paid, and they disagree with eachother.
- Automatic metrics
	- cheap and consistent, but may not match human judgements.
	- given system output and reference translations, compute their similarity.

#### BLEU
- Probably the most common metric.
- Measures n-gram (1-4 gram) overlap between output and reference.
- 1st term is a brevity penalty for output that is too short.
- Typically computed across all sentences, not just a single one.

#### Other Common Metrics
- METEOR: partial credit for matching stems (goes, went) and synonyms (goes, walk).
- ROUGE: more n-gram overlaps, but can skip.
- chrF++: match character n-grams, partial credit for morphological variants.

#### Critiques of Automatic Metrics
- Ignore relevance of words.
	- names and core concepts more important than determiners and punctuation.
- Operate on local level.
- Scores are meaningless
- Human translators score low on BLEU

#### Metrics Shared Task
- Annual events to come up with new metrics.
- Correlate with human judgements.

#### Evaluation Models
- Train a model to evaluate
	- **input:** source, model output
	- **output:** human judgement score
- No references needed
- AKA quality estimation
- **Popular:** Cometkiwi

#### Low-Resource
- What if you do not have enough bitext?
- Get more data
	- hire humans
	- scrape the web
	- generate your own

#### Scraping the Data for Bitext
- CommonCrawl, ParaCraw.
	- only 160 languages
- Need to align the sentences some how.
	- LASER, other embedding methods

#### Generate your Own Data
- Backtranslation (Sennrich + 2016)