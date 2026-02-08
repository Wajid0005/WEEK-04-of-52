# 📈 Yahoo Finance Stock News Scraper

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![BeautifulSoup](https://img.shields.io/badge/BeautifulSoup-BS4-green?style=for-the-badge)

## 📌 Project Overview
**Week 04 Milestone Project**

[cite_start]This project is a web scraping pipeline designed to extract real-time, stock-specific financial news from Yahoo Finance. [cite_start]It was built to overcome common scraping challenges—such as bot detection—and convert unstructured HTML into a clean, analytical dataset.

[cite_start]I focused on extracting news for **Reliance Industries (RELIANCE.NS)**, gathering headlines, timestamps, and source URLs.

---

## 🚀 Key Features
* [cite_start]**Bot Detection Bypass:** Utilizes `requests.Session()` with custom User-Agent headers to mimic a real Chrome browser session.
* [cite_start]**Targeted DOM Parsing:** Uses **BeautifulSoup4** to navigate Yahoo's HTML structure, specifically targeting `subtle-link` classes for articles.
* [cite_start]**Data Cleaning:** Filters incomplete records and standardizes the "Source • Time" metadata format.
* [cite_start]**CSV Export:** Automatically saves the scraped data to `reliance_yahoo_finance_news.csv` for further analysis.

---

## 💻 The "Hero" Code

The core logic of this scraper relies on establishing a persistent session and parsing the specific `div` structures used by Yahoo.

### 1. Session Handling & Request
Standard requests often fail on finance sites. This project uses a session with headers:

```python
import requests
from bs4 import BeautifulSoup

url = "[https://finance.yahoo.com/quote/RELIANCE.NS/news](https://finance.yahoo.com/quote/RELIANCE.NS/news)"
headers = {
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36"
}

session = requests.Session()
response = session.get(url, headers=headers, allow_redirects=True)
