# Project 5: Exploration of migraine pathologies with DNNs

## **August 3, 2019** Finding a Problem Statement and Central Question
It is essential to word your question correctly in order to determine the architecture of your model. With all the research I had done and a general problem statement, 
I had many ideas as to what my project could turn out to be. Thus, I found a condensed explanation of types of questions that machine learning can answer.
Machine Learning Algorithms can be split into three families: Supervised Learning, Unsupervised Learning, and Reinforcement Learning.

![image](https://user-images.githubusercontent.com/67920563/89221067-a486c200-d5a0-11ea-91ac-42478aa762b5.png)

In my research, I only came across machine learning models that were two-class classification problems. For example, the study using AlexNet classified images as either healthy
or a migraine brain. 
Because I would like to conduct a project with both anxiety and migraine data, I could train a classification model to decipher between migraine and anxiety or indicate comorbidity. 
However, I am not sure I have that data available, as I would have to find MRI scans in which both are present. Secondly, it is unknown as to how imaging is truly beneficial to diagnosis of
migraines. Since a correlation between migraines and anxiety is already established, it would generally be more productive for a doctor to question the patient.
I am thus trying to apply this into a research field rather than a simple diagnosis classification. Another use of a classification model would be by taking a possible biomarker
such as grey and white matter ratio and training a model to detect whether there is an abnormality in the ratio or not/find the ratio. Although this could 
save time, there are current methods of measuring this material already, thus not really contributing much.
I could make a supervised learning model with regression; rather than stating, "Which of the following is a biomarker for migraines and anxiety?", I could ask, 
"How likely is it that each possible biomarker correlates with migraines and anxiety?". This would give me some sort of ranking or regression model which could narrow down areas of the body to look 
in for explanation of the known correlation.  
Reinforcement learning wouldn't really fit the question here; perhaps it could be used to test medication or treatment options for migraines.
Unsupervised Learning using dimensional reduction may be the optimal model type for this project; since I have possible biomarkers of anxiety and migraines, I can answer the question: 
"Which biomarkers tend to occur together?". This algorithm would simplify the many possibilites of biomarkers out there for a human analyst. 

## **August 4, 2019** Describing the Data
- Features:
- Target: 
- Type of Data: Continuous and Nominal Data
- Data Summary:


## Architecture
- pairplot
- correlation matrix/heatmap
-PCA w standard scaling
- clustering with AHC/ dbscan/ kmeans
