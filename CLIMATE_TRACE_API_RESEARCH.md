# Climate Trace API Research Summary

**Date:** 2025-11-09
**Project:** Epic Emitters - Air Pollution Tracker

---

## Executive Summary

Climate Trace provides a comprehensive, free, and publicly available API that tracks emissions from 662 million sources globally, with monthly updates through August 2025. The API is currently in beta and provides detailed emissions data at the facility level, including geographic coordinates, pollutant types, and temporal trends.

**Key Finding:** Climate Trace released a groundbreaking air pollution tool in September 2025 that shows PM2.5 pollution plumes affecting 1.6 billion people across 2,500+ urban areas - perfectly aligned with your project goals.

---

## 1. Climate Trace API Capabilities

### API Access
- **Base URL:** `https://api.climatetrace.org/`
- **Documentation:** `https://api.climatetrace.org/v7/docs/index.html`
- **Status:** Beta (use with caution in production)
- **License:** Creative Commons 4.0 (free for all uses)
- **Data Coverage:** 2015-2025 (with ~2 month lag for most recent data)

### Core Endpoints
The API supports:
1. **Asset Search** - Search emitting facilities by:
   - Sector
   - Owner/organization
   - Geographic location

2. **Emissions Query** - Get detailed emissions data for specific assets/facilities

3. **Aggregated Data** - Country-level aggregated emissions

### Data Scale
- **1,813,558** emission sources tracked
- **662,637,077** underlying assets
- **9,560** PM2.5 sources visualized in urban areas
- **2,572** urban areas covered globally

---

## 2. Data Available for Your Project

### ✅ AVAILABLE - Emitter Information

#### Geographic Data
- Facility-level location coordinates
- City, country, and regional data
- Pollution plume visualization (new Sept 2025 feature)
- Coverage in 2,500+ urban areas worldwide

#### Pollutant & Emissions Data
- **Greenhouse Gases:**
  - Carbon dioxide (CO2)
  - Methane (CH4)
  - Nitrous oxide (N2O)

- **Air Pollutants:**
  - PM2.5 (particulate matter) - NEW
  - Co-pollutants harmful to human health - NEW

#### Temporal Data
- Annual emissions (2015-2024)
- Monthly emissions (2021-2025)
- Near real-time updates (2-month lag)

#### Facility Types Tracked
- Power plants
- Heavy manufacturing sites
- Ports and shipping
- Refineries
- Mines
- Oil & gas production
- Cement, aluminum, steel manufacturing
- Transportation (on-road, aviation, shipping, railways)
- Agriculture (crops and livestock)
- Buildings, waste, mineral extraction, forestry

#### Ownership Data
- Organization/company names (where available)
- Facility ownership information

#### "Super Emitters" Identification
Climate Trace identifies **super emitters** as facilities in the top 10% of PM2.5 sources by volume:
- 900 million people exposed to super emitter pollution
- These facilities play an outsized role in air quality impacts

---

## 3. Examples of Available Data

### Case Study: Houston, TX
- ~140 facilities tracked
- ~4 million people exposed to facility emissions

### Case Study: New York City
- Only US metro in top 10 globally for population exposure
- Detailed facility-level tracking available

### Global Coverage
- Highest concentrations in Asia (China, Korea, Japan)
- Comprehensive coverage of major urban areas worldwide

---

## 4. ⚠️ DATA GAPS - Not Available in Climate Trace

### Health Impact Data
Climate Trace does NOT provide:
- Specific health outcome predictions
- Disease/mortality attributions
- Individual health risk assessments
- Medical/epidemiological analysis

### Regulatory/Compliance Data
Climate Trace does NOT provide:
- Violation histories
- Enforcement actions
- Compliance records
- Regulatory penalties or fines
- Inspection records

### Real-time Air Quality
Climate Trace does NOT provide:
- Real-time air quality monitoring
- Current AQI (Air Quality Index) readings
- Short-term exposure forecasts
- Personal exposure monitoring

---

## 5. Additional Data Sources Needed

### For Health Impact Information

#### NASA SEDAC
- **What:** Air Quality Data for Health-Related Applications
- **Resolution:** 1-km spatial resolution
- **Data:** Annual average PM2.5 concentrations
- **Access:** Public, free
- **URL:** https://sedac.ciesin.columbia.edu/

#### WHO Air Quality Database
- **What:** Ground measurements of PM2.5
- **Coverage:** Global, updated every 2-3 years
- **Data:** Annual mean concentrations
- **Access:** Public, free
- **URL:** https://www.who.int/data/gho/data/themes/air-pollution

#### EPA Air Quality Data
- **What:** National-scale PM2.5 and ozone predictions
- **Coverage:** United States
- **Resolution:** High resolution monitoring data
- **Access:** Public API available
- **URL:** https://www.epa.gov/enviro/envirofacts-data-service-api

#### Health Impact Research
For translating pollutant exposure to health outcomes:
- WHO guidelines on PM2.5, ozone, NO2, SO2, CO
- CDC Tracking Network data
- Global Burden of Disease Study data (via World Bank)
- Academic literature on pollution-health relationships

### For Regulatory Compliance & Violations

#### EPA ECHO (Enforcement and Compliance History Online)
- **What:** Inspection, violation, and enforcement data
- **Coverage:** 800,000+ US facilities
- **Data Types:**
  - Clean Air Act violations
  - Clean Water Act violations
  - Resource Conservation and Recovery Act
  - Enforcement actions and penalties
  - Inspection records

- **Access Methods:**
  - **REST API:** JSON/XML output
    - Air Facility Search
    - Enforcement Case Search
    - Detailed Facility Reports
    - All Media Programs Search
  - **Bulk Downloads:** CSV format

- **Website:** https://echo.epa.gov/tools/web-services
- **API Docs:** https://www.epa.gov/enviro/envirofacts-data-service-api

#### EPA Envirofacts API
- **What:** RESTful API for all EPA data holdings
- **Output Formats:** JSON, CSV, Excel, XML, Parquet, PDF
- **Update Frequency:** Weekly
- **Coverage:** All EPA-regulated facilities

#### Citizen Reporting
- **EPA Violation Reporting:** https://echo.epa.gov/report-environmental-violations
- **National Response Center:** 1-800-424-8802 (emergencies)

### For Crowdsourced Data

#### Purple Air
- Cost-effective personal air quality sensors
- Real-time PM2.5 monitoring
- Community network of sensors
- Public API available

#### Citizen Science Platforms
- Water quality monitoring (e.g., Chesapeake Bay Project)
- Mobile apps for pollution reporting (e.g., Bhuvan Ganga)
- Social media data mining (Twitter, Flickr for environmental events)

---

## 6. Recommended Data Integration Strategy

### Core Data Layer (Climate Trace)
Use Climate Trace as your primary data source for:
1. Facility locations and identification
2. Emission quantities by pollutant type
3. Temporal trends (monthly updates)
4. Super emitter identification
5. Pollution plume visualization

### Supplementary Layer 1: Health Context
Integrate health impact data from:
1. **WHO guidelines** - Safe exposure thresholds
2. **EPA/NASA** - Local air quality context
3. **Academic research** - Health outcome relationships
4. **GBD data** - Population-level health burden estimates

### Supplementary Layer 2: Regulatory Context
Integrate compliance data from:
1. **EPA ECHO API** - Violation and enforcement history
2. **State environmental agencies** - Local compliance records
3. **Citizen reports** - Community-reported issues

### Supplementary Layer 3: Real-time Context
Consider integrating:
1. **Purple Air** - Current local air quality
2. **Government monitoring stations** - Official AQI readings
3. **Weather data** - Wind patterns, atmospheric conditions

---

## 7. Technical Recommendations

### API Integration
1. Start with Climate Trace API v7 for core emissions data
2. Implement caching (API is beta, keep requests low)
3. Use bulk downloads for historical analysis
4. Query APIs in this order to minimize external requests:
   - Climate Trace (facility data)
   - EPA ECHO (if US facility - violation data)
   - WHO/NASA (background health context - can be pre-loaded)

### Data Schema Design
Consider a database structure like:
```
Facilities
├── id (Climate Trace asset ID)
├── name
├── location (lat/lon)
├── sector
├── owner
└── super_emitter (boolean)

Emissions
├── facility_id
├── pollutant_type (CO2, CH4, N2O, PM2.5)
├── quantity
├── date (monthly)
└── confidence_level

Violations (if US facility)
├── facility_id
├── violation_type
├── date
├── enforcement_action
└── penalty

Health_Context (by location/pollutant)
├── pollutant_type
├── safe_threshold (WHO)
├── health_effects
└── risk_level

Pollution_Exposure
├── facility_id
├── affected_population
├── plume_geometry
└── urban_area
```

### Visualization Strategy
Based on your inspirations (bluecorridors.org, climatetrace.org/air-pollution):

1. **Interactive Map** (primary view)
   - Facility markers sized by emission volume
   - Color-coded by pollutant type or super-emitter status
   - Pollution plume overlays
   - User location input/detection

2. **Facility Detail Views**
   - Emission trends over time (line charts)
   - Pollutant breakdown (pie/bar charts)
   - Violation history timeline (if available)
   - Affected population radius

3. **Personal Impact View**
   - Distance from user to nearby emitters
   - Total exposure from all nearby sources
   - Health risk context
   - Pollutant-specific breakdowns

4. **Story/Narrative Elements**
   - Contextual explanations
   - Comparisons to safe thresholds
   - Local vs. global context
   - Actionable insights

---

## 8. Key Insights for Your Project

### Strong Alignments
✅ Climate Trace's September 2025 air pollution tool is **perfectly aligned** with your vision - it already visualizes pollution plumes affecting billions of people

✅ Data is **comprehensive and free** - no API fees, Creative Commons license

✅ **Facility-level granularity** - you can show specific emitters responsible for pollution

✅ **Monthly updates** - relatively current data (2-month lag)

✅ **Super emitter identification** - built-in ranking of worst polluters

### Challenges to Address
⚠️ **API is Beta** - may have availability issues, implement robust error handling

⚠️ **Health data separate** - you'll need to integrate multiple sources for health impact narrative

⚠️ **Violation data US-only** - EPA ECHO only covers US facilities; international compliance data harder to access

⚠️ **Real-time gap** - 2-month data lag means not showing "current" air quality

### Opportunities
💡 **Differentiate with regulatory context** - Climate Trace doesn't show violation history; adding EPA ECHO data makes your app unique

💡 **Personal impact calculator** - translate emissions data into "what this means for YOU" based on distance, wind patterns, exposure time

💡 **Community engagement** - integrate citizen reporting to supplement official data

💡 **Narrative storytelling** - Climate Trace provides data; you provide the human story and context

---

## 9. Next Steps

1. **Get API Access**
   - Visit https://api.climatetrace.org/v7/docs/
   - Review endpoint documentation
   - Test queries for your target locations
   - Download sample datasets

2. **Prototype Data Integration**
   - Start with Climate Trace as core
   - Add EPA ECHO for US facilities
   - Pre-load WHO health guidelines

3. **Design User Flow**
   - User enters location → show nearby emitters
   - User clicks facility → show detail + violations + health context
   - User explores map → discover super emitters

4. **Consider Technical Stack**
   - **Frontend:** React/Next.js (for interactive map)
   - **Mapping:** Mapbox GL JS or Leaflet
   - **Backend:** Node.js/Python (for API aggregation)
   - **Database:** PostgreSQL with PostGIS (for geospatial queries)
   - **Caching:** Redis (for Climate Trace responses)

---

## Resources

### Primary Documentation
- Climate Trace API: https://api.climatetrace.org/v7/docs/
- Climate Trace Data Downloads: https://climatetrace.org/data
- Climate Trace Air Pollution Tool: https://climatetrace.org/air-pollution

### Supplementary APIs
- EPA ECHO Web Services: https://echo.epa.gov/tools/web-services
- EPA Envirofacts API: https://www.epa.gov/enviro/envirofacts-data-service-api
- WHO Air Quality Database: https://www.who.int/data/gho/data/themes/air-pollution

### GitHub Resources
- Climate Trace Methodology: https://github.com/climatetracecoalition/methodology-documents
- Climate Trace API Examples: https://github.com/climatetracecoalition/public-api-examples (currently empty)

### Inspirational References
- Blue Corridors: https://bluecorridors.org/
- Climate Trace Air Pollution: https://climatetrace.org/air-pollution
