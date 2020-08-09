![image](https://user-images.githubusercontent.com/67920563/89736518-f5326b00-da37-11ea-971c-9f70b87a4b18.png)

## Abstract
Have you ever been to a doctor and not known how to describe what your feeling? Poor communication between patients and their doctors is one of the leading causes of misdiagnoses, and even death! Because of the lack of known tests, disorders such as migraines and anxiety can only be diagnosed by the patient’s description of symptoms. Thus, it is important to find biomarkers, or measurable indicators of a biological process, for these disorders. Migraines are reoccurring headaches that may cause nausea, vision loss, sensitivity to light, mood changes, and auras; they affect 12% of the world’s population. 50% of Migraine patients are diagnosed with an anxiety disorder. Thus, by examining whether these two disorders share possible biomarkers, we can learn more about the nature of this correlation, as well as how different or similar these two disorders. I applied methods of PCA, Hierarchical clustering, Binomial Regression, and Gradient Boosted Trees to attempt to distinguish each disorder based on possible biomarkers. 

##  Finding a Problem Statement and Central Question
It is essential to word your question correctly in order to determine the architecture of your model. With all the research I had done and a general problem statement, 
I had many ideas as to what my project could turn out to be. Thus, I found a condensed explanation of types of questions that machine learning can answer.
Machine Learning Algorithms can be split into three families: Supervised Learning, Unsupervised Learning, and Reinforcement Learning.

![image](https://user-images.githubusercontent.com/67920563/89221067-a486c200-d5a0-11ea-91ac-42478aa762b5.png)

In my research, I only came across machine learning models that were two-class classification problems. For example, the study using AlexNet classified images as either healthy
or a migraine brain. 
Because I wanted to conduct a project with both anxiety and migraine data, I could have trained a classification model to decipher between migraine and anxiety or indicate comorbidity with MRI scans. However, I did not have that data available, as I would have to find MRI scans in which both are present. Secondly, it is unknown as to how imaging is truly beneficial to diagnosis of
migraines. Since a correlation between migraines and anxiety is already established, it would generally be more productive for a doctor to question the patient.
I thus tried to apply this into a research field rather than a simple diagnosis classification. Another use of a classification model would be by taking a possible biomarker
such as grey and white matter ratio and training a model to detect whether there is an abnormality in the ratio or not/find the ratio. Although this could 
save time, there are current methods of measuring this material already, thus not really contributing much.
I could have made a supervised learning model with regression; rather than stating, "Which of the following is a biomarker for migraines and anxiety?", I could ask, 
"How likely is it that each possible biomarker correlates with migraines and anxiety?". This would give me some sort of ranking or regression model which could narrow down areas of the body to look 
in for explanation of the known correlation.  
Reinforcement learning wouldn't really fit the question here; perhaps it could be used to test medication or treatment options for migraines.
Unsupervised Learning using dimensional reduction was the optimal model type for this project; since I have possible biomarkers of anxiety and migraines, I can answer the question: 
"Which biomarkers tend to occur together?". This algorithm would simplify the many possibilites of biomarkers out there for a human analyst. 

## ** Describing the Data** 
- Features: Glutamate, ceramides, LDL cholesterol, cortisol, ionized magnesium levels, Neocortical 5-HT4 Receptor Binding (which is related to serotonin levels), Systolic Blood Pressure, Volume of the Amygdala and Hippocampus
- Label: Migraine & Anxiety
- Type of Data: Continuous and Nominal Data
- Observations: 40
- Data Summary:
Biomarkers, or measurable indicators of a biological process, can be anything from body temperature, blood pressure, genetic measurements, blood sampling, and other biochemical processes. In this particular project, I made a list of ~60 possible biomarkers, and selected 9. Glutamate, ceramides, LDL cholesterol, cortisol, and ionized magnesium levels can all be measured through blood sampling. Neocortical 5-HT4 Receptor Binding (which is related to serotonin levels) and Volume of the Amygdala and Hippocampus can be measured through brain imagery. My data had 40 observations, 9 features, and 2 labels. All of the data is continuous with the exception of labels. Because of the lack of free data available, I had to generate my own data set using known statistics and facts about each one. Thus, the data should be in a general ball park of what actual data would look like.

![image](https://user-images.githubusercontent.com/67920563/89733999-3f5f2080-da27-11ea-89dd-5569ad4999c9.png)

As seen in the heat map, there is low correlations between the features. The highest correlation (0.66) lies between ceramide concentration and neocortical 5-HT4 receptor bindings. The lowest correlation (0.02) lies between ceramide concentration and Systolic BP.

![image](https://user-images.githubusercontent.com/67920563/89734009-530a8700-da27-11ea-9311-b5969742df35.png)

From the pair plot, we see a lot of positive linear trends between the variables particularly with the migraine data.

## Methods

![image](https://user-images.githubusercontent.com/67920563/89734059-a2e94e00-da27-11ea-912f-984aaeca741d.png)
![image](https://user-images.githubusercontent.com/67920563/89734072-b4caf100-da27-11ea-8540-ce20ace8a35e.png)
![image](https://user-images.githubusercontent.com/67920563/89734296-47b85b00-da29-11ea-99fd-3ada86640e43.png)
The data was then standardized and dimensionally reduced with PCA. Only 45% of the data was explained by the first two principle components, thus not providing a very accurate model. However, the two most important features were determined to be Neocortical 5-HT4 binding and LDL Cholesterol. Low 5-HT4 serotonin receptor bindings have been identified by studies as a possible result of migraines, and thus is suggestive of higher brain serotonin levels following a migraine attack. On the contrary serotonin deficiencies have been linked with anxiety disorders. Migraines and anxiety have also been linked with high LDL cholesterol.


![image](https://user-images.githubusercontent.com/67920563/89734094-eb087080-da27-11ea-9eda-f7440e7f9b8c.png)

Agglomerative hierarchical clustering was chosen due to the fact that combinations of features selected together on height 1 and 2 can offer insight into the necessary conditions for migraines and anxiety to develop. There are two main clusters in the dendrogram; one could argue that three are possible. The green group represents anxiety disorders while the red represents migraines. Overall only four data points are misclassified, leading to about a 90% accuracy.

### AHC/PCA Graph vs. PCA
![image](https://user-images.githubusercontent.com/67920563/89734116-13906a80-da28-11ea-9b30-cb7d3a72347a.png)
![image](https://user-images.githubusercontent.com/67920563/89734119-18551e80-da28-11ea-82fa-efd2aedcd81c.png)

Although current biomarker research tends to use the past clustering methods, Binomial Regressions and Boosted Trees Classifiers can provide more information about the features. Although I did manage to run each of these models, I’ve encountered an error where my accuracies were all 1's, losses were all 0's, and DFC table is all zeroes. I think the error lies with how I formatted my data set. I will include my code in the repository, but I couldn't continue with the error detection due it already being 4 am.
Because the dependent variable is discreet in a binomial regression, the labels 0 and 1 were given to the two disorders. The data was split into training and testing sets in a 50:50 ratio. Because I did not have too much data starting out, I generated another 40 observations as a test set. We do not need one hot encoding, as I was only using numeric columns. After creating an input function, I trained the model as a linear classifier with 100 steps and optimizer FTRL, an optimizer that updates the weights after every decision in order to reduce regret, or the difference between actual lost vs least possible loss. For Boosted Trees, it is suggested to start with as many trees as possible, and tune the trees to between 100-500 with about 2-5 terminal nodes. Choosing between boosted trees and binomial regression depends on the type of data and the number of outliers.

A directional feature contribution data table will best be able to compare the data to the findings from the PCA and Clustering Analysis.
Using a bar plot and a violin plot such as the one from the titanic data set, we are able to see which features are most important to the model. Had my DFC table not been full of zeroes, I would have had some interesting results!


With the newfound information about the importance of certain features derived from both Machine Learning methods, we can narrow down biomarkers the two disorders may have, as well as finding similarities between them. The PCA study identified two important biomarkers: neocortical 5-HT4 binding and LDL Cholesterol. Had we output from the Boosted Trees Estimator, we could have confirmed whether these were truly important in distinguishing the two disorders. Because the cause and correlation between anxiety and migraines is unknown, one could derive information from the biomarkers that were not deemed as important distinguishers. For example, if cortisol levels did not serve as a good distinguishers but are known to be different than healthy subjects in both disorders, this could possibly signify a similarity. Meanwhile, biomarkers that strongly served to distinguish the two disorders could signify that there is no similarity in cause between the two disorders. Thus, healthy patient data should be added in the future.
With the newfound information about the importance of certain features derived from both Machine Learning methods, we can narrow down biomarkers the two disorders may have, as well as finding similarities between them. The PCA study identified two important biomarkers: neocortical 5-HT4 binding and LDL Cholesterol. Had we output from the Boosted Trees Estimator, we could have confirmed whether these were truly important in distinguishing the two disorders. Because the cause and correlation between anxiety and migraines is unknown, one could derive information from the biomarkers that were not deemed as important distinguishers. For example, if cortisol levels did not serve as a good distinguishers but are known to be different than healthy subjects in both disorders, this could possibly signify a similarity. Meanwhile, biomarkers that strongly served to distinguish the two disorders could signify that there is no similarity in cause between the two disorders.

## Reflections, Improvements, and Continuation 
I must say I have a few regrets with this project. In Data Science 146, our professor had told us that his best definition of data science is inputing an X and a Y, and the model would tell us the relationship/rule between the two (6X+3Y=9). I think I may have taken this a little bit too literally, and wanted the model to cook up a perfect recipe telling me why exactly migraines and anxiety are correlated. When this project was mentioned at the beginning of the summer, I had already started thinking of what I could do, since I **love** any application based research/projects. Unfortunately, since the summer was very high paced, I didn't get to put in as many hours as I had expected. Thus, even though I probably read like a hundred different things, I felt like my ideas were still in a premature state. A lot of the things I was reading had a lot of high level math/biology/data science that I didn't understand and had very little time to try to understand. There really wasn't a study with migraines that I could particularly base this project off of, so I was looking at a lot of other biology applications of machine learning to try to find a path. If I had to take this into the future, I would: 
- try to get some real data by changing the topic to a field where the data *is* there and stating that this could be transfered into the area of migraine research
- adding control data (healthy patients!) and looking for bigger data sets
- learn a lot more about how hierarchical clustering is applied (literally everything I was reading was some high level stuff that we didn't cover, there really are a million ways to process and then re-process data and send it to all sorts of places! There were so many nested algorithms it was a little too complex)
- simplify, simplify, simplify! I did not have a problem statement that was clear and cut out, and so I was overwhelmed with solving a gigantic problem!
- try to not hold on to an idea so strongly. I feel like I had many chances to change my topic, simplify it, or go into a different direction. There were definitely moments where I knew that I was in over my head and needed to simplify for the sake of the project, and I refused. Although that can be helpful at times, I ended up with a lot of regret and lack of fulfillment from the project since it feels highly unfinished. Had I done a more simple topic but a much more thorough analysis, I perhaps would have felt more confident in my application. I feel like I have many more ideas of how I could potentially do this in the future, but they are all at early stages and unclear. I know that I wanted to do something with combinations of biomarkers and I had some notion that I could make an optimization algorithm for it, but I still haven't really sorted out how to best do that. 

Overall, I am happy with everything I have learned in this class. I wish I had more time, and that I wasn't a senior. Had I had a year to do this project, I know I would have felt better about my results and found a more clear cut direction. I feel like machine learning is an incredible tool for me to use in the future, and my mind literally cannot stop thinking of the hundreds of applications that haven't even been done yet! I guess that's the exciting part of being in a relatively new field. Many more things to be done!
