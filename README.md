# MBA Admissions & Marketing Analytics – Group Project

This repository contains the work done for an end-to-end data analytics project on the MBA admissions and marketing funnel.  
The goal is to clean, integrate, and analyze multiple datasets (applications, test scores, campaigns, tokens, and leads) to understand:

- How good the incoming leads actually are  
- What drives conversions  
- Which campaigns, platforms, and owners perform best  
---
## 🔍 Project Overview

We worked with **five core datasets**, each owned by a team member:

1. **Applications Dataset** – Applicant profile, education, SOP  
2. **Test Scores Dataset** – MBA test results and related scores  
3. **Campaign Performance Dataset** – Ad spend, clicks, impressions, cost metrics  
4. **Tokens Dataset** – Token payments and basic applicant details  
5. **Performance Marketing Leads Dataset** – Lead details, contact attempts, owner assignment, outcomes  

The data was messy, inconsistent, and scattered.  
We cleaned each dataset, engineered new features, integrated them where possible, and built a **Power BI dashboard** to give a clear view of the admissions funnel and lead quality.
---
## 🎯 Objectives

Main objectives of the project:

1. **Lead Quality & Conversion Analysis**
   - Identify which leads convert, which drop off, and at which stage.
   - Analyze contact attempts, call duration, and mapping to owners.

2. **Factors Affecting Conversion**
   - Study the impact of:
     - Academic performance (graduation percentage, CGPA)
     - Work experience
     - Engagement (answered calls, call duration, lead duration)
     - Campaign/platform and owner performance

3. **Campaign & Platform Effectiveness**
   - Evaluate which campaigns and platforms generate better-quality leads
   - Look at cost per lead (CPL), cost per click (CPC), and lead outcomes

4. **Token & Seriousness Tracking**
   - Understand if token payments indicate seriousness and higher likelihood of conversion
---
## 🧹 Data Cleaning & Preparation

Key cleaning and preprocessing steps done across datasets:

- Handled **missing values**, duplicates, and inconsistent formats.
- Standardized:
  - Date and datetime fields (e.g. `created_time`, `upload_date`, `lsq_created_date`, `last_call_date`)
  - IDs stored in scientific notation (e.g. `1.200000e+17` → converted to string IDs)
  - Text fields (names, emails, phone numbers, platforms, statuses)
- Fixed inconsistent name formats:
  - E.g. `"john wick"`, `"JOHNWICK"`, `"JohnWick"` → standardized to a consistent naming pattern.
- Cleaned noisy / corrupted name entries (junk characters, mojibake, random numbers).
- Converted mixed academic formats:
  - CGPA-style values (e.g. `6.2`, `7.1`) into percentage
  - Kept already-percentage values (e.g. `60`, `72`, `80`) as they are
- Created **positive/negative outcome groupings**:
  - `opportunity_status_group` (e.g. Positive vs Negative based on categories like Warm, Not Eligible, Not Interested, etc.)
---
## 🧮 Feature Engineering

Some of the important derived columns:

- `first_call_seconds`  
  → Duration of first call converted to seconds.

- `lead_duration`  
  → Difference between `lsq_created_date` (lead creation) and `last_call_date`  
  → Used to analyze how long a lead stays “active”.

- `academic_score` (from other teammate datasets)  
  → Combined academic performance metric (e.g., graduation % + test score).

- `opportunity_status_group`  
  → Collapsed many detailed statuses into broad categories (Positive / Negative).

- Buckets / groups:
  - Graduation % buckets (e.g. `<60`, `60–70`, `70–80`, `80+`)
  - Work experience buckets (e.g. `0 yrs`, `1–3 yrs`, `3–5 yrs`, `5+ yrs`)
---
## 📊 Exploratory Data Analysis (EDA)

Some of the core analyses performed:

### 1. Lead Quality & Conversion

- Built a **funnel view**:
  - Total leads → Contacted → Answered → Mapped → Positive / Negative outcome.
- Analyzed:
  - Answered vs Not Answered rates
  - Leads with no owner assigned (unmapped leads)
  - Distribution of `lead_stage`, `status`, and `opportunity_status`

### 2. Engagement & Outcome

- Relationship between:
  - `first_call_seconds` and final outcome
  - `lead_duration` and opportunity status
- Insight: longer, meaningful contact tends to correlate with better outcomes.

### 3. Owner Performance

- Per-owner metrics:
  - Number of leads handled
  - Positive vs Negative outcomes
  - Average call duration
  - Conversion rate

### 4. Academic & Work Profile vs Conversion

- Graduation % bucket vs positive outcome rate
- Work experience bucket vs positive outcome rate
- Degree type vs likelihood of moving to advanced stages

### 5. Platform / Campaign Performance

- Platform-wise performance (e.g. Meta, Google, LinkedIn)
- Campaign-level:
  - Number of leads
  - Cost metrics (from campaign dataset)
  - Conversion indicators (from lead + status data)
---
## 📈 Dashboard (Power BI)

A Power BI dashboard was built to make the analysis usable for non-technical stakeholders.

Key dashboard elements:

- **KPI Cards**
  - Total Leads
  - Answered Rate
  - Conversion Rate
  - Token-paid Leads
  - Avg Call Duration
  - Avg Lead Duration

- **Visuals**
  - Conversion funnel chart
  - Owner performance bar charts
  - Platform-wise lead and conversion distribution
  - Call duration vs outcome visual
  - Lead quality by academic/work experience buckets
  - Conversion trend over time

The dashboard is designed so managers can slice by:
- Platform
- Campaign
- Owner
- Time period
- Lead outcome group
---
## 🚀 Future Work

Planned or potential extensions:

- Build a **predictive model** for lead conversion likelihood.
- Automate data pipelines (ETL) and schedule dashboard refresh.
- Integrate real-time data feeds from CRM/marketing platforms.
- Add more advanced NLP on SOPs to cluster applicant intent and profile types.
---
