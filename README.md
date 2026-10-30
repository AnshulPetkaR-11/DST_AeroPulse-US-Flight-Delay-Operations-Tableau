
# AeroPulse: US Commercial Flight Delay & Operational Congestion Intelligence Dashboard (2024)

![Tableau](https://img.shields.io/badge/Tableau-Desktop_2024.x-E97627?style=flat&logo=tableau&logoColor=white)
![Data Source](https://img.shields.io/badge/Dataset-US_BTS_2024-0A84FF?style=flat)
![Records](https://img.shields.io/badge/Records-500%2C000_Flights-2ea44f?style=flat)
![Institution](https://img.shields.io/badge/Institution-Ramdeobaba_University-B31B1B?style=flat)

---

## 📌 Executive Overview

**AeroPulse** is an interactive visual analytics project developed using **Tableau Desktop** to analyze the structural, geographical, and temporal factors contributing to commercial flight delays across the United States.

Using a dataset of **500,000 commercial domestic flight records** from the US Bureau of Transportation Statistics (BTS) 2024 repository, the dashboard identifies airline operational inefficiencies, airport ground congestion, schedule padding, and seasonal variations in flight delays across major US aviation hubs.

---

## 👥 Authors & Academic Details

- **Anshul Petkar** — Roll No: `B4-30`
- **Yuvraj Verma** — Roll No: `B4-52`
- **Degree:** B.Tech. in Computer Science and Engineering (Data Science and Analytics)
- **Course:** Data Science Tools Lab (DSTL) | Semester V
- **Institution:** Ramdeobaba University, Nagpur
- **Academic Year:** 2026–27

---

## 📊 Key Operational Metrics

| Metric | Value |
|---|---:|
| Total Flight Records | 500,000 |
| On-Time Performance (OTP) | 79.2% |
| Mean Arrival Delay | 7.1 minutes |
| Cancellation Rate | 1.36% |
| Reactionary Late Aircraft Delay | 3.0 million minutes |
| Carrier-Related Delay | 2.5 million minutes |

**Key Insight:** Reactionary late aircraft arrivals and carrier-related operational issues represent major contributors to passenger delays.

---

## 🖥️ Dashboard Architecture

### Page 1: Executive Operations Overview

- **Executive KPI Scorecards:** Four key indicators displaying total flight volume, national OTP, average arrival delay, and cancellation rate.
- **US Geospatial Delay Map:** State-level choropleth visualization highlighting geographical variations in departure delays.
- **Carrier Reliability Leaderboard:** Airline performance comparison against the industry OTP benchmark, featuring Republic Airways (85.9%) and Delta Air Lines (83.4%).
- **Temporal Congestion Heatmap:** A day-of-week versus departure-hour analysis identifying periods of increased operational congestion.
- **Root-Cause Delay Analysis:** Comparative visualization of official DOT delay categories using Tableau Measure Names and Measure Values.

### Page 2: Hub Diagnostics & Congestion

- **Four-Quadrant Hub Matrix:** Scatter plot comparing runway taxi-out time against departure delay to identify airport congestion patterns.
- **Airborne Delay Recovery Analysis:** Diverging bar chart measuring the difference between departure and arrival delays to evaluate schedule recovery.
- **Top 15 Runway Taxi-Out Bottlenecks:** Airport congestion ranking highlighting Chicago O'Hare (ORD – 23.8 minutes) and New York LaGuardia (LGA – 23.5 minutes) against the 19.7-minute baseline.
- **Monthly Seasonality Analysis:** Dual-axis visualization comparing monthly cancellation rates and departure delay trends.

---

## 📁 Repository Structure

```text
DST_AeroPulse-US-Flight-Delay-Operations-Tableau/
│
├── tableau_file/
│   └── AeroPulse_Flight_Intelligence.twb
│
├── dataset/
│   └── flights_2024_500k.csv
│
├── dashboard_images/
│   ├── dashboard_1.png
│   └── dashboard_2.png
│
└── README.md
```

---

## ⚙️ Core Calculated Fields (Tableau)

### 1. Airline Name Mapping

```tableau
CASE [op_unique_carrier]
    WHEN "WN" THEN "Southwest Airlines"
    WHEN "DL" THEN "Delta Air Lines"
    WHEN "AA" THEN "American Airlines"
    WHEN "UA" THEN "United Airlines"
    WHEN "OO" THEN "SkyWest Airlines"
    WHEN "YX" THEN "Republic Airways"
    WHEN "MQ" THEN "Envoy Air"
    WHEN "B6" THEN "JetBlue Airways"
    WHEN "OH" THEN "PSA Airlines"
    WHEN "AS" THEN "Alaska Airlines"
    WHEN "NK" THEN "Spirit Airlines"
    WHEN "F9" THEN "Frontier Airlines"
    WHEN "9E" THEN "Endeavor Air"
    WHEN "G4" THEN "Allegiant Air"
    WHEN "HA" THEN "Hawaiian Airlines"
    ELSE [op_unique_carrier]
END
```

### 2. On-Time Performance (OTP %)

```tableau
SUM(
    IF [arr_delay] <= 14 THEN 1
    ELSE 0
    END
)
/
COUNT([arr_delay])
```

### 3. Airborne Delay Recovery

```tableau
[dep_delay] - [arr_delay]
```

### 4. Cancellation Rate (%)

```tableau
SUM([cancelled]) / COUNT([cancelled])
```

---

## 🚀 How to Run the Project

### Prerequisites

- Tableau Desktop 2024.x or later
- Git installed on your system
- Access to the project repository

### Installation Steps

**1. Clone the repository**

```bash
git clone https://github.com/AnshulPetkar-11/DST_AeroPulse-US-Flight-Delay-Operations-Tableau.git
```

**2. Navigate to the project directory**

```bash
cd DST_AeroPulse-US-Flight-Delay-Operations-Tableau
```

**3. Open the Tableau workbook**

Open the following file using Tableau Desktop:

```text
tableau_file/AeroPulse_Flight_Intelligence.twb
```

**4. Configure the dataset**

If Tableau prompts you to locate the data source, select:

```text
dataset/flights_2024_500k.csv
```

**5. Explore the dashboards**

Navigate through both dashboard pages to explore airline reliability, airport congestion, delay patterns, and operational performance.

---

## 🎯 Project Objectives

- Analyze commercial flight delay patterns across major US airports.
- Identify airlines with comparatively higher on-time performance.
- Examine airport-level ground congestion and taxi-out delays.
- Investigate seasonal and time-based variations in flight delays.
- Identify major operational contributors to departure and arrival delays.
- Develop interactive Tableau dashboards for data-driven decision-making.

---

## 🛠️ Tools & Technologies

- **Data Visualization:** Tableau Desktop
- **Dataset:** US Bureau of Transportation Statistics (BTS) 2024
- **Data Format:** CSV
- **Version Control:** Git & GitHub
- **Domain:** Data Analytics, Aviation Analytics & Business Intelligence

---

## 📌 Conclusion

AeroPulse demonstrates how large-scale flight data can be transformed into meaningful operational intelligence through interactive visual analytics.

By combining airline performance benchmarking, airport congestion analysis, temporal trend identification, and delay attribution, the project provides a comprehensive view of the factors affecting US commercial aviation operations.

The dashboard serves as a practical demonstration of data analytics, visualization, and business intelligence techniques applied to real-world aviation data.

---

**Developed as part of the Data Science Tools Lab (DSTL) academic project at Ramdeobaba University, Nagpur.**
