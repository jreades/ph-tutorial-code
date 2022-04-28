# Supplementary Materials

## Completeness

Table 1 shows the percentage of records for each field in the sample that contain data. While we have not verified that these all contain *useable* data it is nonetheless obvious that some, like Abstract and Institution (and, of course, Author and Title) are effectively complete, while others, such as Supervisor, Funder or DOI, are poorly populated at best. Across the *full* EThOS data set  the DDC is nowhere near as well-populated as in our selected sample (the same holds for some of the other fields), but that’s because we purposively chose records that would enable us to validate our approach against the expert-assigned label.

**Table 1. Completeness of Selected EThOS Metadata Attributes by Decade**

|           Attribute |     1980s |     1990s |      2000s |      2010s |    Overall |
| ------------------: | --------: | --------: | ---------: | ---------: | ---------: |
|              Author |       100 |       100 |        100 |        100 |        100 |
|               Title |       100 |       100 |        100 |        100 |        100 |
|            Abstract |       100 |       100 |        100 |        100 |        100 |
|            Keywords |        87 |        69 |         37 |         49 |         52 |
|                 DDC |       100 |       100 |        100 |        100 |        100 |
|         Institution |       100 |       100 |        100 |        100 |        100 |
|          Department |        46 |        33 |         31 |         53 |         45 |
|          Supervisor |        12 |         9 |         16 |         49 |         33 |
|  Subject Discipline |       100 |       100 |        100 |        100 |        100 |
|            Language |       100 |       100 |        100 |        100 |        100 |
|              Funder |         9 |         7 |          7 |         23 |         16 |
|                 DOI |         4 |         4 |          4 |         11 |          8 |
| **Count by Decade** | **3,583** | **6,931** | **11,249** | **26,980** | **48,743** |

## Additional Examples of Embeddings

In Table 5 are the top-10 most similar words for an array of other terms, demonstrating the extent to which they allow us to identify ‘relatedness’ across a range of disciplines based on the context in which terms are used. The first three terms in Table 5 stress that this is not about the computer developing some underlying understanding of ‘salmon are like rainbow trout’ and ‘Einstein developed the theory of relativity’ but a context-based substitutability based on the window size and weighting that we specified when developing the word embeddings.

**Table 5. Selected Terms and their Top-10 Most Similar**

| Term                                 | Top 10 Similar                                               |
| :----------------------------------- | ------------------------------------------------------------ |
| einstein                             | field_equation, gravity, scalar_field, equation, relativity, gauge_theory, string_theory, quantum_field_theory, non_abelian, minkowski |
| colorectal_cancer                    | cancer, breast_cancer, prostate_cancer, ovarian_cancer, type_diabetes, leukaemia, leukaemic, human_cancer, malignant, brca1 |
| atlantic_salmon                      | salmo, fish, rainbow_trout, salar, salmonid, salmon, oncorhynchus, brown_trout, mykiss, freshwater |
| new_keynesian                        | open_economy, dsge_model, optimal_monetary, dsge, indirect_inference, partial_equilibrium, return_scale, small_open_economy, financial_friction, cge |
| land_use_change                      | land_use, change_climate, environmental_change, vegetation_change, biodiversity, habitat_fragmentation, rainfall, agricultural_intensification, cl... |
| semi_structured                      | semi_structured_interview, interview, participant_observation, in_depth_interview, interview_conduct, interview_focus, focus_group, focus_group_di... |
| influenza_virus                      | virus, viruses, influenza, viral, viral_rna, adenovirus, rna, herpesvirus, norovirus, rna_virus |
| north_east_england                   | group_young, mixed_race, east_midlands, town, experience, britain, old, england, north_of_england, birmingham |
| built_environment                    | build_environment, quality_life, city, urban_form, informal_settlement, urban, social_sustainability, physical_activity, energy_supply, sustainabl... |
| information_communication_technology | ict, icts, communication_technology, information_technology, new_medium, internet, telecommunication, digital_technology, knowledge_economy, techn... |
| urban_regeneration                   | regeneration, urban_development, city, initiative, planning_policy, urban, cultural_policy, urban_design, urban_policy, public_policy |
| gravitational_wave_detector          | interferometer, gravitational_wave, astronomical, detector, device, laser, semiconductor_laser, collimation, lasers, ultra_low |
| cultural_heritage                    | heritage, cultural, landscape, contemporary, national_identity, buddhist, tourism, community, modernisation, intangible |
| cultural_capital                     | bourdieuas, bourdieu, cultural, literary, symbolic, social_capital, solidarity, elite, assert, habitus |

