

## Note
This is a threats to validity reproduction project as part of the MSR course 2022 at UniKo, CS department, SoftLang Team

### Team name: Yankee
### Student names: 
- Akash Ravishankar
- Neha Nagesh
- Abhishek Harsha Raj

## Objective of reproduction

### Description
Reproduction of issues reported in stackoverflow. The aim was to reproduce the java issues found on Stackoverflow.

### Input Data
Java questions are extracted from Stackoverflow using [StackExchage API](https://api.stackexchange.com/docs/search#fromdate=2020-01-01&todate=2022-07-25&order=desc&sort=activity&tagged=java&filter=default&site=stackoverflow&run=true)

### Output Data
A CSV file which contains the reproducibility status is obtained as output which is used for further analysis where we see the total percentage of questions that are reproducible or irreproducible in the given data. 


## Findings of reproduction

### Process delta:

i) We first extracted the data dump from StackExchange API base as shown in paper, but we had to modify the query in order to obtain the ideal data dump for further processing. 

ii) From the data dump, we were able to reproduce most of the preprocessing steps like selecting only Java based questions.

iii) We weren't able to randomly sample the data as the process was not very well defined. Hence, we decided to go with the top 400 questions out of which we decided to select 150 questions as our sample.



### Output delta:

i) We weren't able to obtain the "No AcceptedAnswers" category due to our data being a small snapshot and was only available with 'AcceptedAnswerIDs'. Hence, in the analysis part we have zero results for this category.


## Implementation

### Hardware requirements:
i) x86 64-bit CPU (Intel/AMD Architechture)

ii) 4GB RAM 

iii) 1 GB free disk space

### Software Requirements:
i) Windows 10 or 11

ii) VS Code Editor

iii) Anaconda Navigator

iv) Eclipse IDE 2021-03 or IntelliJ IDE (Latest Version).

v) Chrome Browser to access Stack Overflow.


### Validation

i) Reproducibility status in the final output file is based on the amount of modifications done during manual analysis.

ii) It is important for us to observe by reproducing the error message given by a Stackoverflow user in a particular question in order to conclusively determine whether what we are reproducing is same as what has been mentioned by the user.

### Data

**Input:** For our reproduction we have used CSV files that contain data from StackExchange API in order to perform manual analysis.

**Output:** From the above input, we try to obtain the total count of the various reproducibility status, accepted answers(exists/not-exists) and hence calculate the percentage of these present in our data.

### MSR Study enhancement

### Threat:

i) The paper encourages manual processing to identify if a stackoverflow question is reproducible or not. When manual processing is involved, generalizability is 
affected. This in turn is one of the threats posed in the paper.

ii) Since there is a small sample taken into consideration, there may be a large number of such subset samples which may come across as irreproducible. This is another
threat that can be observed.

### Traces:

References in the paper related to the threat:

Y. Tian, D. Lo, and J. Lawall. Automated construction of a software-specific word similarity database. In Proc. CSMR-WCRE, pages 44–53, 2014. 
M. L. McHugh. The chi-square test of independence. BM, 23(2):143–149, 2013.

### Theory:

i) This is a threat in general because there is no rule of generalization that can be applied since it has a low number of samples. If there are multiple samples during the manual study that cannot be reproduced, then the effort would not result in insignificant results.

ii) When there is a statistical issue such as a significance level problem, it is just hard to classify data in general because there are too many uknowns.

### Methodology: 

Since generalizability is a major threat for this paper, we would need to implement automation. Implementing automation by scraping pages in order to determine 
a question's reproducibility is complicated in itself and there must be a way to determine it using certain methods. But unfortunately it is not possible to do so and
we would be considering the 'Score' and 'Answer Count' parameters that are present in the data in order to determine the reproducibility factor in general. 

### Feasibility: 

i) We consider only java questions and not any other programming language questions in order to address the threats via our research experiment. We don't address other programming languages because the threats chosen by us and the way in which they will be addressed do not require us to do so in order for the experiment to fit the course.

ii) Parsing through each and every page to implement generalizability to the process is complicated especially when it comes to parsing through every single page 
to identify if reproduction is possible or not. Hence we have adopted the score and Answer Count parameter data from the dataset provided in order to determine 
the percentage of data that is reproducible.

### Process:

i) First we consider the dataset with Java based StackOverflow questions that we extract using StackOverflow API base.

ii) Using this dataset, we extract the 'Score' and 'Answer Count' parameter data in order to calculate the percentage of reproducibility, irreproducibility and
probably reproducible data. 

iii) Based on certain 'Score' and 'Answer Count' value, we determine if data is reproducible or not.

iv) Based on the final percentages obtained, we produce a pie chart for different cases 

    a) Pie chart for reproducibility based on 'Score' parameter.
    b) Pie chart for reproducibility based on 'Answer Count' parameter.
    c) Pie chart for reproducibility based on both 'Score' and 'Answer Count' parameter which will finally give us the exact aspect.

### Data:

i) As taken in the previous implementation of the MSR study, we have taken into consideration the same dataset i.e final_out.csv that we have consumed from 
the stackoverflow API base.

ii) This data will be used for performing all the operations as per our requirement.

### Results:

To solve the threat of generalizability, we have implemented the following steps as this process would be applicable in any scenario:

i) Production of piechart for reproducible, probably reproducible and irreproducible questions only using the 'Score' parameter which would define the validity 
of the question and how much it makes sense overall. It is similar to a rating (Ex: Movie rating). 

ii) Production of piechart with percentage ratio for reproducible and irreproducible questions only using the 'Answer Count' parameter which would define the 
number of answers given to that question. 

iii) Finally, production of piechart with percentage ratio for reproducible, probably reproducible and irreproducible questions using 'Score' and 'Answer Count' parameters which would give us the filtered result of data which would provide us the final filtered data with which we can clearly classify the data's reproducibility factor.





