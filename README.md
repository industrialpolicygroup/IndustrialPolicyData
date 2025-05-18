# MeasuringIndustrialPolicy_MainDataset_Public
In this repo you can find the main dataset for the replication in Juhász, Réka and Lane, Nathaniel and Oehlsen, Emily and Pérez, Verónica C., Measuring Industrial Policy: A Text-Based Approach (2025). This work was possible thanks to the Global Trade Alert (GTA) dataset, which was kindly shared with us by their team. We especially thank Johannes Fritz for helpful discussions about the GTA project.

The main file used in our analysis contains information at the "Measure" or "Intervention" level, we transform this dataset in multiple ways to obtain the desired figures and tables in our main text and appendix. If you have more questions regarding specific tables or figures please reachout to authors.


## Data Description

The dataset `data/JLOP_2025` contains 47,283 observations that are used throughout the analysis of `Measuring Industrial Policy: A Text-Based Approach (2025)`. This specific version of the data can be used to replicate the descriptives table G.3. In the appendix of the working paper from May 2025. The Data contains the following variable.


| Variable | label | 
| --- | --- |
| CountryImposing_cleaned | Name of country/ies deploying policy	|
| AnnouncedYear | 	Year the policy was announced	|
| MeasureID | 	Unique ID for each policy	|
| D_IP_bert_3 | 	=1 if labelled IP by BERT 3 class model; 0 otherwise	|
| D_OTHER_INTENTION_bert_3 | =1 if labelled Other Intention by BERT 3 class model; 0 otherwise	|
| D_NOT_ENOUGH_INFO_bert_3 | =1 if labelled Not Enough Information by BERT 3 class model; 0 otherwise	|
| MeasureAffectedProducts | 2012 HS6 sector codes affected by policy |
| MAST_chapterName | Policy instrument classification by MAST Chapter	|
| MeasureType | In-House Policy instrument classification by GTA	|
| firm_specific | =1 if the policy is directed to specific firms (Opposite to national policies in the draft)	|
| ImplementationLevel | Implementation level of the policy	|
| same_year_published | =1 if the policy was recorded by GTA  in the same year that they were announced |

## Note on Time Series

To produce the time series in the paper, we follow GTA guidance and use only policies recorded by the GTA in the same year that they were announced for this exercise. This is due to the substantial backfilling of data which is a living dataset. By using only policies recorded in the same years as they were announced, we ensure the comparability of data across both more distant and recent years.

Therefore, to produce any time series analysis the database in this repo must be filtered to keep only the observations for which `same_year_published == 1`. 


