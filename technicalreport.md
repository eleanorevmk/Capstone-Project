Technical Report: Final Capstone Project
Eleanore van Marwijk Kooy - CHI
December 18th, 2017

	Travelers want to spend the least amount of time en route and more time enjoying their final destination! My intention with this project is to predict whether or not a flight will be delayed, and to what extent (how many minutes).

When approaching this project, I was overwhelmed and shocked by the sheer quantity of data. From 2015 alone, there were almost 6 million individual observations.The U.S. Department of Transportation's (DOT) Bureau of Transportation Statistics annually tracks the performance of large airlines domestically. The reports are published monthly in the Air Travel Consumer Report. This dataset was originally published on Kaggle as 3 distinct CSV files which I had to concatenate. I imported, performed EDA on, and cleaned the entire data set, but for processing time purposes I took a sample of 50,000 randomly sampled observations to perform my modeling, and train test split.
	
The data needed quite a bit of manipulating during EDA and pre-processing, including removing unnecessary features, rows and columns where a large quantity of null values existed. There was no need to impute or use another method for addressing nulls because, even after having removed the nulls, there were still over 5 million individual observations. I had to concatenate the 3 CSV files and merge them on IATA (spell ot) codes to make one large data frame I could manipulate. My X variables were all my features that I thought would influence flight delays: month, day of the week, airline, origin and destination airport, taxi time out, scheduled time, elapsed time, distance, and taxi time in. My target variable (y) was a column called Arrival Delay: this was the difference between actual arrival time and expected arrival time, in minutes (a negative value would indicate the flight arrived early, a zero meant the flight arrived as expected, and a positive value signified a delay was present).
	
For regression, I chose a Random Forest Regressor and a Gradient Boosting Regressor models. For classification, I investigated the Random Forest Classifier, Gradient Boosting Classifier, Support Vector Machine, and Logistic Regression. HYPERPARAMS. A high R^2 value was what I determined success by for Regression. For classification models, I used accuracy score (Accuracy = N Predicted correctly / N All observations ). 
In the future, I think it would be beneficial for me to run the model with the entire 5 million data points or a larger cross section of data. This would allow me to continue exploring my knowledge of Amazon Web Service (AWS) cloud computing. Additionally, it might be interesting to investigate possibilities with building a recommendation engine that suggests the flight with smallest chance of delay. I would use clustering (unsupervised learning). Another method to consider would be to use groupby method to group certain features. For example, I might group airports by ‘major’ (larger/busier) airports and smaller (more regional, seeing less travelers), or possibly group months by seasons (quarterly).

What did you do for pre-processing; backing up assumptions (correlation matrix or common sense); domain knowledge
Mention why I did both regressor and classifier; and say which one you chose best (actual score, best final result, and why)
Confusion matrix and classification reports
Two distinct sections for modeling (classifier vs. regressor)
*A delayed flight was one that arrived 1+ minutes later than the expected arrival time






