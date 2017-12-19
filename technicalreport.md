Technical Report: Final Capstone Project
Eleanore van Marwijk Kooy - CHI
December 18th, 2017

	Travelers want to spend the least amount of time en route, struggling with delay flights and cramped quarters, and more time enjoying their final destination. My intention with this project is to predict whether or not a domestic flight will be delayed, and to what extent (how many minutes). When approaching this project, I was overwhelmed and shocked by the sheer quantity of data. From 2015 alone, there were almost 6 million individual observations.The U.S. Department of Transportation's (DOT) Bureau of Transportation Statistics annually tracks the performance of large airlines domestically. The reports are published monthly in the Air Travel Consumer Report. This dataset was originally published on Kaggle as 3 distinct CSV files which I had to concatenate. I imported, performed EDA on, and cleaned the entire data set, but for processing time purposes I took a sample of 50,000 randomly sampled observations to work with.
	
The data needed quite a bit of manipulating during EDA and pre-processing, including removing unnecessary features, rows and columns where a large quantity of null values existed. There was no need to impute or use another method for addressing nulls because, even after having removed the nulls, there were still over 5 million individual observations. I concatenated the 3 CSV files and merged them on IATA (three-letter airport identifier codes) codes to make one large data frame I could manipulate. There were some features that, because of domain knowledge, I was able to remove entirely: they were either irrelevant to predicting my target variable or had an inherent correlation that would give my model an accuracy that was much too high. My X variables were all my features that I thought would influence flight delays: month, day of the week, airline, origin and destination airport, taxi time out, scheduled time, elapsed time, distance, and taxi time in. My target variable (y) was a column called Arrival Delay: this was the difference between actual arrival time and expected arrival time, in minutes (a negative value would indicate the flight arrived early, a zero meant the flight arrived as expected, and a positive value signified a delay was present). I dummied out all the airlines, the airports, and the days of the week, and months.
I initially was only going to do a classification model that determined whether or not a flight would arrive on early/on-time or late. However, for an additional challenge,  I decided to try and predict the I scaled because the variance because the variables are quite high. I train test split to validate your model to make sure my model could perform well on unseen data. Deciding it would be wise to use fewer features (I had over 700 because of all the dummy variables) and thus prevent overfitting and artificially high R^2/accuracy scores, I investigated feature importances and decided to use the top 20 as my X features.
	Regression
For regression, I chose a Random Forest Regressor and a Gradient Boosting Regressor model. I tried using Gradient Boosting Regressor but my most accurate R^2 value resulted from a Random Forest Regressor model: 0.889. This means that approximately 89% of the variance in my data could be explained by my model.
Classification
For classification, I investigated the Random Forest Classifier, Gradient Boosting Classifier, Support Vector Machine, and Logistic Regression. Gradient Boosting Classifier yielded the highest score of 0.896. To determine success for my Classification models, I used accuracy score (Accuracy = N Predicted correctly / N All observations ).

Next Steps and Future Implementation

In the future, I think it would be beneficial for me to run the model with the entire 5 million data points or a larger cross section of data. This would allow me to continue exploring my knowledge of Amazon Web Service (AWS) cloud computing. Additionally, it might be interesting to investigate possibilities with building a recommendation engine that suggests the flight with smallest chance of delay. I would use clustering (unsupervised learning). Another method to consider would be to use groupby method to group certain features. For example, I might group airports by ‘major’ (larger/busier) airports and smaller (more regional, seeing less travelers), or possibly group months by seasons (quarterly). 

A delayed flight is defined as one that arrives at the gate 1 or more minutes after the expected arrival time. In the future, I may consider redefining what I thought to be “delayed” and alter the threshold, perhaps giving flights a window of +/- five minutes to be considered ‘on-time’.

Confusion Matrix Interpretation:
True Negatives: 10,0061 times the model correctly predicted there was no delay
False Negatives: 1,227 times the model incorrectly predicted there was no delay when there actually was
False Positives: 484 times the model predicted there was a delay when there was none.
True Positives: 4,728 times the model correctly predicted there was a delay 

I was hesitant about including the column “Departure Delay” as I suspected it may be contributing to my strong scores. However, I did some research and realized there was something important to consider. Airlines have a practice of ‘cushioning’ flight times: this means that the total flight time that is advertised is actually greater than they expect it to be: airlines account for small delays during boarding, traffic during take-off and taxi, etc; Thus, I decided to include the column “Departure Delay” because a flight that departs late does not necessarily mean it will arrive late because of the ‘grace period’. Additionally, some airlines cushion more than others so it would be difficult to account for the varying degrees of cushioning. I would also like to implement a GridSearch and build in a pipeline. 




