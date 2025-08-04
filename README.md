# 📘 Web Scraper Notebooks

This repository contains Jupyter notebooks organized around different scraping use cases including job listing platforms, news, Google search results, and course platforms. Each branch targets a specific kind of data and includes preprocessing for downstream NLP or ML tasks.

---

## 🔹 JSearch

Scrapes job data from the [JSearch API](https://rapidapi.com/letscrape-6bRBa3QguO5/api/jsearch), hosted on RapidAPI.

### Key Features:
- Uses paginated API requests with query parameters like job role, country, and page.
- Extracts:  
  - `job_id`, `job_title`, `employer_name`, `job_city`, `job_country`  
  - `job_description`, `job_type` and `job_posted_at_datetime_utc`
- Handles API rate limits (HTTP 429)
- Cleans and formats `job_description`
- Converts timestamps into `dd-mm-yyyy hh:mm` format
- Exports clean structured job data as CSV
- Does EDA on 
  - `Top 10 Companies`,  `Job Distribution by City`, 
  - `Top 30 Most Frequent Words in Job Descriptions`, 
  - `Bi-gram and Tri-gram on Job Descriptions`

## 🔹 Google Jobs (SerpAPI)

Leverages [SerpApi](https://serpapi.com/) to extract job listing snippets from Google Jobs.

### Key Features:
- Uses `engine=google_jobs` to perform location-based job search
- Extracts data like:
  - `title`, `company_name`, `location`, `posted_at` 
- Converts “x days ago” into actual UTC datetime using a timestamp reference
- One-page limit per API call (SerpApi restriction)
- Saves formatted dataset to CSV

---

## 🔹 News Article

Scrapes raw search engine results or online news content.

### Key Features:
- Accepts query inputs (e.g. `"AI developments"` or `"AI regulation news"`)
- Uses scraping or external APIs to collect:
  - Titles, URLs, snippets, and sometimes publication dates
- May include article text extraction logic (`newspaper3k` or `requests + BS4`)
- Focused on analyzing content trends or gathering articles for NLP analysis

---

## 🔹 Coursera Courses Scraper

Scrapes course listings from [Coursera.org](https://www.coursera.org/).

### Key Features:
- Extracts metadata from course search results:
  - `Title`, `Organization`, `Skills`, `Duration`, `Rating`, etc.
- Parses nested or noisy fields like `Metadata` to isolate skills and durations
- Handles pagination manually across multiple pages (up to 50)
- Includes cleaning logic for empty or malformed fields
- Saves to Excel and performs basic cleaning + formatting

---

## 🛠 Requirements

Ensure these libraries are installed before running the notebooks:

- `requests`
- `pandas`
- `nltk`
- `seaborn`
- `matplotlib`
- `tqdm`
- `bs4`
