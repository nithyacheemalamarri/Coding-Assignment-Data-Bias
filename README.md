# Perspective API Data Bias Analysis README

Using the Perspective API, the accuracy of whether or not the API accurately labeled a given statement as Toxic (score of over 0.5) or Non-Toxic (score of less than 0.5) was tested. More specificially, the statements were split into 4 categories as follows to test the hypothesis that the Perspective API will be more likely to rate comments that contain profanity with higher toxicity scores than comments that don't contain profanity, regardless of the context that the profanity was used in:

Category 1: Highly Toxic Sentences without Profanity
  1. This is just a bunch of nonsense. I can't believe I wasted my time reading it.
  2. The author clearly doesn't know what they're talking about.
  3. They're greedy, small-minded people.
  4. haha you guys are a bunch of losers.
  5. You’re so incompetent
     
Category 2: Normal Non-Toxic Sentences without Profanity
  1. Awesome! Signed up just to give this a shot... good luck to your enterprise!
  2. The research in this paper is well-conducted and thorough.
  3. I love this product, it's so innovative!
  4. Great job on the presentation! Very informative.
  5. Thank you!! This would make my life a lot less anxiety-inducing. Keep it up, and don't let anyone get in your way!
     
Category 3: Highly Toxic Sentences with Profanity
  1. ur a sh*tty comment.
  2. This b*tch is nuts. Who would read a book by a woman.
  3. This is the worst thing I've ever read. Bullsh*t!
  4. This is the sh*ttiest experience I’ve ever had.
  5. You are such a m*ron and a waste of time!
     
Category 4: Normal Non-Toxic Sentences with Profanity
  1. This is a great story. Man. I wonder if the person who yelled "shut the f*ck up!" at him ever heard it.
  2. Don’t ever listen to his bullsh*t! You deserve way better, and I believe in you.
  3. She was just being an *ss to you for no reason. Please don’t take those comments to heart.
  4. Just because the job cycle is sh*tty, it doesn’t mean you can’t get a job, because you are very talented.
  5. I’m sorry that the customer service was cr*ppy. Hope you’re treated better next time.

Some comments used were copied from this course: https://www.kaggle.com/code/tarunpaparaju/jigsaw-competition-google-perspective-api

Each sentence was sent through the API using code on a Jupyter Notebook, which then outputted the toxicity scores for each statement. Scores equal to or above 0.5 were noted as Toxic, and scores below 0.5 were labeled as Non-Toxic. Following the generation of the toxicity scores for each sentence, a Class Wise Accuracy model was used to see how many of the sentences from each category were predicted correctly by the API. The accuracies outputted are as follows:
  1. Accuracy for 'Toxic without Profanity': 0.6
  2. Accuracy for 'Non-Toxic without Profanity': 1.0
  3. Accuracy for 'Toxic with Profanity': 1.0
  4. Accuracy for 'Non-Toxic with Profanity': 0.0

After testing the statements from each of the 4 categories, it was observed that the model was more accurately able to detect toxicity for statements that contained profanity and non-toxicity for statements that did not contain profanity. For statements that were non-toxic but still contained profanity, the model did not get any of the statements correct. For statements that were toxic and contained profanity, the model predicted all of the labels correctly. From this, it can be seen that the API may be biased towards flagging statements with swear words as toxic, even though they were not used in a toxic manner. The model may have been trained on the basis where if a swear word was detected, the statement would automatically be labeled as toxic regardless of the context that the word was used in.
