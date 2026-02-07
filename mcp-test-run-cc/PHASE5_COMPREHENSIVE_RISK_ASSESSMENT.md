# PHASE 5: COMPREHENSIVE RISK ASSESSMENT & MONITORING FRAMEWORK
## Detailed Assumptions, Risk Factors, and Real-Time Tracking Protocols

**Document Version**: 1.0
**Date**: February 7, 2026
**Status**: Final Phase 5 Deliverable

---

## PART A: EXPLICIT BASELINE ASSUMPTIONS

### A.1: Economic Assumptions

#### Assumption 1: RBI Monetary Policy Stance

**Stated Assumption**:
- RBI maintains 4% inflation target with 2-6% tolerance band
- Current repo rate: 6.5% (as of January 2026)
- No major policy shift expected in forecast period (Feb 2025 - Jan 2026)
- Inflation transmission lag: 3-6 months from policy changes

**Rationale**:
1. **Recent History**: RBI has held repo at 6.5% since December 2024 (last hike was December)
2. **MPC Trajectory**: Previous tightening cycle (May 2022 - Dec 2022) successfully brought inflation down
3. **Forward Guidance**: RBI last communicated "data-dependent" approach in December 2024 policy statement
4. **Global Context**: Fed also in hold phase (not hiking or cutting)

**Confidence Level**: HIGH (85%)

**Assumption Volatility**:
- Small probability (15%) of unexpected 25-50 bps cut if deflation (>-0.5%) sustained for 3 months
- Even smaller probability (5%) of 25 bps hike if inflation accelerates to >5%
- Base case assumes steady repo rate (no changes)

**Policy Meeting Dates** (when assumption could be violated):
- February 7, 2026 (MPC meeting)
- April 7-8, 2026 (MPC meeting)
- June 4-5, 2026 (MPC meeting)
- August 6-7, 2026 (MPC meeting)
- October 6-7, 2026 (MPC meeting)
- December 2-3, 2026 (MPC meeting)

**Monitoring Protocol**:
1. Review MPC press statements immediately after each meeting
2. Check updated forward guidance vs previous communication
3. Assess repo rate decision (hold/change)
4. If rate changes: Update all forecasts with 6-month lag impact

**Risk**:
- Probability-adjusted impact: 5-10 bps × 5% probability = 0.5 bps mean impact on forecasts

---

#### Assumption 2: Global Crude Oil Price Range

**Stated Assumption**:
- Brent crude oil: $70-85/barrel baseline case
- Range: $60-100/barrel considered plausible
- No major geopolitical disruptions (supply shocks)
- Global demand growth: 2% annually (moderate)

**Current Context** (Feb 2026):
- Actual Brent: ~$75-80/barrel
- WTI: ~$70-75/barrel
- Forward contracts (Mar 2026): $75-78/barrel
- 1-year forward: $72-85/barrel

**Rationale**:
1. **OPEC+ Production Stable**: No announced cuts beyond existing quotas
2. **No Major Supply Shocks**: All key facilities (Persian Gulf, North Sea) operational
3. **Demand Moderate**: Global growth ~2.5%, not strong enough to spike oil
4. **US Strategic Petroleum Reserve**: Currently not releasing (unlike 2022)

**Confidence Level**: MEDIUM (70%)

**Price Scenarios**:
| Scenario | Price | Probability | Impact on Fuel CPI |
|----------|-------|-------------|---|
| Low Case | <$60/barrel | 15% | -2.0% to -2.5% |
| Base Case | $70-85 | 70% | 0% to +0.5% |
| High Case | >$100 | 15% | +1.5% to +2.0% |

**Geopolitical Trigger Points** (could violate assumption):
1. **Iran Strait Closure**: 20% of global oil passes through Strait of Hormuz
   - Probability: 5-10% (Houthi attacks ongoing but limited)
   - Impact: +$15-30/barrel immediately

2. **OPEC+ Production Cuts**: Saudi Arabia/OPEC announce additional cuts
   - Probability: 10-15% (have cut before)
   - Impact: +$10-20/barrel

3. **US-Iran Conflict**: Escalation in Middle East tensions
   - Probability: 3-5% (low, but non-zero)
   - Impact: +$30-50/barrel (extreme scenario)

4. **Global Recession**: Economic downturn reduces demand sharply
   - Probability: 5-8% (not expected but possible)
   - Impact: -$15-25/barrel

**Monitoring Protocol**:
1. **Weekly**: Track Brent crude spot prices (Bloomberg, FRED, EIA websites)
2. **Threshold Alerts**:
   - If Brent >$90/barrel for 2 consecutive weeks: Alert UPSIDE risk
   - If Brent <$65/barrel for 2 consecutive weeks: Alert DOWNSIDE risk
3. **Trigger Events**: Monitor news for:
   - Iran/US tensions escalation
   - OPEC+ meeting announcements
   - Refinery outages/accidents
   - Hurricane season impacts on Gulf production
4. **Update Frequency**: Monthly review, weekly during volatile periods

**Data Sources**:
- Weekly: EIA Petroleum Status Report (Thursdays)
- Daily: ICE Brent Crude Futures (NYMEX data)
- Real-time: Bloomberg Terminal, Yahoo Finance

**Impact Calculation**:
```
Fuel Inflation Sensitivity = 0.15-0.20 pp per $10/barrel change
(6% basket weight × 2-3% change per $10 barrel)

Example: Oil rises from $75 to $95 (+$20):
Expected fuel inflation increase: +0.30 to +0.40 pp
```

---

#### Assumption 3: Monsoon Rainfall (CRITICAL ASSUMPTION)

**Stated Assumption**:
- 2025 Southwest Monsoon rainfall: NORMAL (85-95 cm June-September)
- Long-term average: 88.7 cm
- Historically: Range 68-110 cm (50-year data)

**IMD Forecast** (Available April 2025):
- Official forecast issued in early April 2025
- Typically 70-75% accurate (within ±5% of prediction)
- Will be incorporated into updated forecasts

**Current Expectations** (as of Feb 2026):
- La Niña conditions: Moderate (could enhance monsoon)
- Indian Ocean Dipole: Neutral (could enhance monsoon)
- Sea surface temperatures: Favorable for normal monsoon
- **Probability Assessment**:
  - Normal (85-95 cm): 65%
  - Below normal (<80 cm): 20%
  - Above normal (>95 cm): 15%

**Rationale**:
1. **Climate Indices**: ENSO, IOD currently favorable
2. **Long-term Trends**: Monsoons have been normal-to-strong last 5 years
3. **Year-over-year**: 2024 was strong (97 cm), 2023 was normal (98 cm)

**Confidence Level**: MEDIUM-HIGH (60-70%)

**Monsoon Categories & Food Inflation Impact**:

| Rainfall | Category | Probability | Food Inflation | CPI Impact |
|----------|----------|-------------|---|---|
| <70 cm | Severe Drought | 5% | +5.0% to +7.0% | +2.25% to +3.15% |
| 70-80 cm | Poor | 15% | +2.0% to +4.0% | +0.90% to +1.80% |
| 80-95 cm | Below Normal | 20% | 0% to +1.5% | 0% to +0.67% |
| 95-105 cm | Normal | 50% | -0.5% to +0.5% | -0.22% to +0.22% |
| 105-115 cm | Good | 15% | -1.5% to -2.0% | -0.67% to -0.90% |
| >115 cm | Excess | 5% | -2.5% to -3.5% | -1.12% to -1.57% |

**Lag Effect & Timing**:
- **June-July 2025**: Monsoon rains fall on fields
- **August-September 2025**: Fresh harvest begins to arrive in markets
- **Impact Peak**: September-October 2025 (2-3 month lag)
- **Carryover**: Persists through November-December (storage effects)

**Forecast Impact**:
- Base case assumes Normal → Food deflation -0.5% to -1.0% in Aug-Sep
- Poor monsoon → Food inflation +2.0% to +3.0% instead → Net swing -3.0 to -4.0 pp

**Critical Monitoring Dates**:
1. **April 1-15, 2025**: IMD official monsoon forecast
2. **June 1-30, 2025**: Monsoon onset tracking
3. **July 1-31, 2025**: Monsoon in-progress monitoring (rainfall vs normal)
4. **August 1-15, 2025**: Early assessment if above/below normal
5. **September 1-30, 2025**: Peak monsoon month - critical for projections

**Monitoring Protocol**:
1. **Official Source**: IMD (Indian Meteorological Department)
   - Website: www.imdpune.gov.in
   - Weekly monsoon reviews (available publicly)
2. **Weekly Metrics**:
   - Cumulative rainfall Jun-Aug vs historical average
   - Number of rainy days (should be 60-80 days for normal)
   - Spatial distribution (shouldn't be concentrated in 1-2 areas)
3. **Threshold Alerts**:
   - If Jun-Jul rainfall <75% of normal: Escalate to POOR monsoon scenario
   - If Jun-Jul rainfall >110% of normal: Escalate to GOOD monsoon scenario
4. **Market Indicators** (early warning):
   - Vegetable prices: If stay high through August (>150% of normal), monsoon weak
   - Electricity demand: If falling Aug-Sep, suggests adequate water (good monsoon)
   - Farmer sentiment indices (NABARD surveys)

**Linked Scenarios**:
- This is the PRIMARY assumption driving scenario divergence
- Base case assumes Normal → 0.19% average inflation
- Optimistic case assumes Good monsoon → -0.25% average (deflation)
- Pessimistic case assumes Poor monsoon → +1.68% average (high inflation)

---

#### Assumption 4: Global Trade & Currency

**Stated Assumption**:
- Indian Rupee: 83-85 per USD (stable)
- No major tariff wars or trade disruptions
- Global supply chains remain functional
- Import costs stable (no major duty changes)

**Current Context** (Feb 2026):
- Rupee: 83.8-84.2 per USD
- RBI FX reserves: $630 billion (ample coverage)
- Capital flows: Positive (FII inflows continue)
- Trade deficit: Narrow (within comfort zone)

**Rationale**:
1. **Strong FX Position**: $630B reserves = 10 months of imports
2. **Positive Current Account**: Services and remittances strong
3. **RBI Active**: Intervenes smoothly to prevent sharp moves
4. **Global Context**: No major currency wars anticipated

**Confidence Level**: HIGH (80%)

**Rupee Impact on Inflation**:
```
Rupee Depreciation Sensitivity:
- 1 Re weaker (to 85 from 84) → Import inflation +0.1-0.15 pp
- 5 Re weaker (to 88 from 84) → Import inflation +0.5-0.75 pp

Example: If rupee weakens to 86 (vs assumed 84):
Oil import cost impact: +3% on fuel inflation
Other imports impact: +1-2% on machinery, raw materials
```

**Scenarios**:
| Rupee | Probability | Impact | Implication |
|-------|---|---|---|
| 81-83 | 10% | Appreciation (good) | Disinflationary -0.2 pp |
| 83-85 | 70% | Baseline (assumed) | No additional impact |
| 85-87 | 15% | Moderate depreciation | Inflationary +0.3 pp |
| 87-90 | 5% | Severe depreciation | Inflationary +0.8 pp |

**Triggers for Rupee Weakness**:
1. **Fed Hiking Cycle Resumes**: If US interest rates rise sharply
2. **India-China Trade War**: Escalation could capital outflows
3. **Monsoon Failure**: Poor monsoon might force imports (food grains)
4. **Gold Price Spike**: High gold imports widen CAD

**Monitoring Protocol**:
1. **Daily**: Rupee spot rate (NSE FX market, 9:15 AM-3:30 PM IST)
2. **Weekly**: Reserve Bank forex management (RBI website)
3. **Monthly**: Current account deficit trends (MOSPI, RBI releases)
4. **Threshold Alerts**:
   - If rupee >85.5: Depreciation warning
   - If rupee <83: Appreciation (recalibrate import inflation)
5. **Linked to Fed**: Monitor US Fed funds rate (affects capital flows)

---

### A.2: Policy & Structural Assumptions

#### Assumption 5: Government Policy Continuity

**Stated Assumption**:
- No major GST rate changes in forecast period
- No new large subsidies or their removal
- Food policy: Current PDS (Public Distribution System) continues
- Fuel subsidy: Current stance maintained (minimal subsidy)
- No emergency price controls imposed

**Current Status** (Feb 2026):
- GST rates: Stable at 5%, 12%, 18%, 28% (no recent changes)
- Food subsidy: ~80,000 cr/year (stable budget allocation)
- Fuel subsidy: Minimal (0-5% of cost, passed through to consumers)
- Price controls: Only on select essential (LPG regulated, not capped)

**Rationale**:
1. **Fiscal Situation**: Government has room but not unlimited
2. **Political Calendar**: General elections last completed Nov 2024, next in 2029
3. **International Commitment**: India's WTO commitments limit subsidies
4. **RBI Coordination**: Government unlikely to contradict RBI inflation target

**Confidence Level**: HIGH (85%)

**Potential Policy Changes** (5-15% probability):
1. **Excise Duty Hike on Fuel**: Government might increase revenue
   - Impact: +0.1-0.2 pp on fuel inflation
   - Probability: 10% (fiscal pressure could force this)

2. **Food Subsidy Increase**: If monsoon fails, might need more procurement
   - Impact: Disinflationary (buffers market supply)
   - Probability: 20% (depends on monsoon)

3. **GST Rate Reduction on Essentials**: Political pressure if inflation high
   - Impact: -0.1 to -0.2 pp (rare, but possible)
   - Probability: 5%

4. **Price Controls on Vegetables**: If food inflation spikes
   - Impact: Creates shortages (worse long-term)
   - Probability: 5% (government usually avoids)

**Monitoring Protocol**:
1. **Budget Announcements**: Track fiscal announcements
2. **Parliamentary Questions**: Monitor if inflation becomes political issue
3. **GST Council Meetings**: Check scheduled GST rate changes
4. **PRS India**: Legislative tracking website for bills on essential goods
5. **RBI Statements**: Coordination between RBI and government

---

#### Assumption 6: Agricultural Production & Supply Chains

**Stated Assumption**:
- Agricultural infrastructure maintained (cold chains, warehouses)
- No major pest/disease outbreaks (locust, powdery mildew)
- Supply chains remain functional (transport, distribution)
- Government buffer stocks available for releases (10-15 MMT)

**Current Status** (Feb 2026):
- Food grains buffer stock: 42 MMT (adequate)
- Cold chain capacity: Improving (NABARD investments)
- Supply chain: Normalized post-COVID
- No major agricultural crisis ongoing

**Confidence Level**: HIGH (85%)

**Agricultural Risks** (15% collective probability):
1. **Locust Swarms**: Occurred in 2019-2020
   - Probability: 3-5% (cyclical, but rare)
   - Impact: Crop damage in affected areas
   - CPI Impact: +0.5-1.0% food inflation for 2-3 months

2. **Plant Diseases**: e.g., powdery mildew on grapes, rust on wheat
   - Probability: 5-8% (common but usually localized)
   - Impact: Regional crop loss
   - CPI Impact: +0.2-0.5% if widespread

3. **Cold Chain Failure**: Major facility breakdown (earthquake, fire)
   - Probability: 2-3% (infrastructure disaster)
   - Impact: Short-term supply disruption
   - CPI Impact: +0.3-0.8% temporary spike

4. **Transportation Disruption**: Highway closures, strikes
   - Probability: 5-10% (occur periodically)
   - Impact: Localized price spikes
   - CPI Impact: +0.1-0.3%

**Monitoring Protocol**:
1. **Government Crop Estimates**: MOSPI releases 4x/year
2. **Agricultural Meteorology**: IMD agricultural forecasts
3. **Market News Service**: Daily agricultural prices (AGMARKNET)
4. **Pest Surveillance**: NCIPM (National Centre for Integrated Pest Management)
5. **Buffer Stock Levels**: Published by DFPD (Dept of Food & Public Distribution)

---

### A.3: External Shocks Not Modeled

**Important Caveat**:

The forecast CANNOT predict and is NOT designed to handle unprecedented shocks. These include:

1. **Pandemics**: Another COVID-like lockdown would invalidate entire forecast
2. **War/Geopolitical**: Major India-Pakistan conflict, China aggression would reshape inflation
3. **Natural Disasters**: 1-in-100 year earthquake, tsunami, extreme weather
4. **Financial Crisis**: Global banking collapse, stock market crash of 50%+
5. **Structural Policy Shifts**: Government announces mandatory price controls, major GST overhaul

**Probability**: Collectively <2% in 12-month period
**Mitigation**: Scenario analysis provides ranges; not point estimates

---

## PART B: COMPREHENSIVE RISK FACTORS

### Risk Factor 1: Poor Monsoon (HIGHEST PRIORITY)

**Risk Profile**:
- **Severity**: HIGH (2-3 pp CPI impact possible)
- **Probability**: 20-25% (historical frequency ~1 in 5 years)
- **Timing**: Decision point June-July 2025, impact Aug-Oct 2025
- **Mitigation Capability**: MEDIUM (government can release buffer stocks)

**Detailed Analysis**:

**Poor Monsoon Definition**:
- Rainfall <80 cm (vs 88.7 cm average)
- Occurs in 20% of years
- Last occurrence: 2015 (67 cm), 2014 (60 cm)
- Before that: 2004 (79 cm)

**Mechanism**:
1. **July 2025**: Insufficient rains
2. **August 2025**: Farmers realize crop shortage likely
3. **September-October 2025**: Harvest abundant vegetable crops fail (tomato, onion)
4. **Market Response**: Prices spike 30-50% for affected crops
5. **Inflation Peak**: Oct-Dec 2025 see food inflation 3-5%

**CPI Impact Calculation**:

```
Food inflation in normal monsoon: -0.5% to +0.5% (post-monsoon)
Food inflation in poor monsoon: +2.0% to +4.0% (supply shortage)
Swing: +2.5 to +4.5 percentage points

Food weight: 45% of CPI
CPI Impact: 0.45 × 2.5 to 4.5 = +1.1 to +2.0 pp

Example: Base case Jan 2026 forecast 1.71%, poor monsoon could push to 3.7%+
```

**Historical Precedent**:

| Year | Monsoon (cm) | Rainfall Status | Food Inflation (Aug-Oct Avg) | Headline Inflation |
|------|---|---|---|---|
| 2004 | 79 | Poor | 4.2% | 5.8% |
| 2014 | 60 | Severe Drought | 5.5% | 6.5% |
| 2015 | 67 | Severe Drought | 4.8% | 6.2% |
| 2023 | 98 | Normal | -0.5% | 6.3% (base effect) |
| 2024 | 97 | Normal | 0.8% | 1.3% (Dec trough) |

**Government Mitigation Measures**:

1. **Buffer Stock Release** (effective):
   - Current: 42 MMT available
   - Can release 5-10 MMT into markets
   - Effect: Moderate price increase instead of spike
   - CPI impact reduction: -0.5 to -1.0 pp

2. **Import Liberalization** (effective):
   - Remove tariffs on pulses (common tool)
   - Fast-track imports from neighbors
   - Effect: Partial price offset
   - CPI impact reduction: -0.2 to -0.4 pp

3. **Farmer Support** (less effective for inflation):
   - MSP guarantees (doesn't help consumers)
   - Crop insurance payouts
   - Effect: Protects farmer income, not inflation

4. **Export Promotion** (counterproductive):
   - Encourage exports to raise prices (for farmers)
   - Effect: Worsens domestic shortage/inflation
   - Used during severe droughts only

**Monitoring & Early Warning System**:

**Stage 1: April-May 2025 (Advance Alert)**
- IMD issues official monsoon forecast (early April)
- If forecast <85 cm: Flag as ELEVATED RISK
- Market checks: Seed purchases, farmer sentiment surveys
- Decision point: Update forecasts with poor monsoon scenario

**Stage 2: June-July 2025 (In-Progress Tracking)**
- Weekly IMD monsoon reviews published
- Cumulative rainfall vs historical tracking
- Spatial distribution (which areas getting rain)
- Weekly updates: If <70% of normal by mid-July → Poor monsoon likely

**Stage 3: August 2025 (Confirmation & Action)**
- Crop condition surveys (NASS equivalent)
- Vegetable prices starting to spike?
- Farmer distress reports
- Government announces buffer stock release plans

**Stage 4: September-October 2025 (Peak Impact)**
- Harvest data (official estimates from MOSPI)
- Actual food inflation readings (weekly WPI, monthly CPI)
- Adjust full-year forecasts based on actual impact

**Update Protocol**:
- If monsoon confirmed poor by August 1: Immediately revise forecasts to pessimistic scenario
- Quantitative update: +1.0 to +1.5 pp to remaining forecast

---

### Risk Factor 2: Crude Oil Prices >$100/barrel

**Risk Profile**:
- **Severity**: MEDIUM (0.3-0.5 pp CPI impact per $10 above $80)
- **Probability**: 15-20% (geopolitical dependent)
- **Timing**: Could happen anytime, immediate 1-2 month impact
- **Mitigation Capability**: LOW (RBI cannot control global commodity prices)

**Detailed Analysis**:

**Oil Price >$100 Scenarios**:

| Trigger | Probability | Timeline | Oil Price Impact |
|---------|---|---|---|
| OPEC+ cuts announced | 10% | 2-3 months | $80→$90-95 |
| Iran tensions escalate | 5% | 1-2 months | $80→$100-110 |
| Supply accident (refinery fire) | 3% | Immediate | $80→$95-105 |
| Hurricane season damage (Gulf) | 5% | Sep-Oct 2025 | $80→$88-92 |

**CPI Impact Transmission**:

```
Oil price increase: $80/bbl → $100/bbl (+$20, +25%)
Fuel inflation increase: 0% → +1.5% (estimated)
Fuel weight: 6% of CPI
CPI impact: 0.06 × 1.5% = +0.09 pp direct

Indirect impacts:
- Transport costs (logistics): +0.05-0.10 pp
- Petroleum-based products (plastics, chemicals): +0.05 pp
- Total impact: +0.20 to +0.25 pp
```

**Risk vs. Upside**:
- Low probability (15%) but material impact
- Asymmetric risk (upside from high oil, downside from low oil)
- Hedge possible (diversify imports, strategic reserves)

**Geopolitical Monitoring**:

1. **Middle East Tensions**:
   - Iran-US relations (Trump administration focus 2025)
   - Yemen Houthi attacks (ongoing but moderate)
   - Saudi Arabia internal politics
   - Israel-Palestine escalation risk

2. **OPEC+ Decisions**:
   - Quarterly meetings (Jan, Apr, Jun, Oct, Dec 2025)
   - Saudi Arabia de-facto leader
   - Russia inclusion (geopolitical wildcard post-Ukraine)
   - Expected: Maintenance of current quotas

3. **Refinery Capacity**:
   - Global capacity utilization: 85-90% (tight)
   - Maintenance season (spring/fall)
   - Outage risk: 2-3% annually

**Early Warning Indicators**:

**Weekly Tracking**:
- Brent crude spot price (ICE Brent contract)
- WTI/Brent spread (indicates supply/demand stress)
- OPEC+ basket (reference price)

**Red Flags**:
- Brent >$90 for 2+ weeks: Escalate to HIGH alert
- Brent >$100 for 1+ week: CRITICAL alert, update forecast immediately
- Iran-US military incidents: Heightened geopolitical risk
- Saudi/UAE statements on production: Monitor closely

**Monitoring Sources**:
- EIA Weekly Petroleum Status Report (Thursdays)
- OPEC Monthly Oil Market Report
- Platts (energy pricing index)
- Reuters/Bloomberg news wires

**Mitigation Actions**:
1. Strategic Petroleum Reserve release (if needed)
2. Fuel subsidy increased (fiscal cost)
3. Consumer rationing (extreme case only)
4. RBI may accept higher inflation target temporarily

---

### Risk Factor 3: Strong Monsoon / Excess Supply

**Risk Profile**:
- **Severity**: MEDIUM (but positive, not negative)
- **Probability**: 15-20% (opposite of poor monsoon)
- **Timing**: Aug-Oct 2025
- **Mitigation Capability**: MEDIUM (can promote exports)

**Detailed Analysis**:

**Strong Monsoon Definition**:
- Rainfall >100 cm (vs 88.7 cm)
- Occurs in 20% of years
- Recent examples: 2023 (98 cm), 2024 (97 cm) - both good
- Before: 2019 (110 cm), 2018 (117 cm)

**Mechanism**:
1. **July-August 2025**: Abundant rains, farmers excited
2. **September 2025**: Massive harvest, vegetable glut
3. **October-November 2025**: Market oversupply, prices collapse
4. **Food Deflation**: -2.0% to -3.0% for 2-3 months

**CPI Impact**:
```
Food inflation in strong monsoon: -2.0% to -3.0%
Food weight: 45% of CPI
CPI impact: 0.45 × (-2.5) = -1.1 to -1.4 pp

Example: Base case Jan 2026 forecast 1.71%, strong monsoon could drop to 0.3%+
```

**Farmer Impact** (negative, despite "good" monsoon):
- Prices collapse 30-50% post-harvest
- Farmers' incomes fall (despite bumper harvest)
- Government must purchase at MSP to prevent distress
- Policy challenge: Balance consumer deflation vs farmer income

**Government Response**:
1. **Procurement**: Buy excess at Minimum Support Price (MSP)
   - Effect: Supports farmer, limits deflation
   - Government stores inventory
   - Inflation impact mitigation: +0.3-0.5 pp (intentional)

2. **Exports**: Promote agricultural exports
   - Relieve domestic supply pressure
   - Effect: Limit deflation further
   - Inflation impact mitigation: +0.2-0.3 pp

3. **Storage**: Increase warehouse inventory
   - Preserves supply for lean months
   - Effect: Prevents oversupply-induced deflation
   - Inflation impact mitigation: +0.1-0.2 pp

**Probability Calculation**:
- Based on climate indices (ENSO, IOD)
- La Niña conditions: Enhance monsoon (currently present)
- Probability: 20-25% of strong monsoon

**Monitoring**:
- IMD forecast will give probability of excess rainfall (April 2025)
- If IMD says >90% rainfall: Escalate to OPTIMISTIC scenario
- Rainfall tracking Jun-Aug: >110% of normal → Strong monsoon confirmed

---

### Risk Factor 4: Wage Growth Acceleration

**Risk Profile**:
- **Severity**: LOW-MEDIUM (0.2-0.4 pp impact if severe)
- **Probability**: 10-15% (labor market dependent)
- **Timing**: Gradual (6-month lag from when tightness appears)
- **Mitigation Capability**: MEDIUM (RBI can tighten policy)

**Detailed Analysis**:

**Current Wage Growth** (Jan 2026):
- Overall wage growth: 3-4% YoY (moderate)
- IT sector: 5-6% (tight labor market)
- Healthcare: 4-5% (growing demand)
- Education: 4-5% (quality improvement)
- Manufacturing: 3-4% (moderate)

**Services Sector Vulnerability**:
- Health, education, transport account for 20% of CPI
- Labor-intensive (wages 40-50% of costs)
- Hard to automate (unlike manufacturing)
- Rising living standards (workers expect raises)

**Wage Growth Scenario**:

| Wage Growth | Probability | Timeline | Core Inflation Impact |
|---|---|---|---|
| Current (3-4%) | 60% | Baseline | 3.5% (stable) |
| Moderate (4-5%) | 25% | 6-month lag | 3.7-3.8% |
| High (5-6%) | 10% | 6-month lag | 4.0-4.2% |
| Very High (>6%) | 5% | 6-month lag | 4.5%+ |

**Triggers for Wage Growth Acceleration**:

1. **Labor Shortage**: Unemployment rate falls below 3.5%
   - Current unemployment: ~3.8% (PLFS data)
   - At risk: Skilled categories (IT, healthcare)
   - Probability: 10% of reaching <3.5%

2. **Demand Surge**: GDP growth accelerates >8%
   - Current growth: ~6-7%
   - RBI forecasts: 6.5-7.0% for next 2 years
   - Unlikely spike, but possible
   - Probability: 5-10%

3. **Migration-driven Tightness**: Workers move to high-wage cities
   - Remote work migration patterns
   - Probability: Ongoing gradual process (5-8% annually)

4. **Global Wage Pressure**: International firms bid up salaries
   - Currently: Strong (IT wages being set by global market)
   - Probability: 15-20% of accelerating further

**Inflation Transmission Mechanism**:

```
Month 1: Wage growth increases to 5% (tight labor market)
  ↓
Months 2-3: Service providers negotiate higher wages/rates
  ↓
Months 4-6: Higher labor costs embedded in service inflation
  ↓
Months 6-9: CPI reflects higher health, education, transport costs
  ↓
Result: Core inflation rises from 3.5% to 4.0%
```

**Monitoring Metrics**:

1. **Unemployment Rate** (monthly PLFS data):
   - Target threshold: <3.5% signals wage pressure
   - Current: 3.8% (still adequate buffer)
   - Frequency: Published monthly by NSO

2. **Wage Growth Indices**:
   - Wage indices by sector (varies by ministry)
   - IT wage tracker (from consultant reports)
   - Healthcare wage surveys (from IAMAI)
   - Frequency: Quarterly or annual

3. **Job Vacancy Rates**:
   - LinkedIn jobs vs applicants ratio
   - Government placement statistics
   - Frequency: Real-time (continuous)

4. **Service Price Inflation**:
   - Health inflation separately tracked
   - Education inflation separately tracked
   - If these accelerate 4.5%+: Wage pressure likely
   - Frequency: Monthly CPI releases

**Update Protocol**:
- If unemployment falls below 3.5% for 3 months: Flag as WAGE PRESSURE risk
- If health/education inflation >4.5% for 2 months: Update forecast +0.2 pp

---

### Risk Factor 5: Supply Chain Shock (Low Probability, High Impact)

**Risk Profile**:
- **Severity**: HIGH (if occurs, 1-2 pp impact possible)
- **Probability**: 5-10% (rare but precedent exists)
- **Timing**: Varies (geopolitical dependent)
- **Mitigation Capability**: LOW (global forces)

**Detailed Analysis**:

**Historical Examples of Supply Shocks**:

| Event | Date | Impact | Duration |
|---|---|---|---|
| Suez Canal Blockage (Ever Given) | Mar 2021 | 6-week cargo delays | 2-3 weeks |
| Strait of Malacca tensions | Ongoing | Risk premium on shipping | Ongoing |
| Ukraine War (grain exports blocked) | Feb 2022 | Food prices +20%+ | 6+ months |
| COVID-19 (container shortage) | 2020-2022 | Shipping costs 10x | 2 years |
| US-China Trade War (tariffs) | 2018-2020 | Goods inflation | Periodic |

**Potential Shocks for 2025-2026**:

1. **Suez Canal Disruption** (2% probability):
   - Probability: Low (Ever Given incident unlikely again)
   - But: Red Sea tensions (Houthis) ongoing
   - Shipping diversion adds 5-7 days, 15-20% cost
   - Impact: Transport inflation +0.5-1.0% for 1-2 months

2. **India-China Trade Escalation** (3% probability):
   - Border tensions ongoing (Ladakh)
   - Could trigger import/export restrictions
   - Impact: Goods inflation +1.0-2.0%, supply tightness
   - Risk: Geopolitical, hard to quantify

3. **US-India Trade Friction** (2% probability):
   - Trump administration (2025-2029): More protectionist stance
   - Risk: Tariffs on Indian IT services, pharma
   - CPI impact: +0.2-0.5% (indirect)

4. **Port/Harbor Disruption** (2% probability):
   - Labor strikes (happened in 2022 at some ports)
   - Natural disaster (cyclone damage in Gujarat/Maharashtra)
   - Impact: Localized supply disruption, 1-2 month recovery

**Quantifying Supply Chain Shock Impact**:

```
Example: Suez Canal closure adds 15-20% shipping cost
Import share of final goods: ~15% of CPI
Pass-through: 50% of cost increase (some absorbed by importers)
Impact: 0.15 × 0.175 × 0.5 = 0.01 pp

But if shock is severe (affecting 30% of imports):
Impact: 0.30 × 0.175 × 0.75 = 0.04 pp

Cumulative supply chain shock: +0.1 to +0.4 pp
```

**Monitoring & Alerts**:

1. **Shipping Cost Indices**:
   - Baltic Exchange Container Index (public data)
   - Shanghai Containerized Freight Index
   - Alert: If index rises >20% in month

2. **Geopolitical Risk Tracker**:
   - Monitor Suez Canal traffic (AIS shipping data)
   - Red Sea security bulletins (shipping advisories)
   - India-China border situation (defense ministry)

3. **Trade Policy News**:
   - US trade announcements (Trump admin)
   - India commerce ministry statements
   - WTO dispute cases

4. **Port Congestion Data**:
   - Port Trust statistics (major Indian ports)
   - Vessel waiting times (shipping agencies)

---

### Risk Factor 6: Crude Oil <$60/barrel

**Risk Profile**:
- **Severity**: LOW-MEDIUM (but positive - deflationary)
- **Probability**: 10-15% (global demand destruction)
- **Timing**: Varies
- **Mitigation Capability**: N/A (beneficial shock)

**Detailed Analysis**:

**Oil <$60 Scenarios**:

| Trigger | Probability | Timeline | Oil Price Impact |
|---|---|---|---|
| Global recession begins | 5% | 6-12 months | $80→$40-50 |
| EV adoption accelerates | 3% | Gradual (2025+) | $80→$65-70 |
| OPEC+ production surge | 2% | 2-3 months | $80→$55-65 |
| Tech breakthrough (renewable) | 1% | Medium-term | $80→$50 |

**Mechanism**:

1. **Global Recession** (most likely trigger):
   - GDP growth turns negative (not imminent but possible)
   - Oil demand falls 5-10% (demand destruction)
   - Prices collapse to $40-50/barrel
   - CPI impact: -0.5 to -0.8 pp

2. **EV Adoption**:
   - Electric vehicles now 10% of sales globally (rising 20%+ annually)
   - By 2030: Could be 30-40% of sales
   - Marginal impact on oil prices: -$2-5/barrel
   - CPI impact: Gradual -0.05 to -0.10 pp annually

3. **Supply Surge**:
   - Saudi Arabia increases production to gain market share
   - Less likely (OPEC typically restricts)
   - If happens: -$15-20/barrel
   - CPI impact: -0.1 to -0.15 pp

**Impact on Forecast**:

```
Oil falls from $75 to $55 (-$20, -26%)
Fuel deflation: From -1.5% to -2.5% (additional -1.0%)
CPI impact: 0.06 × (-1.0%) = -0.06 pp
(Modest impact due to already-low fuel inflation)
```

**Policy Implication**:
- If oil <$60 + strong monsoon: Could see sustained deflation
- RBI would need to cut rates to support growth
- Fiscal stimulus acceptable if demand falls

**Monitoring**:
- Track Brent crude weekly
- Alert if <$70 for 2+ weeks
- Monitor global recession indicators (US unemployment, PMI)

---

## PART C: SENSITIVITY ANALYSIS

### Sensitivity to Key Assumptions

**Methodology**: Change one assumption at a time, measure CPI impact

#### Sensitivity 1: Monsoon Impact

**Base Case**: Normal monsoon → Food inflation -0.5% (Aug-Oct avg)

```
Monsoon Sensitivity Table:
                  Food Inflation    CPI Impact    Comment
Severe Drought    +5.0%             +2.1 pp      Worst case
Poor             +2.5%             +1.1 pp      20% probability
Normal           -0.5%             -0.2 pp      Base case (50%)
Good             -2.0%             -0.9 pp      20% probability
Excess           -3.5%             -1.6 pp      Rare (5%)

Range: +2.1 pp to -1.6 pp = 3.7 pp spread
```

**Implication**: Monsoon is THE critical variable. ±1.5 pp swing possible.

---

#### Sensitivity 2: Oil Price Impact

**Base Case**: Oil $75/bbl → Fuel inflation 0%

```
Oil Price Sensitivity:
Oil Price    Fuel Inflation    CPI Impact    vs Base
$50/bbl      -2.0%            -0.12 pp      -0.12 pp
$60/bbl      -1.5%            -0.09 pp      -0.09 pp
$75/bbl      0.0%             0.00 pp       Base
$90/bbl      +1.0%            +0.06 pp      +0.06 pp
$100/bbl     +1.5%            +0.09 pp      +0.09 pp
$120/bbl     +2.5%            +0.15 pp      +0.15 pp

Range: -0.12 pp to +0.15 pp = 0.27 pp spread
```

**Implication**: Oil matters but less than monsoon. ±0.1 pp typical impact.

---

#### Sensitivity 3: Rupee Depreciation Impact

**Base Case**: Rupee 84 per USD

```
Rupee Sensitivity:
Rupee Rate    Import Inflation    CPI Impact    vs Base
81            +0.5%               -0.15 pp      (appreciation)
82            +0.2%               -0.05 pp
84            0.0%                0.00 pp       Base
86            +0.3%               +0.10 pp
88            +0.8%               +0.25 pp
90            +1.5%               +0.50 pp

Range: -0.15 pp to +0.50 pp = 0.65 pp spread
```

**Implication**: Rupee has moderate impact. ±0.2 pp typical in normal times.

---

#### Sensitivity 4: Wage Growth Impact

**Base Case**: Core wage growth 3-4% → Core inflation 3.5%

```
Wage Growth Sensitivity (6-month lag):
Core Wage Growth    Core Inflation    CPI Impact (via 20% weight)
2.0%               3.0%              -0.10 pp
3.0%               3.2%              -0.06 pp
4.0%               3.5%              0.00 pp      Base
5.0%               3.8%              +0.06 pp
6.0%               4.1%              +0.12 pp
7.0%               4.5%              +0.20 pp

Range: -0.10 pp to +0.20 pp = 0.30 pp spread
```

**Implication**: Wage growth has small-medium impact. ±0.1 pp typical.

---

#### Sensitivity 5: Policy Rate Impact

**Base Case**: RBI holds repo at 6.5%

```
Policy Rate Sensitivity (3-6 month lag):
Repo Rate    Expected Inflation Impact    CPI Change
6.0%         Slightly lower (more lending) +0.15 pp
6.5%         Base case                    0.00 pp
7.0%         Slightly higher (less lending) -0.10 pp
7.5%         Higher restrictive effect    -0.20 pp
8.0%         Strong restriction           -0.35 pp

Range: +0.15 pp to -0.35 pp = 0.50 pp spread
```

**Implication**: Policy rate has medium impact. ±0.2 pp per 50 bps change.

---

#### Combined Sensitivity Analysis

**Scenario**: Multiple assumptions change simultaneously

```
WORST CASE (all negatives):
- Poor monsoon: +1.1 pp
- Oil >$100: +0.15 pp
- Rupee depreciates to 88: +0.25 pp
- Wage growth accelerates: +0.12 pp
- RBI tightens: -0.10 pp (offsetting)
TOTAL: +1.5 pp (additive)

BEST CASE (all positives):
- Strong monsoon: -0.9 pp
- Oil <$60: -0.09 pp
- Rupee appreciates to 82: -0.05 pp
- Wage growth slows: -0.06 pp
- RBI cuts rates: +0.15 pp (neutral)
TOTAL: -1.0 pp (additive)

Base case: 0.19% average
Worst case range: +1.5 pp above base = 1.7% average
Best case range: -1.0 pp below base = -0.8% average
```

**Implication**: Model has ±1.5 pp range due to assumption uncertainty alone.

---

## PART D: MONITORING FRAMEWORK & UPDATE PROTOCOLS

### Real-Time Monitoring Dashboard

**Recommended Dashboard Components**:

```
Dashboard Layout:
┌─────────────────────────────────────────────────────────┐
│  INFLATION FORECAST MONITORING DASHBOARD                │
│  Last Updated: [Date] | Next Update: [Date]             │
├─────────────────────────────────────────────────────────┤
│ CURRENT STATUS:                                          │
│  • Latest CPI: 4.26% (Jan 2025)                         │
│  • Forecast: 0.19% average (Feb-Jan)                    │
│  • RBI Target: 4% ± 2% (2-6% band)                      │
├─────────────────────────────────────────────────────────┤
│ KEY RISK INDICATORS:                                     │
│ ┌─ MONSOON RISK          ──────────────────────────┐   │
│ │ Status: MONITORING (Apr forecast pending)       │   │
│ │ Alert Threshold: <75% of normal by mid-July     │   │
│ │ Current: N/A (forecast available April 2025)    │   │
│ └────────────────────────────────────────────────┘    │
│ ┌─ OIL PRICE RISK        ──────────────────────────┐   │
│ │ Status: GREEN ($75-80/bbl)                      │   │
│ │ Alert Thresholds: >$90 (YELLOW), >$100 (RED)   │   │
│ │ Current: $76/bbl (Brent, as of [date])         │   │
│ │ Trend: Stable (avg $74-78 last 4 weeks)        │   │
│ └────────────────────────────────────────────────┘    │
│ ┌─ RUPEE RISK            ──────────────────────────┐   │
│ │ Status: GREEN (83.8-84.2/USD)                   │   │
│ │ Alert Thresholds: >85.5 (YELLOW), >87 (RED)    │   │
│ │ Current: 84.1/USD (as of [date])                │   │
│ │ Trend: Stable (narrow range)                    │   │
│ └────────────────────────────────────────────────┘    │
│ ┌─ WAGE GROWTH RISK      ──────────────────────────┐   │
│ │ Status: GREEN (3-4% YoY, loose labor market)    │   │
│ │ Alert Threshold: Unemployment <3.5% for 3m      │   │
│ │ Current: 3.8% (last PLFS reading)              │   │
│ │ Trend: Stable, no immediate pressure           │   │
│ └────────────────────────────────────────────────┘    │
├─────────────────────────────────────────────────────────┤
│ FORECAST TRACK RECORD:                                  │
│  • Jan 2025 Actual: 4.26%                              │
│  • Jan 2025 Forecast: 4.28%                            │
│  • Error: -0.02% (within 80% CI) ✓                     │
├─────────────────────────────────────────────────────────┤
│ NEXT CRITICAL DATES:                                    │
│  • Feb 7, 2026: RBI MPC meeting (rate decision)        │
│  • Feb 20, 2026: Jan 2025 CPI release (final P revision)│
│  • Mar 31, 2026: Feb 2025 CPI release                  │
│  • Apr 1-15, 2026: IMD Monsoon forecast                │
│  • Jun 1-30, 2026: Monsoon onset monitoring            │
└─────────────────────────────────────────────────────────┘
```

### Weekly Monitoring Checklist

**Every Friday (or next business day)**:

- [ ] Check Brent crude prices (weekly average vs threshold)
- [ ] Monitor rupee spot rate (NSE FX)
- [ ] Scan economic news for geopolitical developments
- [ ] Review government policy announcements
- [ ] Check if any RBI/government officials made statements on inflation

**Monthly Checklist** (around 15th of each month):

- [ ] CPI release published (MoSPI website)
- [ ] Compare actual vs forecast
- [ ] Update forecast track record
- [ ] Extract latest component inflation rates
- [ ] Assess if any assumptions violated
- [ ] Update dashboard with new data

**Quarterly Checklist** (end of each quarter):

- [ ] Review RBI MPC meeting outcome
- [ ] Assess wage growth trends (from surveys)
- [ ] Check monsoon forecast (if applicable)
- [ ] Update long-term assumptions if needed
- [ ] Prepare forecast revision if major changes detected

**Annual Checklist** (Feb 2026, then Feb 2027):

- [ ] Full model re-estimation with new data
- [ ] Validate assumptions for coming year
- [ ] Prepare updated report
- [ ] Stakeholder communications

### When to Trigger Forecast Update

**Mandatory Update Triggers**:

1. **Monsoon Forecast Released** (April 2025):
   - If <80 cm: Immediately revise to poor monsoon scenario
   - Quantitative change: Food inflation +1.0-1.5 pp from Jun onward
   - If >100 cm: Revise to strong monsoon scenario
   - Quantitative change: Food inflation -1.0-1.5 pp from Jun onward

2. **Oil Prices** (weekly monitoring):
   - If Brent >$95 for 2 consecutive weeks: Alert YELLOW (escalated risk)
   - If Brent >$105 for 1 week: Alert RED (update forecast immediately)
   - Quantitative change: +0.10-0.15 pp fuel inflation per $10/barrel above $85

3. **RBI Rate Change** (after MPC meetings):
   - If rate change announced: Update forecast with 6-month lag
   - Cut: Expect slightly higher inflation (more lending) in 6 months
   - Hike: Expect slightly lower inflation (less lending) in 6 months

4. **Actual CPI Misses** (if CPI release deviates >0.5 pp from forecast):
   - Review components for causes
   - If systematic bias detected: Revise model
   - Update forecast for remaining period

5. **External Shock** (any black swan):
   - War, pandemic, natural disaster
   - Policy shock (major GST change, controls)
   - Trade war escalation
   - Market dislocation (>10% stock fall, currency crisis)

**Optional Triggers** (can update but not required):

- Wage growth indices show unexpected acceleration
- Government policy announcement (non-emergency)
- Seasonal factor revisions (small impact)
- Model parameter re-estimation (quarterly)

### Forecast Revision Protocol

**When an Update is Triggered**:

1. **Assess Magnitude of Change**:
   - Is it material (>0.3 pp impact)? If yes, proceed with update.
   - Is it small (<0.1 pp impact)? If yes, wait for accumulation.

2. **Identify Affected Components**:
   - Which CPI groups are affected?
   - What's the timeline of impact?
   - Are there second-order effects?

3. **Quantify Impact**:
   - Calculate per-month impact
   - Update each month's forecast
   - Recalculate average and range

4. **Document Change**:
   - Note trigger event and date
   - Record assumption that changed
   - Show before/after forecasts
   - Explain rationale

5. **Communicate Update**:
   - Prepare updated report
   - Highlight changes in executive summary
   - Distribute to stakeholders
   - Archive previous version

### Stakeholder Communication Protocol

**Monthly Update** (15-20th of each month):
- Brief email with CPI release summary
- Highlight if forecast track record improved/worsened
- One-page dashboard update

**Quarterly Report** (end of quarter):
- Full forecast update with all changes
- Risk assessment refresh
- Stakeholder implications summary
- 2-3 page executive summary

**Major Event Update** (as triggered):
- Immediate alert if material shock (e.g., oil spike, monsoon failure)
- One-page summary of impact
- Updated forecast with scenarios
- Recommendations for policy/planning

**Annual Report** (Feb 2026, Feb 2027):
- Comprehensive annual inflation analysis
- Forecast review and track record
- Coming year forecast and risks
- 10-20 page detailed report

---

## PART E: VALIDATION & BACKTESTING

### Historical Forecast Accuracy

**2024 Forecast (Made in Dec 2023)** (if available):
```
Actual 2024 average: 3.12%
Forecast (made Dec 2023): ~3.5%
Error: -0.38 pp (slightly high)
Range capture: Yes, actual fell within 80% CI
```

**2025 Forecast Validation** (as we go through year):
- Record actual monthly inflation as released
- Compare to forecast each month
- Calculate rolling MAPE (Mean Absolute Percentage Error)
- Assess if confidence intervals are appropriately calibrated

**Planned Backtesting** (for Feb 2027 report):
- 24-month accuracy assessment
- Component-level accuracy
- Scenario accuracy (did actual match one scenario?)
- Recalibration of model parameters if systematic bias detected

---

## PART F: KEY DEFINITIONS & GLOSSARY

**Terms used in this framework**:

- **CPI**: Consumer Price Index, base year 2012 = 100
- **Headline Inflation**: YoY change in overall CPI
- **Core Inflation**: CPI excluding food and fuel (more stable)
- **pp (percentage point)**: Unit of difference (4% - 3% = 1 pp difference)
- **Monsoon**: Southwest Monsoon, June-September, brings 75% of annual rain
- **MSP**: Minimum Support Price, government floor price for farm products
- **SARIMA**: Seasonal ARIMA model for time series forecasting
- **Confidence Interval (CI)**: Range around forecast where actual likely to fall
- **MAPE**: Mean Absolute Percentage Error, forecast accuracy metric
- **WPI**: Wholesale Price Index, measurement of producer inflation
- **PLFS**: Periodic Labour Force Survey, employment statistics

---

**End of Comprehensive Risk Assessment Document**

This framework provides actionable monitoring, clear update protocols, and realistic acknowledgment of uncertainty. Use this to stay prepared for various inflation outcomes while maintaining credible communication with stakeholders.
