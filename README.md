# 📘 Web Scraper Notebooks

This repository contains several Jupyter notebooks focused on web scraping and job listings data extraction using APIs such as **SerpApi**, **JSearch** (via RapidAPI), and text preprocessing for downstream tasks like analysis or ML.

---

## 🔹 JSearch

This notebook focuses on scraping job data using the [JSearch API](https://rapidapi.com/letscrape-6bRBa3QguO5/api/jsearch). It includes:

- Configuration of `query_params` to search for job listings in India
- Scraping multiple pages with pagination control
- Extraction of key job attributes like:
  - `job_title`, `employer_name`, `job_city`, `job_description`
  - `salary_min`, `salary_max`, and `job_posted_at_datetime_utc`
- Rate-limit handling (`HTTP 429`)
- Formatted timestamps to `dd-mm-yyyy hh:mm`
- Exporting final data to CSV

---

## 🔹 SerpApi

This notebook scrapes Google Jobs search results using [SerpApi](https://serpapi.com/):

- Uses the `engine=google_jobs` with filters for location and query
- Extracts job-related metadata:
  - `title`, `company_name`, `location`, `posted_at`
- Converts relative timestamps ("3 days ago") into UTC format
- Outputs a clean CSV file with job info

> Note: Limited to 1 page per request due to SerpApi constraints.

---

## 🔹 Text Preprocessing

This notebook performs extensive text processing on the `job_description` column:

- Lowercasing and punctuation removal
- Tokenization using NLTK’s `word_tokenize`
- Stopword removal (`nltk.corpus.stopwords`)
- Creation of new features like `tokenized_desc` and `tokenized_desc_join`
- Visualization of most common words via a barplot using Seaborn
- Distribution plot of word counts per job description

---

## 🛠 Requirements

Ensure the following packages are installed before running the notebooks:

- `requests`
- `pandas`
- `nltk`
- `seaborn`
- `matplotlib`
- `tqdm`

Also, download necessary NLTK resources:

```python
import nltk
nltk.download('punkt')
nltk.download('stopwords')
