# July 29, 2020

## Using NLP to build a sarcasm classifier
1. **Question 1:** Pick two or three news sources and select a few news titles from their feed (about 5 is likely enough).  For example you could select CNN, Fox News, MSNBC, NPR, 
PBS, Al Jazeera, RT (Russia Today), Deutsche Welle, Facebook, BBC, France24, CCTV, NHK World or another source you wish you analyze.  Run your sarcasm 
model to predict whether the titles are interpreted as sarcastic or not.  Analyze the results and comment on the different news sources you have selected.

-	I picked two sources from CNN, one source from the Onion, and one from Fox News (the sentence list is in this respective order). I must say I’m a little upset with the sarcasm detector, since it said that the MOST sarcastic/satirical “news” network was the LEAST sarcastic!!! If this is a good model, then I’m quite taken aback by the lack of quality in news systems here!
-	Looking at the results, the first CNN headline about the FBI is the most sarcastic, although still not very much so (e -02)
-	The other two CNN & Fox headlines had about the same results; they were not very sarcastic at all (e -06)
	The Onion (in a sudden turn of events) was the least sarcastic, even though the title was pretty sarcastic in my opinion (e -10) ! 
-	Overall I would say that the model did not do a good job. I can’t really tell if the second CNN source is sarcastic or just sassy; either way I expected it to be a little bit more sarcastic than the Fox report about DC schools. I amn’t sure why it picked up the first one as the most sarcastic either. 

## Text generation with an RNN
2. **Question 2:** Use the generate_text() command at the end of the exercise to produce synthetic output from your RNN model.  Run it a second time and review the output.  How has your RNN model been able to “learn” and “remember” the shakespeare text in order to reproduce a similar output?

- The model predicts the next character in the sequence of Shakespeare’s writing. The model maps strings into numerical representations; it creates two tables converting each from the other. The predicting begins by choosing a string and setting the number of characters to generate. Then, the prediction distribution of the next character is given using the beginning string. A categorical distribution is used to calculate the index of the predicted character, which is then used as the next input to the model. Because the output is fed back into the model, the model learns more about context of the text. Thus, the model will learn when to capitalize characters, insert paragraph indents, and use similar vocabulary. Different starting strings will affect the outcome. Although the output is different, it maintains similar characteristics.

## Neural machine translation with attention
3. **Question 3:** Use the translate() command at the end of the exercise to translate three sentences 
from Spanish to English.  How did your translations turn out? 

 
