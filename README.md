
# Electronic MoCA Dataset

The electronic MoCA dataset description for users. Adapted from [Thai MoCA test](https://www.google.com/url?sa=i&url=http%3A%2F%2Fwww.phimaimedicine.org%2F2013%2F01%2Fmild-cognitive-dysfunction.html&psig=AOvVaw3fBPjS7zE9YKG1ZAQOKeIz&ust=1694510035896000&source=images&cd=vfe&opi=89978449&ved=0CBAQjRxqFwoTCMiE-febooEDFQAAAAAdAAAAABAE)


## Walkthrough

The dataset consists of two main parts: 
- [**Demographic**](###Demographic)
    > demographic data related to patients or subject participating in cognitive assessment with e-MoCA. The pariticipant information is encoded with numerical code and hash number identifiers.
- [**Cognitive Assessment**](###Cognitive-Asessment)
    > Cognive assessment data from each test composing the e-MoCA tools. The assessments are divided into 7 categories by cognitive function in the same manner of original [MoCA test](https://www.parkinsons.va.gov/resources/MOCA-Test-English.pdf) which are 
      1. Visual + Spatial 
      2. Naming 
      3. Memory 
      4. Attention 
      5. Language 
      6. Abstraction
      7. Orientation
### Demographic

In this dataset, the demographic data is stored in 3 files
- **summary.txt**
    containing following columns
    | No. | Column name | Description |
    | ---:| ---: | --- |
    | 1|patient_id|Identifier of subject|
    |2|citizen_id| Masked citizen id |
    |3|staff_id|Identifier for a practitioner who administrate the assessment to the subject|
    |4|education| Numerical code for education as described in `edu.txt`|
    |5|test_date| Datetime when the test is being administrated|
    |6|test_province| Province in which subject participate in assessment|
    |7|test_location| The assessment sites as described in `location.txt`|
    
    other columns is not relate to the cognitive assessment and can be dropped
- **edu.txt**
    file containing map between numeric code and the actual value of education
- **location.txt**
    Assessment site 

### Cognitive Assessment

The dataset is divided into 7 categories in the same way as original MoCA test design. however, our tools impliment [Thai language version](https://www.google.com/url?sa=i&url=http%3A%2F%2Fwww.phimaimedicine.org%2F2013%2F01%2Fmild-cognitive-dysfunction.html&psig=AOvVaw3fBPjS7zE9YKG1ZAQOKeIz&ust=1694510035896000&source=images&cd=vfe&opi=89978449&ved=0CBAQjRxqFwoTCMiE-febooEDFQAAAAAdAAAAABAE)

* The first category is *Visuo/spatial* domain
    * Containing all `visuospatial_p{number}.txt` files. The other files dubbed `visuospatial_p{number}t.txt` is time series data that we can neglect it for now.
    * The important data for each table in a file is following
    
    |No|Colume name| Description|
    |---:| --- | --- |
    | 1|patient_id|Identifier of subject|
    |2|score| Evaluated scaled score by the psychologist administrated the assessment (only use value which `seq_no = 1` )|
    |3|create_date|The datetime that the data is recorded|
    |4|seq_no| The number specified the order of the evaluation where `0` indicate *automated data collection by eMoCA* and `1` indicate evaluation process by psychologist|

* The second one is *Naming* domain
    * The only file that should be used is `naming_score.txt` with the following description
    
    |No|Colume name| Description|
    |---:| --- | --- |
    | 1|patient_id|Identifier of subject|
    |2|score| Evaluated scaled score by the psychologist |
    |3|create_date|The datetime that the data is recorded|
    |4|animal{#num}|The participant answer to the corresponding question|
    |5|animal{#num}_check|Psychologists evaluation for that question|

* The third one is *Memory/Delayed Recall* domain
    * This domain contain two tasks, Meomorization and Recall. However, only *Recall* is being evaluated as scaled score in original MoCA test so, we can use only `delayed_recall.txt` file. The important columns are listed here
    
    |No|Colume name| Description|
    |---:| --- | --- |
    | 1|patient_id|Identifier of subject|
    |2|score| Evaluated domain's scaled score by the psychologist|
    |3|create_date|The datetime that the data is recorded|

* The fourth one is *Attention* domain
    * This domain has 4 questions. Each question assessment is store in `att_p{num}.txt`. The most important columns in each files are the same.
    
    |No|Colume name| Description|
    |---:| --- | --- |
    | 1|patient_id|Identifier of subject|
    |2|score| Evaluated question's scaled score by the psychologist |
    |3|create_date|The datetime that the data is recorded|
    
    However, there are some additional columns in `att_p1.txt`, `att_p2.txt` and `att_p4.txt` which are **answer{num}** that store the answer from participant during the test. And for `att_p3.txt` there is columns `timecount` storing the total number of times participant knock the table (responding to task assignment).

* The fifth one is *Language* domain
    * This domain is quite overlooked in terms of language assessment, so we have only two question stored in files `lang_p{num}.txt`. The important columns are listed here
    
    |No|Colume name| Description|
    |---:| --- | --- |
    | 1|patient_id|Identifier of subject|
    |2|score| Evaluated question's scaled score by the psychologist |
    |3|create_date|The datetime that the data is recorded|

    Additional column in part one is in part two where the total number of ก.ไก่ word maybe be of use for analysis in column `wordcount` 

* The sixth one is *Abstraction* domain
    * This domain is stored in only one `abs.txt` file.
    
    |No|Colume name| Description|
    |---:| --- | --- |
    | 1|patient_id|Identifier of subject|
    |2|score| Evaluated domain's scaled score by the psychologist |
    |3|answer{num}|Evaluate score by psychologist for each question|
    |4|create_date|The datetime that the data is recorded|

* The last one is *Orientation* domain
    * This domain is stored in only one `ori.txt` file.
    
    |No|Colume name| Description|
    |---:| --- | --- |
    | 1|patient_id|Identifier of subject|
    |2|score| Evaluated domain's scaled score by the psychologist |
    |3|answer{num}|Evaluate score by psychologist for each question|
    |4|create_date|The datetime that the data is recorded|





    
## Authors

- [@wp1631](https://www.github.com/wp1631)

