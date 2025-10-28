## Molecular surveillance supports differing roles in West Nile virus transmission between Culex pipiens and Culex restuans (Diptera: Culicidae) in Chicago, Illinois
Benjamin Burgunder, Jian Yang, Johnny Uelman, Rebecca Lee Smith, Patrick Irwin, Jordan Palmer, Megan L. Fritz

The Chicago metropolitan area is a hotspot for human West Nile virus (WNV) cases.
Despite extensive surveillance and research, predicting WNV cases in Chicago on a local scale is
a major challenge. Most studies and mosquito surveillance efforts do not differentiate between
the cryptic species Culex pipiens Linnaeus and Culex restuans (Theobald), key vectors of WNV,
due to the challenge of distinguishing them morphologically. This obscures each species’
respective role in transmission and may blunt the accuracy of local case forecasting. We used
species-specific PCR diagnosis to identify Chicago mosquitoes across 21 sites in July and
August of 2021 and 2022. We found that the percentage of Cx. restuans collected fell between
July and August, with Culex pipiens often serving as the sole species recorded from sites in
August. We found that the balance between our target species could vary,
sometimes dramatically, across years. Following species identification, we pooled our specimens
and determined infection prevalence using quantitative reverse transcription polymerase chain
reaction (RT-qPCR). We found that both species were highly infected with WNV and observed
no significant difference in their infection rates between months. We extend our findings to
assess the accuracy of a human case prediction model. We found no evidence to support the
molecular separation of these species in routine Chicago WNV surveillance.

Written in R (Version 4.41)

Code and Dataframe Guide:
-
Non-self-explanatory variable names are detailed below as 'Key Variables.'

ALLSampleOrganization_All_Quarters.csv
-
CSV containing a row for every sample tested as part of our work to identify the species identity of Culex collected in Chicago. Samples identified as Cx. restuans, pipiens, salinarius, or Unknown.

| Variable | Definition | 
| :--- | :---: | 
| TRAP ID | site name |
| Month |	month data |
| Year | year data |
| Abdomen Species ID | molecular species identification |

BaseHexMap.csv
-
CSV containing the category, latitude, longitude, residual, and human cases of each trapping site. Site data provided by the Northwest Mosquito Abatement District.

| **Variable** | **Definition** |
|---------------|----------------|
| Trap.ID | site name |
| Cases | site human cases |
| Category | site categorization |
| X | longitude |
| Y | latitude |

Categorized_binGroup.csv
-
CSV containing the MLE estimations, site categorization, high, and low confidence intervals for our target species across our two sampling months as calculated by R Package 'binGroup' (Bilder et al. 2010), using a 95% bias- and skewness-corrected confidence intervals as recommended by Biggerstaff 2008.

| **Variable** | **Definition** |
|---------------|----------------|
| Species | species identification (P = *Cx. pipiens*, R = *Cx. restuans*) |
| Month | month data (J = July, A = August) |
| Category | site categorization (L = lower, E = expected, H = higher) |
| PointEst | binGroup MLE estimate |
| Lower | lower confidence interval |
| Upper | upper confidence interval |
| Scale | infection rate scale |

Comp_Haversine.csv
-
CSV containing the haversine formula-estimated distance between sites and the difference between their proportion Cx. pipiens. 

| **Variable** | **Definition** |
|---------------|----------------|
| Site1 | site 1 |
| Site2 | site 2 |
| Diff in Prop | difference in percentage *Cx. pipiens* between sites |
| Quarter | month-year of sampling |
| Distance | haversine formula–calculated distance between sites (km) |
| Difference | proportion difference in percentage *Cx. pipiens* between sites |

MIRcalcALL.csv
-
CSV containing the collection details and minimum infection rate of sites.

| **Variable** | **Definition** |
|---------------|----------------|
| Month | month data |
| Species | species data |
| Hex | sampling site |
| Category | site categorization |
| Year | year data |
| summed\_MQ | total mosquitoes |
| Positive | number of positive pools |
| TotalSamples | total pools |
| FracPos | fraction positive pools |
| MIR | minimum infection rate |
| Category\_fac | factor of site category |
| Month\_f | factor of month data |


Prev_Haversine.csv
-
CSV containing the haversine formula-estimated distance between sites and the difference between their minimum infection rates. 

| **Variable** | **Definition** |
|---------------|----------------|
| Site1 | site 1 |
| Site2 | site 2 |
| Distance | haversine formula-calculated distance between sites (km) |
| Rate1 | MIR of site 1 |
| Rate2 | MIR of site 2 |
| Absdiff | absolute difference in MIR between sites |
| Quarter | month-year of sampling |
| Month\_f | factor of month data |

Pub_Comp.qmd
-
qmd file of R code that wrangles composition data, produces a graph of site composition by collection month and year, a map of site categorization and composition, and a raw count of all analyzed specimens by species identity. Finally, contains stepwise clustered binomial model reduction analysis of key variables across the entire dataset and then between July sampling events.

Pub_Haversine.qmd
-
qmd file of distance vs. differences in site composition or minimum infection rate.

Pub_prev.qmd
-
qmd file containing MIR clustered binomial model reduction analysis of species identity, collection period, site category, and MIR. Produces graphs of MIR by species and category, positivity of sites map, a MLE comparison between species and collection month as generated by binGroup (Bilder et al. 2010), and a MLE comparison between species, site category, and collection month as generated by binGroup (Bilder et al. 2010).

RestID_Full.csv
-
csv file containing collection information and site composition.

| **Variable** | **Definition** |
|---------------|----------------|
| Month | month data |
| Category.x | site category |
| Trap.ID | site name |
| Year | year data |
| Num.Rest | number of *Cx. restuans* collected |
| Num.Pip | number of *Cx. pipiens* collected |
| PropPip | percentage *Cx. pipiens* collected |
| X | longitude |
| Y | latitude |


Yearless_IPS.csv
-
csv file of species, month, point estimate, and lower and upper confidence intervals as generated by binGroup (Bilder et al. 2010), using a 95% bias-
and skewness-corrected confidence intervals as recommended by Biggerstaff 2008.

| **Variable** | **Definition** |
|---------------|----------------|
| Species | species data |
| Month | month data |
| PointEst | binGroup MLE estimate |
| Lower | lower confidence interval |
| Upper | upper confidence interval |
| Scale | infection rate scale |
| CI | type of confidence interval (bsc = bias- and skewness-corrected, sc = skewness-corrected) |


