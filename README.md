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
##📌 Problem ##
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

### 2. **Exploratory Data Analysis (EDA)**

####  **Distribution by Rate Plan** 

Histograms of customer acquisition for plans A, B, and C by start date.

  <img width="705" height="1221" alt="image" src="https://github.com/user-attachments/assets/9101a653-fdf8-40c4-abd0-115f89649832" />

#### **Service Quality**
Monthly analysis of three service categories:

| Category | Description |
|---|---|
| No service | Customer was not answered on any call |
| First call | Customer was answered on the first attempt |
| More than one call | Customer had to call multiple times on the same day |

First-call resolution improved consistently from August through November, reflecting ongoing operational gains.

| <img width="580" height="453" alt="image" src="https://github.com/user-attachments/assets/d68d322d-ae88-4347-b1fe-7b3e8a403e09" />
| <img width="580" height="453" alt="image" src="https://github.com/user-attachments/assets/f418114c-3ff5-4e8a-98c5-d420b4e126b2" />
| <img width="619" height="453" alt="image" src="https://github.com/user-attachments/assets/1d3c0d3e-106c-4bb1-9c74-5ff3613bba80" />
 |
 
####  **Average Wait Time per Month**

Waiting time dropped 40.3% from August to November — a strong signal of improved operator efficiency over the analysis period.

<img width="711" height="511" alt="image" src="https://github.com/user-attachments/assets/3c2fdd0d-d39e-4d81-94bd-9706120c5a63" />

| Month | Average Wait Time |
|---|---|
| August | 402 seconds |
| September | 348 seconds |
| October | 321 seconds |
| November | 240 seconds |

####  Agent Ranking
Operator classification by:
1. Low-performing operators (sorted ascending by AHT % and calls %):
- Some operators handled only 1 call with abnormally low AHT  requires investigation (possible inactivity or logging issues).
- Others handled a moderate number of calls but had disproportionately high AHT, suggesting slow resolution times.

2. High-performing operators (sorted descending):
- Concentrated a higher share of total calls with competitive AHT percentages.
- These operators represent the benchmark for service efficiency.

### 3.  Statistical Tests

####  Hypothesis 1 — Missed Call Rate by Tariff Plan (ANOVA + Tukey) 
**Hypothesis:** Is there a significant difference in the missed call rate between plans A, B, and C?
- One-way ANOVA and post-hoc Tukey test were applied for multiple comparisons between groups.
- Plan C showed the greatest difference in missed call behavior compared to both A and B. Clients on Plan C may be receiving a different level of service, or their call volume patterns differ significantly.

####  Independent T-test Inbound vs. Outbound Call Duration
**Hypothesis:** Is the average duration of inbound calls equal to that of outbound calls?
- Duration distributions were compared between `in` and `out` calls.
- Inbound and outbound calls have statistically different durations. This suggests the nature of the interaction (customer-initiated vs. company-initiated) significantly affects how long calls last — relevant for operator scheduling and AHT targets.

####  Paired T-test Average Waiting Time Across Months
**Hypothesis:** Is the average wait time equal across all months?
- Wait times of inbound vs outbound calls were compared by month.
- The 40.3% reduction in waiting time from August to November is statistically significant not due to chance. This confirms a real operational improvement over the period analyzed.

---
## 📊 Key Findings

- **Service efficiency improved month over month**  First-call resolution rose from a baseline in August to 5,233 users in November (+12.3% vs October), while waiting time dropped 40.3% over the same period.

- **Waiting time is too high in early months**  August's average of 402 seconds (~6.7 min) is a critical pain point. Reducing this to November levels (240 sec) should be the operational benchmark going forward.

- **Plan C users experience significantly more missed calls** Both ANOVA and Tukey HSD confirmed Plan C differs from A and B. A targeted review of service allocation for Plan C clients is recommended.

- **Call duration differs by direction**  Inbound and outbound calls have statistically different durations, requiring separate AHT benchmarks for each call type.

- **Operator performance is uneven** Some low-performing operators handled only 1 call across the entire period, while others showed high AHT relative to peers. Targeted coaching or workload redistribution is needed.

- **Calling more than once in the same day is rare** This confirms that, in most cases, issues are resolved on first contact  a positive indicator for overall service quality.

---

## ✅ Recommendations
- Reinforce agent allocation in August and September to reduce wait times
- Design an improvement plan for operators identified in the low-performance ranking
- Review the rate plan with the highest missed call rate and implement service improvements
- Monitor AHT per agent monthly as a productivity indicator

---

