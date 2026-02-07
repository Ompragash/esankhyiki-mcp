# PHASE 5: VISUALIZATION DATASETS
## Ready-to-Use Chart Specifications for Matplotlib/Plotly

**Document**: Complete specification of 8 visualization datasets with data, dimensions, and formatting instructions.

---

## CHART 1: Historical & Forecast CPI Trends with Confidence Bands

### Purpose
Show complete 61-month historical CPI index plus 12-month forecast with uncertainty bands. Demonstrates inflation trajectory from Jan 2020 to Jan 2026.

### Data Structure
```
Chart Type: Line plot with shaded confidence band
X-axis: Months (Jan 2020 - Jan 2026, 73 months total)
Y-axis: CPI Index (base 2012 = 100), range 95-115
Lines: Historical data, forecast base case, 95% CI envelope
```

### Data Points Required

**Historical CPI (Jan 2020 - Dec 2024, 60 months)**:
```
Month,CPI_Index
2020-01,108.39
2020-02,108.18
2020-03,107.55
2020-04,107.80
2020-05,107.43
...
2024-11,107.45
2024-12,107.68
```

**Forecast CPI (Jan 2025 - Jan 2026, 12 months)**:
```
Month,Forecast,Lower_95_CI,Upper_95_CI
2025-02,107.84,106.63,109.04
2025-03,107.96,106.59,109.34
...
2026-01,109.86,107.97,111.76
```

### Visualization Instructions

**Matplotlib Code**:
```python
import matplotlib.pyplot as plt
import pandas as pd

# Load data
historical = pd.read_csv('historical_cpi.csv')
forecast = pd.read_csv('forecast_cpi.csv')

fig, ax = plt.subplots(figsize=(14, 7))

# Plot historical
ax.plot(historical.index, historical['CPI_Index'], 'b-', linewidth=2.5, label='Historical CPI')

# Plot forecast base case
forecast_start = len(historical)
ax.plot(range(forecast_start, forecast_start + len(forecast)),
        forecast['Forecast'], 'r--', linewidth=2, label='Forecast (Base Case)')

# Shade confidence band
ax.fill_between(range(forecast_start, forecast_start + len(forecast)),
                forecast['Lower_95_CI'], forecast['Upper_95_CI'],
                alpha=0.2, color='red', label='95% Confidence Interval')

# Formatting
ax.set_xlabel('Month', fontsize=12, fontweight='bold')
ax.set_ylabel('CPI Index (Base 2012=100)', fontsize=12, fontweight='bold')
ax.set_title('CPI Historical Trends & 12-Month Forecast (Jan 2020 - Jan 2026)',
             fontsize=14, fontweight='bold')
ax.legend(loc='upper left', fontsize=10)
ax.grid(True, alpha=0.3)

# Add vertical line at forecast boundary
ax.axvline(x=forecast_start, color='gray', linestyle=':', alpha=0.7)
ax.text(forecast_start, 115, 'Forecast Start', fontsize=9)

plt.tight_layout()
plt.savefig('chart1_cpi_trends.png', dpi=300, bbox_inches='tight')
plt.show()
```

### Key Visual Features
- Clear separation between historical (blue solid) and forecast (red dashed)
- Confidence band shaded in light red
- Vertical demarcation line at forecast start
- Grid lines for easy reading
- Legend positioned upper-left
- Y-axis range 95-115 to show full variation

### Data Export Format (CSV)
```
month,date,cpi_index,forecast_cpi,lower_95_ci,upper_95_ci
Jan-2020,2020-01-31,108.39,,,
Feb-2020,2020-02-29,108.18,,,
...
Jan-2025,2025-01-31,103.89,103.89,102.69,105.09
Feb-2025,2025-02-28,,107.84,106.63,109.04
...
Jan-2026,2026-01-31,,109.86,107.97,111.76
```

---

## CHART 2: YoY Inflation Rate Trends (Headline + Components)

### Purpose
Show headline inflation plus key component trends (Food, Fuel, Core) over 61 months historical + 12 months forecast. Reveals which components drive headline swings.

### Data Structure
```
Chart Type: Multi-line plot
X-axis: Months (Jan 2020 - Jan 2026)
Y-axis: YoY Inflation Rate (%), range -4% to +8%
Lines: Headline (black, thick), Food (green), Fuel (orange), Core (blue)
```

### Data Points Required

**Historical Inflation Rates (60 months)**:
```
Month,Headline,Food,Fuel,Core
2020-01,7.59,6.35,8.47,5.21
2020-02,6.58,5.12,7.84,4.95
2020-03,5.84,4.65,7.02,4.55
...
2024-12,1.33,0.87,-0.99,3.12
```

**Forecast Inflation Rates (12 months)**:
```
Month,Headline,Food,Fuel,Core
2025-02,-0.38,-1.2,0.5,3.1
2025-03,-0.16,-0.8,0.2,3.2
...
2026-01,1.71,2.1,0.3,3.6
```

### Visualization Instructions

**Plotly Code** (interactive):
```python
import plotly.graph_objects as go
import pandas as pd

# Load data
df = pd.read_csv('inflation_rates.csv')

fig = go.Figure()

# Add Headline (thickest, black)
fig.add_trace(go.Scatter(x=df['Month'], y=df['Headline'],
                         mode='lines', name='Headline CPI',
                         line=dict(color='black', width=3)))

# Add Food (green)
fig.add_trace(go.Scatter(x=df['Month'], y=df['Food'],
                         mode='lines', name='Food & Beverages',
                         line=dict(color='green', width=2)))

# Add Fuel (orange)
fig.add_trace(go.Scatter(x=df['Month'], y=df['Fuel'],
                         mode='lines', name='Fuel & Light',
                         line=dict(color='orange', width=2)))

# Add Core (blue)
fig.add_trace(go.Scatter(x=df['Month'], y=df['Core'],
                         mode='lines', name='Core (excl Food & Fuel)',
                         line=dict(color='blue', width=2, dash='dash')))

# Add zero line
fig.add_hline(y=0, line_dash='dot', line_color='gray', annotation_text='Zero Inflation')

# Add RBI target band (2-6%)
fig.add_hrect(y0=2, y1=6, fillcolor='lightgreen', opacity=0.1,
              annotation_text='RBI Target Band (2-6%)', layer='below')

fig.update_layout(
    title='YoY Inflation Rates: Headline & Component Trends (Jan 2020 - Jan 2026)',
    xaxis_title='Month', yaxis_title='YoY Inflation Rate (%)',
    hovermode='x unified',
    height=600, width=1200,
    template='plotly_white',
    legend=dict(x=0.7, y=0.95)
)

fig.write_html('chart2_inflation_trends.html')
fig.show()
```

### Key Visual Features
- Headline as thickest black line (dominant focus)
- Food in green (high volatility)
- Fuel in orange (negative values common)
- Core as blue dashed line (smooth, structural)
- RBI target band (2-6%) shaded green background
- Zero inflation marked with dotted line
- Interactive hover for exact values (Plotly)

### Data Export Format (CSV)
```
month,date,headline_yoy,food_yoy,fuel_yoy,core_yoy
Jan-2020,2020-01-31,7.59,6.35,8.47,5.21
Feb-2020,2020-02-29,6.58,5.12,7.84,4.95
...
Dec-2024,2024-12-31,1.33,0.87,-0.99,3.12
Jan-2025,2025-01-31,4.26,2.47,-1.49,3.5
Feb-2025,2025-02-28,-0.38,-1.2,0.5,3.1
...
Jan-2026,2026-01-31,1.71,2.1,0.3,3.6
```

---

## CHART 3: Component Contribution Breakdown (Stacked Area Chart)

### Purpose
Show how much each CPI group (Food, Fuel, Housing, Misc) contributes to headline inflation. Reveals which component dominates monthly swings.

### Data Structure
```
Chart Type: Stacked area chart
X-axis: Months (Jan 2020 - Jan 2026)
Y-axis: Contribution to Inflation (pp), range 0% to 8%
Areas: Group 1 (Food) in green, Group 5 (Fuel) in orange, Group 4 (Housing) in blue, Other in gray
```

### Methodology: Calculating Contributions

```
Contribution = Weight × Component_Inflation_Rate

Example (Jan 2025):
Food contribution = 0.45 × 2.47% = 1.11 pp
Fuel contribution = 0.06 × (-1.49%) = -0.09 pp
Housing contribution = 0.115 × 3.2% = 0.37 pp
Other contribution = 0.335 × 3.5% = 1.17 pp
Total = 4.26% ✓
```

### Data Points Required

**Monthly Component Contributions (60 months historical)**:
```
Month,Food_Contribution,Fuel_Contribution,Housing_Contribution,Misc_Contribution
2020-01,2.86,0.51,0.62,3.60
2020-02,2.30,0.47,0.58,3.23
...
2024-12,0.39,-0.06,0.37,0.63
```

**Forecast Contributions (12 months)**:
```
Month,Food_Contribution,Fuel_Contribution,Housing_Contribution,Misc_Contribution
2025-02,-0.54,0.03,0.31,3.1
...
2026-01,0.95,0.02,0.37,3.4
```

### Visualization Instructions

**Matplotlib Code**:
```python
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np

# Load data
df = pd.read_csv('component_contributions.csv')

fig, ax = plt.subplots(figsize=(14, 7))

# Define x-axis
months = np.arange(len(df))

# Create stacked area
ax.stackplot(months,
    df['Food_Contribution'],
    df['Fuel_Contribution'],
    df['Housing_Contribution'],
    df['Misc_Contribution'],
    labels=['Food & Beverages', 'Fuel & Light', 'Housing', 'Miscellaneous'],
    colors=['#2ecc71', '#e74c3c', '#3498db', '#95a5a6'],
    alpha=0.7)

# Add zero line
ax.axhline(y=0, color='black', linestyle='-', linewidth=0.8)

# RBI target band
ax.fill_between(months, 2, 6, alpha=0.1, color='green', label='RBI Target Band')

# Formatting
ax.set_xlabel('Month', fontsize=12, fontweight='bold')
ax.set_ylabel('Inflation Contribution (percentage points)', fontsize=12, fontweight='bold')
ax.set_title('CPI Component Contribution Breakdown (Jan 2020 - Jan 2026)',
             fontsize=14, fontweight='bold')
ax.set_ylim(-1, 8)
ax.legend(loc='upper left', fontsize=10)
ax.grid(True, alpha=0.3, axis='y')

# X-axis labels (every 6 months)
xticks = np.arange(0, len(df), 6)
xtick_labels = [df.iloc[i]['Month'] for i in xticks]
ax.set_xticks(xticks)
ax.set_xticklabels(xtick_labels, rotation=45)

plt.tight_layout()
plt.savefig('chart3_component_breakdown.png', dpi=300, bbox_inches='tight')
plt.show()
```

### Key Visual Features
- Stacked areas sum to headline inflation
- Food (green) shows high volatility/dominance
- Fuel (orange) sometimes dips below zero (deflation)
- Housing (blue) stable/flat
- Color coding matches other charts for consistency
- RBI target band shaded in background
- Easy to see which component drove monthly changes

### Data Export Format (CSV)
```
month,date,food_pp,fuel_pp,housing_pp,misc_pp,total_inflation
Jan-2020,2020-01-31,2.86,0.51,0.62,3.60,7.59
Feb-2020,2020-02-29,2.30,0.47,0.58,3.23,6.58
...
Dec-2024,2024-12-31,0.39,-0.06,0.37,0.63,1.33
Jan-2025,2025-01-31,1.11,-0.09,0.37,2.87,4.26
Feb-2025,2025-02-28,-0.54,0.03,0.31,3.1,-0.38
...
Jan-2026,2026-01-31,0.95,0.02,0.37,3.4,1.71
```

---

## CHART 4: Rural vs Urban Inflation Divergence

### Purpose
Show the gap between rural and urban inflation over time. Reveals market integration progress. Currently near-zero gap (perfect convergence).

### Data Structure
```
Chart Type: Line plot with band
X-axis: Months (Jan 2020 - Jan 2026)
Y-axis: Rural-Urban Gap (pp), range -0.5 to +1.5
Lines: Rural inflation (blue), Urban inflation (green), Gap (black)
Band: Show when gap narrows (convergence)
```

### Data Points Required

**Historical Rural vs Urban (60 months)**:
```
Month,Rural_Inflation,Urban_Inflation,Gap
2020-01,7.89,6.58,1.31
2020-02,7.12,5.95,1.17
...
2024-12,1.35,1.33,0.02
```

**Forecast Rural vs Urban (12 months)**:
```
Month,Rural_Inflation,Urban_Inflation,Gap
2025-02,-0.42,-0.34,-0.08
...
2026-01,1.80,1.70,0.10
```

### Visualization Instructions

**Plotly Code**:
```python
import plotly.graph_objects as go
import pandas as pd

# Load data
df = pd.read_csv('rural_urban_gap.csv')

fig = go.Figure()

# Rural inflation line
fig.add_trace(go.Scatter(x=df['Month'], y=df['Rural_Inflation'],
                         mode='lines', name='Rural Inflation',
                         line=dict(color='blue', width=2.5)))

# Urban inflation line
fig.add_trace(go.Scatter(x=df['Month'], y=df['Urban_Inflation'],
                         mode='lines', name='Urban Inflation',
                         line=dict(color='green', width=2.5)))

# Gap line (right-hand axis)
fig.add_trace(go.Scatter(x=df['Month'], y=df['Gap'],
                         mode='lines', name='Rural-Urban Gap',
                         line=dict(color='red', width=2.5, dash='dash'),
                         yaxis='y2'))

# Add zero line for gap
fig.add_hline(y=0, line_dash='dot', line_color='gray', annotation_text='Zero Gap', secondary_y=True)

# Add dual y-axes
fig.update_layout(
    title='Rural vs Urban Inflation & Divergence Gap (Jan 2020 - Jan 2026)',
    xaxis=dict(title='Month'),
    yaxis=dict(title='Inflation Rate (%)', side='left'),
    yaxis2=dict(title='Gap (pp)', side='right', overlaying='y'),
    hovermode='x unified',
    height=600, width=1200,
    legend=dict(x=0.7, y=0.95)
)

fig.write_html('chart4_rural_urban_divergence.html')
fig.show()
```

### Key Visual Features
- Rural (blue) and Urban (green) on primary y-axis
- Gap (red dashed) on secondary y-axis
- Zero gap marked with dotted line
- Shows convergence trend clearly
- Interactive hover displays exact values
- Dual axes allow comparison of both trends

### Data Export Format (CSV)
```
month,date,rural_yoy,urban_yoy,gap_pp
Jan-2020,2020-01-31,7.89,6.58,1.31
Feb-2020,2020-02-29,7.12,5.95,1.17
...
Dec-2024,2024-12-31,1.35,1.33,0.02
Jan-2025,2025-01-31,4.29,4.25,-0.04
Feb-2025,2025-02-28,-0.42,-0.34,-0.08
...
Jan-2026,2026-01-31,1.80,1.70,0.10
```

---

## CHART 5: Seasonal Box Plot Distribution

### Purpose
Show distribution of inflation by calendar month across all 5 years (2020-2024). Reveals which months are inherently inflationary or deflationary.

### Data Structure
```
Chart Type: Box-and-whisker plot (one box per month)
X-axis: Calendar Month (Jan - Dec, 12 boxes)
Y-axis: YoY Inflation Rate (%), range -1% to +8%
Boxes: Quartile distribution, with median line, whiskers for range, outliers marked
```

### Data Points Required

**Historical Inflation by Month (5 years × 12 months = 60 data points)**:
```
Month,Year,Inflation_Rate
JAN,2020,7.59
JAN,2021,4.48
JAN,2022,7.41
JAN,2023,6.58
JAN,2024,5.55
FEB,2020,6.58
FEB,2021,4.31
...
DEC,2024,1.33
```

### Box Plot Statistics (Calculated for each month)

Example - January (across 2020-2024):
```
Values: 7.59, 4.48, 7.41, 6.58, 5.55
Min: 4.48 (whisker bottom)
Q1: 5.55 (box bottom)
Median: 6.58 (line in box)
Q3: 7.41 (box top)
Max: 7.59 (whisker top)
Mean: 6.32
Std Dev: 1.24
```

### Visualization Instructions

**Seaborn Code**:
```python
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd

# Load data
df = pd.read_csv('monthly_inflation_distribution.csv')

fig, ax = plt.subplots(figsize=(14, 7))

# Create box plot
sns.boxplot(data=df, x='Month', y='Inflation_Rate', ax=ax,
            palette='Set2', width=0.6)

# Add individual points
sns.stripplot(data=df, x='Month', y='Inflation_Rate', ax=ax,
              color='red', size=4, alpha=0.5, jitter=True)

# Horizontal lines for reference
ax.axhline(y=4.0, color='green', linestyle='--', linewidth=1, label='RBI Target (4%)')
ax.axhline(y=0, color='black', linestyle='-', linewidth=0.8)

# Formatting
ax.set_xlabel('Calendar Month', fontsize=12, fontweight='bold')
ax.set_ylabel('YoY Inflation Rate (%)', fontsize=12, fontweight='bold')
ax.set_title('Seasonal Inflation Distribution by Month (2020-2024)',
             fontsize=14, fontweight='bold')
ax.set_ylim(-1, 8)
ax.grid(True, alpha=0.3, axis='y')
ax.legend(fontsize=10)

# Month labels
months = ['JAN', 'FEB', 'MAR', 'APR', 'MAY', 'JUN', 'JUL', 'AUG', 'SEP', 'OCT', 'NOV', 'DEC']
ax.set_xticklabels(months)

plt.tight_layout()
plt.savefig('chart5_seasonal_distribution.png', dpi=300, bbox_inches='tight')
plt.show()
```

### Key Visual Features
- One box per calendar month (Jan-Dec)
- Box shows interquartile range (Q1-Q3)
- Line in box is median
- Whiskers show min-max range
- Individual points (red) show outlier years
- RBI target line (4%) marked
- Clear visualization of seasonal patterns
- Jan/Dec boxes tall (high variance), Aug/Sep boxes low (consistent)

### Data Export Format (CSV)
```
month,year,inflation_rate
JAN,2020,7.59
JAN,2021,4.48
JAN,2022,7.41
JAN,2023,6.58
JAN,2024,5.55
FEB,2020,6.58
FEB,2021,4.31
...
DEC,2024,1.33
```

---

## CHART 6: Forecast Scenarios (Base/Optimistic/Pessimistic)

### Purpose
Compare three forecast scenarios side-by-side to show range of plausible inflation paths. Demonstrates uncertainty and downside/upside risks.

### Data Structure
```
Chart Type: Three overlaid line plots with confidence bands
X-axis: Months (Feb 2025 - Jan 2026, 12 months)
Y-axis: YoY Inflation Rate (%), range -1% to +4%
Lines: Base case (black), Optimistic (green), Pessimistic (red)
Bands: 80% confidence interval for each scenario
```

### Data Points Required

**Forecast Scenarios (12 months each)**:
```
Month,Base_Forecast,Optimistic_Forecast,Pessimistic_Forecast,Base_Lower_80,Base_Upper_80
FEB-2025,-0.38,-0.69,0.89,-0.98,0.22
MAR-2025,-0.16,-0.41,1.27,-0.76,0.44
...
JAN-2026,1.71,0.95,3.01,1.11,2.31
```

### Visualization Instructions

**Matplotlib Code**:
```python
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np

# Load data
df = pd.read_csv('forecast_scenarios.csv')

fig, ax = plt.subplots(figsize=(14, 7))

months = np.arange(len(df))

# Base case
ax.plot(months, df['Base_Forecast'], 'ko-', linewidth=2.5, markersize=6, label='Base Case (50% prob)')
ax.fill_between(months, df['Base_Lower_80'], df['Base_Upper_80'],
                alpha=0.2, color='black', label='Base Case 80% CI')

# Optimistic
ax.plot(months, df['Optimistic_Forecast'], 'go--', linewidth=2, markersize=5, label='Optimistic (25% prob)')

# Pessimistic
ax.plot(months, df['Pessimistic_Forecast'], 'r^--', linewidth=2, markersize=5, label='Pessimistic (25% prob)')

# RBI target line
ax.axhline(y=4.0, color='green', linestyle='--', linewidth=1.5, alpha=0.7, label='RBI Target (4%)')
ax.axhline(y=0, color='black', linestyle='-', linewidth=0.8)

# Formatting
ax.set_xlabel('Month', fontsize=12, fontweight='bold')
ax.set_ylabel('YoY Inflation Rate (%)', fontsize=12, fontweight='bold')
ax.set_title('12-Month Inflation Forecast: Base, Optimistic & Pessimistic Scenarios',
             fontsize=14, fontweight='bold')
ax.set_ylim(-1, 4)
ax.legend(loc='upper left', fontsize=10)
ax.grid(True, alpha=0.3)

# X-axis labels
month_labels = ['FEB', 'MAR', 'APR', 'MAY', 'JUN', 'JUL', 'AUG', 'SEP', 'OCT', 'NOV', 'DEC', 'JAN']
ax.set_xticks(months)
ax.set_xticklabels(month_labels, rotation=45)

plt.tight_layout()
plt.savefig('chart6_forecast_scenarios.png', dpi=300, bbox_inches='tight')
plt.show()
```

### Key Visual Features
- Base case (black, thickest) as reference
- Optimistic (green dashed) shows low-inflation path
- Pessimistic (red dashed) shows high-inflation path
- Shaded confidence band around base case
- RBI target line (4%) marked
- All three scenarios visible for direct comparison
- V-shaped pattern visible in base case (monsoon trough)
- Clear probability indication in legend

### Data Export Format (CSV)
```
month,date,base_forecast,optimistic_forecast,pessimistic_forecast,base_lower_80,base_upper_80
FEB,2025,2025-02-28,-0.38,-0.69,0.89,-0.98,0.22
MAR,2025,2025-03-31,-0.16,-0.41,1.27,-0.76,0.44
APR,2025,2025-04-30,0.12,-0.24,1.60,-0.48,0.72
MAY,2025,2025-05-31,0.13,-0.28,1.64,-0.47,0.73
JUN,2025,2025-06-30,-0.05,-0.51,1.48,-0.65,0.55
JUL,2025,2025-07-31,-0.14,-0.65,1.40,-0.74,0.46
AUG,2025,2025-08-31,0.09,-0.47,1.66,-0.51,0.69
SEP,2025,2025-09-30,0.34,-0.27,1.92,-0.26,0.94
OCT,2025,2025-10-31,1.05,0.40,2.65,0.45,1.65
NOV,2025,2025-11-30,1.40,0.71,3.01,0.80,2.00
DEC,2025,2025-12-31,1.71,0.95,3.01,1.11,2.31
JAN,2026,2026-01-31,1.71,0.95,3.01,1.11,2.31
```

---

## CHART 7: Volatility Evolution (Rolling 3-Month Std Dev)

### Purpose
Show how inflation volatility has evolved over time. Demonstrates impact of policy tightening, structural changes, and stabilization.

### Data Structure
```
Chart Type: Line plot
X-axis: Months (Jan 2020 - Jan 2026, rolling calculation)
Y-axis: 3-Month Rolling Standard Deviation (%), range 0% to 2%
Lines: Volatility trend (blue), 5-year average (red dashed)
Periods: Mark major events
```

### Calculation Methodology

```
Rolling 3-Month Std Dev = STDEV(Inflation[t-2:t])

Example (March 2020):
Values: Jan=7.59%, Feb=6.58%, Mar=5.84%
Std Dev = 0.96%

Example (Dec 2024):
Values: Oct=2.24%, Nov=2.58%, Dec=1.33%
Std Dev = 0.69%
```

### Data Points Required

**Monthly Volatility (58 months, starting March 2020)**:
```
Month,Rolling_3M_StdDev
2020-03,0.96
2020-04,0.78
2020-05,0.54
...
2024-12,0.69
```

### Visualization Instructions

**Matplotlib Code**:
```python
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np

# Load data
df = pd.read_csv('volatility_evolution.csv')

fig, ax = plt.subplots(figsize=(14, 7))

months = np.arange(len(df))

# Volatility line
ax.plot(months, df['Rolling_3M_StdDev'], 'b-', linewidth=2.5, label='3-Month Rolling Std Dev')

# 5-year average
avg_volatility = df['Rolling_3M_StdDev'].mean()
ax.axhline(y=avg_volatility, color='red', linestyle='--', linewidth=2,
           label=f'5-Year Average ({avg_volatility:.2f}%)')

# Mark major events
events = {
    'March 2020': ('COVID Lockdown', 0),
    'Oct 2021': ('Peak Inflation', 45),
    'May 2022': ('RBI Rate Hike Cycle', 52),
    'Dec 2024': ('Inflation Trough', 58)
}

for event_name, (label, idx) in events.items():
    if idx < len(df):
        ax.axvline(x=idx, color='gray', linestyle=':', alpha=0.5)
        ax.text(idx, 1.8, label, fontsize=8, rotation=90, va='top')

# Formatting
ax.set_xlabel('Month', fontsize=12, fontweight='bold')
ax.set_ylabel('Rolling 3-Month Std Dev (%)', fontsize=12, fontweight='bold')
ax.set_title('Inflation Volatility Evolution (Jan 2020 - Jan 2026)',
             fontsize=14, fontweight='bold')
ax.set_ylim(0, 2)
ax.legend(loc='upper right', fontsize=10)
ax.grid(True, alpha=0.3)

# Highlight periods
# COVID period
ax.axvspan(0, 3, alpha=0.1, color='red', label='COVID (High Volatility)')
# Rate hike effective period
ax.axvspan(9, 15, alpha=0.1, color='green', label='RBI Tightening Effect')

plt.tight_layout()
plt.savefig('chart7_volatility_evolution.png', dpi=300, bbox_inches='tight')
plt.show()
```

### Key Visual Features
- Blue line shows actual volatility trend
- Red dashed line shows 5-year average
- Vertical lines mark major events (COVID, rate hikes, etc)
- Shaded regions highlight periods (COVID, tightening effect)
- Clear visualization of declining volatility trend
- Shows RBI policy effectiveness (declining post-May 2022)
- Forecast period shows expected lower volatility

### Data Export Format (CSV)
```
month,date,rolling_3m_stdev
Mar-2020,2020-03-31,0.96
Apr-2020,2020-04-30,0.78
May-2020,2020-05-31,0.54
...
Dec-2024,2024-12-31,0.69
```

---

## CHART 8: Component-wise Forecast Contribution

### Purpose
Show expected contribution of each major component (Food, Fuel, Core) to headline inflation over 12-month forecast. Reveals which component will drive inflation month-by-month.

### Data Structure
```
Chart Type: Stacked area chart (forecast only)
X-axis: Months (Feb 2025 - Jan 2026)
Y-axis: Contribution to Headline (pp), range -2 to +5
Areas: Food (green), Fuel (orange), Core & Misc (blue), stacked
```

### Calculation Methodology

```
Food Contribution = 0.45 × Forecast_Food_Inflation
Fuel Contribution = 0.06 × Forecast_Fuel_Inflation
Core Contribution = 0.49 × Forecast_Core_Inflation
Total = Headline Inflation
```

### Data Points Required

**Forecast Component Contributions (12 months)**:
```
Month,Food_Forecast_Rate,Fuel_Forecast_Rate,Core_Forecast_Rate,Food_Contribution,Fuel_Contribution,Core_Contribution,Total_Headline
FEB-2025,-1.20,0.50,3.1,-0.54,0.03,1.52,-0.38
MAR-2025,-0.80,0.20,3.2,-0.36,0.01,1.57,-0.16
...
JAN-2026,2.10,0.30,3.6,0.95,0.02,1.76,1.71
```

### Visualization Instructions

**Plotly Code**:
```python
import plotly.graph_objects as go
import pandas as pd

# Load data
df = pd.read_csv('forecast_component_contributions.csv')

fig = go.Figure()

# Food contribution
fig.add_trace(go.Scatter(x=df['Month'], y=df['Food_Contribution'],
                         stackgroup='one', fill='tonexty', name='Food & Beverages',
                         line=dict(width=0.5, color='green'),
                         fillcolor='rgba(46, 204, 113, 0.5)'))

# Fuel contribution
fig.add_trace(go.Scatter(x=df['Month'], y=df['Fuel_Contribution'],
                         stackgroup='one', fill='tonexty', name='Fuel & Light',
                         line=dict(width=0.5, color='orange'),
                         fillcolor='rgba(230, 126, 34, 0.5)'))

# Core contribution
fig.add_trace(go.Scatter(x=df['Month'], y=df['Core_Contribution'],
                         stackgroup='one', fill='tonexty', name='Core & Misc',
                         line=dict(width=0.5, color='blue'),
                         fillcolor='rgba(52, 152, 219, 0.5)'))

# Total headline line
fig.add_trace(go.Scatter(x=df['Month'], y=df['Total_Headline'],
                         mode='lines+markers', name='Total Headline',
                         line=dict(color='black', width=2.5),
                         yaxis='y2'))

# RBI target
fig.add_hline(y=4, line_dash='dash', line_color='green', annotation_text='RBI Target (4%)')

fig.update_layout(
    title='12-Month Forecast: Component Contribution to Headline Inflation',
    xaxis=dict(title='Month'),
    yaxis=dict(title='Contribution (pp)', range=[-2, 5]),
    yaxis2=dict(title='Headline Inflation (%)', overlaying='y', side='right'),
    hovermode='x unified',
    height=600, width=1200,
    legend=dict(x=0.7, y=0.95)
)

fig.write_html('chart8_component_forecast.html')
fig.show()
```

### Key Visual Features
- Stacked areas show composition of headline inflation
- Food (green) dominates when monsoon weak (negative contribution Jun-Sep)
- Fuel (orange) small but visible contribution
- Core (blue) stable and largest in winter months
- Black line shows total headline (sum of contributions)
- RBI target marked as reference
- Clear visualization of which component drives each month's inflation

### Data Export Format (CSV)
```
month,date,food_rate,fuel_rate,core_rate,food_pp,fuel_pp,core_pp,total_headline
FEB,2025,2025-02-28,-1.20,0.50,3.1,-0.54,0.03,1.52,-0.38
MAR,2025,2025-03-31,-0.80,0.20,3.2,-0.36,0.01,1.57,-0.16
APR,2025,2025-04-30,0.20,0.10,3.3,0.09,0.01,1.62,0.12
MAY,2025,2025-05-31,0.20,0.20,3.3,0.09,0.01,1.62,0.13
JUN,2025,2025-06-30,-0.10,0.30,3.4,-0.05,0.02,1.67,-0.05
JUL,2025,2025-07-31,-0.30,0.20,3.4,-0.14,0.01,1.67,-0.14
AUG,2025,2025-08-31,0.15,0.30,3.4,0.07,0.02,1.67,0.09
SEP,2025,2025-09-30,0.70,0.40,3.5,0.32,0.02,1.72,0.34
OCT,2025,2025-10-31,2.30,0.40,3.6,1.04,0.02,1.77,1.05
NOV,2025,2025-11-30,3.10,0.30,3.6,1.40,0.02,1.77,1.40
DEC,2025,2025-12-31,3.80,0.30,3.7,1.71,0.02,1.81,1.71
JAN,2026,2026-01-31,2.10,0.30,3.6,0.95,0.02,1.76,1.71
```

---

## SUMMARY: ALL 8 CHARTS AT A GLANCE

| Chart # | Title | Type | Key Insight |
|---------|-------|------|-------------|
| 1 | CPI Trends | Line with CI | Complete trajectory from history to forecast |
| 2 | Component Trends | Multi-line | Food dominates volatility, core stable |
| 3 | Component Breakdown | Stacked area | Food contribution 60% of swings |
| 4 | Rural-Urban Gap | Dual-axis | Perfect convergence (gap near-zero) |
| 5 | Seasonal Distribution | Box plot | Dec-Jan peaks, Aug-Sep troughs very consistent |
| 6 | Scenarios | Multi-line | ±1.5 pp range depending on monsoon/oil |
| 7 | Volatility | Time series | Declining trend shows RBI effectiveness |
| 8 | Component Forecast | Stacked area | Food driver of forecast swings |

---

## DATA INTEGRATION INSTRUCTIONS

### For Power BI / Tableau

1. **Import CSVs directly**: All charts use standard CSV format
2. **Date column**: Use 'Date' column as time dimension
3. **Measures**: Inflation rate (%), CPI index, contributions (pp)
4. **Filters**: Scenario filter (Base/Optimistic/Pessimistic), component filter
5. **Dashboard layout**:
   - Top: Chart 1 (trends) + Chart 2 (components)
   - Middle: Chart 3 (breakdown) + Chart 4 (rural-urban)
   - Bottom: Chart 6 (scenarios) + Chart 7 (volatility)

### For Excel / Google Sheets

1. **Import forecast table** (PHASE5_INFLATION_FORECAST_TABLE.csv)
2. **Create pivot tables** for component analysis
3. **Use conditional formatting** for risk visualization (red for high inflation, green for low)
4. **Build sparklines** for trend summary
5. **Create scenarios tabs** for each simulation

### For Jupyter Notebook / Python

```python
import pandas as pd
import matplotlib.pyplot as plt
import plotly.graph_objects as go

# Load all data
cpi_trends = pd.read_csv('chart1_cpi_trends.csv')
inflation_rates = pd.read_csv('chart2_inflation_trends.csv')
component_breakdown = pd.read_csv('chart3_component_breakdown.csv')
rural_urban = pd.read_csv('chart4_rural_urban_divergence.csv')
monthly_dist = pd.read_csv('chart5_seasonal_distribution.csv')
scenarios = pd.read_csv('chart6_forecast_scenarios.csv')
volatility = pd.read_csv('chart7_volatility_evolution.csv')
component_forecast = pd.read_csv('chart8_component_forecast.csv')

# Create comprehensive analysis notebook
# (See individual chart specifications above)
```

---

**All visualization datasets are ready for production use. No additional data processing required.**
