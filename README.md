# AdultIncomePredictionModel

[Project Slides](https://docs.google.com/presentation/d/1wlX1ak79aP0rGmflBEt2sHieJBmz0I-9mw0_XTRJn8c/edit?usp=sharing)

The dataset we used comes from the UCI Machine Learning Laboratory with 14 variables and over 30000 entries
https://www.kaggle.com/code/aditimulye/adult-income-dataset-from-scratch/notebook 

We built a model that predicts the income of adults based on 14 different variables.
After running many tests and predictions, we have concluded that migitating bias with this small dataset would be hard to do without creating lots of synthetic data. When our prediction model was actually working, it was predicting pretty well with the underlying distribution of our data. One of our biggest problems in this project was the prediction model as it kept getting different results everytime it was run. This may be seen when reviewing the project as rerunning the notebook will produce different results than what is seen on our side.

The first step we took after realizing the fairness inequality in our dataset was resampling our data to only white and black people as those two groups were the only groups above 2000 records. This move slightly balanced the dataset more; however, we still had the issue of not having enough entries with more than a 50,000 dollar income. The split was about 78% less than 50,000 and 22% more. With this in mind, our model could predict 0's on everything and get a minimum score of around 78%.

Our next step was to figure out if our models had any mistakes with either overfitting/underfitting or just producing large coefficients for very few features. This caused us to create some regularization by adding dropout layers to our prediction model. After doing so, we saw a few more 1's (more than 50,000 dollar income) get predicted.

Our last step was analyzing the fairness of our model, this was dependent on the predictions created by our model which often came out as producing all 0's. This caused a large issue in analyzing the fairness, but we had a couple tests where our model worked and gave us very similar distributions in predicted values to the real values which we thought was pretty fair according to the data that was given.

If we had more time, we would change a couple things. The first being the model we used. After completing assignment #3, we realized that it is very possible to create a good model with this dataset, we were just headed in the wrong direction. That being using a custom model rather than the XGBoost model which was provided to us in the last assignment. The second change we would make would probably be learning more about aequiatas and understanding how to compute the fairness in our model properly. Even though this step was dependent on our model, We don't think we had the proper tools to mitigate the bias without help from the professor or TA
