# 📺 OTT Platform Analytics Dashboard — Power BI

> A self-initiated end-to-end Power BI project analysing four major OTT streaming platforms (Netflix, Amazon Prime, Disney+ Hotstar, Apple TV+) and the global box office — spanning ~33,500 rows across 10 interactive report pages.

---

## 🎬 Project Overview

This is a personal analytics project built out of interest in the streaming content landscape and global movie economics. The dashboard covers two parallel analytical tracks:

- **OTT Content Libraries** — what each streaming platform offers by genre, content type, age rating, country, and year
- **Movie Box Office** — Bollywood vs Hollywood revenue, budgets, scores, languages, and geographic distribution

| Metric | Value |
|---|---|
| Total rows processed | ~33,500 |
| Source files | 6 (4 OTT platform CSVs + 2 movie CSVs) |
| Report pages | 10 |
| Data model tables | 16 |
| Custom visuals | 5 |

---

## 📁 Repository Structure

```
├── data/
│   ├── Netflix.csv                    # 5,332 titles
│   ├── amazon_prime_titles.csv        # 9,687 titles
│   ├── hotstar.csv                    # 6,877 titles
│   ├── apple.csv                      # 170 titles
│   ├── Final_Bollywood.csv            # 1,321 films
│   └── Final_Hollywood.csv            # 10,177 films
├── Final.pbix                         # Power BI report file
├── Dashboard.gif                      # Dashboard preview
└── README.md
```

---

## 📊 Dashboard Pages

### Pages 1–3 — Navigation Layer (Home, Movies Hub, OTT Hub)
Landing and navigation pages with animated platform logos (GIF), action buttons routing to all platform and movie pages. Dark cinematic aesthetic throughout.

### Page 4 — Netflix
| Visual | Purpose |
|---|---|
| Ribbon Chart | Content type split across release years |
| Map | Country of origin distribution |
| Bar Chart | Rating distribution (TV-MA, TV-14, etc.) |
| Gauge | Total catalogue titles |
| Scrolling Ticker ×2 | Live scrolling titles with rating and year |
| KPI Cards ×4 | Genre, Cast, Director, Country context |
| Slicers ×4 | Type, Year, Rating, Genre |

### Page 5 — Amazon Prime
| Visual | Purpose |
|---|---|
| Filled Map | Country distribution of content |
| Donut Chart | Movies vs TV Shows split |
| Area Chart | Cumulative content additions by year |
| Bar Chart | Rating distribution |
| Ribbon Chart | Genre evolution over time |
| KPI Cards ×4 | Dynamic title, genre, rating, director |
| Slicer | Release year |

### Page 6 — Disney+ Hotstar
| Visual | Purpose |
|---|---|
| Clustered Bar | Age rating breakdown by content type |
| Column Chart | Content volume by year |
| Clustered Column | Genre × content type breakdown |
| Donut Chart | Movies vs TV split |
| Word Cloud | Title frequency cloud |
| 3D BI Visual | Genre exploration in 3D space |
| Gauge + KPI Cards | Library size metrics |
| Slicers ×3 | Genre/age rating, type, year |

### Page 7 — Apple TV+
| Visual | Purpose |
|---|---|
| Column Chart | IMDb score distribution |
| Line Chart | Runtime distribution |
| Column Chart | Releases by year |
| Word Cloud | Original title cloud |
| Gauge | Total titles |
| KPI Cards ×2 | Genre, total runtime |
| Slicers ×2 | Genre, release year |

### Page 8 — Movies Overview (Bollywood + Hollywood Combined)
Cross-cinema view: total films, genres, and box office revenue KPIs, Score vs Revenue scatter, language donut, country bar chart, budget distribution — filterable by title slicer.

### Page 9 — Hollywood
Detailed Hollywood box office: Revenue + Budget by genre (grouped column), production country map, revenue by release date, ~10,177 films with slicers for genre, title, language, and date.

### Page 10 — Bollywood
Bollywood box office: Revenue vs Budget by title, production country map, score-based ribbon chart, ~1,321 films with genre, title, and year slicers.

---

## 🗄️ Data Model — 16 Tables

**OTT Platform Tables**
| Table | Type |
|---|---|
| `amazon_prime_titles` | Raw Source |
| `hotstar` | Raw Source |
| `Table_cleaned_amazon_prime_titles` | Cleaned (Power Query) |
| `Table_cleaned_hotstar` | Cleaned (Power Query) |
| `Table_cleaned_apple` | Cleaned (Power Query) |
| `Table_cleaned_netflix_titles_2` | Cleaned (Power Query) |
| `Netflix Main` | Normalised Fact |
| `Netflix Genre` | Normalised Dimension |
| `Netflix Cast` | Normalised Dimension |
| `Netflix Director` | Normalised Dimension |
| `Netflix Country` | Normalised Dimension |
| `Netflixnew` | Working Table |

**Movies Tables**
| Table | Type |
|---|---|
| `Final Bollywood` | Movie Fact |
| `Bollywood Genre` | Movie Dimension |
| `Final Hollywood` | Movie Fact |
| `Final_Imbd` | Combined Append View |

---

## ⚙️ Power Query Transformations

1. **Schema Standardisation** — Unified column names and data types across 6 files with varying date formats and numeric conventions
2. **Netflix Schema Normalisation** — Split multi-value columns (cast, director, country, genre) into 4 separate linked tables
3. **Bollywood Genre Normalisation** — Split genre column into `Bollywood Genre` dimension table for slicer filtering
4. **Date Hierarchy Extraction** — Extracted Year/Month/Day from Netflix `date_added` for ribbon chart time axis
5. **Null & Missing Value Handling** — Managed null directors, cast, countries, and ratings across all platform files
6. **Revenue/Budget Cleaning** — Type conversion, symbol removal, and zero-value handling in Bollywood/Hollywood financial fields
7. **Combined Movies Append** — Appended Bollywood + Hollywood into `Final_Imbd` for cross-cinema analysis
8. **Apple TV+ Enrichment** — Retained IMDb scores, TMDb popularity, and runtime as analytical dimensions

---

## 🎨 Custom Visuals (5)

| Visual | Publisher | Used On |
|---|---|---|
| **Globe Map** | Microsoft | Geographic pages |
| **3D BI** | INFORMAXYZ | Hotstar (Genre 3D) |
| **Scrolling Text (Scroller)** | Fredrik Hedenström | Netflix (Title Ticker) |
| **Word Cloud 2.0** | Microsoft | Hotstar, Apple TV+ |
| **Lollipop / PL Chart** | Margarida Prozil | Hotstar |

---

## 🛠️ Technical Stack

| Tool | Purpose |
|---|---|
| **Power BI Desktop** | Report authoring, visuals, action button navigation |
| **Power Query (M)** | ETL: cleaning, normalisation, splitting, appending |
| **DAX** | Count/sum measures, filtered KPI cards, gauge calculations |
| **Schema Normalisation** | Multi-value column handling for Netflix data |
| **AppSource Custom Visuals** | 5 custom visuals for enhanced storytelling |
| **Cross-domain Modelling** | Two independent domains (OTT + Movies) in one model |

---

## 🔑 Key Learnings

- Handling real-world denormalised data — multi-value string columns common in entertainment datasets
- Building a dual-domain data model (OTT content + movie financials) without cross-contamination
- Using action button navigation to create a multi-section dashboard that feels like a product
- Integrating 5 distinct custom visuals while maintaining visual consistency across 10 pages
- Comparing datasets of vastly different scales (Apple TV+ at 170 titles vs Amazon Prime at 9,687+)

---

*Personal project · Power BI · Entertainment Analytics · 2023*
