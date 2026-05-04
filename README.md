# Call Center Agent Efficiency Analysis – Call center

##  Project Description
Analysis of the operational efficiency of agents in a telecommunications call center. The objective is to identify low-performing operators using productivity KPIs, evaluate customer service quality, and validate statistical hypotheses about call behavior by rate plan.

---

## 🎯 Objectives
- Identify low-performing agents based on AHT and call volume
- Analyze service quality: answered calls, unanswered calls, and wait time
- Evaluate statistical differences in missed calls between rate plans A, B, and C
- Compare wait times between inbound and outbound calls

---
##📌 Problem
CallMeMaybe needed to identify underperforming operators and understand service quality based on the following KPIs:
- Incoming and outgoing call loss rate
- Average Handle Time (AHT) per customer call
- Number of calls answered
- Agent response time
- Number of times a customer called on the same day
---
## 🛠️ Tools and Libraries

| Library | Usage |
|---|---|
| `Pandas` | Data manipulation and cleaning |
| `NumPy` | Numerical operations |
| `Matplotlib / Seaborn` | KPI visualization and rankings |
| `SciPy` | Statistical tests: T-test and ANOVA |
| `Statsmodels` | Tukey test for multiple comparisons |

---

## 📐 Methodology

### 1. Data Cleaning
- Conversion of date columns to datetime format
- Replacement of null values in `operator_id` with 0 to identify unanswered calls
- Removal of duplicates considering `user_id`, `date`, `direction`, and `total_call_duration`

### 2. Exploratory Data Analysis (EDA)

####  Distribution by Rate Plan
Histograms of customer acquisition for plans A, B, and C by start date.
  <img width="705" height="1221" alt="image" src="https://github.com/user-attachments/assets/9101a653-fdf8-40c4-abd0-115f89649832" />

#### Service Quality
Monthly analysis of three service categories:

| Category | Description |
|---|---|
| No service | Customer was not answered on any call |
| First call | Customer was answered on the first attempt |
| More than one call | Customer had to call multiple times on the same day |

First-call resolution improved consistently from August through November, reflecting ongoing operational gains.

| !<img width="580" height="453" alt="image" src="https://github.com/user-attachments/assets/d68d322d-ae88-4347-b1fe-7b3e8a403e09" />
| !<img width="580" height="453" alt="image" src="https://github.com/user-attachments/assets/f418114c-3ff5-4e8a-98c5-d420b4e126b2" />
 | !<img width="619" height="453" alt="image" src="https://github.com/user-attachments/assets/1d3c0d3e-106c-4bb1-9c74-5ff3613bba80" />
 |
####  Average Wait Time per Month

| Month | Average Wait Time |
|---|---|
| August | 402 seconds |
| September | 348 seconds |
| October | 321 seconds |
| November | 240 seconds |

####  Agent Ranking
Operator classification by:
- **AHT (Average Handle Time):** Total accumulated handling time
- **Percentage of calls answered** out of the total for the period

### 3.  Statistical Tests

####  ANOVA + Tukey
**Hypothesis:** Is there a significant difference in the missed call rate between plans A, B, and C?
- One-way ANOVA and post-hoc Tukey test were applied for multiple comparisons between groups.

####  Independent T-test
**Hypothesis:** Is the average duration of inbound calls equal to that of outbound calls?
- Duration distributions were compared between `in` and `out` calls.

####  Paired T-test
**Hypothesis:** Is the average wait time equal across all months?
- Wait times of inbound vs outbound calls were compared by month.

---
##  Key Findings
- Most customers are answered on the **first call**, indicating overall efficiency in reception
- The highest wait times are concentrated in **August and September**, improving toward the end of the year
- It is uncommon for a customer to call more than once on the same day
- There are statistically significant differences in missed calls between rate plans

---

## ✅ Recommendations
- Reinforce agent allocation in August and September to reduce wait times
- Design an improvement plan for operators identified in the low-performance ranking
- Review the rate plan with the highest missed call rate and implement service improvements
- Monitor AHT per agent monthly as a productivity indicator

---
---
om
