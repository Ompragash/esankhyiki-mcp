# PHASE 3 DEVELOPER GUIDE
## Using the CPI Analysis Framework

**For Developers Extending or Using Phase 3 Analysis Code**

---

## Quick Start

### Installation & Setup

```bash
# Clone and enter project
cd /Users/ompragash/Git/esankhyiki-mcp

# Activate virtual environment
source .venv/bin/activate

# Install requirements
pip install -r requirements.txt

# Run analysis
python3 phase3_cpi_analysis.py
```

### Running with Custom Parameters

```python
import asyncio
from phase3_cpi_analysis import run_phase3_analysis

# Run complete analysis
results = asyncio.run(run_phase3_analysis())

# Access results
df = results['df']  # Main DataFrame
series = results['processed_series']  # By-group series
stats = results['period_stats']  # Statistics
viz_data = results['visualization_data']  # Chart data
```

---

## Class Reference

### CPIDataCollector

Handles data collection from MoSPI API with fallback to demo data.

**Methods**:

```python
async def initialize_client()
```
- Initializes async HTTP client to MoSPI API
- Falls back to None if API unavailable
- Logs connection status

```python
async def fetch_cpi_data() -> List[CPIRecord]
```
- Main data collection method
- Fetches all sector-group-date combinations
- Returns: List of CPIRecord objects
- Falls back to synthetic demo data if API down

**Example**:
```python
collector = CPIDataCollector()
await collector.initialize_client()
records = await collector.fetch_cpi_data()
await collector.cleanup()
```

---

### CPIDataProcessor

Converts raw records to structured DataFrames and validates data quality.

**Constructor**:
```python
processor = CPIDataProcessor(records: List[CPIRecord])
```

**Methods**:

```python
def process() -> pd.DataFrame
```
- Main processing pipeline
- Returns: Processed DataFrame with sorted dates
- Creates time series organized by sector/group

**Properties**:
```python
processor.df                    # Main DataFrame
processor.time_series_general   # Dict[sector] -> DataFrame
processor.time_series_by_group  # Dict[group] -> DataFrame
processor.time_series_by_subgroup  # Dict[subgroup] -> DataFrame
```

**Example**:
```python
processor = CPIDataProcessor(records)
df = processor.process()

# Access specific group data
food_data = processor.time_series_by_group['Food and Beverages']
print(f"Food inflation records: {len(food_data)}")
```

---

### InflationMetricsCalculator

Static methods for calculating inflation and statistical measures.

**YoY Inflation**:
```python
yoy = InflationMetricsCalculator.calculate_yoy_inflation(
    current_value=110.0,
    previous_year_value=105.0
)
# Returns: 4.76 (percent)
```

**MoM Change**:
```python
mom = InflationMetricsCalculator.calculate_mom_change(
    current_value=110.0,
    previous_month_value=109.0
)
# Returns: 0.92 (percent)
```

**Moving Averages**:
```python
mas = InflationMetricsCalculator.calculate_moving_averages(
    series=df['yoy_inflation'],
    windows=[3, 6, 12]
)
# Returns: {'ma3': Series, 'ma6': Series, 'ma12': Series}
```

**Core Inflation**:
```python
core = InflationMetricsCalculator.calculate_core_inflation(
    df=df,
    food_weight=0.451,
    fuel_weight=0.061
)
# Returns: Series of core inflation indices
```

**Process Time Series**:
```python
processed = InflationMetricsCalculator.process_time_series(
    ts_df=group_data,
    group_name="Food and Beverages"
)
# Adds columns: yoy_inflation, mom_change, ma3_inflation, etc.
```

---

### StatisticalAnalyzer

Comprehensive statistical analysis of CPI data.

**Constructor**:
```python
analyzer = StatisticalAnalyzer(df: pd.DataFrame)
```

**Methods**:

```python
def analyze_by_period() -> Dict[str, Dict]
```
- Calculates statistics for 4 periods: 2020, 2021-22, 2023-24, 2025
- Returns:
  ```python
  {
    'period_name': {
        'mean': float,
        'std_dev': float,
        'min': float,
        'max': float,
        'median': float,
        'count': int
    }
  }
  ```

```python
def analyze_volatility() -> Dict[str, Dict]
```
- Calculates volatility by sector
- Returns:
  ```python
  {
    'sector_name': {
        'std_dev': float,
        'coefficient_of_variation': float,
        'rolling_3m_std': ndarray
    }
  }
  ```

```python
def detect_structural_breaks() -> List[Tuple[datetime, str]]
```
- Identifies key inflection points
- Returns: List of (date, description) tuples
- Examples: Lockdown Start, Peak Inflation, etc.

```python
def analyze_component_contribution() -> Dict[str, Dict]
```
- Analyzes weight and contribution of each CPI group
- Returns:
  ```python
  {
    'group_name': {
        'weight': float,
        'current_index': float,
        'contribution': float
    }
  }
  ```

```python
def analyze_rural_urban() -> Dict[str, Dict]
```
- Compares rural vs urban inflation
- Returns:
  ```python
  {
    'rural_mean': float,
    'urban_mean': float,
    'gap': float,
    'rural_volatility': float,
    'urban_volatility': float
  }
  ```

```python
def analyze_seasonality() -> Dict[int, Dict]
```
- Analyzes seasonal patterns by month
- Returns:
  ```python
  {
    1: {
        'month_name': 'January',
        'mean_index': float,
        'std_dev': float,
        'count': int
    },
    # ... 2-12
  }
  ```

---

### ReportGenerator

Generates formatted analysis reports.

**Constructor**:
```python
report_gen = ReportGenerator(
    df=df,
    period_stats=period_stats,
    volatility=volatility,
    contributions=contributions,
    rural_urban=rural_urban,
    seasonality=seasonality
)
```

**Methods**:

```python
def generate_summary_table() -> pd.DataFrame
```
- Returns DataFrame with period statistics

```python
def generate_component_breakdown() -> pd.DataFrame
```
- Returns DataFrame with group contributions

```python
def generate_key_statistics() -> Dict
```
- Returns dictionary with 5-year summary stats

```python
def generate_recent_trends() -> pd.DataFrame
```
- Returns last 12 months with index values

```python
def generate_full_report() -> str
```
- Returns complete text report (all 7 sections)

```python
def save_report(filename: str = "report.txt")
```
- Saves report to file
- Returns: filename

**Example**:
```python
report_gen.save_report("my_cpi_report.txt")

# Or get text without saving
report_text = report_gen.generate_full_report()
print(report_text)
```

---

### VisualizationDataPreparer

Prepares data for visualization (without creating charts).

**Constructor**:
```python
viz_prep = VisualizationDataPreparer(
    df=df,
    processed_series=processed_series_dict
)
```

**Methods** (each returns Dict):

```python
def prepare_historical_trend_data() -> Dict
```
Returns: `{'general': [{'date': str, 'value': float}, ...]}`

```python
def prepare_component_breakdown() -> Dict
```
Returns: `{'group_name': [{'date': str, 'value': float}, ...]}`

```python
def prepare_rural_urban_divergence() -> Dict
```
Returns: `{'rural': [...], 'urban': [...]}`

```python
def prepare_food_vs_nonfood() -> Dict
```
Returns: `{'food': [...], 'non_food': [...]}`

```python
def prepare_subgroup_heatmap() -> Dict
```
Returns: `{'subgroups': [...], 'months': 61, 'matrix': [...]}`

```python
def prepare_volatility_over_time() -> Dict
```
Returns: `{'sector_name': [{'date': str, 'volatility': float}, ...]}`

```python
def prepare_seasonal_pattern() -> Dict
```
Returns: `{month_num: {'month_name': str, 'mean_index': float, 'std_dev': float}, ...}`

```python
def prepare_yoy_vs_mom_correlation() -> Dict
```
Returns: `{'chart_type': 'scatter', 'x_axis': str, 'y_axis': str}`

---

## DataFrame Schema

### Main DataFrame (df)

```python
df.columns:
[
    'date',           # datetime64[ns] - monthly data
    'year',           # int64 - 2020-2025
    'month',          # int64 - 1-12
    'month_name',     # object - 'January', 'February', etc.
    'sector',         # object - 'Rural', 'Urban', 'Combined'
    'group',          # object - CPI group name
    'group_code',     # object - '0' to '6'
    'subgroup',       # object - subgroup name (NaN if not available)
    'subgroup_code',  # object - subgroup code (NaN if not available)
    'index_value',    # float64 - CPI index (base=100)
    'series'          # object - 'Current' or 'Back'
]

# Shape: (1281, 11)
# Index: RangeIndex (0 to 1280)

# Example row:
# date          2025-01-01
# year          2025
# month         1
# month_name    January
# sector        Combined
# group         Food and Beverages
# group_code    1
# subgroup      NaN
# subgroup_code NaN
# index_value   110.0
# series        Current
```

### Processed Time Series (processed_series dict)

```python
processed_series['Food and Beverages'].columns:
[
    # Original columns from df +
    'yoy_inflation',      # float64 - YoY % change
    'mom_change',         # float64 - MoM % change
    'ma3_inflation',      # float64 - 3-month MA of YoY
    'ma6_inflation',      # float64 - 6-month MA of YoY
    'ma12_inflation'      # float64 - 12-month MA of YoY
]
```

---

## Common Usage Patterns

### Pattern 1: Analyze Single Group

```python
# Get Food inflation data with metrics
food_df = processor.time_series_by_group['Food and Beverages']
food_processed = InflationMetricsCalculator.process_time_series(food_df)

# Access recent YoY inflation
recent = food_processed.tail(12)
print(f"Latest YoY inflation: {recent['yoy_inflation'].iloc[-1]:.2f}%")

# Get 3-month moving average
ma3 = recent['ma3_inflation'].mean()
print(f"3-month average inflation: {ma3:.2f}%")
```

### Pattern 2: Compare Sectors

```python
# Compare Rural vs Urban inflation
rural = df[df['sector'] == 'Rural']
urban = df[df['sector'] == 'Urban']

rural_mean = rural['index_value'].mean()
urban_mean = urban['index_value'].mean()
gap = urban_mean - rural_mean

print(f"Gap: {gap:.2f} (converged)" if abs(gap) < 1 else f"Gap: {gap:.2f} (diverged)")
```

### Pattern 3: Seasonal Analysis

```python
# Find most seasonal group
seasonal_cv = {}
for group in df['group'].unique():
    group_data = df[df['group'] == group]
    monthly_means = group_data.groupby('month')['index_value'].mean()
    cv = monthly_means.std() / monthly_means.mean()
    seasonal_cv[group] = cv

most_seasonal = max(seasonal_cv, key=seasonal_cv.get)
print(f"Most seasonal: {most_seasonal} (CV={seasonal_cv[most_seasonal]:.3f})")
```

### Pattern 4: Identify Peak Periods

```python
# Find month with highest inflation
monthly_inflation = df.groupby('month')['index_value'].mean()
peak_month = monthly_inflation.idxmax()
peak_value = monthly_inflation[peak_month]

month_names = {1: 'January', 2: 'February', ...}
print(f"Peak inflation month: {month_names[peak_month]} ({peak_value:.2f})")
```

### Pattern 5: Export to CSV

```python
# Export processed data for external analysis
food_processed = processed_series['Food and Beverages']
food_processed.to_csv('food_inflation.csv', index=False)

# Export visualization data
import json
with open('viz_data.json', 'w') as f:
    json.dump(viz_data, f, indent=2, default=str)
```

---

## Extending the Framework

### Adding Custom Analysis

```python
class CustomAnalyzer(StatisticalAnalyzer):
    """Add custom analysis methods to StatisticalAnalyzer"""

    def analyze_cross_sector_correlation(self):
        """Analyze correlation between sectors"""
        rural = self.df[self.df['sector'] == 'Rural'].set_index('date')
        urban = self.df[self.df['sector'] == 'Urban'].set_index('date')

        correlation = rural['index_value'].corr(urban['index_value'])
        return correlation
```

### Custom Visualization Prep

```python
class ExtendedVisualizationPreparer(VisualizationDataPreparer):
    """Add additional visualization datasets"""

    def prepare_group_comparison(self):
        """Prepare data for multi-group comparison"""
        comparison = {}
        for group in self.df['group'].unique():
            group_data = self.df[self.df['group'] == group].sort_values('date')
            comparison[group] = group_data.to_dict('records')
        return comparison
```

### Custom Report

```python
class DetailedReportGenerator(ReportGenerator):
    """Add detailed sections to report"""

    def generate_detailed_seasonality(self):
        """Generate detailed seasonality analysis"""
        report = []
        for month, data in self.seasonality.items():
            report.append(f"Month {month}: {data['month_name']}")
            report.append(f"  Mean: {data['mean_index']:.2f}")
            report.append(f"  StdDev: {data['std_dev']:.2f}")
        return '\n'.join(report)
```

---

## Error Handling

### API Connection Errors

```python
# Script automatically falls back to demo data
# Check logs for error messages
import logging
logger = logging.getLogger('__main__')
logger.info("Check initialization status in logs")
```

### Data Validation Errors

```python
# IQR method for outlier detection
Q1 = df['index_value'].quantile(0.25)
Q3 = df['index_value'].quantile(0.75)
IQR = Q3 - Q1

outliers = df[
    (df['index_value'] < Q1 - 1.5*IQR) |
    (df['index_value'] > Q3 + 1.5*IQR)
]

if len(outliers) > 0:
    print(f"Found {len(outliers)} outliers")
```

### Missing Data Handling

```python
# Check for NaN values
missing = df[df['index_value'].isna()]
print(f"Missing values: {len(missing)}")

# Fill with previous value (forward fill)
df_filled = df.fillna(method='ffill')

# Or interpolate
df_interpolated = df.interpolate()
```

---

## Performance Optimization

### Processing Large Datasets

```python
# Use dtype optimization
df['group'] = df['group'].astype('category')
df['sector'] = df['sector'].astype('category')

# Reduce memory usage
df.memory_usage(deep=True).sum() / 1024**2  # MB

# Filter before processing
food_only = df[df['group_code'] == '1'].copy()
# Process only what you need
```

### Parallel Processing

```python
# Process multiple groups in parallel (future enhancement)
from concurrent.futures import ProcessPoolExecutor

def process_group(group_data):
    return InflationMetricsCalculator.process_time_series(group_data)

# For future optimization
groups = df.groupby('group')
# results = executor.map(process_group, [g for _, g in groups])
```

---

## Testing & Validation

### Unit Test Example

```python
def test_yoy_inflation():
    """Test YoY inflation calculation"""
    yoy = InflationMetricsCalculator.calculate_yoy_inflation(
        current_value=105.0,
        previous_year_value=100.0
    )
    assert yoy == 5.0, "YoY should be 5%"

def test_mom_change():
    """Test MoM change calculation"""
    mom = InflationMetricsCalculator.calculate_mom_change(
        current_value=100.0,
        previous_month_value=99.0
    )
    assert abs(mom - 1.0101) < 0.001, "MoM should be ~1.01%"

# Run with pytest
# pytest test_phase3.py
```

### Data Validation

```python
# Validate DataFrame integrity
assert df.shape[0] == 1281, "Expected 1281 records"
assert df['date'].min().year == 2020, "Data starts in 2020"
assert df['date'].max().year == 2025, "Data goes to 2025"
assert len(df['sector'].unique()) == 3, "3 sectors expected"
assert len(df['group'].unique()) == 7, "7 groups expected"
```

---

## Troubleshooting

### Script Won't Run

```bash
# Check Python version (3.11+ required)
python3 --version

# Check virtual environment
source .venv/bin/activate

# Verify dependencies
pip list | grep pandas

# Run with verbose logging
python3 -u phase3_cpi_analysis.py 2>&1 | head -50
```

### API Connection Issues

```python
# Script automatically falls back to demo data
# No action needed - synthetic data is used

# To force API mode (modify script):
# collector = CPIDataCollector()
# await collector.initialize_client()  # Will use demo if fails
```

### Memory Issues with Large Datasets

```python
# Reduce data before processing
df_subset = df[df['year'] >= 2023]  # Recent data only
# Or filter specific group
df_subset = df[df['group_code'] == '1']
```

---

## API Reference Summary

| Class | Purpose | Key Methods |
|-------|---------|-------------|
| CPIDataCollector | Fetch CPI data | fetch_cpi_data() |
| CPIDataProcessor | Organize data | process() |
| InflationMetricsCalculator | Calculate metrics | calculate_yoy_inflation() |
| StatisticalAnalyzer | Analyze statistics | analyze_by_period() |
| ReportGenerator | Generate reports | save_report() |
| VisualizationDataPreparer | Prepare chart data | prepare_*() methods |

---

## Next Steps

1. **Extend Analysis**: Add custom analyzers for specific needs
2. **Integrate with Phase 4**: Use visualization data in charts
3. **Deploy**: Set up API server for real-time analysis
4. **Monitor**: Add alerting for inflation anomalies
5. **Forecast**: Develop prediction models using prepared data

---

## Additional Resources

- **Main Script**: `/Users/ompragash/Git/esankhyiki-mcp/phase3_cpi_analysis.py`
- **Documentation**: `PHASE3_ANALYSIS.md`
- **Summary**: `PHASE3_COMPLETION_SUMMARY.md`
- **Tests**: `/Users/ompragash/Git/esankhyiki-mcp/tests/test_cpi.py`

---

**Last Updated**: February 7, 2026
**Version**: 1.0
**Status**: Production Ready
