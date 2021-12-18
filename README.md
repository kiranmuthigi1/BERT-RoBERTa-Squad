# Studying Weakly Supervised Models Performance - BERT (+modifications) with SQUAD

## Description:

Problem statement: To compare the performance of pre-trained weakly supervised models (BERT, RoBERTa) on Question-Answering tasks with different hyperparameter settings and fine tuning.

Solution approach: We design solutions where we train different pre-trained BERT models over SQUAD dataset after stacking them with Deep NNs to extract start and end pointers for the answer. We then proceed to compare their results.

Value/benefit of your solution: Our solution helps in understanding which hyperparameters work better with BERT for SQUAD and whether RoBERTa which in theory should perform better in weakly supervised scenarios, performs better than BERT here. 

## Performance:

We rank in top 16 of all models on SQUAD dataset.

Our F-1 score (89.4%) beats Google’s BERT Large (82%).

## Use Case Example - Optimizing search engine user experience:

An exciting use case of Question Answering Models is improving the User experience in search engines.
Let’s say the user searches for a question in the search engine. Now the search engine will fetch a list of links for the user which might have the information that the user seeks.

How do we guide the user as to what are the contents of the link that might interest the user. It is impractical to expect the user to click on all of them to look at their contents and see if a subtext answers their question.

There are two possible ways to go about this:

Show any random or first few lines from the text in that link.

Apply the QNA model to it, extract the best matching subtext which would likely answer the user’s query and display it along with the link in the UI.

## Approach:

Here is the solution diagram:

<img width="867" alt="Screen Shot 2021-12-17 at 11 51 53 PM" src="https://user-images.githubusercontent.com/33013911/146629697-fe586357-0a44-45d7-a71d-6dfe451b0446.png">



## About this repo:

This has two folders: Data and Scripts. The data folder has all the epoch-scores (F1 score and EM score) for all the 18 combinations (split up by constant and decay learning rate).

The scripts folder has all the notebooks for all the 18 combinations (split up by constant and decay lr).

## Running this code:

We recommend running these notebooks on a TPU on Google Colab. The Colab has cells to install any dependency that we may need (transformers, tokenizers, etc). In data, we provide vocab and merge files for RoBERTa.

## Results:

Here are the outputs for all the 18 models trained by us:


<img width="527" alt="Screen Shot 2021-12-17 at 7 55 16 PM" src="https://user-images.githubusercontent.com/12792573/146629304-b7696ef7-e0e8-4f4c-9bab-69dc59ab03bf.png">
<img width="514" alt="Screen Shot 2021-12-17 at 7 57 05 PM" src="https://user-images.githubusercontent.com/12792573/146629305-db477029-4757-4b6b-8e68-650b8caa7a77.png">
<img width="648" alt="Screen Shot 2021-12-17 at 7 59 37 PM" src="https://user-images.githubusercontent.com/12792573/146629306-692086db-fd20-4bea-9323-48f3ffc109df.png">
<img width="572" alt="Screen Shot 2021-12-17 at 8 08 42 PM" src="https://user-images.githubusercontent.com/12792573/146629308-042372d7-6008-48aa-b932-e38855b43184.png">
<img width="648" alt="Screen Shot 2021-12-17 at 8 10 28 PM" src="https://user-images.githubusercontent.com/12792573/146629309-2eb59566-a0d2-4daa-ba31-6bfc26c3f4a2.png">
<img width="691" alt="Screen Shot 2021-12-17 at 9 07 30 PM" src="https://user-images.githubusercontent.com/12792573/146629310-b9ca942a-e4ea-45fa-be8e-537054dcfd3c.png">

## Observations:

1. RoBerta with last 3 embedding layers average, batch size of 64 and decay learning rate performs the best among all the models.

2. This model gives an Exact Match score of 81.4 and F-1 Score of 89.4.

3. Varying batch size have negligible effect on the performance.

4. This shows us that RoBERTa is better at generalization than traditional BERT and that RoBERTa should be preferred over BERT for weakly supervised cases.
We have seen some advantage of using decay lr over constant lr. The gain in score is small, but cannot be ignored.



