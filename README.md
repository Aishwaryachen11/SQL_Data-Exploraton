### GLOBAL COVID-19 IMPACT AND VACCINATION ANALYSIS

#### **1. Introduction**

The COVID-19 pandemic has had a profound impact on the global population, resulting in millions of cases and deaths. As countries and regions have responded differently to the pandemic, the outcomes have varied significantly. This analysis seeks to explore the spread of COVID-19, the effectiveness of mitigation measures, and the progress of vaccination campaigns around the world. By leveraging SQL queries to analyze global COVID-19 data, this project aims to provide insights into infection rates, mortality rates, and the percentage of populations vaccinated, thereby offering valuable information for policymakers, healthcare professionals, and researchers.

#### **2. Objectives**

The objectives of this project are:

Analyze Infection and Mortality Rates: To evaluate the severity of COVID-19 across different countries and continents by calculating infection rates and death percentages.
Assess Vaccination Progress: To examine the extent to which different populations have been vaccinated and understand how vaccination rates correlate with COVID-19 outcomes.
Identify High-Risk Regions: To identify countries and continents with the highest infection rates, death counts, and lowest vaccination rates.
Provide Actionable Recommendations: To offer recommendations for improving public health responses based on the data insights.

#### **3. Methodology**

**3.1 Data Sources**
Covid_Deaths.CovidDeaths: This table contains data on COVID-19 cases, deaths, and population metrics across various countries.
Covid_vaccinations.CovidVaccinations: This table includes data on COVID-19 vaccinations across different countries and continents.

**Dataset Description**
The datasets used in this analysis are focused on COVID-19 statistics which is taken from Our World in Data (https://ourworldindata.org/covid-deaths), including data on reported cases, deaths, and vaccination progress across different countries and continents. These datasets provide a comprehensive view of the pandemic's impact globally and are crucial for understanding the spread and control of the virus.

**1. Covid_Deaths.CovidDeaths**

This dataset contains detailed information about COVID-19 cases and deaths reported globally. The key attributes of this dataset include:

iso_code: The ISO 3166-1 alpha-3 code representing each country.

continent: The continent to which the country belongs.

location: The name of the country or region.

date: The date of the reported data.

total_cases: The cumulative number of confirmed COVID-19 cases up to that date.

new_cases: The number of new COVID-19 cases reported on that date.

total_deaths: The cumulative number of deaths attributed to COVID-19 up to that date.

new_deaths: The number of new deaths reported on that date.

population: The total population of the country or region.

population_density: The population density of the country or region (people per square kilometer).

median_age: The median age of the population.

aged_65_older: The percentage of the population aged 65 and older.

gdp_per_capita: The gross domestic product per capita.

life_expectancy: The average life expectancy in years.

hospital_beds_per_thousand: The number of hospital beds per 1,000 people.

human_development_index: The Human Development Index value, which measures a country's average achievements in health, knowledge, and standard of living.

**2. Covid_vaccinations.CovidVaccinations**

This dataset provides data on the vaccination efforts against COVID-19 across the world. The key attributes of this dataset include:

iso_code: The ISO 3166-1 alpha-3 code representing each country.

continent: The continent to which the country belongs.

location: The name of the country or region.

date: The date of the reported data.

total_vaccinations: The cumulative number of COVID-19 vaccine doses administered.

people_vaccinated: The cumulative number of people who have received at least one dose of a COVID-19 vaccine.

people_fully_vaccinated: The cumulative number of people who have been fully vaccinated (received all required doses).

new_vaccinations: The number of new vaccine doses administered on that date.

total_vaccinations_per_hundred: The total number of vaccinations per 100 people in the total population.

people_vaccinated_per_hundred: The number of people vaccinated per 100 people in the total population.

people_fully_vaccinated_per_hundred: The number of people fully vaccinated per 100 people in the total population.

population: The total population of the country or region.

stringency_index: A composite measure based on nine response indicators including school closures, workplace closures, and travel bans, rescaled to a value from 0 to 100 (100 = strictest).

**Data Sources and Credibility**
Both datasets are derived from global databases that aggregate and harmonize COVID-19 data from official government sources, international health organizations like the World Health Organization (WHO), and other reputable institutions. The data is updated regularly to ensure it reflects the most current information available.

**Purpose of the Datasets**
The datasets serve as a critical resource for analyzing the impact of COVID-19, tracking the progression of the pandemic, and evaluating the effectiveness of public health interventions, including vaccination campaigns. By analyzing these datasets, we can gain insights into the virus's spread, the effectiveness of containment measures, and the relationship between various demographic factors and COVID-19 outcomes.

**3.2 Analysis Steps**

Data Cleaning and Preparation:
Replace NULL values with zeros using COALESCE to ensure accurate calculations.
Handle potential division by zero cases in rate calculations.

Calculation of Infection and Mortality Rates:
Determine the percentage of populations infected by COVID-19.
Calculate the death percentage among confirmed COVID-19 cases for each country.

Vaccination Progress Analysis:
Calculate the cumulative number of people vaccinated in each country.
Determine the percentage of the population vaccinated over time.

Identifying High-Risk Regions:
Identify countries with the highest infection rates and death counts.
Examine continental trends in death counts and vaccination progress.

### **QUERY EXECUTION**
SQL Query was executed in Google Cloud, Big Query. 

You can view the results of the BigQuery query [here](https://console.cloud.google.com/bigquery?sq=891015959491:6dce298f69b84930b10767858997b1b8).

**Basic Data from CovidDeaths**
Argentina on 01-01-2020 with no cases or deaths recorded.
Afghanistan on 01-01-2021 with 51,526 total cases and 2,191 total deaths.
Insight: The sample shows that by January 2021, Afghanistan had a 4.25% death rate among confirmed cases, indicating a significant mortality impact. Argentina and Mexico show NaN values for early dates, likely due to no data being recorded at that time.

Afghanistan on 01-01-2021: 51,526 total cases, 0 new cases, 2,191 total deaths, population 38.93 million.
Algeria on 01-01-2021: 99,897 total cases, 287 new cases, 2,762 total deaths, population 43.85 million.
Insight: Afghanistan had stopped recording new cases on that specific date, possibly due to data reporting delays. Algeria continued to report new cases, with a relatively low increase indicating possible containment or underreporting.

**Total Cases and Deaths by Country:**
•	Death Percentage: This analysis shows the percentage of people who have died after contracting COVID-19 in different countries. A higher death percentage indicates either a more severe outbreak or potential issues in healthcare quality and access.
•	Country Comparisons: Countries with a significantly higher death percentage compared to others might indicate either a late response to the pandemic, overwhelmed healthcare systems, or population demographics (e.g., older populations).
•	Data Integrity: By using COALESCE, you ensure that the calculation is robust, even in the presence of missing or zero values, which can be critical in real-world data where such issues are common.

Afghanistan: 51,526 total cases, 2,191 deaths, 4.25% death rate.
Albania: 58,316 total cases, 1,181 deaths, 2.02% death rate.
Insight: Afghanistan's higher death percentage suggests a more severe outbreak or challenges in healthcare, while Albania shows a slightly lower death rate, indicating potentially better management or different demographic impacts.

Afghanistan: 51,526 total cases, 2,191 deaths, 4.25% death rate.
Algeria: 99,897 total cases, 2,762 deaths, 2.76% death rate.
Insight: Algeria, with a larger case count but lower death percentage compared to Afghanistan, might have had better healthcare infrastructure or more effective mitigation measures.

**2. Total Cases vs. Population**
•	Infection Rate: This analysis shows the percentage of the population infected with COVID-19 in each country. A higher percentage indicates widespread community transmission.
•	Public Health Response: Countries with a lower percentage of infected populations might have had more effective public health measures (e.g., lockdowns, mask mandates, vaccination drives).
•	Population Size Impact: The infection rate is particularly telling when comparing countries with similar population sizes, as it provides a clearer picture of the relative severity of the outbreak.

Afghanistan: 38.93 million population, 51,526 total cases, 0.13% of the population infected.
Albania: 2.88 million population, 58,316 total cases, 2.03% of the population infected.
Insight: Despite Afghanistan's larger population, Albania had a significantly higher percentage of its population infected, highlighting possible differences in virus spread and containment.

**3. Countries with the Highest Infection Rate**
•	Hotspots Identification: This query helps identify which countries had the highest infection rates relative to their population size. These countries could be considered COVID-19 hotspots and might have needed more urgent international support.
•	Analysis of Spread: By examining the highest infection count and the percent of the population infected, one can infer how quickly the virus spread in different regions.
•	Risk Factors: Countries with high infection rates might be evaluated for common factors such as urban density, travel restrictions, public health infrastructure, and policy responses.

Albania: 2.03% of its population infected.
Afghanistan: 0.13% of its population infected.
Insight: Albania's higher infection rate could indicate denser population areas, higher community transmission, or earlier/later intervention measures compared to Afghanistan.

**4. Countries with the Highest Death Count**
•	Mortality Analysis: This query identifies the countries with the highest total deaths, providing a straightforward measure of where the pandemic has been most deadly.
•	Policy Implications: Countries with the highest death counts might be scrutinized for their healthcare capacity, government response, and population demographics. This insight could inform future policy and preparedness planning.
•	Temporal Trends: By looking at the date in conjunction with this data, trends in mortality over time can be identified, such as whether deaths peaked during specific waves of the pandemic.

Algeria: 2,762 deaths.
Afghanistan: 2,191 deaths.
Insight: Algeria and Afghanistan both show high death counts, but Algeria's total deaths being higher reflects its higher total cases and population size.

**5. Continental Analysis of Death Counts**
•	Continental Overview: This query aggregates the total death counts by continent, offering a macro view of where the impact of the pandemic has been most severe globally.
•	Resource Allocation: Understanding which continents faced the highest death tolls can guide international aid and resource distribution during global health crises.
•	Continental Variations: Differences in death counts between continents might reflect factors such as varying levels of healthcare infrastructure, differences in government policies, and population health.

Africa: 2,762 deaths.
Asia: 2,191 deaths.
Insight: Africa and Asia had the most recorded deaths in this sample, with other continents like Europe and the Americas showing no data in the sample, likely due to earlier data or missing entries.

**6. Global COVID-19 Numbers**
Insights:
•	Global Mortality Rate: This query gives a global picture of the mortality rate, calculated as the percentage of deaths among confirmed cases.
•	Data Accuracy: The use of COALESCE ensures that the global figures account for all reported cases and deaths, reducing the impact of missing data.
•	Global Impact: The overall death percentage provides insight into the severity of the pandemic on a global scale and can be used to compare the relative success of different mitigation strategies across regions.

Total Cases: The total number of COVID-19 cases globally is approximately 150.57 million.
Total Deaths: The total number of COVID-19 deaths globally is about 3.18 million.
Death Percentage: The global death percentage (i.e., the proportion of confirmed cases that resulted in death) is 2.11%.
Insight: A global death rate of 2.11% indicates that slightly more than 2 out of every 100 confirmed COVID-19 cases resulted in death. This suggests the significant impact of the pandemic worldwide, highlighting the need for continued efforts to manage and mitigate the virus's spread.

**7. Total Population vs. Vaccinations**
•	Vaccination Progress: This query shows the cumulative number of people vaccinated in each country and calculates the percentage of the population that has been vaccinated over time.
•	Public Health Insights: Countries with high vaccination percentages might be better positioned to control the spread of the virus, potentially leading to lower infection and death rates.
•	Temporal Analysis: The rolling calculation allows you to see how vaccination efforts have progressed over time in different locations, which can be correlated with changes in infection rates and mortality.

For Afghanistan, the data available from February 2020 shows that there were no recorded vaccinations initially (as expected for early pandemic dates).
Insight: The absence of vaccination data early in the pandemic for Afghanistan reflects the timeline before vaccines became available. This emphasizes the critical role that vaccines later played in combating the pandemic and the importance of rolling out vaccination programs as soon as possible once vaccines were developed.

**8. Analysis Using CTE (Common Table Expressions)**
Insights:
•	Simplified Analysis: By using a CTE, complex calculations are broken down into manageable steps, making it easier to follow the logic and ensuring cleaner code.
•	Vaccination Efficiency: This query refines the vaccination analysis by calculating the percentage of the population vaccinated using a rolling sum, providing insight into how quickly vaccination campaigns were able to reach significant portions of the population.
•	Comparison Across Countries: This analysis allows for a straightforward comparison across different countries, making it easier to identify leaders and laggards in the vaccination effort.

**Recommendations:**

Enhanced Healthcare Support: Countries and regions with high death percentages and death counts should be prioritized for international aid, including medical supplies and healthcare worker support.
Focused Vaccination Campaigns: Areas with high infection rates should be targeted for accelerated vaccination efforts to curb the spread of the virus.
Continued Monitoring: Regular updates and monitoring of these key metrics will be essential for managing ongoing waves of the pandemic and preparing for future public health emergencies.


