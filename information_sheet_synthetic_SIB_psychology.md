# Information Sheet

## Title: Synthetic SIB Datasets

**Description**:
This information sheet describes the synthetic datasets simulating Sentiment, Intensity, and Breadth for the psychology domain, followig the pipeline outlined in stage 1 of LSC-Eval, an evaluation framework introduced in https://arxiv.org/abs/2503.08042

## Data Collection Methodology

- **Source**: Input sentences come from the academic psychology corpus: https://github.com/naomibaes/psychology_corpus
- **Time Frame**: 1970-2019

## Data Structure 

- **Format**: csv
- **Time slicing**:
    - 5-year: random samples of up to 1,500 sentences from each 5-year time slices in the corpus period (1970-2019) (time is labelled in the file name)
    - all-year: dataset merging the sentences from the 5-year samples above (not labelling time)
      
### Synthetic Sentiment
- **Columns**: `['baseline', 'negative_variation', 'positive_variation']`
- **Schema**:
  - `baseline`: Randomly sampled input neutral corpus sentences to vary/induce semantic change in.
  - `negative_variation`: Output sentences once the LLM varies the input sentence to contain more negative sentiment
  - `positive_variation`: Output sentences after the LLM varies the input sentence to contain more positive sentiment
 
  - ### Example Dataset: Semantic Variation in Abuse Contexts (Sentences) 1970-1974

| **baseline** | **negative_variation** | **positive_variation** |
|--------------|-------------------------|-------------------------|
| This paper attempts to show how a public health measure, by reducing production and withdrawing methylamphetamine (Methedrine) from retail pharmacists, dramatically affected the prevalence of its abuse in a provincial population. | This paper attempts to show how a public health measure, by reducing production and withdrawing methylamphetamine (Methedrine) from retail pharmacists, beneficially impacted the way individuals address its abuse in a provincial population. | This paper attempts to show how a public health measure, by reducing production and withdrawing methylamphetamine (Methedrine) from retail pharmacists, severely curbed the devastating prevalence of its abuse in a provincial population. |
| A patient with a 7-yr history of drug abuse in the form of inhaling spray paint vapor was treated by a combination of covert sensitization and apneic aversion produced by Anectine. | A patient with a 7-yr history of drug abuse in the form of inhaling spray paint vapor was treated with innovative approaches like covert sensitization and apneic aversion produced by Anectine, showing potential for positive recovery. | A patient with a 7-yr history of drug abuse in the form of inhaling spray paint vapor was treated by a combination of harsh covert sensitization and distressing apneic aversion produced by Anectine. |
| Child abuse has lately reached epidemic proportions, with the most severe cases occurring in children under three years of age. | Child abuse awareness has lately reached significant proportions, with increased efforts focused on protecting children under three years of age. | Child abuse has lately escalated to epidemic proportions, with the most tragic cases occurring in children under three years of age. |

### Synthetic Intensity
- **Columns**: `['baseline', 'high_intensity', 'low_intensity']`
- **Schema**:
  - `baseline`: Randomly sampled natural corpus sentences to vary/induce semantic change in.
  - `high_intensity`: Output sentences once the LLM varies the input sentence to contain higher intensity
  - `low_intensity`: Output sentences once the LLM varies the input sentence to contain lower intensity
 
  - ### Example Dataset: Semantic Variation in Abuse-Related Language

| **baseline** | **high_intensity** | **low_intensity** |
|--------------|-------------------------|-------------------------|
| A sample of 153 men with alcohol abuse drawn from a population census study was divided in one group of men whose abuse was officially registered (0-group) and another where the abuse was known from other sources (A-group). | A sample of 153 men with **severe** alcohol abuse drawn from a population census study was divided into one group of men whose abuse was officially registered (0-group) and another where the abuse was **notoriously** known from other sources (A-group). | A sample of 153 men with **mild** alcohol abuse drawn from a population census study was divided into one group of men whose abuse was officially registered (0-group) and another where the abuse was **discreetly** known from other sources (A-group). |
| Judges recorded the concurrent undesirable social responses of: (a) verbal abuse and (b) aggression, withdrawal, and inattention. | Judges recorded the concurrent **shocking** social responses of: (a) verbal abuse and (b) **intense aggression**, **alarming withdrawal**, and **troubling inattention**. | Judges recorded the concurrent **mild** social responses of: (a) verbal abuse and (b) **slight aggression**, **minor withdrawal**, and **minimal inattention**. |
| This measure coincided with the midpoint of a four-year survey into drug abuse which was being carried out in that area. | This measure coincided with the midpoint of a four-year survey into **severe and widespread** drug abuse which was being carried out in that area. | This measure coincided with the midpoint of a four-year survey into **occasional instances** of drug abuse which was being carried out in that area. |

### Synthetic Breadth
- **Columns**: `['sentence', 'label', 'year']`
- **Schema**:
  - `sentence`: Sentence containing the co-hyponym that is randomly sampled from the natural corpus.
  - `label`: "synthetic_" signifies that it is a co-hyponym context (sentence) and the next part labels the co-hyponym (it is replaced with the target term due to the replacement strategy approach).
  - `year`: Year from which the sentence is randomly sampled from in the corpus
 
  - ### Example Dataset: Semantic Variation in Abuse-Related Language
    
## Data Volume 
- *Note*: Information pertains to the final cleaned "nyt_corpus.csv" dataset that we compiled within the specified year range.

- **Year Range**: 01/1930 - 12/2023
  - Unique values for year: 94; unique values for month: 12
- **Total Articles**: 10,891,026
- **Total Size**: 4,062,237 KB
- **Section Types**: 91 (some may be duplicates due to incorrect parsing, e.g., 'Archives', '|Archives')

## Usage and Licensing

- **Permissions**: Users must comply with the New York Times API terms of service. Scripts can be downloaded and used under the Creative Commons Attribution 4.0 International License, which "requires that users give appropriate credit, provide a link to the license, and indicate if changes were made. It allows for both commercial and non-commercial use of the work, as long as attribution is provided. This is in line with the general requirement for attribution in the Creative Commons Attribution (CC BY) licenses."
- **Attribution**: Please credit the New York Times as the data source, and this GitHub repository if you re-use the scripts.

## Data Quality and Limitations

- **Quality Control**: Articles have been cleaned to remove duplicates and incomplete entries.
- **Known Limitations**: The corpus may contain biases inherent to the New York Times' reporting. Additionally, as full-text articles are not available, tokens are limited, affecting the comprehensiveness of the dataset.

# Data Statement

### Purpose:
This data statement provides a comprehensive overview of the New York Times Article Corpus, which has been compiled for research and analysis purposes. The corpus aims to facilitate studies in various fields, including but not limited to, journalism, data science, natural language processing, and historical research.

### Scope:
- **Content**: Articles from the New York Times spanning from January 1930 to December 2023.
- **Data Points**: Title, section name, snippet, lead paragraph, year, month, and web URL of each article.

### Methodology:
- Data was collected using the New York Times API, specifically from the endpoint `https://api.nytimes.com/svc/archive/v1/{year}/{month}.json`.
- Only metadata and article snippets are included due to API restrictions and terms of service.

### Usage:
- **Research and Analysis**: This corpus can be used for text analysis, trend identification, and other research purposes.
- **Education**: Suitable for educational purposes to demonstrate data scraping, cleaning, and analysis techniques.
- **Development**: Can be utilized in developing machine learning models and natural language processing applications.

### Quality and Limitations:
- **Quality Control**:
  - The dataset has undergone cleaning to remedy 116,799 malformed rows and rows where the number of columns did not match the header. Additionally, 79 rows were removed where the year did not meet the specified criteria (not a 4-digit number or not within the range 1930-2023), and rows in the year 1851 were also removed.
- **Limitations**:
  - The corpus may reflect biases inherent in the New York Times' reporting.
  - Full-text articles are not available, which may limit the depth of certain analyses.
  - The data is as comprehensive as allowed by the API restrictions, focusing on snippets, lead paragraphs, and titles.
- **NA counts for each column in the final cleaned data frame - "nyt_corpus_cleaned.csv"**:
  - Number of NA values, total rows, and percentage of NA values in each column:
  - Column 0: NA Count = 615, Total Rows = 10891026, Percentage = 0.01%
  - Column 1: NA Count = 2295, Total Rows = 10891026, Percentage = 0.02%
  - Column 2: NA Count = 4494865, Total Rows = 10891026, Percentage = 41.27%
  - Column 3: NA Count = 5979376, Total Rows = 10891026, Percentage = 54.90%
  - Column 4: NA Count = 0, Total Rows = 10891026, Percentage = 0.00%
  - Column 5: NA Count = 0, Total Rows = 10891026, Percentage = 0.00%
  - Column 6: NA Count = 0, Total Rows = 10891026, Percentage = 0.00% 

### Ethical Considerations:
- Users must comply with the New York Times API terms of service and ensure proper attribution: [NYT API Terms](https://developer.nytimes.com/terms).
- Consider the ethical implications of the data usage, especially regarding the representation of sensitive topics and historical contexts.

### Acknowledgements: 
- Code for some scripts were inspired from Salvatore Giorgi's repository: https://osf.io/uya29/

### Contact Information:
- **Compiled by**: Hugo Lyons Keenan & Naomi Baes
- **Emails**: [hugo0076@gmail.com](mailto:hugo0076@gmail.com) & [naomi_baes@hotmail.com](mailto:naomi_baes@hotmail.com)
- **Support**: For questions, please contact [hugo0076@gmail.com](mailto:hugo0076@gmail.com).

### Citation:
Please cite this corpus as follows:
Hugo Lyons Keenan & Naomi Baes. "New York Times Article Corpus (1930-2023)." Retrieved from [https://github.com/naomibaes/NYT].
