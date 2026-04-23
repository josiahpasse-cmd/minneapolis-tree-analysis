# Are Tree Planting Rates in the City of Minneapolis Impacted by Homeownership Rates?
## 1. Research Question
Do neighborhoods with higher rates of homeownership tend to have more trees planted and cared for by nonprofit groups and city governments?
## 2. Hypothesis
 - **null** - The majority household type of a neighborhood does not have an effect on the number of trees per square mile maintained by the city and nonprofits within a neighborhood.
 - **alternative hypothesis** - Neighborhoods where the majority household type is Owner have a higher number of trees per square mile maintained by the city and nonprofits.
## 3. Data Description
* My data was obtained from a group of Minnesota researchers who compiled data on trees from the Minneapolis-St.Paul Metropolitan Area. Their purpose was "*to examine fine-scale patterns of tree biodiversity across MSP.*". The compiled data fit the needs for my analysis as well, however.
* Each observation represents an inventory record of a tree collected between 2012 and 2022 in the twin cities. This data was filtered in the analysis to only include samples within the city limits of Minneapolis.
* 228,957 tree observations within the city limits of Minneapolis were included. 
* cleaning: Many unneeded columns were dropped from the data. Data was filtered to the city of Minneapolis. Column headings were adjusted from more scientific terminology to more human-friendly column names.
* transformation - neighborhood: Each specimen was categorized into the neighborhood where it was observed using a geojson file with shapes that define the neighborhoods of Minneapolis provided by the city of Minnepolis. The latitude and longitude of the tree observation was used to match with the shapes provided by the geojson file.
* transformation - common name: The common name was derived for each tree using a mapping from the epithet + genus (scientific name) to a common_name mapping. AI (Gemini) was used to assist in generating this mapping. The mapping was then reviewed by a human (me!) and applied to the data.
## 4. Methods
Summarize how you analyzed the data:
* Permutation Test Statistic: The difference between the mean trees per square mile of neighborhoods where a majority of households rent vs neighborhoods where a majority of household own their homes.
* Data was simulated under the null by randomly shuffling the majority_household_type for each value in the sample data and reevaluating the test statistic for the shuffled data.
* The Median and Mean trees per square mile by neighborhood were the two metrics used in bootstrapping.
* The CLT does not apply to the Median trees per square mile because...............
## 5. Results
Present your main findings:
* Key Summary Statistics: 
* Observed test statistic: 1031
* P value: 0.0002
* Median trees per square mile by neighbhorhood: 4,434
* Median trees per square mile by neighbhorhood: 4,136
## 6. Uncertainty Estimation
Discuss your resampling results:
* 10,000 resamples were collected
* The 95% confidence interval for our median trees per square mile by neighborhoods was [3863.9357, 4763.9401]
* The 95% confidence interval for our mean trees per square mile by neighborhoods was [3861.5501, 4394.0750]
* Through bootstrapping we can be 95% confident that the actual value of this mean is between 3862 and 4394 trees per square mile.
## 7. Limitations
In this analysis, we were limited by a number of things. Trees are constantly dying and new trees are planted. In this analysis, we looked at a snapshot collected over the course of a decade (2012 - 2022) that is now almost 4 years out of date. Lots can change in that time, so our data may not completely reflect the current state of trees maintained by municipal governments and nonprofits today. An additional factor is the emerald ash borer which has hit the state during those years, but has certainly continued to decimate the populations of ash trees since the end of our data collection period.

Another key limitation is the groups that provided tree samples. Our data contains trees tracked by the City of Minneapolis and some key nonprofit groups. There are **MANY** trees that fall outside of this scope. A non-exhaustive list includes...
 - Trees planted by homeowners/landlords
 - Trees planted and cared for by commercial businesses
 - Wild trees
 - Trees planted and cared for by private educational groups (colleges, private schools)
 - Other non-profit groups that don't keep accurate records of trees planted or didn't volunteer records

 There are many trees in Minneapolis that fall outside the scope, and may contain trends not found in our data or that directly oppose our findings.
## 8. References
Data Sources
https://opendata.minneapolismn.gov/datasets/cityoflakes::minneapolis-neighborhoods/about
https://portal.edirepository.org/nis/mapbrowse?packageid=knb-lter-msp.2.2
https://tableau.minneapolismn.gov/views/MinneapolisNeighborhoodDownloadData/Neighborhood?%3Aembed=y&%3Aiid=7&%3AisGuestRedirectFromVizportal=y

Trees MetaData
https://portal.edirepository.org/nis/metadataviewer?packageid=knb-lter-msp.2.2
[Mapping tree scientific names to common names with Gemini's help](https://gemini.google.com/share/30993c492520)