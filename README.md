# IndustrialPolicyData
In this repo you can find the main datasets for the replication in Juhász, Réka and Lane, Nathaniel and Oehlsen, Emily and Pérez, Verónica C., Measuring Industrial Policy: A Text-Based Approach (2025). We gratefully acknowledge the use of the Global Trade Alert (GTA) dataset, kindly shared with us by the GTA team. We are particularly thankful to Johannes Fritz for helpful discussions about the GTA project.

The main file used in our analysis (`JLOP_2025`) contains information at the "Measure" or "Intervention" level, we transform this dataset in multiple ways to obtain the desired figures and tables in our main text and appendix. If you have more questions regarding specific tables or figures please reach out to the authors.

Our analysis also uses the file `JLOP_impementing_agencies_2025` which contains information at the "Measure"-"Implementing Agency" level. This means that each measure is listed separately for each implementing agency with which it is associated. We use this dataset to obtain all figures relating to implementing agencies in our main text and appendix. If you have any questions regarding specific tables or figures please reach out to the authors.

## Data Description

### JLOP_2025

The dataset `data/JLOP_2025` contains 47,283 observations that are used throughout the analysis of `Measuring Industrial Policy: A Text-Based Approach (2025)`. This specific version of the data can be used to replicate the descriptives table G.3. In the appendix of the working paper from May 2025. The Data contains the following variables.


| Variable | label | 
| --- | --- |
| CountryImposing_cleaned | Name of country/ies deploying policy	|
| AnnouncedYear | 	Year the policy was announced	|
| MeasureID | 	Unique ID for each policy	|
| StateActTitle | Title of the State Act that implemented the measure/interventon. One State Act may contain multiple interventions |
| D_IP_bert_3 | 	=1 if labelled IP by BERT 3 class model; 0 otherwise	|
| D_OTHER_INTENTION_bert_3 | =1 if labelled Other Intention by BERT 3 class model; 0 otherwise	|
| D_NOT_ENOUGH_INFO_bert_3 | =1 if labelled Not Enough Information by BERT 3 class model; 0 otherwise	|
| MeasureAffectedProducts | 2012 HS6 sector codes affected by policy |
| MAST_chapterName | Policy instrument classification by MAST Chapter	|
| MeasureType | In-House Policy instrument classification by GTA	|
| firm_specific | =1 if the policy is directed to specific firms (Opposite to national policies in the draft)	|
| ImplementationLevel | Implementation level of the policy	|
| same_year_published | =1 if the policy was recorded by GTA  in the same year that they were announced |

### JLOP_implementing_agencies_2025

The dataset `data/JLOP_implementing_agencies_2025` contains 14,194 observations that are used to conduct analysis relating to agencies implementing industrial policy in `Measuring Industrial Policy: A Text-Based Approach (2025)`.  There are fewer observations than in `JLOP_2025` for two reasons: 1) we only gathered data on the agencies implementing industrial policies, 2) the data only contains observatons for which we identified at least one implementing agency from the same country as the country imposing the policy. The data contains the following variables.

| Variable | label | Notes |
| --- | --- | --- |
| CountryImposing_cleaned | Name of country/ies deploying policy | Note that the dataset only includes observations for which the country of the implementing agency is the same as the country imposing the policy. Therefore, `CountryImposing_cleaned` also provides the name of the country associated with the implementing agency.
| AnnouncedYear | 	Year the policy was announced	| |
| MeasureID | 	Unique ID for each policy	| Note that while each "Measure" has a unique `MeasureID`, this dataset is not unique in `MeasureID` as it lists each `ImplementingAgency` for each `MeasureID` as a separate observation.
| ImplementingAgency | Name of the national government agency implementing the policy | We provide the own-language names of implementing agencies named in latin-script languages. We provide English translations of the names of implementing agencies named in non-latin-script languages. The aim of the standardization of the implementing agency's names is to make identifying the agency as easy as possible. |
| StateActTitle | Title of the State Act that implemented the measure/interventon. One State Act may contain multiple interventions | |
| D_IP_bert_3 | 	=1 if labelled IP by BERT 3 class model; 0 otherwise	| Note as we only collected data on the agencies implementing industrial policies, `D_IP_bert_3` = 1 for every observation in this dataest.
| D_OTHER_INTENTION_bert_3 | =1 if labelled Other Intention by BERT 3 class model; 0 otherwise	| Note as we only collected data on the agencies implementing industrial policies, `D_OTHER_INTENTION_bert_3` = 0 for every observation in this dataest. |
| D_NOT_ENOUGH_INFO_bert_3 | =1 if labelled Not Enough Information by BERT 3 class model; 0 otherwise	| Note as we only collected data on the agencies implementing industrial policies, `D_NOT_ENOUGH_INFO_bert_3` = 0 for every observation in this dataest |
| MeasureAffectedProducts | 2012 HS6 sector codes affected by policy | |
| MAST_chapterName | Policy instrument classification by MAST Chapter	| |
| MeasureType | In-House Policy instrument classification by GTA	| |
| firm_specific | =1 if the policy is directed to specific firms (Opposite to national policies in the draft)	| |
| ImplementationLevel | Implementation level of the policy	|
| same_year_published | =1 if the policy was recorded by GTA  in the same year that they were announced | |

## Note on Time Series

To produce the time series in the paper, we follow GTA guidance and use only policies recorded by the GTA in the same year that they were announced for this exercise. This is due to the substantial backfilling of data which is a living dataset. By using only policies recorded in the same years as they were announced, we ensure the comparability of data across both more distant and recent years.

Therefore, to produce any time series analysis the database in this repo must be filtered to keep only the observations for which `same_year_published == 1`. 