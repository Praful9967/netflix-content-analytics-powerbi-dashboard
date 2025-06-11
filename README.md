# netflix-content-analytics-powerbi-dashboard
🎬 Power BI dashboard analyzing 15K+ Netflix titles by genre, ratings, country availability, and box office to uncover strategic insights for content planning, release optimization, and audience engagement.

# 🎬 Netflix Content Analytics Dashboard | Power BI + DAX

This project presents a data-rich Power BI dashboard built using a cleaned dataset of ~15,000 Netflix titles. It aims to provide business insights into **content performance**, **regional availability**, **audience ratings**, and **strategic content investments** using **advanced DAX measures** and clean visual storytelling.

---

## 📊 Dashboard Preview
![Dashboard photo](https://github.com/user-attachments/assets/de6dcd3e-b707-43c8-a37c-9d8b5498d7c2)


---

## 🔍 Project Objectives

✅ Understand which genres and regions drive the most engagement  
✅ Evaluate IMDb, Rotten Tomatoes, and Metacritic scores to build a content quality index  
✅ Identify top-performing directors and titles  
✅ Track content trends by year and country availability  
✅ Use data-driven KPIs to guide Netflix’s **content acquisition, regional strategy**, and **release optimization**

---

## 💼 Business Value

This dashboard isn't just for analysis — it delivers **clear business use cases**:

- 📈 **Content Strategy**: Pinpoint genres with the highest IMDb ratings to inform future content production.
- 🌍 **Market Expansion**: Analyze country-wise content availability to identify underserved regions.
- 🎯 **Release Optimization**: Track delay between theatrical release and Netflix release to reduce content lag.
- 🏆 **Quality vs Quantity**: Balance prestige content (award-winning) with popular content (box office hits).
- 🧠 **Audience Insights**: Use IMDb votes as a proxy for engagement and feedback loop.

---

## 📦 Dataset Overview

The dataset includes:
- 15K+ Netflix titles
- Genres, languages, runtime, country availability
- Director, writer, and actor metadata
- Ratings: IMDb, Rotten Tomatoes, Metacritic
- Box office and release dates
- Award nominations, IMDb votes, and hidden gem scores

---

## 🧮 KPIs & DAX Measures

| KPI Name                    | Purpose                                               |
|----------------------------|-------------------------------------------------------|
| Content Quality Score       | Weighted average of IMDb, RT, and Metacritic scores  |
| Awards Conversion %         | % of titles nominated for at least one award         |
| Days to Netflix Release     | Measures licensing/release delay                     |
| Regional Content Count      | Tracks country-wise content distribution             |
| Avg IMDb Score by Genre     | Genre-level quality measurement                      |
| Box Office vs IMDb Votes    | Correlates theatrical performance with stream appeal |

---

## 🧼 Data Cleaning (Python Preview)

```python
# Filled missing values and formatted box office column
df_n.fillna({'Director': 'Unknown', 'Writer': 'Unknown', 'Actors': 'Unknown',
             "Genre":"Not mentioned","Languages":"Not Mentioned",
             "Country Availability":"Not mentioned","View Rating":"Unknown"}, inplace=True)
df_n.drop_duplicates(subset=['Title', 'Netflix Release Date'], inplace=True)
df_n["IMDb Score"].fillna(df_n["IMDb Score"].median(), inplace=True)
df_n['Boxoffice'] = df_n['Boxoffice'].replace('[\$,]', '', regex=True).astype(float)
df_n.to_excel("Cleaned_Netflix.xlsx")
