# BBC News Comprehensive Text Analysis — Analysis Report

## 1. Dataset and method

The dataset contains **2,225** BBC News documents, **9,635** vocabulary terms and **286,774** nonzero document-term entries, organized into 5 news categories. The input `.mtx` is a sparse term-frequency matrix, not raw article prose. `.terms` contains vocabulary entries (some stemmed), `.docs` contains identifiers, and `.classes` provides category labels. The analysis uses Python standard libraries, NumPy, Pandas and Matplotlib; no specialized NLP libraries.

## 2. Summary statistics

| Metric | Value |
|---|---:|
| Documents | 2,225 |
| Vocabulary terms | 9,635 |
| Total word occurrences | 425,832 |
| Mean words per document | 191.39 |
| Mean characters per token | 5.32 |
| Median term frequency | 10.00 |
| Standard deviation of term frequencies | 111.59 |
| Vowel/consonant ratio in stored tokens | 0.601 |
| Zipf log-log slope | -1.286 |
| Document-length upper outliers (1.5×IQR) | 57 |

## 3. Findings and visual insights

The most frequent non-stopword terms are **year, peopl, game, time, first, govern, world, get, plai, film**. Stopwords have been removed from the top-terms charts to reveal more interpretable themes; the full unfiltered counts remain in `word_statistics.csv`. The terms may contain stemming artifacts because the vocabulary is already processed.

The rank-frequency chart (`08_zipf_law.png`) shows a strongly skewed term distribution. A fitted log-log slope of **-1.286** can be compared with the idealized Zipf exponent of -1, but this fitted value is descriptive rather than a formal goodness-of-fit test. The weighted word-length histogram shows a mean token length of **5.32** characters; the overlaid normal curve is a visual reference, not a claim of normality.

The character-frequency charts show the relative dominance of letters and provide a vowel/consonant ratio. Punctuation may be missing because the provided term list is preprocessed. The document-length box plot identifies **57** high-length outliers by the conventional 1.5×IQR rule. Category comparison and the richness scatter chart examine whether document length is associated with type-token ratio. A lower ratio in longer documents can arise mechanically from repeated words; it is not necessarily lower writing quality.

## 4. Patterns, phrases and sentiment

Email, phone, URL, hashtag, mention, date, currency and sentence regex extraction requires original character sequences. **No raw articles were included in the four input files**, so no authentic regex matches, sentence lengths or ordered n-grams can be claimed from these files. `extracted_patterns.json` records this limitation; adding actual `.txt` articles to `original_articles/` activates extraction and ordered bigrams/trigrams. The co-occurrence CSV is **document-level co-occurrence, not phrase frequency**. Keyword-based sentiment scores are exploratory counts, not validated sentiment labels.

## 5. Challenges and solutions

The main challenge is the sparse MatrixMarket format and the absence of original text. A custom streaming-compatible parser converts term/doc indices from one-based indexing and aggregates counts without constructing a huge dense matrix. The `.classes` file uses zero-based document indices; these are aligned separately. Because the dataset stores tokens rather than sentences, the implementation reports unavailable measures explicitly and supplies a distinct original-text processing path. Regex boundaries and optional phone normalization help prevent common false positives when original text is present, although real-world patterns remain more diverse than the examples.

## 6. Conclusions

The project demonstrates reliable file loading, regex functions, statistical frequency analysis, character analysis, Pandas grouping/pivots, 13 saved visualizations, Zipf analysis, document-level co-occurrence and keyword sentiment. It avoids reconstructing fictitious news prose. To complete sentence-level and regex-based evaluation on real content, add original `.txt` news articles and rerun the same script.
