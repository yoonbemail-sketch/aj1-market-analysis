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

## 4. 프로젝트 여정 (My Project Journey & Process)

Phase 0: Project Definition & Strategy (Novemver 2025)
* 2025-11-11 : Defining the Goal.
  - Context: As a recent University of Waterloo graduate(Math, Computational Mathematics & Mathematical Optimization - OR), my objective is to secure a high-impact role in consulting, finance, or tech analytics.
  - The gap: Lacking of formal co-op experiance, I need a strong portfolio that demonstrates not just a technical skill,s but a structured, high-level approach to problem solving.
* 2025-11-11 : Adopting a "Reverse Learning" Strategy.
  - The Why: Decided againist passive learning(e.g., "watching online courses"). Instead, I am adopting a "Reverse Learning" methodology.
  - The Process: 1. Define a complex, real world business problem. 2. Learn and apply the necessary tools ( SQL, Python, Power BI) in the process of solving it.
  - The Value: This project's log itself; tracking all attempts, failures, and pivots; will be the core deliverable, proving my problem solving skills.
* 2025-11-12 : Topic Selection & Scoping.
  - Initial Brainstorm: Leveraged my personal domain interest (fashion, sneaker resale) and academic background (Optimization).
  - The Pivot : I pivoted from a simple "how to profit" model to a far deeper business questions: "Why did Air Jordan 1 High resale market, once a 'guaranteed win,' completely collapse (bust)?"
  - Why this topic is better : It's a real-world "bloom-and-bust" cycle analysis. It allows me to model market volatility, risk, and saturation; key problems that top consulting and finance firms solve today.
 
Phase 1: Data Sourcing & Environment Setup (Today)
* 2025-11-12: Initial Data Reconnaissance (The First Blocker).
  - Attempt 1: Searched Kaggle for existing datasets on "Air Jordan 1", "StockX", etc.

  - Result (Fail): No comprehensive, transaction-level datasets exist that cover the 2018-2025 "boom-and-bust" period.

  - Insight: This failure is not a blocker; it's the project's first major opportunity. It forces the project to move from simple "analysis" to complex "data engineering." The value now lies in building the dataset from scratch.

* 2025-11-12: Strategic Pivot (The "Kream" Idea).
  - Hypothesis: Instead of relying on StockX (global) alone, I will scrape data from Kream (the top Korean resale platform).
  
  - Value: This creates a unique and powerful analytical angle: Comparative Market Analysis. (e.g., "Did the bubble burst in Korea at the same time as the global market? Was there a time lag? Which factors mattered more in each region?")

* 2025-11-12: Environment & Tooling Setup.

  - IDE: Set up Visual Studio Code (VS Code) (over the heavier Visual Studio) as the primary IDE, given its lightweight nature and powerful extensions for Python and data science.

  - Repo: Created this GitHub repository to serve as the central, public 'source of truth' for all code, analysis, and this process log.

* 2025-11-12: Next Step 

Beginning initial reconnaissance on Kream.co.kr.

Using Chrome Developer Tools (F12) to inspect the Network tab (Fetch/XHR) to identify potential hidden APIs. This is the first step in designing the Python (Requests/BeautifulSoup) scraper. All findings will be logged here.




















