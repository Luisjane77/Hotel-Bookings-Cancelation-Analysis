### Are Cancellations an Enemy or an Opportunity?

Revenue Management Project | Python | Hospitality Analytics

---

# Project Overview

Cancellations are often perceived as a problem in hotel operations. However, from a **Revenue Management perspective**, cancellations can also represent **flexibility in inventory and an opportunity to optimize pricing and demand management**.

This project analyzes hotel booking data to answer a strategic question:

> **Are cancellations a threat to hotel revenue, or are they part of the demand optimization process?**

Using booking data, the analysis explores cancellation behavior across:

* Market segments
* Distribution channels
* Booking lead time
* Seasonality (month of arrival)

The goal is to identify **patterns that support smarter revenue strategies** such as pricing policies, booking restrictions, and overbooking decisions.

---

# Dataset

The dataset contains hotel booking records including reservation details, guest segmentation, and booking behavior.

Each row represents **a single reservation**.

Key variables used in this analysis include:

| Variable                  | Description                      |
| ------------------------- | -------------------------------- |
| `market_segment`          | Customer segment                 |
| `distribution_channel`    | Booking channel                  |
| `lead_time`               | Days between booking and arrival |
| `arrival_date_year`       | Year of arrival                  |
| `arrival_date_month`      | Month of arrival                 |
| `is_canceled`             | Booking cancellation indicator   |
| `stays_in_week_nights`    | Weeknight stays                  |
| `stays_in_weekend_nights` | Weekend stays                    |

---

# Data Preparation

Before calculating any metrics, the dataset was cleaned and validated following **Revenue Management analytical best practices**.

### Data preparation steps

1. Verified dataset structure

   * Each row represents **one reservation**

2. Created base metrics

```
total_nights = stays_in_week_nights + stays_in_weekend_nights
reservations = 1
```

3. Identified anomalous records

   * Reservations with **0 nights**

4. Validated cancellation logic

   * `reservation_status` consistent with `is_canceled`

5. Removed reservations with no real stay

```
df = df[df["total_nights"] > 0]
```

This removed only **0.6% of records**, preventing noise in demand analysis.

6. Created analytical variables

Lead time buckets:

```
0–7 days
8–30 days
31–90 days
91–180 days
180+ days
```

Arrival month:

```
arrival_month_number
```

---

# Key Metrics

The main KPI analyzed is:

### Cancellation Rate

```
Cancellation Rate = Cancelled Reservations / Total Reservations
```

Calculated across:

* Market segment
* Distribution channel
* Lead time bucket
* Arrival month

---

# Analysis

## 1 Market Segment Analysis

Cancellation rates vary significantly across customer segments.

Typical pattern observed:

| Segment                | Cancellation Behavior     |
| ---------------------- | ------------------------- |
| Direct                 | Lowest cancellation rates |
| Corporate              | Stable demand             |
| Online Travel Agencies | Moderate cancellations    |
| Groups                 | Highest cancellation rate |

### Revenue Insight

Group bookings tend to cancel more frequently due to:

* event planning uncertainty
* contract flexibility
* long booking windows

However, they still provide **important base demand for forecasting**.

---

# 2 Distribution Channel Analysis

Distribution channels show different cancellation behaviors.

Typical pattern:

| Channel                 | Behavior             |
| ----------------------- | -------------------- |
| Direct                  | Lowest cancellations |
| Corporate               | Stable demand        |
| TA/TO (travel agencies) | Higher cancellations |

### Revenue Insight

OTA channels provide:

* early demand visibility
* strong booking volume

But also bring **higher cancellation risk**.

This suggests the need for:

* channel mix optimization
* flexible cancellation policies
* controlled inventory allocation.

---

# 3 Lead Time Analysis

Lead time is one of the strongest predictors of cancellation behavior.

Observed pattern:

| Lead Time   | Cancellation Trend      |
| ----------- | ----------------------- |
| 0–7 days    | Very low cancellations  |
| 8–30 days   | Moderate cancellations  |
| 31–90 days  | High cancellations      |
| 91–180 days | Very high cancellations |
| 180+ days   | Highest cancellations   |

### Revenue Insight

The earlier a reservation is made, the more likely it is to cancel.

This explains why many hotels offer **free cancellation for early bookings**.

Early reservations provide:

* demand signals
* forecasting visibility
* pricing flexibility

---

# 4 Seasonality Analysis

Cancellation behavior also changes across months.

Seasonality impacts:

* booking behavior
* travel uncertainty
* demand volatility

In many cases:

* high season → lower cancellations
* shoulder seasons → higher cancellations

This can influence:

* minimum stay restrictions
* cancellation policies
* overbooking levels.

---

# Strategic Revenue Management Insights

The analysis shows that **cancellations are not purely negative**.

In many cases, they are part of the **demand discovery process**.

Key takeaways:

### Early bookings improve forecasting

Even if some cancel, early bookings provide visibility into demand trends.

---

### Distribution channels require balance

OTA channels bring volume but higher cancellations.

Hotels should manage:

* channel mix
* pricing parity
* inventory allocation.

---

### Lead time is a powerful forecasting variable

Cancellation probability increases with booking window length.

This insight supports:

* demand forecasting models
* dynamic overbooking strategies.

---

### Flexible cancellation policies can drive demand

Allowing cancellations can increase early bookings and improve revenue optimization.

---

# Revenue Strategy Implications

Based on the findings, several strategies can improve revenue performance:

### Controlled Overbooking

Using historical cancellation patterns to safely oversell inventory.

---

### Dynamic Cancellation Policies

Stricter cancellation policies during high-demand periods.

---

### Channel Optimization

Balance OTA and direct bookings to manage cancellation risk.

---

### Lead Time Pricing

Implement pricing strategies based on booking window.

Example:

* early booking discounts
* last-minute premium pricing.

---

# Tools Used

Python
Pandas
Jupyter Notebook
Kaggle

---

# Final Thought

In Revenue Management, cancellations are not just lost bookings.

They are signals.

Signals about **customer behavior, booking patterns, and demand uncertainty**.

Understanding those signals allows hotels to transform cancellations from a risk into a **strategic advantage**.
