# India Air Pollution Data Sources

**Date:** 2025-11-15
**Project:** Epic Emitters - Air Pollution Tracker
**Focus:** India-specific data sources for emissions, violations, and air quality

---

## Executive Summary

India has a comprehensive ecosystem of government, academic, and crowdsourced air pollution data. The Central Pollution Control Board (CPCB) is the primary government authority managing air quality monitoring and industrial emissions tracking through multiple portals and systems. While data availability is extensive, API access is limited compared to US/international sources, and violation/enforcement data has transparency challenges.

**Key Finding:** India has deployed continuous emissions monitoring systems (OCEMS) for 17 categories of highly polluting industries, providing real-time industrial emissions data. However, public access to this data is inconsistent across states, with significant data gaps (60-80% missing data in some cases).

---

## 1. Government Air Quality Monitoring Data

### Central Pollution Control Board (CPCB)

#### National Air Quality Index
- **Portal:** https://app.cpcbccr.com/AQI_India/
- **Alternative:** https://cpcb.nic.in/National-Air-Quality-Index/
- **Coverage:** Real-time AQI from monitoring stations across India
- **Pollutants Monitored:**
  - PM2.5 (Particulate Matter < 2.5 μm)
  - PM10 (Particulate Matter < 10 μm)
  - SO2 (Sulfur Dioxide)
  - NO2 (Nitrogen Dioxide)
  - CO (Carbon Monoxide)
  - O3 (Ozone)

#### Central Control Room (CCR) Dashboard
- **Portal:** http://app.cpcbccr.com/ccr/
- **Data Available:**
  - Continuous Ambient Air Quality Monitoring Stations (CAAQMS) data
  - Advanced search and download functionality
  - Hourly/daily data by station and pollutant
- **Limitations:**
  - Limited download capacity (1 week for 15-min data per station/pollutant)
  - No public API currently available
  - Requires manual download

#### Open Government Data (OGD) Platform
- **Portal:** https://data.gov.in/
- **Resources:**
  - Real-time Air Quality Index: https://data.gov.in/resource/real-time-air-quality-index-various-locations
  - Historical Daily Data: https://data.gov.in/catalog/historical-daily-ambient-air-quality-data
  - CPCB Datasets: https://data.gov.in/ministrydepartment/Central%20Pollution%20Control%20Board

#### API Access via data.gov.in
- **API Endpoint Example:** `https://api.data.gov.in/resource/3b01bcb8-0b14-4abf-b6f2-c1bfd384ba69`
- **Authentication:** API key required (get from data.gov.in dashboard after login)
- **Output Format:** JSON (can be converted to CSV)
- **Parameters:**
  - `api-key`: Your API key
  - `format`: json
  - `limit`: Number of records
  - `filters[city]`: Filter by city name
  - `filters[pollutant_id]`: Filter by pollutant type (PM10, PM2.5, etc.)

**Example API Request:**
```
https://api.data.gov.in/resource/3b01bcb8-0b14-4abf-b6f2-c1bfd384ba69?api-key=YOUR_API_KEY&format=json&limit=100&filters[city]=Delhi&filters[pollutant_id]=PM2.5
```

**Status:** ⚠️ API for real-time air quality index does not currently exist; requires request via "Request API" button on data.gov.in

#### APISetu - Government API Platform
- **Portal:** https://directory.apisetu.gov.in/api-collection/cpcb
- **Description:** Open API Platform from Ministry of Electronics and IT
- **Purpose:** Enable swift, transparent, safe information sharing
- **Status:** CPCB API collection listed, but direct access details limited (403 errors on direct access attempts)

### State Pollution Control Boards (SPCBs)

Each state has its own SPCB with varying levels of data availability:

#### Examples:
- **Maharashtra:** https://mpcb.gov.in/
- **Delhi:** Delhi Pollution Control Committee (DPCC)
- **Assam:** https://www.pcbassam.org/

**Key Systems:**
- **OCMMS (Online Consent Management and Monitoring System):** https://ocmms.nic.in/
  - Manages industry compliance
  - Issues environmental clearances
  - Tracks consent to operate/establish

- **Parivesh Portal:** https://parivesh.nic.in/
  - Environmental, forest, wildlife, and CRZ clearances
  - Online submission and monitoring of proposals
  - Tracks environmental clearances granted

---

## 2. Industrial Emissions Monitoring

### OCEMS (Online Continuous Emission Monitoring Systems)

#### Background
- Supreme Court directive (2017): All 17 categories of highly polluting industries must install OCEMS
- Real-time emissions/effluent monitoring with connectivity to SPCBs and CPCB servers
- Data must be displayed on publicly accessible OCEMS web portals

#### Data Access
- **OCEMS Live Data:** https://cpcb.nic.in/ocems-live-data/
- **OCEMS Data Visualization:** https://cpcb.nic.in/ocems7/
- **OCEMS Data Submission:** https://cpcb.nic.in/ocems4/
- **RTDMS (Real-Time Data Management System):** https://rtdms.cpcb.gov.in/

#### API for Data Submission
- CPCB provides API Version 1.0 for Technology Providers for Data Submission (TPDS)
- **Purpose:** For equipment suppliers/technology providers to submit emissions data
- **Access:** Requires industry code from CPCB
- **Limitation:** API designed for submission, not public data retrieval

#### Coverage and Limitations

**17 Categories of Highly Polluting Industries:**
- Power plants
- Refineries
- Cement manufacturing
- Steel plants
- Pulp & paper
- Fertilizers
- Petrochemicals
- Sugar
- Distilleries
- And others

**Data Quality Issues (per CEEW research):**
- ⚠️ **60% of small industries** violate pollution limits
- ⚠️ **81% (2019) and 77% (2020)** of stacks had >1,000 hours of missing data (~42 days)
- ⚠️ Only **37 out of 691 stacks** (2020) had zero instances of missing data >72 hours
- ⚠️ Only **20 out of 32 states/UTs** had publicly accessible OCEMS portals (as of Dec 2021)
- ⚠️ Only **9 of 20 portals** provided historical data >1 month
- ⚠️ Only **6 of 9 portals** allowed data download

**Key Insight:** While OCEMS infrastructure exists, data completeness and public accessibility remain major challenges.

---

## 3. Violations and Enforcement Data

### Regulatory Framework

#### Environmental Laws and Penalties
- **Environment Protection Act (EPA):**
  - Imprisonment: 5-7 years
  - Fine: Up to ₹100,000
  - Or both

- **Air (Prevention and Control of Pollution) Act:**
  - First offense: Up to ₹10,000 fine
  - Continuing offense: Additional ₹5,000/day
  - Imprisonment: Up to 6 years with fine

- **Recent Changes (November 2024):**
  - Decriminalization of certain violations
  - Replacement of imprisonment with monetary penalties for specific offenses

#### Enforcement Authorities
- Central Pollution Control Board (CPCB)
- State Pollution Control Boards (SPCBs)
- National Green Tribunal (NGT)
- Appellate Authority

### Available Enforcement Data

#### Public Databases
⚠️ **Limited Availability** - Unlike the US EPA ECHO system, India does not have a comprehensive, centralized public database of violations and enforcement actions.

**What's Available:**
1. **CPCB Annual Reports:**
   - Portal: https://cpcb.nic.in/
   - Content: Summary of enforcement actions, major cases
   - Format: PDF reports (not structured data/API)
   - Example: https://cpcb.nic.in/openpdffile.php?id=... (Annual Report 2020-21)

2. **State-Level Enforcement Orders:**
   - Published by individual SPCBs (inconsistent)
   - Example: Haryana SPCB enforcement orders at https://hspcb.org.in/
   - Format: Individual PDF documents

3. **National Green Tribunal (NGT) Orders:**
   - Major environmental cases and penalties
   - Notable examples:
     - Sterlite copper plant closure (Tamil Nadu)
     - Vedanta ₹100 crore fine (2019) for pollution breaches
   - Access: Through NGT website and news reports

4. **OCMMS Compliance Records:**
   - Consent to operate/establish status
   - Portal: https://ocmms.nic.in/
   - Access: Requires authorization, not fully public

**Key Gap:** No comprehensive API or searchable database of facility-level violations, enforcement actions, and penalties comparable to EPA ECHO.

### Compliance Challenges

According to research:
- Pollution control boards often lack capacity and resources for strict monitoring
- 60% of small industries in violation of limits
- Selective penalization even when failed test reports available
- Enforcement is inconsistent across states

---

## 4. US Embassy Air Quality Monitoring

### Coverage
US Embassy and Consulates monitor PM2.5 at:
- **New Delhi** (US Embassy)
- **Mumbai** (US Consulate)
- **Kolkata** (US Consulate)
- **Chennai** (US Consulate)
- **Hyderabad** (US Consulate)

### Data Access

#### Official Portal
- **Website:** https://in.usembassy.gov/embassy-consulates/new-delhi/air-quality-data/
- **Data:** NowCast Air Quality Index (AQI) based on PM2.5
- **Algorithm:** US EPA's NowCast algorithm
- **Update Frequency:** Real-time

#### API Access via AQICN (World Air Quality Index)
- **Delhi:** https://aqicn.org/city/india/new-delhi/us-embassy/
- **Mumbai:** https://aqicn.org/city/india/mumbai/us-consulate/
- **API Endpoint Examples:**
  - Delhi: https://aqicn.org/data-platform/api/H7024
  - Mumbai: https://aqicn.org/data-platform/api/H7020
- **API Docs:** https://aqicn.org/api/

#### Historical Data
- **AQICN Platform:** Download daily AQI for all 5 US consulate locations
- **GitHub Archive (2013-2016):** https://github.com/maelle/usaqmindia
- **OpenAQ (August 2016+):** https://openaq.org/ (also ropenaq for R users)

**Advantages:**
- ✅ High data quality (US EPA standards)
- ✅ Reliable uptime
- ✅ API access available
- ✅ Historical data accessible

**Limitations:**
- ⚠️ Only 5 locations
- ⚠️ Only PM2.5 (no other pollutants)
- ⚠️ Compound-level monitoring (not city-wide)

---

## 5. Academic and Research Institutions

### UrbanEmissions.Info

#### Overview
- **Website:** https://urbanemissions.info/
- **Description:** Comprehensive data repository for energy, emissions, and air pollution analysis in India
- **Maintained by:** Independent air quality research group

#### Available Data

**1. India Ambient Monitoring Data:**
- **Portal:** https://urbanemissions.info/india-air-quality/india-ambient-monitoring-data/
- **Coverage:** Annual summaries (2013-2021)
- **Data:** Air quality monitoring network data compiled from CPCB, CAAQMS, SAFAR
- **Format:** Downloadable datasets with documentation

**2. Reanalyzed PM2.5 Concentrations:**
- **Portal:** https://urbanemissions.info/india-air-quality/india-satpm25/
- **Coverage:** Indian Subcontinent, 1998-2022
- **Resolution:** 0.1° grid resolution (~11 km)
- **Source:** Satellite-based reanalysis
- **Use Case:** Historical PM2.5 trends, spatial analysis

**3. Delhi-Specific Data:**
- **Time Series:** https://urbanemissions.info/delhi-india/delhi-ambient-monitoring-data-timeseries/
- **Box Plots:** https://urbanemissions.info/delhi-india/delhi-ambient-monitoring-data-boxplots/
- **DPCC Archived Data:** Available by emailing simair@urbanemissions.info
- **Coverage:** Delhi Pollution Control Committee data from 6 continuous monitoring stations

**Advantages:**
- ✅ Well-documented datasets
- ✅ Long-term historical data
- ✅ Spatial coverage (grid data)
- ✅ Quality-controlled reanalysis

### IIT Delhi - CERCA

#### Overview
- **Organization:** Arun Duggal Centre of Excellence for Research in Climate Change and Air Pollution
- **Website:** https://cerca.iitd.ac.in/
- **Established:** February 16, 2018
- **Purpose:** Climate change and air pollution research

#### Available Data
- **AQI Data Portal:** https://cerca.iitd.ac.in/category/aqi-data
- **Research Data:** PM2.5 elemental, organic, and black carbon fractions
- **Studies:** Source apportionment, pollution forecasting
- **Publications:** https://cas.iitd.ac.in/publication (Centre for Atmospheric Sciences)

#### Key Projects
- Real-time source apportionment study for Delhi
- COVID-19 lockdown air quality analysis
- Collaboration with IISER Mohali, TERI, IIT-Kanpur

### IIT Madras / IITM (Indian Institute of Tropical Meteorology)

#### Emissions Inventory
- **Lead:** IITM Pune, with TERI collaboration
- **2022 Emissions Inventory:**
  - Fine spatial resolution: 500m × 500m
  - Previous IITM SAFAR: 2km × 2km resolution
  - Use: Pollution forecasting

#### Research Focus
- PROMOTE (APHH) project
- Air quality modeling
- Delhi pollution studies (chloride-rich particles research)

**Access:** Research publications, conference papers; raw data typically requires collaboration/request

---

## 6. Crowdsourced and Low-Cost Sensor Networks

### PurpleAir in India

#### NASA Citizen Science Project
- **Locations:** Delhi (urban), Hamirpur (rural north), Bengaluru (urban south)
- **Partnership:** NASA Air Quality Citizen Science project
- **Deployment:** Networks in Delhi and Indo-Gangetic Plain
- **Data Access:** https://www2.purpleair.com/ and https://aqicn.org/network/purpleair/

#### Research Validation
- Study: "Seasonally optimized calibrations improve low-cost sensor performance" (2023)
- **Finding:** Lower-cost sensors can fill critical data gaps in India
- **Challenge:** India has sparse regulatory monitoring; low-cost sensors help
- **Validation:** Collocation with reference beta attenuation monitors

#### Data Quality
- Calibration needed for accurate readings
- Seasonally optimized models improve performance
- Public API available through PurpleAir platform

### IQAir Community

- **Website:** https://www.iqair.com/air-quality-community
- **Description:** World's largest air quality community
- **Coverage:** Includes India locations
- **Data:** Crowdsourced air quality monitoring
- **Access:** Public air quality map, mobile app

### Other Initiatives

- **Mobile Apps:** Pollution reporting apps (similar to Bhuvan Ganga for water)
- **Social Media:** Twitter, Flickr used for passive crowdsourcing of environmental events
- **Local Networks:** Community-led sensor deployments in pollution hotspots

**Advantages:**
- ✅ Fills gaps in government monitoring
- ✅ Real-time data availability
- ✅ Community engagement
- ✅ Cost-effective scaling

**Limitations:**
- ⚠️ Variable data quality
- ⚠️ Requires calibration
- ⚠️ Coverage depends on community participation
- ⚠️ May not measure regulatory compliance parameters

---

## 7. Commercial Air Quality APIs

### AQICN (World Air Quality Index)

- **Website:** https://aqicn.org/map/india/
- **Coverage:** 100+ countries including major Indian cities
- **API:** https://aqicn.org/api/
- **Data:** Real-time AQI from government and crowd-sourced sensors
- **Sources:** CPCB stations, US Embassy, PurpleAir, others
- **Access:** Free and commercial tiers
- **Output:** JSON, real-time and historical data

**Example Cities Covered:**
- Delhi: https://aqicn.org/city/delhi/
- Mumbai, Bangalore, Chennai, Kolkata, Hyderabad, and many others

### Ambee API

- **Website:** https://www.getambee.com/api/air-quality
- **Service:** Air Quality API with India coverage
- **Data Available:**
  - Real-time AQI
  - PM2.5, PM10, NO2, CO, SO2, O3
  - Historical records
  - Forecasts and insights
  - Pollen, fire, and other environmental data

**Query Methods:**
- By city name (e.g., "Bangalore")
- By coordinates (lat/lon)
- Bulk requests

**Commercial:** Paid API service with free trial

### AQI.in

- **Website:** https://www.aqi.in/
- **Coverage:** Real-time air pollution for Indian cities
- **Cities:** Delhi (https://www.aqi.in/in/dashboard/india/delhi), Mumbai, Bangalore, Chennai, and others
- **Data Display:** AQI dashboard, charts, historical graphs
- **API:** Not clearly documented; primarily a visualization platform

---

## 8. Data Gaps and Challenges for India

### Major Gaps

#### 1. Violation and Enforcement Data ⚠️
- **No centralized public database** like EPA ECHO
- State-level enforcement orders scattered across SPCB websites
- No API or structured data access
- Historical compliance records not publicly available
- Penalty and fine information not systematically tracked

#### 2. OCEMS Data Accessibility ⚠️
- Only 20/32 states have public OCEMS portals
- Only 6 states allow historical data download
- 60-80% of data missing for many facilities
- No unified national OCEMS API for public access
- Requires state-by-state navigation

#### 3. Real-Time Air Quality API ⚠️
- data.gov.in API for real-time AQI does not currently exist
- Must rely on third-party aggregators (AQICN, Ambee)
- Government portals require manual downloads
- Limited programmatic access to official data

#### 4. Facility-Level Attribution
- Industrial emissions data (OCEMS) doesn't easily link to ambient air quality
- No integrated system showing "which facility is affecting which neighborhood"
- Ownership data not always public
- Facility names/identifiers inconsistent across systems

#### 5. Health Impact Data
- No integrated health outcome database linked to pollution exposure
- Must rely on academic studies and WHO guidelines
- Local health department data not publicly accessible
- No facility-specific health impact assessments

### Data Quality Issues

- **Missing Data:** 60-80% gaps in OCEMS monitoring
- **Selective Enforcement:** Not all violations result in penalties
- **Reporting Lag:** Government data often has weeks/months delay
- **Inconsistent Standards:** State-level variation in data quality and accessibility
- **Limited Historical Archives:** Many portals only show recent data

### Transparency Challenges

- **Limited Public Access:** Many systems require authorization
- **No Open APIs:** Most government data requires manual download
- **Fragmented Systems:** Data scattered across CPCB, SPCBs, OCMMS, Parivesh, etc.
- **Format Issues:** PDFs instead of structured data in many cases

---

## 9. Recommended Data Integration Strategy for India

### Tier 1: Primary Data Sources (Use These First)

#### For Facility-Level Emissions:
1. **Climate Trace API** - Global coverage including India
   - Facility locations, emissions by pollutant, super emitter identification
   - Best available source for comprehensive facility-level data

#### For Real-Time Air Quality:
1. **AQICN API** - Aggregates CPCB + US Embassy + crowdsourced data
   - Easiest API access
   - Good city coverage
   - Historical data available

2. **data.gov.in API** (when available)
   - Official government source
   - Requires API key
   - Currently limited availability

#### For Historical Analysis:
1. **UrbanEmissions.Info** - Curated datasets
   - 1998-2022 PM2.5 reanalysis
   - Annual summaries 2013-2021
   - Well-documented, quality-controlled

### Tier 2: Supplementary Data Sources

#### For High-Quality Urban Monitoring:
1. **US Embassy Data via AQICN**
   - Delhi, Mumbai, Kolkata, Chennai, Hyderabad
   - Most reliable PM2.5 data
   - API access available

#### For Crowdsourced Data:
1. **PurpleAir Network**
   - Real-time community sensors
   - Fills monitoring gaps
   - Public API

#### For Industrial Emissions (when accessible):
1. **State OCEMS Portals**
   - Check state-by-state availability
   - Download where possible
   - Supplement Climate Trace data

### Tier 3: Manual/Research Sources

#### For Violations (limited):
1. **CPCB Annual Reports** - Summary enforcement data
2. **NGT Orders** - Major cases and penalties
3. **News Monitoring** - Track major pollution incidents and enforcement

#### For Academic Context:
1. **IIT Delhi/CERCA publications**
2. **IITM research reports**
3. **UrbanEmissions.Info blog and analysis**

### Workarounds for Data Gaps

#### Violation Data (Since No ECHO Equivalent):
- **Approach 1:** Focus on emissions data (Climate Trace) + air quality exceedances
- **Approach 2:** Identify facilities exceeding WHO/national standards based on emissions
- **Approach 3:** Use news scraping for major enforcement actions
- **Approach 4:** Show "compliance status unknown" for India vs. "compliance history" for US

#### Real-Time Data (Limited Official API):
- **Approach 1:** Use AQICN API as primary source
- **Approach 2:** Integrate PurpleAir for real-time citizen data
- **Approach 3:** Supplement with Ambee API (commercial)
- **Approach 4:** Web scraping of CPCB dashboards (backup option, less reliable)

#### OCEMS Data (Inconsistent Access):
- **Approach 1:** Rely on Climate Trace for facility-level emissions
- **Approach 2:** State-by-state manual downloads for priority cities
- **Approach 3:** Partner with research institutions (CEEW, IIT) for processed OCEMS data
- **Approach 4:** Acknowledge limitations in UI ("Government monitoring data incomplete")

---

## 10. Implementation Recommendations for India

### User Experience Design

#### 1. Data Availability Transparency
Show users what data is/isn't available:
- ✅ "Emissions data from Climate Trace (2021-2025)"
- ✅ "Air quality from CPCB + US Embassy monitoring"
- ⚠️ "Violation data: Limited availability in India"
- ⚠️ "Some industrial emissions data missing"

#### 2. Phased Rollout by City
Start with cities having best data availability:
- **Phase 1:** Delhi, Mumbai (US Embassy + CPCB + good research data)
- **Phase 2:** Bangalore, Chennai, Kolkata, Hyderabad (US Embassy + CPCB)
- **Phase 3:** Other major cities (CPCB + Climate Trace)
- **Phase 4:** Smaller cities (Climate Trace primary)

#### 3. Comparative Context
For facilities:
- Show emissions relative to WHO guidelines
- Show exceedance of national ambient air quality standards
- Even without violation history, show "likely non-compliant" based on emissions

### Technical Implementation

#### Database Schema Extensions for India
```
India_Facilities (extends Facilities table)
├── cpcb_station_id
├── spcb_state
├── ocems_availability (boolean)
├── ocems_portal_url
├── parivesh_clearance_id
└── data_completeness_score (0-100%)

India_AirQuality
├── station_id
├── source (CPCB/US_Embassy/PurpleAir)
├── pollutant_type
├── value
├── timestamp
├── data_quality_flag
└── city

India_Enforcement (when available)
├── facility_id
├── enforcement_type (NGT/SPCB/CPCB)
├── date
├── description
├── source_url
└── penalty_amount (if available)
```

#### API Integration Priority
1. **Climate Trace** - Core facility data
2. **AQICN** - Real-time air quality
3. **data.gov.in** - When API becomes available
4. **UrbanEmissions.Info** - Historical context (manual download, cache)
5. **PurpleAir** - Crowdsourced real-time
6. **State OCEMS** - State-by-state (manual, as available)

#### Caching Strategy
- Cache Climate Trace data (updates monthly)
- Cache UrbanEmissions.Info data (updates annually)
- Refresh AQICN data every 1 hour
- Refresh PurpleAir every 10-30 minutes
- Pre-download data.gov.in datasets weekly

### Unique Value Propositions for India

1. **First Integrated View:**
   - Combine facility emissions (Climate Trace) + air quality (CPCB/US Embassy) + health context
   - No existing platform does this integration for India

2. **Transparency About Data Gaps:**
   - Show what's known vs. unknown
   - Educate users about monitoring limitations
   - Create demand for better government transparency

3. **Crowdsourced Validation:**
   - Allow users to report pollution incidents
   - Validate against official data
   - Build community around air quality monitoring

4. **Advocacy Tool:**
   - Help citizens identify super emitters near them
   - Provide data for RTI (Right to Information) requests
   - Support environmental litigation with data

---

## 11. Data Access Summary Table

| Data Source | Type | Coverage | API | Cost | Quality | Update Frequency |
|------------|------|----------|-----|------|---------|------------------|
| **Climate Trace** | Facility emissions | All India | ✅ Yes | Free | High | Monthly |
| **CPCB CAAQMS** | Air quality | 200+ stations | ⚠️ Limited | Free | Medium | Hourly |
| **data.gov.in API** | Air quality | National | ⚠️ Request needed | Free | High | Real-time* |
| **AQICN** | Air quality | Major cities | ✅ Yes | Freemium | High | Real-time |
| **US Embassy** | PM2.5 | 5 cities | ✅ (via AQICN) | Free | Very High | Real-time |
| **UrbanEmissions.Info** | Historical analysis | India-wide | ❌ Manual | Free | Very High | Annual |
| **OCEMS Portals** | Industrial emissions | 20/32 states | ⚠️ Varies | Free | Low-Medium | Real-time* |
| **PurpleAir** | Crowdsourced PM2.5 | Limited | ✅ Yes | Free | Medium | Real-time |
| **Ambee** | Air quality | India-wide | ✅ Yes | Paid | High | Real-time |
| **CPCB Reports** | Enforcement | National | ❌ PDFs | Free | Medium | Annual |
| **NGT Orders** | Major penalties | National | ❌ Manual | Free | High | Ad-hoc |

*Real-time = Claims real-time, but may have delays or gaps

---

## 12. Key Contacts and Resources

### Government Portals
- CPCB Main: https://cpcb.nic.in/
- CPCB ENVIS: https://cpcbenvis.nic.in/
- Open Government Data: https://data.gov.in/
- APISetu: https://directory.apisetu.gov.in/
- Parivesh: https://parivesh.nic.in/
- OCMMS: https://ocmms.nic.in/

### Research Organizations
- UrbanEmissions.Info: https://urbanemissions.info/
- IIT Delhi CERCA: https://cerca.iitd.ac.in/
- CEEW (Council on Energy, Environment and Water): https://www.ceew.in/
- TERI (The Energy and Resources Institute): https://www.teriin.org/

### International Resources
- US Embassy India Air Quality: https://in.usembassy.gov/embassy-consulates/new-delhi/air-quality-data/
- AQICN India: https://aqicn.org/map/india/
- WHO Air Quality Database: https://www.who.int/data/gho/data/themes/air-pollution

### For Data Requests
- CPCB archived data: Contact via cpcb.nic.in
- Delhi DPCC data: simair@urbanemissions.info
- State SPCB data: Contact individual state boards
- Academic collaborations: Reach out to IIT Delhi, IITM, CEEW

---

## 13. Next Steps for India Integration

1. **Set Up API Access:**
   - Register at data.gov.in for API key
   - Get AQICN API key
   - Test Climate Trace queries for Indian facilities
   - Explore PurpleAir API for Indian sensors

2. **Download Static Datasets:**
   - UrbanEmissions.Info historical PM2.5 data
   - CPCB annual summaries
   - WHO India air quality baselines

3. **State-by-State Assessment:**
   - Identify which states have accessible OCEMS portals
   - Prioritize states with major cities in Phase 1
   - Document download procedures for each

4. **Build India-Specific Features:**
   - City selection for Delhi/Mumbai/Bangalore
   - Comparison to Indian NAAQS (National Ambient Air Quality Standards)
   - Integration of Indian health guidelines (ICMR data if available)

5. **Community Engagement:**
   - Partner with Indian environmental NGOs
   - Engage with citizen science communities
   - Plan for user-reported data validation

---

## Conclusion

India presents both opportunities and challenges for the Epic Emitters project:

**Strengths:**
- Extensive monitoring infrastructure (CPCB, CAAQMS, OCEMS)
- Growing crowdsourced data (PurpleAir, citizen science)
- Strong academic research community
- Climate Trace provides global facility-level baseline

**Challenges:**
- Limited API access to official data
- No centralized violation/enforcement database
- Significant data quality and completeness issues
- Fragmented data across multiple systems
- Variable transparency across states

**Strategy:**
Focus on what's available (emissions data via Climate Trace, air quality via AQICN/CPCB, crowdsourced via PurpleAir), acknowledge limitations transparently, and position the app as a tool for transparency and advocacy rather than just information display.

The lack of violation data actually creates an opportunity: your app can highlight the transparency gap and empower citizens to demand better environmental monitoring and enforcement.
