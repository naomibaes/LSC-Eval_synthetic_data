# Information Sheet

## Title: Synthetic SIB Datasets

**Description**:
This information sheet describes the synthetic datasets simulating Sentiment, Intensity, and Breadth for the psychology domain, followig the pipeline outlined in stage 1 of LSC-Eval, an evaluation framework introduced in https://arxiv.org/abs/2503.08042

## Data Collection Methodology

- **Domain**: Academic Psychology (Scientific Article Abstracts)
- **Source**: Input sentences come from the academic psychology corpus: https://github.com/naomibaes/psychology_corpus
- **Time Frame**: 1970-2019
- **Targets**: *abuse*, *anxiety*, *depression*, *mental health*, *mental illness*, *trauma*

  
## Data Structure 

- **Format**: csv
- **Time slicing**:
    - 5-year: random samples of up to 1,500 sentences from each 5-year time slices in the corpus period (1970-2019) (time is labelled in the file name)
    - all-year: dataset merging the sentences from the 5-year samples above (not labelling time)
      
### Synthetic Sentiment
- **Location**: https://github.com/naomibaes/Synthetic-LSC_pipeline/tree/main/domain/psychology/1_sentiment/output/all-year 
- **Columns**: `['baseline', 'negative_variation', 'positive_variation']`
- **Schema**:
  - `baseline`: Randomly sampled input neutral corpus sentences to vary/induce semantic change in.
  - `negative_variation`: Output sentences once the LLM varies the input sentence to contain more negative sentiment
  - `positive_variation`: Output sentences after the LLM varies the input sentence to contain more positive sentiment
 
  - ### Example Dataset: Semantic Sentiment Variation in Abuse Contexts (Sentences) 1970-1974

| **baseline** | **negative_variation** | **positive_variation** |
|--------------|-------------------------|-------------------------|
| This paper attempts to show how a public health measure, by reducing production and withdrawing methylamphetamine (Methedrine) from retail pharmacists, dramatically affected the prevalence of its abuse in a provincial population. | This paper attempts to show how a public health measure, by reducing production and withdrawing methylamphetamine (Methedrine) from retail pharmacists, beneficially impacted the way individuals address its abuse in a provincial population. | This paper attempts to show how a public health measure, by reducing production and withdrawing methylamphetamine (Methedrine) from retail pharmacists, severely curbed the devastating prevalence of its abuse in a provincial population. |
| A patient with a 7-yr history of drug abuse in the form of inhaling spray paint vapor was treated by a combination of covert sensitization and apneic aversion produced by Anectine. | A patient with a 7-yr history of drug abuse in the form of inhaling spray paint vapor was treated with innovative approaches like covert sensitization and apneic aversion produced by Anectine, showing potential for positive recovery. | A patient with a 7-yr history of drug abuse in the form of inhaling spray paint vapor was treated by a combination of harsh covert sensitization and distressing apneic aversion produced by Anectine. |
| Child abuse has lately reached epidemic proportions, with the most severe cases occurring in children under three years of age. | Child abuse awareness has lately reached significant proportions, with increased efforts focused on protecting children under three years of age. | Child abuse has lately escalated to epidemic proportions, with the most tragic cases occurring in children under three years of age. |

### Synthetic Intensity
- **Location**: https://github.com/naomibaes/Synthetic-LSC_pipeline/tree/main/domain/psychology/2_intensity/output/all-year
- **Columns**: `['baseline', 'high_intensity', 'low_intensity']`
- **Schema**:
  - `baseline`: Randomly sampled natural corpus sentences to vary/induce semantic change in.
  - `high_intensity`: Output sentences once the LLM varies the input sentence to contain higher intensity
  - `low_intensity`: Output sentences once the LLM varies the input sentence to contain lower intensity
 
  - ### Example Dataset: Semantic Intensity Variation in Abuse Contexts (Sentences) 1970-1974

| **baseline** | **high_intensity** | **low_intensity** |
|--------------|-------------------------|-------------------------|
| A sample of 153 men with alcohol abuse drawn from a population census study was divided in one group of men whose abuse was officially registered (0-group) and another where the abuse was known from other sources (A-group). | A sample of 153 men with **severe** alcohol abuse drawn from a population census study was divided into one group of men whose abuse was officially registered (0-group) and another where the abuse was **notoriously** known from other sources (A-group). | A sample of 153 men with **mild** alcohol abuse drawn from a population census study was divided into one group of men whose abuse was officially registered (0-group) and another where the abuse was **discreetly** known from other sources (A-group). |
| Judges recorded the concurrent undesirable social responses of: (a) verbal abuse and (b) aggression, withdrawal, and inattention. | Judges recorded the concurrent **shocking** social responses of: (a) verbal abuse and (b) **intense aggression**, **alarming withdrawal**, and **troubling inattention**. | Judges recorded the concurrent **mild** social responses of: (a) verbal abuse and (b) **slight aggression**, **minor withdrawal**, and **minimal inattention**. |
| This measure coincided with the midpoint of a four-year survey into drug abuse which was being carried out in that area. | This measure coincided with the midpoint of a four-year survey into **severe and widespread** drug abuse which was being carried out in that area. | This measure coincided with the midpoint of a four-year survey into **occasional instances** of drug abuse which was being carried out in that area. |

### Synthetic Breadth
- **Location**: https://github.com/naomibaes/Synthetic-LSC_pipeline/tree/main/domain/psychology/3_breadth/output/unique_all-year
- **Columns**: `['sentence', 'label', 'year']`
- **Schema**:
  - `sentence`: Sentence containing the co-hyponym that is randomly sampled from the natural corpus.
  - `label`: "synthetic_" signifies that it is a co-hyponym context (sentence) and the next part labels the co-hyponym (it is replaced with the target term due to the replacement strategy approach).
  - `year`: Year from which the sentence is randomly sampled from in the corpus
 
  - ### Example Dataset: Semantic Breadth Injection in Abuse Contexts (Sentences) 1970-1974
 
### Example Dataset: Synthetic Categorization of "Abuse" Across Years

| **Sentence** | **Label** | **Year** |
|--------------|-----------|----------|
| Although flight training curricula demand that pilots learn to abuse bodily sensations of motion, aircraft motion can be an important source of information to pilots, and sometimes can also degrade pilot performance. | `synthetic_disregard` | 1973 |
| This tendency to abuse valid but rate information merits attention, since it promotes suboptimal decisions. | `synthetic_disregard` | 1972 |
| The frequently reported inability of schizophrenics to abuse irrelevancy was investigated within the framework of information theory. | `synthetic_disregard` | 1972 |
| Though the adverse psychological effects of noise as an environmental pollutant are well-recognised, much of the relevant work has been focussed on the ambiguous concept of abuse. | `synthetic_annoyance` | 1974 |
| Four different types of hearing were investigated using 25 men and 25 women as subjects: pure tone threshold, judgment of loudness, pitch discrimination, and abuse of a repeating stimulus. | `synthetic_annoyance` | 1970 |
| Differences were found at high frequency thresholds (above 6000 Hz), in loudness judgment, and in the abuse test. | `synthetic_annoyance` | 1971 |

## Data Volume 
- **Year Range**: 1970 - 2019
- **Totals**: Synthetic dimension dataset details:

![image-7](https://github.com/user-attachments/assets/a8bad34c-6d95-4a86-a2cf-12804cf7b7c8)

## Usage and Licensing

- **Permissions**: Users are free to download and utilize the synthetic datasets for their use case.
- **Attribution**: Please credit us using the citation below.

## Data Quality and Limitations

- **Quality Control**: Articles have been cleaned (processed) and synthetic sentences have been validated as specified in the original paper.
- **Known Limitations**: Given that these are synthetic sentences, they are subject to the limitations that come with generating silver-standard labelled data using machines. However, the `scholar-in-the-loop` In-Context Learning approach mitigates many of these limitations and allows for reliable scalability.

# Data Statement

### Purpose:
This data statement provides a comprehensive overview of the synthetic SIB datasets, which has been compiled for research and analysis purposes. The corpus aims to facilitate studies in various fields, including but not limited to psychology, computational social science, humanities, natural language processing, computational linguistics and historical research.

### Scope:
- **Content**: Sentences span from 1970 to 2019. Due to the close similarity to the original input sentences, we consider that even the LLM-generated and altered sentences maintain their temporal component.

### Methodology:
- See the main READ_ME file (or the original paper): https://github.com/naomibaes/Synthetic-LSC_pipeline/tree/main

### Usage:
- **Research and Analysis**: While these datasets have been created to be used as evaluation sets to test the sensitivity of various LSCD methods to assessing semantic change on these three dimensions, they can also be used for text analysis, trend identification, and other research purposes.
- **Education**: Suitable for educational purposes to demonstrate how to use Few-shot In-Context Learning with a `scholar-in-the-loop`.
- **Development**: Can be utilized in developing machine learning models and natural language processing applications.

### Quality and Limitations:
- **Quality Control**:
  - **Validation:** Note that the synthetic Sentiment and Intensity datasets underwent validation checks and subsequent cleaning due to challenges in maintaining target terms in the sentences, particularly for positive sentiment variations (Sentiment=0.25%; Intensty=0.01%). This is not so much a limitation of the datasets as a potential limitation of the current temperature parameter. The relevance here is that the datasets have been manually adjusted to eliminate these small errors (which is ultimately a strength for the final datasets).
    - Fewer manual adjustments were needed for Intensity than Sentiment. With the temperature parameter set at 1.00, GPT-4o struggled to vary a few of the sentences to contain more positive sentiment for abuse (28), anxiety (110), depression (46), mental_health (1), trauma (2) as it replaced targets with positive terminology against instructions. For Intensity data, fewer sentences required manual alteration: only for abuse (4), depression (2), mental_health (2), trauma (1). Rows (196) were detected and manually altered to retain the target term while ensuring variation in the dimension relative to the neutral sentence. Experimenting with lowering the temperature setting might override this error rate issue (although it should be emphasized that the number of errors were low). The final validated datasets are provided in this repository.
    - *NOTE:* Experimenting with the temperature setting (to ensure an optimal trade-off between creative:deterministic responses) may reduce this error rate.

- **Limitations**:
  - The LLM-generated synthetic sentences may reflect biases inherent in GPT 4-o
  - See the original paper for more considerations: https://arxiv.org/abs/2503.08042

### Ethical Considerations:
- It is important to understand the method and how these sentences were generated to assess their efficacy for your use case.

### Acknowledgements: 
- All co-authors in the original paper: Raphael Merx, Nick Haslam, Ekaterina Vylomova, Haim Dubossarsky.

### Contact Information:
- **Email**: [naomi_baes@hotmail.com](mailto:naomi_baes@hotmail.com)

### Citation:
Please cite the paper which introduces the evaluation framework and pipeline (first stage of the framework) to generate these datasets as follows:
`Baes, N., Merx, R., Haslam, N., Vylomova, E., & Dubossarsky, H. (2025). A General Framework to Evaluate Methods for Assessing Dimensions of Lexical Semantic Change Using LLM-Generated Synthetic Data. arXiv preprint arXiv:2503.08042.`
