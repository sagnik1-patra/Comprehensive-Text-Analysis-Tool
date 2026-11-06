
# Comprehensive Text Analysis Tool Using Python

## BBC News Dataset | NLP Foundations | Statistical Analysis | Data Visualization

A comprehensive **Text Analysis Tool** developed using core Python libraries, including **Regular Expressions (Regex), NumPy, Pandas, and Matplotlib**, to extract meaningful insights from textual datasets.

This project analyzes the **BBC News Dataset**, containing articles from five different news categories. It implements word frequency analysis, character-level statistics, vocabulary richness analysis, regular expression pattern extraction, document-level comparisons, keyword-based sentiment analysis, and data visualization.

The project demonstrates fundamental **Natural Language Processing (NLP)** techniques without relying on specialized NLP libraries such as NLTK or spaCy.

---

## 1. Project Overview

Text analysis is an important component of Natural Language Processing that involves extracting meaningful information, identifying patterns, and understanding statistical properties of textual data.

The primary objective of this project is to build a Python-based text analysis system capable of processing large textual datasets and generating statistical insights through numerical computations and graphical representations.

The system uses the BBC News Dataset to investigate:

- Word frequency distributions
- Most frequently occurring terms
- Word length distributions
- Character frequency distributions
- Vocabulary richness
- Document length variations
- Category-wise textual characteristics
- Word co-occurrence patterns
- Zipf's Law
- Keyword-based sentiment indicators
- Relationships between different text metrics

The tool automatically generates CSV files, JSON reports, statistical summaries, and visualization graphs.

### Main Visualization: Top 20 Most Frequent Words

![Top 20 Most Frequent Words](results/02_top20_horizontal.png)

**Figure 1:** Horizontal bar chart displaying the 20 most frequently occurring meaningful terms in the BBC News Dataset after stopword filtering.

This visualization highlights the dominant vocabulary patterns across the news collection and helps identify frequently discussed topics.

---

## 2. Objectives

The main objectives of this project are:

1. Develop a comprehensive text analysis system using Python.
2. Load and process textual information from multiple dataset files.
3. Implement regular expressions for extracting structured patterns.
4. Perform statistical analysis using NumPy.
5. Organize and manipulate text statistics using Pandas.
6. Generate informative visualizations using Matplotlib.
7. Analyze word frequency distributions and vocabulary characteristics.
8. Compare textual properties across different news categories.
9. Examine Zipf's Law in natural language.
10. Implement exploratory keyword-based sentiment analysis.
11. Generate structured analysis reports automatically.
12. Export results in CSV, JSON, TXT, and PNG formats.
13. Provide an interactive visualization interface using Matplotlib widgets.

---

## 3. Dataset Description

### Dataset Name

**BBC News Dataset**

### Dataset Type

Preprocessed news document-term frequency dataset.

### Dataset Statistics

| Attribute | Description |
|---|---|
| Dataset | BBC News |
| Total Documents | 2,225 |
| Vocabulary Size | 9,635 terms |
| Total Word Occurrences | 425,832 |
| Number of Categories | 5 |
| Data Representation | Sparse document-term matrix |
| Matrix Format | Matrix Market (.mtx) |
| Vocabulary Format | .terms |
| Document Identifiers | .docs |
| Category Labels | .classes |

### News Categories

The dataset consists of five categories:

1. Business
2. Entertainment
3. Politics
4. Sport
5. Technology

These categories enable comparisons of vocabulary usage, document length, and other textual characteristics.

### Dataset Files

**bbc.mtx**

Contains the sparse document-term frequency matrix. Each nonzero entry represents the frequency of a vocabulary term within a particular document.

**bbc.terms**

Contains the vocabulary terms corresponding to matrix rows.

**bbc.docs**

Contains document identifiers corresponding to matrix columns.

**bbc.classes**

Contains the category labels assigned to documents.

### Important Dataset Limitation

The supplied BBC dataset is a **bag-of-words representation**, not a collection of original article paragraphs.

Therefore, the dataset preserves word occurrence frequencies but does not preserve original sentence structure or word order.

As a result:

- Word frequencies can be calculated accurately.
- Document-level vocabulary statistics can be calculated.
- Category-wise comparisons can be performed.
- Character statistics can be estimated from stored vocabulary tokens.
- Original sentence lengths cannot be recovered.
- Ordered bigrams and trigrams cannot be recovered.
- Original emails, phone numbers, URLs, and dates cannot be reliably reconstructed.

The implementation supports optional original `.txt` articles for analyses requiring complete textual sequences.

---

## 4. Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| NumPy | Numerical and statistical analysis |
| Pandas | Data processing and tabular analysis |
| Matplotlib | Data visualization |
| Regex (`re`) | Pattern extraction and text processing |
| Collections | Word frequency counting |
| JSON | Structured output storage |
| pathlib | File and directory management |
| CSV | Exporting statistical results |
| Jupyter Notebook | Interactive code execution |

### Python Libraries

```python
from pathlib import Path
from collections import Counter, defaultdict

import re
import json
import math
import csv
import sys

from urllib.parse import urlparse

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

from matplotlib.widgets import RadioButtons
```

The project uses core Python libraries rather than specialized NLP frameworks.

---

## 5. Project Architecture

The project follows a modular processing architecture.

```text
                BBC NEWS DATASET
                       |
                       v
              DATA LOADING MODULE
                       |
                       v
             DATA VALIDATION MODULE
                       |
                       v
            DOCUMENT-TERM PROCESSING
                       |
                       v
               TEXT STATISTICS
                       |
          +------------+------------+
          |            |            |
          v            v            v
      NumPy         Pandas        Regex
     Analysis       Analysis      Analysis
          |            |            |
          +------------+------------+
                       |
                       v
              ADVANCED ANALYSIS
                       |
          +------------+------------+
          |            |            |
          v            v            v
       Zipf's      Vocabulary    Keyword
        Law         Richness     Sentiment
          |            |            |
          +------------+------------+
                       |
                       v
               VISUALIZATION
                       |
                       v
               OUTPUT GENERATION
                       |
          +------------+------------+
          |            |            |
          v            v            v
         CSV          JSON          PNG
                       |
                       v
                ANALYSIS REPORT
```

---

## 6. Project Folder Structure

```text
Comprehensive Text Analysis Tool/
|
|-- bbc.mtx
|-- bbc.terms
|-- bbc.classes
|-- bbc.docs
|
|-- comprehensive_text_analysis.py
|-- BBC_Analysis_Jupyter_One_Cell.ipynb
|-- README.md
|-- ANALYSIS_REPORT.md
|-- requirements.txt
|
|-- original_articles/
|   |-- Optional original text articles
|
|-- results/
|   |
|   |-- 01_top20_words.png
|   |-- 02_top20_horizontal.png
|   |-- 03_word_length_histogram.png
|   |-- 04_character_frequency.png
|   |-- 05_letter_frequency.png
|   |-- 06_punctuation_frequency.png
|   |-- 07_document_length_boxplot.png
|   |-- 08_zipf_law.png
|   |-- 09_category_comparison.png
|   |-- 10_richness_scatter.png
|   |-- 11_dashboard_2x2.png
|   |-- 12_sentence_length_boxplot.png
|   |-- 13_bigram_analysis.png
|   |
|   |-- document_statistics.csv
|   |-- word_statistics.csv
|   |-- top_50_words.csv
|   |-- words_longer_than_10.csv
|   |-- groupby_word_length.csv
|   |-- groupby_first_character.csv
|   |-- pivot_length_by_first_character.csv
|   |-- crosstab_length_vowels.csv
|   |-- category_summary.csv
|   |-- top_document_cooccurrences.csv
|   |-- sentiment_keyword_scores.csv
|   |-- bigrams.csv
|   |-- trigrams.csv
|   |
|   |-- extracted_patterns.json
|   |-- summary_statistics.json
|   |-- cleaned_processed_text.txt
```

The `results` directory is created automatically when the analysis executes.

---

## 7. Installation and Setup

### Step 1: Install Python

Install Python 3.10 or newer.

Verify the installation:

```bash
python --version
```

### Step 2: Download the Project

Download or extract the project into a local directory.

Example Windows location:

```text
C:\Users\sagni\Downloads\Comprehensive Text Analysis Tool
```

### Step 3: Open the Project Directory

Open Command Prompt and execute:

```bat
cd /d "C:\Users\sagni\Downloads\Comprehensive Text Analysis Tool"
```

### Step 4: Install Required Libraries

```bash
pip install numpy pandas matplotlib
```

Alternatively, if the provided `requirements.txt` is available:

```bash
pip install -r requirements.txt
```

### Step 5: Verify Dataset Files

Ensure that all four BBC dataset files are present in the project directory:

```text
bbc.mtx
bbc.terms
bbc.classes
bbc.docs
```

### Step 6: Execute the Python Script

```bash
python comprehensive_text_analysis.py --show
```

This command performs the analysis, displays visualizations, and saves output files.

To generate outputs without displaying graphs:

```bash
python comprehensive_text_analysis.py
```

### Step 7: Execute in Jupyter Notebook

Install Jupyter if necessary:

```bash
pip install notebook
```

Start Jupyter:

```bash
jupyter notebook
```

Open:

```text
BBC_Analysis_Jupyter_One_Cell.ipynb
```

Run the analysis cell using:

```text
Shift + Enter
```

The notebook version uses directory detection compatible with Jupyter rather than relying on the script-only `__file__` variable.

---

## 8. Methodology

The project is divided into five major analytical components.

### Part 1: Data Loading and Exploration

The first module loads the dataset using Python file I/O.

The system reads the sparse matrix and maps vocabulary terms to individual documents.

#### Main Operations

- Read input files using encoding fallbacks.
- Parse Matrix Market coordinate data.
- Validate dataset dimensions.
- Convert matrix indices to Python indexing.
- Aggregate document-level word frequencies.
- Calculate document statistics.
- Create Pandas DataFrames.
- Export results to CSV.

#### Calculated Statistics

- Total number of documents
- Total word occurrences
- Vocabulary size
- Estimated character counts from stored terms
- Average word length
- Average document length
- Number of unique words per document
- Vocabulary richness

#### Average Word Length

Average word length is calculated as:

\[
\text{Average Word Length} =
\frac{\sum_i f_i L_i}{\sum_i f_i}
\]

Where:

- \(f_i\) represents the frequency of term \(i\).
- \(L_i\) represents the length of term \(i\).

#### Vocabulary Richness

The Type-Token Ratio (TTR) is used:

\[
TTR = \frac{\text{Unique Words}}{\text{Total Words}}
\]

A higher TTR indicates a larger proportion of unique vocabulary relative to document length.

**Generated Output:**

```text
results/document_statistics.csv
```

---

### Part 2: Regular Expression Pattern Extraction

Regular expressions are implemented to identify structured patterns in textual data.

The extraction module supports:

- Email addresses
- Phone numbers
- Hashtags
- Mentions
- URLs
- URL domains
- Dates
- Currency amounts

#### Email Extraction

Example:

```python
emails = re.findall(
    r'[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}',
    text
)
```

#### Phone Number Extraction

Supported examples:

```text
(123) 456-7890
123-456-7890
+1-123-456-7890
```

The system also supports normalization of recognized North American phone numbers.

#### URL Extraction

Supported examples:

```text
https://example.com
http://example.org
www.example.net
```

Extracted URLs can be grouped by domain.

#### Date Extraction

Supported formats include:

```text
12/05/2024
05-12-2024
December 12, 2024
```

#### Currency Extraction

Examples:

```text
$100
£50
€75
```

#### Hashtag and Mention Extraction

Examples:

```text
#Python
#DataScience
@username
```

#### Output

```text
results/extracted_patterns.json
```

**Important:** Authentic pattern extraction requires original article text. The supplied matrix dataset does not contain the original character sequences.

Users can add `.txt` articles to the `original_articles` directory to activate genuine regex extraction.

---

### Part 3: Text Statistics Using NumPy

NumPy is used to calculate statistical properties of the vocabulary and document collection.

#### Word Frequency Analysis

The system creates a frequency dictionary using Python's `Counter`.

```python
word_frequency = Counter()

for document in documents:
    word_frequency.update(document)
```

The resulting frequencies are converted into NumPy arrays.

#### Statistical Measures

The following measures are calculated:

- Mean
- Median
- Standard deviation
- 25th percentile
- 50th percentile
- 75th percentile

Example:

```python
frequencies = np.array(list(word_frequency.values()))

mean_frequency = np.mean(frequencies)
median_frequency = np.median(frequencies)
std_frequency = np.std(frequencies)

percentiles = np.percentile(
    frequencies,
    [25, 50, 75]
)
```

#### Character-Level Analysis

The system examines the characters appearing in vocabulary terms.

It calculates:

- Character frequency
- Letter frequency
- Most common characters
- Least common characters
- Vowel count
- Consonant count
- Vowel-to-consonant ratio

#### Vowel-to-Consonant Ratio

\[
VCR = \frac{\text{Total Vowels}}{\text{Total Consonants}}
\]

The result helps characterize the composition of stored vocabulary terms.

#### Sentence Length Analysis

The system includes regex-based sentence splitting for optional original articles.

When only the BBC matrix files are available, sentence length statistics are explicitly marked unavailable.

Document length statistics are analyzed separately.

---

### Part 4: Data Visualization Using Matplotlib

Matplotlib is used to generate graphical representations of the statistical findings.

The project generates **13 visualization files**.

#### Visualization 1: Top 20 Word Frequencies

![Top 20 Words](results/01_top20_words.png)

Displays the most frequent meaningful terms in the dataset.

#### Visualization 2: Horizontal Word Frequency Chart

![Horizontal Word Frequency](results/02_top20_horizontal.png)

Provides a more readable representation of the top 20 words, with frequency labels.

This is the primary visualization for the project.

#### Visualization 3: Word Length Distribution

![Word Length Histogram](results/03_word_length_histogram.png)

Displays the distribution of word lengths, weighted by word occurrence frequency.

A normal distribution reference curve is overlaid for comparison.

#### Visualization 4: Character Frequency

![Character Frequency](results/04_character_frequency.png)

Displays the 15 most frequent characters appearing in stored vocabulary tokens.

#### Visualization 5: Letter Frequency

![Letter Frequency](results/05_letter_frequency.png)

Analyzes the relative frequency of alphabetic characters.

#### Visualization 6: Punctuation Frequency

![Punctuation Frequency](results/06_punctuation_frequency.png)

Examines punctuation retained in vocabulary tokens.

Because the BBC dataset is preprocessed, punctuation may be absent or heavily reduced.

#### Visualization 7: Document Length Box Plot

![Document Length Box Plot](results/07_document_length_boxplot.png)

Displays document word-count variation and helps identify unusually long documents.

This is a document-length plot rather than a sentence-length plot.

#### Visualization 8: Zipf's Law

![Zipf's Law](results/08_zipf_law.png)

Illustrates the relationship between word rank and frequency using logarithmic axes.

#### Visualization 9: Category Comparison

![Category Comparison](results/09_category_comparison.png)

Compares average document lengths across BBC news categories.

#### Visualization 10: Vocabulary Richness

![Vocabulary Richness](results/10_richness_scatter.png)

Examines the relationship between document length and Type-Token Ratio.

#### Visualization 11: Combined Dashboard

![Text Analysis Dashboard](results/11_dashboard_2x2.png)

Combines four analytical visualizations into a 2×2 dashboard:

1. Most frequent terms
2. Document length distribution
3. Category-wise document lengths
4. Vocabulary richness

#### Visualization 12: Sentence Length Analysis

![Sentence Length](results/12_sentence_length_boxplot.png)

Displays sentence length statistics when original article text is available.

Otherwise, the figure explains that sentence-level data is unavailable.

#### Visualization 13: Bigram Analysis

![Bigram Analysis](results/13_bigram_analysis.png)

Displays frequent ordered bigrams when original article text is supplied.

Without original text, the figure documents the dataset limitation.

---

### Part 5: Pandas Data Analysis

Pandas is used for structured data manipulation, grouping, sorting, filtering, and statistical aggregation.

#### Word Statistics DataFrame

The word-level DataFrame contains:

| Column | Description |
|---|---|
| Word | Vocabulary term, used as index |
| Frequency | Total occurrence count |
| Length | Number of characters |
| First Character | Initial character |
| Vowel Count | Number of vowels |

#### Grouping by Word Length

The analysis calculates:

- Number of vocabulary terms per length
- Total word occurrences
- Average term frequency

#### Grouping by First Character

Words are grouped according to their starting characters.

#### Sorting and Filtering

The system extracts:

- Top 50 most frequent words
- Words longer than 10 characters
- Word frequency rankings

#### Pivot Tables

Pivot tables compare word lengths against first characters.

#### Cross-Tabulations

Cross-tabulations examine word length and vowel count relationships.

#### Generated CSV Files

```text
word_statistics.csv
top_50_words.csv
words_longer_than_10.csv
groupby_word_length.csv
groupby_first_character.csv
pivot_length_by_first_character.csv
crosstab_length_vowels.csv
category_summary.csv
```

---

## 9. Advanced Features and Bonus Implementations

### 9.1 Zipf's Law Analysis

Zipf's Law describes a common statistical pattern in natural language.

It suggests that word frequency is approximately inversely proportional to rank.

\[
f(r) \propto \frac{1}{r^s}
\]

Where:

- \(f(r)\) is the frequency of a word at rank \(r\).
- \(r\) is the word's rank.
- \(s\) is the Zipf exponent.

For many natural language collections, \(s\) is approximately 1.

The project calculates a fitted log-log slope using NumPy.

```python
slope, intercept = np.polyfit(
    np.log10(ranks),
    np.log10(frequencies),
    1
)
```

The resulting graph helps evaluate whether the BBC vocabulary exhibits a Zipf-like distribution.

**Output:**

```text
results/08_zipf_law.png
```

---

### 9.2 Interactive Dashboard

The project includes an interactive visualization using Matplotlib's `RadioButtons` widget.

Users can select news categories and observe changes in document length distributions.

For the script version, run:

```bash
python comprehensive_text_analysis.py --interactive
```

The interactive interface requires a supported graphical Matplotlib backend.

For Jupyter Notebook, an interactive backend such as `ipympl` may be required.

---

### 9.3 N-Gram Extraction

The project implements reusable functions for:

- Bigrams
- Trigrams

A bigram consists of two consecutive words.

Example:

```text
machine learning
artificial intelligence
```

A trigram consists of three consecutive words.

Example:

```text
natural language processing
```

Example implementation:

```python
def ngrams(tokens, n):
    return Counter(
        tuple(tokens[i:i+n])
        for i in range(len(tokens)-n+1)
    )
```

Since the BBC matrix does not preserve word order, authentic ordered n-grams are generated only from optional original text articles.

Outputs:

```text
results/bigrams.csv
results/trigrams.csv
```

---

### 9.4 Document-Level Word Co-occurrence

The system analyzes terms that frequently appear together within the same documents.

This helps identify thematic relationships between vocabulary terms.

For example, terms associated with finance may frequently appear together in business documents.

**Important:** Document-level co-occurrence does not mean that two words appear next to each other.

Output:

```text
results/top_document_cooccurrences.csv
```

---

### 9.5 Keyword-Based Sentiment Analysis

The project implements an exploratory sentiment scoring mechanism using predefined positive and negative word lists.

Positive keywords include:

```text
good
great
growth
success
profit
improve
strong
```

Negative keywords include:

```text
bad
loss
decline
crisis
failure
risk
weak
```

The sentiment keyword score is calculated as:

\[
S = P - N
\]

Where:

- \(P\) is the count of positive keywords.
- \(N\) is the count of negative keywords.

Interpretation:

| Score | Interpretation |
|---|---|
| Positive | More positive keywords |
| Negative | More negative keywords |
| Zero | Balanced or absent keywords |

These are keyword-count indicators, not validated sentiment classifications.

Output:

```text
results/sentiment_keyword_scores.csv
```

---

## 10. Results and Observations

### 10.1 Dataset Processing

The system successfully processes the BBC document-term dataset.

Key dataset characteristics:

| Metric | Result |
|---|---:|
| Documents | 2,225 |
| Vocabulary Terms | 9,635 |
| Total Word Occurrences | 425,832 |
| News Categories | 5 |
| Visualization Files | 13 |

### 10.2 Word Frequency Analysis

The word frequency analysis reveals that vocabulary usage is unevenly distributed.

A relatively small number of terms account for a large share of word occurrences, while many terms appear less frequently.

The horizontal bar chart makes it easier to identify the most dominant meaningful terms.

Stopword filtering improves interpretability by removing common grammatical words from the main frequency charts.

### 10.3 Word Length Analysis

The word length histogram shows how token lengths are distributed across the dataset.

The analysis provides information about common vocabulary lengths and the relative frequency of longer words.

The normal curve serves as a reference rather than proof that word lengths follow a normal distribution.

### 10.4 Character Frequency Analysis

Character-level analysis identifies differences in the frequency of individual letters.

The vowel-to-consonant ratio provides an additional numerical description of the vocabulary.

Because the source vocabulary is preprocessed, these findings describe the stored tokens rather than the original article characters.

### 10.5 Document Length Analysis

Document word counts vary across the collection.

The box plot helps identify:

- Typical document lengths
- Differences in document size
- Extremely long documents
- Statistical outliers

Outliers are identified using the conventional 1.5 × interquartile range method.

### 10.6 Category-Wise Comparison

Category-wise analysis compares average document lengths across business, entertainment, politics, sport, and technology.

This provides a way to investigate differences in writing characteristics between news categories.

### 10.7 Vocabulary Richness

Vocabulary richness is measured using Type-Token Ratio.

The scatter plot examines how vocabulary richness changes with document length.

Longer documents may naturally have lower Type-Token Ratios because common words are repeated more often.

Therefore, TTR should be interpreted alongside document length.

### 10.8 Zipf's Law

The Zipf visualization examines whether word frequencies follow a rank-frequency relationship.

The distribution is evaluated using logarithmic axes and a fitted straight line.

The fitted slope provides a descriptive estimate of the relationship between word rank and frequency.

### 10.9 Pattern Extraction

The regex module supports extraction of structured patterns from original text.

However, the BBC matrix does not contain sufficient information to recover the original patterns.

The tool therefore reports unavailable pattern results instead of generating artificial matches.

---

## 11. Output Files

The project generates several categories of outputs.

### Statistical Data

```text
document_statistics.csv
word_statistics.csv
top_50_words.csv
words_longer_than_10.csv
```

### Grouping and Comparison

```text
groupby_word_length.csv
groupby_first_character.csv
pivot_length_by_first_character.csv
crosstab_length_vowels.csv
category_summary.csv
```

### Advanced Analysis

```text
top_document_cooccurrences.csv
sentiment_keyword_scores.csv
bigrams.csv
trigrams.csv
```

### Structured Outputs

```text
summary_statistics.json
extracted_patterns.json
```

### Processed Text

```text
cleaned_processed_text.txt
```

When original articles are unavailable, this file records the limitation rather than pretending to contain reconstructed prose.

### Analysis Report

```text
ANALYSIS_REPORT.md
```

The report includes dataset statistics, findings, visual interpretations, limitations, challenges, and conclusions.

---

## 12. Challenges Faced and Solutions

### Challenge 1: Sparse Matrix Representation

**Problem:** The dataset is stored in Matrix Market format instead of ordinary text files.

**Solution:** A custom parser was implemented to read matrix dimensions, term indices, document indices, and frequencies.

### Challenge 2: Missing Original Article Text

**Problem:** Original sentence structure and word order are unavailable.

**Solution:** The project separates valid bag-of-words analysis from tasks that require original text.

### Challenge 3: Large Vocabulary

**Problem:** Processing thousands of vocabulary terms requires efficient frequency aggregation.

**Solution:** Python's `Counter` and NumPy arrays are used for efficient computation.

### Challenge 4: Text Encoding

**Problem:** Text files may contain different character encodings.

**Solution:** The file-loading module attempts multiple encodings, including UTF-8, ASCII, Windows-1252, and Latin-1.

### Challenge 5: Visualization Readability

**Problem:** Long word labels can overlap in vertical bar charts.

**Solution:** A horizontal bar chart with value labels was implemented.

### Challenge 6: Jupyter Notebook Compatibility

**Problem:** The `__file__` variable is not available inside Jupyter Notebook cells.

**Solution:** The notebook version uses compatible directory detection.

### Challenge 7: Regex Accuracy

**Problem:** Real-world patterns can have multiple valid formats.

**Solution:** Regex patterns include boundary checks, format alternatives, and normalization where appropriate.

---

## 13. Project Advantages

- Uses only core Python and scientific computing libraries.
- Does not require specialized NLP packages.
- Supports thousands of documents.
- Provides modular analysis functions.
- Generates multiple statistical outputs.
- Produces 13 visualization files.
- Supports Jupyter Notebook execution.
- Includes Zipf's Law analysis.
- Implements exploratory sentiment keyword detection.
- Supports optional original text processing.
- Automatically exports CSV and JSON files.
- Provides category-wise comparisons.
- Includes an interactive Matplotlib visualization.
- Explicitly distinguishes authentic results from unavailable analyses.

---

## 14. Limitations

Although the project provides extensive text analysis functionality, certain limitations exist.

1. The BBC dataset contains preprocessed term frequencies rather than complete articles.
2. Original word order is unavailable.
3. Original sentence lengths cannot be calculated from the supplied matrix.
4. Regex extraction requires original text.
5. Ordered bigram and trigram analysis requires original articles.
6. Some vocabulary terms may be stemmed or normalized.
7. Keyword-based sentiment analysis does not account for negation, sarcasm, or context.
8. Vocabulary richness can be influenced by document length.
9. The Zipf fit is descriptive and is not a formal statistical goodness-of-fit test.
10. Character analysis reflects stored vocabulary terms rather than original punctuation and formatting.

These limitations are explicitly handled to maintain analytical reliability.

---

## 15. Future Enhancements

The project can be extended with additional capabilities.

### Full Article Processing

Integrate original BBC article text to enable accurate sentence analysis and regex extraction.

### Advanced Text Cleaning

Implement more sophisticated tokenization, normalization, and text preprocessing.

### TF-IDF Analysis

Calculate Term Frequency-Inverse Document Frequency to identify category-specific vocabulary.

### Document Similarity

Use cosine similarity to identify related news articles.

### Topic Modeling

Implement statistical topic discovery techniques.

### Improved Sentiment Analysis

Use more comprehensive sentiment dictionaries and contextual analysis.

### Interactive Web Dashboard

Develop a browser-based dashboard using Streamlit or Dash.

### Named Entity Recognition

Extract people, organizations, and locations from original articles.

### Time-Series Analysis

Analyze topic trends over time when reliable publication dates become available.

### Automated News Classification

Train machine learning models to classify news documents into the five BBC categories.

---

## 16. Applications

The techniques implemented in this project can be applied to:

- News article analysis
- Document analytics
- Digital libraries
- Academic research
- Social media analysis
- Customer feedback analysis
- Content categorization
- Search engine preprocessing
- Vocabulary analysis
- Text mining
- Information retrieval
- Natural Language Processing education

---

## 17. Evaluation Rubric Coverage

| Evaluation Criteria | Implementation |
|---|---|
| Code Functionality | Modular Python functions and file handling |
| Regex Implementation | Pattern extraction for original text |
| Data Analysis | NumPy and Pandas statistics |
| Visualizations | 13 generated visualization files |
| Code Quality | Modular structure, documentation, error handling |
| Report and Insights | Automatically generated analysis report |
| Zipf's Law Bonus | Rank-frequency visualization and slope analysis |
| Interactive Dashboard Bonus | Matplotlib RadioButtons |
| N-Gram Bonus | Ordered n-grams for original text |
| Sentiment Bonus | Positive and negative keyword scoring |

The implementation covers the major assignment components while explicitly documenting the dataset-dependent limitations.

---

## 18. Conclusion

The **Comprehensive Text Analysis Tool Using Python** demonstrates how core Python libraries can be used to analyze large text datasets and extract meaningful statistical information.

By integrating **Regular Expressions, NumPy, Pandas, and Matplotlib**, the project provides a structured framework for text processing, numerical analysis, and graphical interpretation.

The BBC News Dataset is used to examine vocabulary characteristics, word frequencies, document lengths, character distributions, vocabulary richness, category-level differences, and Zipf's Law.

Additional features such as keyword-based sentiment analysis, word co-occurrence, interactive visualization, and optional n-gram extraction extend the functionality of the system.

The project establishes a practical foundation for further work in **Natural Language Processing, Text Mining, Data Science, and Machine Learning**.

---

## 19. References

1. BBC News Dataset — BBC news classification collection.
2. Python Documentation — https://docs.python.org/3/
3. NumPy Documentation — https://numpy.org/doc/
4. Pandas Documentation — https://pandas.pydata.org/docs/
5. Matplotlib Documentation — https://matplotlib.org/stable/
6. Python Regular Expressions — https://docs.python.org/3/library/re.html
7. Matrix Market Format — https://math.nist.gov/MatrixMarket/

---

## 20. Project Summary

**Project Title:** Comprehensive Text Analysis Tool Using Python

**Dataset:** BBC News Dataset

**Programming Language:** Python

**Core Libraries:** Regex, NumPy, Pandas, Matplotlib

**Dataset Size:** 2,225 documents

**Vocabulary Size:** 9,635 terms

**Total Word Occurrences:** 425,832

**Categories:** Business, Entertainment, Politics, Sport, Technology

**Visualization Files:** 13

**Output Formats:** CSV, JSON, TXT, PNG, Markdown

**Execution Environments:** Python Script, Jupyter Notebook

**Domain:** Natural Language Processing and Data Analytics

---

**Comprehensive Text Analysis Tool — Exploring textual data through Python, statistical computing, and visualization.**
