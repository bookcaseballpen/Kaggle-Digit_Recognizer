# Kaggle-Digit_Recognizer
<<<<<<< HEAD
=======
library(caret)
library(rpart)

train<- read.csv("train.csv")
test<- read.csv("test.csv")

seperate testing set and training set


inTrain<- createDataPartition(train$label,p=0.6,list=F)
training<- train[inTrain,]
testing<- train[-inTrain,]
training$label<- as.factor(training$label)
testing$label<- as.factor(testing$label)

filter out non-critical elements base on the training set, use tree list method for the predcition. I feels is problem is not a regression problem.

fitrt<- train(label~.,method="rpart",data=training,tunelength=50)
fitknn<- train(label~.,method="knn", data=training[sample(1:25201,5000),-nearZeroVar(train)])
predictions<- predict(fitrt, newdata=testing)
confusionMatrix(prediction, testing$lable)



The accuracy is 70%

I changed the tunelength to 80, the acurracy increased to 81%, seems the predication is no the right track. well test on different tunelength and try to reach around 97% for the first submission.

I will try different method in next step.

after servrial run trying on rpart, I found the level of tree did not increaed the presentage too much.

therefor I found another method only called knn. K-nearest neighbors algorithm.
with 500 sample test, the result hits 84% 5000 sample at 93%

Use verboseIter to see the progress
set trainControl()




>>>>>>> e2e8a5b... till first submission
