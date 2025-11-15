# Air Jordan 1 High 리셀 시장 붕괴 분석 (AJ1 Market Bust Analysis)

이 프로젝트는 Kream과 StockX 데이터를 기반으로 '에어 조던 1 하이' 리셀 시장의 흥망성쇠(Boom & Bust) 사이클을 분석하고, 그 원인을 모델링하는 것을 목표로 합니다.

---

## 1. 프로젝트 목적 (The "Why")

[여기에 목적을 적으세요. 예시:]
* 한때 '치트키'였던 AJ1 리셀 시장이 왜, 어떻게 붕괴했는지 데이터로 증명한다.
* "유행", "발매 수량", "거시 경제" 같은 변수들이 리셀 가격에 미치는 영향을 분석한다.
* 이 과정을 통해 Python, SQL, Power BI를 활용한 엔드투엔드(End-to-End) 데이터 분석 포트폴리오를 완성한다.

## 2. 핵심 질문 (The "Direction")

이 프로젝트를 통해 답을 찾고자 하는 핵심 질문들입니다.

[여기에 방향을 적으세요. 예시:]
1.  AJ1 High 리셀가의 정점(Peak)은 언제였으며, 하락은 언제부터 시작되었는가?
2.  시장의 '붕괴'를 주도한 핵심 요인은 무엇인가? (발매량 증가? 콜라보 남발? 유행의 변화?)
3.  폭락 속에서도 가치를 방어한 '승자' 모델과, 가장 많이 하락한 '패자' 모델은 무엇인가?
4.  한국(Kream)과 글로벌(StockX) 시장은 동일하게 움직였는가, 아니면 시차(Lag)가 존재했는가?

## 3. 기술 스택 (The "How")

* **Data Sourcing:** Python (`Requests`, `BeautifulSoup`) - Kream, StockX 데이터 스크래핑
* **Database:** SQL (PostgreSQL 또는 SQLite) - 수집한 데이터 저장 및 관리
* **Analysis:** Python (`Pandas`, `Scikit-learn`) - 데이터 정제, 분석, 예측 모델링
* **Visualization:** Power BI - 최종 분석 결과 대시보드
* **Editor:** VS Code

## 4. Project Journey & Process Log

### Phase 0: Project Definition & Strategy (November 2025)

* **2025-11-11: Defining the Goal.**
    * **Context:** As a recent University of Waterloo graduate (Math, Computational Mathematics & Mathematical Optimization - OR), my objective is to secure a high-impact role in consulting, finance, or tech analytics.
    * **The Gap:** Lacking formal co-op experience, I need a strong portfolio that demonstrates not just technical skills, but a structured, high-level approach to problem-solving.
* **2025-11-11: Adopting a "Reverse Learning" Strategy.**
    * **The Why:** Decided against passive learning (e.g., "watching online courses"). Instead, I am adopting a **"Reverse Learning"** methodology.
    * **The Process:** 1. Define a complex, real-world business problem. 2. Learn and apply the necessary tools (`SQL`, `Python`, `Power BI`) in the *process* of solving it.
    * **The Value:** This project's log itself—tracking all attempts, failures, and pivots—will be the core deliverable, proving my problem-solving process.
* **2025-11-12: Topic Selection & Scoping.**
    * **Initial Brainstorm:** Leveraged my personal domain interest (fashion, sneaker resale) and academic background (Optimization).
    * **The Pivot:** I pivoted from a simple "how to profit" model to a far deeper business question: **"Why did the Air Jordan 1 High resale market, once a 'guaranteed win,' completely collapse (bust)?"**
    * **Why this topic is better:** It's a real-world "boom-and-bust" cycle analysis. It allows me to model market volatility, risk, and saturation—key problems that top consulting and finance firms solve daily.

---

### Phase 1: Data Sourcing & Environment Setup (November 2025)

* **2025-11-12: Initial Data Reconnaissance (The First Blocker).**
    * **Attempt 1:** Searched Kaggle for existing datasets on "Air Jordan 1", "StockX", etc.
    * **Result (Initial Assessment):** Initially assessed that no *perfect*, single-file dataset existed for my specific Kream + AJ1 hypothesis.
    * **Insight:** This perceived gap forced a valuable technical deep-dive.

* **2025-11-12: Strategic Pivot 1 (The "Kream" Idea).**
    * **Hypothesis:** Instead of relying on StockX (global) alone, I will scrape data from **Kream** (the top Korean resale platform).
    * **Value:** This creates a unique and powerful analytical angle: **Comparative Market Analysis.** (e.g., "Did the bubble burst in Korea at the same time as the global market?")

* **2025-11-12: Environment & Tooling Setup.**
    * **IDE:** Set up **Visual Studio Code (VS Code)** as the primary IDE.
    * **Language/Tools:** Installed Python 3.14 (after troubleshooting `PATH` issues), VS Code Python Extension, and the `requests` library (`py -m pip install requests`).
    * **Repo:** Created this GitHub repository to serve as the central, public 'source of truth' for all code, analysis, and this process log.

* **2025-11-12: Technical Deep-Dive (Attempting to Scrape Kream).**
    * **Blocker 1 (Login Wall):** Used Chrome Developer Tools (F12) to inspect the network. Discovered that key data (historical transactions) is protected behind a **login wall**.
    * **Blocker 2 (Token Auth):** Identified that Kream uses `Authorization: Bearer` token (JWT) for authentication. Found the core API endpoint: `https://api.kream.co.kr/api/p/products/...`
    * **Attempt 1 (Simple Headers):** Ran `scraper.py` (v1) using `requests` with a valid `Bearer` token and basic headers.
        * **Result:** `Status Code: 500 (Internal Server Error)`.
    * **Attempt 2 (Full Headers):** Hypothesized the `500` error was due to missing headers. Ran `scraper.py` (v2) with the *entire* header block from F12.
        * **Result:** `Status Code: 500 (Internal Server Error)`.
    * **Attempt 3 (Synced Headers):** Hypothesized the error was a mismatch between dynamic keys. Ran `scraper.py` (v3) with a freshly synced "set" of `authorization` token, `request_key`, and `x-kream-client-datetime`.
        * **Result:** `Status Code: 500 (Internal Server Error)`.

* **2025-11-12: Current Analysis & Next Step.**
    * **Conclusion:** The persistent `500` (Internal Server Error), instead of a `401` (Unauthorized), strongly implies:
        1.  Our `authorization` token is likely *valid*.
        2.  The server is *receiving* the request but *crashing* during processing.
        3.  This is the hallmark of a sophisticated, server-side **anti-scraping system** that is detecting non-human patterns (e.g., via dynamic token/key mismatches, client fingerprinting).
    * **Insight:** The existence of other "bots" (as I theorized) confirms a technical path exists, but it's likely not via simple `requests`. It probably involves advanced methods (e.g., mobile app API reverse-engineering).
    * **Next Step:** Further investigation into Kream's anti-bot measures is required. [Pivot decision on hold]


---

## Phase 2: Initial Data Analysis (EDA) with Power BI

* **2025-11-14: Loading Sample Data.**
    * **Action:** Loaded the sample dataset (`kream_83900.csv`) provided by my friend into Power BI Desktop. This file represents the transaction data for a single model (AJ1 Chicago 'Lost & Found').
    * **Status:** This is just a sample; the full data collection for all AJ1 models is not yet complete.

* **2025-11-14: Data Transformation (Power Query).**
    * **Objective:** Clean the raw data so it can be used for analysis.
    * **Challenge 1 (Price):** `price` column was text (e.g., "300,000원").
    * **Solution:** Used **[Transform Data]** (Power Query). Used **[Replace Values]** to remove "원" and ",". Changed data type to "Whole Number".
    * **Challenge 2 (Date):** `date` column was text.
    * **Solution:** Changed data type to "Date".

* **2025-11-14: Initial Visualization (First Insights).**
    * **Action 1:** Created a **Line Chart** (`price` on Y-axis, `date` on X-axis).
    * **Troubleshooting:** Had to fix Power BI's default behavior by setting the Y-axis to **[Don't summarize]** and the X-axis to use `date` (not 'Date Hierarchy').
    * **Result 1:** Successfully visualized the price trend over time for this single product.
    * **Action 2:** Added a **Slicer** visual linked to the `size` column.
    * **Result 2:** Successfully created an interactive dashboard where I can filter the price trend by specific sneaker size.

---

## Phase 1.5: Data Collection (Refinement & Iteration)

* **2025-11-14: Critical Finding (Data Quality Issue).**
    * **The Problem:** During the analysis, I discovered a major flaw in the initial data extraction. The scraper program was outputting 3 columns (`size`, `price`, `date`). However, for items marked **"빠른 배송" (Fast Shipping)**, this text **overwrote the actual transaction date** in the `date` column.
    * **Immediate Impact:** I had to manually delete these corrupted rows in Excel to make the Power BI import work, which resulted in significant **data loss**.

* **2025-11-14: Strategic Decision (Scraper v2).**
    * **The Goal:** Stop the data loss and make the data clean from the source.
    * **The Plan:** I will modify (or have my friend modify) the scraping program to fix this bug.
    * **Proposed Change:** The new program will be updated to output **4 columns** (e.g., `size`, `price`, `date`, `shipping_option`). This will correctly separate the "Fast Shipping" tag from the `date` column and preserve 100% of the data.
    * **Next Step:** Pause full analysis in Power BI and return to the Python scraping phase to build a complete, clean dataset.














