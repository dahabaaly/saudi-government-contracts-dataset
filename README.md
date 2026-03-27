# 🏗️ Saudi Government Contracts Dataset | بيانات عقود الحكومة السعودية

![Records](https://img.shields.io/badge/Records-253-blue?style=flat-square)
![Sectors](https://img.shields.io/badge/Sectors-7-green?style=flat-square)
![Regions](https://img.shields.io/badge/Regions-10%2B-orange?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)
![Source](https://img.shields.io/badge/Source-tenders.etimad.sa-red?style=flat-square)

Open dataset of Saudi government contract awards from **[tenders.etimad.sa](https://tenders.etimad.sa)** (Etimad) — Saudi Arabia's official government procurement portal.

Covers **253 classified awards** across **7 sectors** and **10+ regions**. Each award includes subcontractor categories, enabling targeted prospecting, market research, and spending analysis.

---

## 📁 What's Inside

| File | Description |
|------|-------------|
| `data/awards.json` | Full list of award records with sector, region, ministry, value, and subcontractor categories |
| `data/sector-summary.json` | Aggregated sector breakdown with total SAR values and top subcontractor categories |
| `index.html` | GitHub Pages site with interactive stats and CTA |

---

## 📊 Dataset Schema

Each award record in `data/awards.json` contains:

| Field | Type | Description |
|-------|------|-------------|
| `id` | number | Etimad tender ID |
| `title` | string | Arabic contract title |
| `ministry` | string | Awarding government entity |
| `value_sar` | number | Contract value in Saudi Riyals |
| `region` | string | Geographic region |
| `sector` | string | Sector classification |
| `subcontractor_categories` | string[] | Relevant subcontractor work categories |

---

## 📈 Sector Breakdown

| Sector | Awards | Total Value |
|--------|--------|-------------|
| 🏥 Health | 134 | SAR 6.3M |
| 🪖 Military | 34 | SAR 27.9M |
| 🏗️ Infrastructure | 29 | SAR 40.8M |
| 🏢 Other | 27 | SAR 15.1M |
| 🛒 Commercial | 23 | SAR 5.2M |
| 🎓 Education | 3 | SAR 3.4M |
| 💻 IT | 3 | SAR 2.2M |

---

## 🔧 Most Common Subcontractor Categories

- **FM** (Facilities Management)
- **Maintenance**
- **Civil Works**
- **MEP** (Mechanical, Electrical, Plumbing)
- **Security Systems**
- **Supplies**
- **Catering**
- **Landscaping**
- **IT Infrastructure**
- **Medical Equipment**
- **Furniture**

---

## 💻 Usage Examples

### JavaScript (Browser / Node.js)

```javascript
// Fetch the dataset
const response = await fetch(
  'https://raw.githubusercontent.com/dahabaaly/saudi-government-contracts-dataset/main/data/awards.json'
);
const data = await response.json();

// Filter by sector
const infrastructure = data.awards.filter(a => a.sector === 'infrastructure');

// Filter by subcontractor category
const fmContracts = data.awards.filter(a =>
  a.subcontractor_categories.includes('FM')
);

// Sort by value
const topContracts = data.awards.sort((a, b) => b.value_sar - a.value_sar);

console.log(`Found ${infrastructure.length} infrastructure contracts`);
```

### Python

```python
import requests

url = "https://raw.githubusercontent.com/dahabaaly/saudi-government-contracts-dataset/main/data/awards.json"
data = requests.get(url).json()

# Filter by sector
military = [a for a in data["awards"] if a["sector"] == "military"]

# Filter by region
riyadh = [a for a in data["awards"] if a["region"] == "الرياض"]

# Filter by subcontractor category
mep_contracts = [
    a for a in data["awards"]
    if "MEP" in a["subcontractor_categories"]
]

# Total value
total_value = sum(a["value_sar"] for a in data["awards"])
print(f"Total contract value: SAR {total_value:,.0f}")
print(f"Military contracts: {len(military)}")
print(f"MEP opportunities: {len(mep_contracts)}")
```

---

## 🎯 Use Cases

- **Subcontractor Prospecting** — Find active contracts in your category (FM, MEP, civil, catering...) across Saudi regions
- **Market Research** — Understand which sectors and ministries are spending the most, and where
- **Academic Research** — Government procurement patterns, spending distribution, regional development analysis
- **Government Spending Analysis** — Track contract awards by ministry, sector, and region over time
- **Competitive Intelligence** — Identify market opportunities before competitors do

---

## 🧠 Intelligence Layer

This dataset is a **sample**. For **real-time daily award intelligence** delivered to your sector:

> Visit **[Jatakai](https://jatakai.com)** — جاتك | استخبارات المناقصات الحكومية

Jatakai monitors tenders.etimad.sa daily, classifies every new award by sector and subcontractor category, and delivers actionable intelligence directly to you — so you never miss a relevant contract.

---

## 🤝 Contributing

Contributions welcome:
- Additional award records from tenders.etimad.sa
- Improved sector/subcontractor classification
- Analysis scripts and notebooks
- Bug fixes and schema improvements

Please open an issue or submit a pull request.

---

## 📂 Data Source

All data is sourced from **[tenders.etimad.sa](https://tenders.etimad.sa)** — Saudi Arabia's official government procurement portal (منصة اعتماد للمشتريات الحكومية). This is public government data provided under Saudi e-Government Authority guidelines.

---

## 📄 License

MIT License — free to use, modify, and distribute.

Powered by **[Jatakai](https://jatakai.com)** — Real-time Saudi government contract intelligence.
