# Supplementary Materials

## Context

word2vec is a fairly ‘simple’ embedding approach and has now been largely supplanted at large commercial firms (such as Google and Facebook) by algorithms with names like [BERT](https://pypi.org/project/fast-bert/), [SBERT](https://www.sbert.net/) and [RoBERTa](https://huggingface.co/docs/transformers/model_doc/roberta). These further enhance our ability to work with corpora by disentangling—that is, providing distinct embeddings for—‘bank’ (a place that provides financial services) and ‘bank’ (the land at the side of a river). The approaches employed in this tutorial do not provide that level of disambiguation.

If you are interested *primarily* in document similarity then it is possible to improve on this approach using a dedicated [Document Embedding](https://radimrehurek.com/gensim/models/doc2vec.html) algorithm instead. That said, we’ve often found these results to be less intuitive that the ones derived from word embeddings.

## A Note on Replicability

If you are concerned with *full replicability* of your results, then please also note that you need to **change the number of `workers` from 4 to 1** when running the word2vec algorithm. More than one worker means the process is running in parallel and you cannot guarantee that documents/words will be passed to the modelling process in the *_same order_* every time. When that happens the derived embeddings may differ. So if you use multiple workers then the results should be *_consistent_*, but not *_exactly the same_*, from run to run. Of course, running with only one worker will also increase the model run time substantially!

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

## Manifold Learning

 [t-SNE](https://en.wikipedia.org/wiki/T-distributed_stochastic_neighbor_embedding) (t-distributed Stochastic Neighbour Embedding) is another commonly-used manifold learning technique; however, it is designed to emphasise visibility (local structure) and its parameters are less conducive to preserving global structure in an intuitive way. We’d suggest using UMAP in preference to t-SNE for most applications where both levels of structure are needed to support clustering.

## Measuring Success

One of the standard approaches in Machine Learning to quantifying the performance of a classifier model is the [Confusion Matrix](https://en.wikipedia.org/wiki/Confusion_matrix) in which:

> Each row of the [matrix](https://en.wikipedia.org/wiki/Matrix_(mathematics)) represents the instances in an actual class while each column represents the instances in a predicted class

So if the embdding+UMAP+cluster approach works well, the the predicted class should be largely the same as the actual class. If we were to lay this out in a table with actual DDC in the row labels and predicted cluster in the column lables then we should have entries _mainly_ on the diagonal where the row and column labels are the same. 

#### Confusion matrix (2 Clusters)

But we can also investigate this result in a more nuanced way using something called the Confusion Matrix and Classifiction Report. Recall that the DDC plot in Figure 3 shows some Social Science theses clearly mapped on to the Science-like space. Here we make use of the derived cluster label to compare the DDC label to the cluster-derived one!

```python
# Classification report gives a (statistical) sense of power (TP/TN/FP/FN)
print(classification_report(clustered_df[f'ddc{ddc_level}'], clustered_df[f'Cluster_Name_{num_clusters}']))

# A confusion matrix is basically a cross-tab without totals,
# which I think are nice to add
pd.crosstab(columns=clustered_df[f'Cluster_Name_{num_clusters}'],
            index=clustered_df[f'ddc{ddc_level}'],
            margins=True, margins_name='Total')
```

At the top level, the expert-assigned DDC and automated cluster values line up extraordinarily well:

**Table 7. Confusion matrix for top-level DDC classes and clusters**

|                         | Science Cluster | Social Sciences Cluster | Total  |
| ----------------------: | --------------: | ----------------------: | ------ |
|         **Science DDC** |          26,591 |                     479 | 27,070 |
| **Social Sciences DDC** |             676 |                  20,948 | 21,624 |
|               **Total** |          27,267 |                  21,427 | 48,694 |

In other words, just 1.8% of the records classified as ‘Science’ were misclassified as Social Sciences in our automated analysis (479/27,070), and 3.1% of theses classified by librarians as being from the Social Sciences were assigned to the Science cluster (676/21,624).

#### Classification report (2 Clusters)

The confusion matrix can then be used as the basis for calculating [precision and recall](https://en.wikipedia.org/wiki/Precision_and_recall) values. Precision is <img alt="T_{P} / (T_{P}+F_{P})" src="https://render.githubusercontent.com/render/math?math={T_{P} / (T_{P}+F_{P})}" />, where <img alt="T_{P}" src="https://render.githubusercontent.com/render/math?math={T_{P}}" /> is the number of correctly-predicted observations (true positives), and <img alt="F_{P}" src="https://render.githubusercontent.com/render/math?math={F_{P}}" /> is the number of incorrectly-predicted observations (false positives) in that class. Recall measures something slightly different: <img alt="T_{P}/(T_{P}+F_{N})" src="https://render.githubusercontent.com/render/math?math={T_{P}/(T_{P}+F_{N})}" /> where <img alt="f_{N}" src="https://render.githubusercontent.com/render/math?math={F_{N}}" /> is the number of observations falsely assigned to *other* classs (false negatives). For the 2-cluster formulation above this yields a precision and recall (averaged over the two classes) of 0.98. Accuracy is calculated as <img alt="(T_{P} + T_{N})/(T_{P} + T_{N} + F_{P} + F_{N})" src="https://render.githubusercontent.com/render/math?math={(T_{P} + T_{N})/(T_{P} + T_{N} + F_{P} + F_{N})}" /> and is also 0.98.

|                 | precision | recall | f1-score | support |
| --------------- | --------- | ------ | -------- | ------- |
| Science         | 0.98      | 0.98   | 0.98     | 27070   |
| Social sciences | 0.98      | 0.97   | 0.97     | 21624   |
| accuracy        |           |        | 0.98     | 48694   |
| macro avg       | 0.98      | 0.98   | 0.98     | 48694   |
| weighted avg    | 0.98      | 0.98   | 0.98     | 48694   |

In short: using nothing more than a short abstract and title for a PhD thesis we’ve been able to correctly classify them into Social and Physical sciences with 98% accuracy!

#### Confusion Matrix (4 Clusters)

In the confusion matrix we are again looking for values that are ‘off’ the diagonal as an indicator of poor or declining clustering performance:

**Table 8. Confusion matrix for 2nd level DDC classes and clusters**

|            Expert Class | Biology Cluster | Economics Cluster | Physics Cluster | Social sciences Cluster | Total  |
| ----------------------: | --------------: | ----------------: | --------------: | ----------------------: | ------ |
|         **Biology DDC** |          17,498 |               214 |             514 |                     178 | 18,404 |
|       **Economics DDC** |             417 |            11,063 |              79 |                   1,050 | 12,609 |
| **Social sciences DDC** |             230 |                45 |           8,349 |                      42 | 8,666  |
|         **Physics DDC** |             165 |             1,880 |              15 |                   6,955 | 9,015  |
|               **Total** |          18,310 |            13,202 |           8,957 |                   8,225 | 48,694 |

Clearly, clustering is still performing well: although accuracy has fallen to 0.90 with average precision and recall of 0.89, Biology and Phyics are more readily distinguished with precision of 0.96 and 0.95, and recall of 0.93 and 0.96, respectively. This squares nicely with the intuition developed from looking at the UMAP embedding in Figure 3 above where we saw much greater overlap between the selected social science DDCs than the selected science DDCs. This effect neatly encapsulates one of the advantages to this approach: the visualisation, clustering, and validation results all reinforce one another, giving us confidence that what we’re seeing isn’t simply an artefact of the data or sheer good luck.