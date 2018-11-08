
# Homework02: 
# Recommender System Using MovieLens Dataset

#### The goal of this homework is making movie recommendations using two basic CF algorithms: K-NN and Matrix Factorization.

### Ratings Dataset


![png](https://ws1.sinaimg.cn/large/006tNbRwly1fx0deu5h0uj30af07eaa7.jpg)


There are more ratings in score 4 and 3 than that in other scores, showing that most of users are neutralistic. However, some users might rate their favorite movies only 4 stars while some rate it as 5 stars due to personality variance.

# Collaborative Filtering Recommendation Model

## Evaluate Knn (Self-Implementation)

### Fitting time vs. Neighbor size 


![png](https://ws4.sinaimg.cn/large/006tNbRwly1fx0dejbu7lj30ce07q74h.jpg)


The running time increases as k increases.

### Mean_Absolute _Error (MAE) & Root Mean Squared Error (RMSE)
#### Primary accuracy metric : MAE


![png](https://ws1.sinaimg.cn/large/006tNbRwly1fx0det7mzqj30c207qjrq.jpg)


Observation :
The MAE of both train and test data increase as the neighbor size increases.

#### Secondary accuracy metric: RMSE


![png](https://ws2.sinaimg.cn/large/006tNbRwly1fx0de69tqej30c607qt92.jpg)


Observation :
The RMSE of both train and test data increase as the neighbor size increases.

### How does Data size impact the accuracy of KNN (Self-implement)?


![png](https://ws3.sinaimg.cn/large/006tNbRwly1fx0degzf6xj30az07q0t5.jpg)


The MAE and RMSE go down as sample sizes increases. 

### How does sample size impact the run-time of KNN (self-implement)?


![png](https://ws3.sinaimg.cn/large/006tNbRwly1fx0del9dmhj30aq07qq34.jpg)


The fitting time goes up as the sample size going up.

## Evaluate Knn by surprise
### Fitting time vs. Neighbor size 


![png](https://ws2.sinaimg.cn/large/006tNbRwly1fx0def7qicj30bo07qjrm.jpg)


As shown above, when k is around 55, the fitting time is highest, meaning that the model is most complex at this neighbor size. The lowest fitting time is at k =75 approximately. While the run time of KNN without baseline is monotonically increasing by the increment of k. 


### Mean_Absolute _Error (MAE) & Root Mean Squared Error (RMSE)

#### Primary accuracy metric : MAE


![png](https://ws2.sinaimg.cn/large/006tNbRwly1fx0dehk91gj30b807qdg3.jpg)


The MAE is around 0.67 and it changes little by the increment of neighbor size.

#### Secondary accuracy metric: RMSE


![png](https://ws1.sinaimg.cn/large/006tNbRwly1fx0deg4en7j30bi07qwes.jpg)


The RMSE is around 0.873 and it changes little by the increment of neighbor size.

#### The comparison of MAE and RMSE:

1. Since the errors are squared before taking averages, some large errors would be given higher weights. When large errors are undesirable, using RMSE to eveluate the model would be useful. RMSE increases with the variance of the frequency distribution of error magnitudes.

2. RMSE has a tendency to be increasingly larger than MAE as the test sample size increases. So this is a problem when comparing RMSE computed from different test sample sizes. 

#### The results of MAE and RMSE for our model:
We can use both MAE and RMSE to eveluate the model.

As the plot showing, MAE is much less than RMSE, which is normal. This also indicates that there are some large error outliers of the results. 

The large errors in the results means that our recommender predict completely wrong rating scores so that some users would get recommendations on movies that they don't like, which is unexpected from us. In this case, there is a approximately 0.2 difference between MAE and RMSE, which indicates that there is about 20% variance in the individual errors in the sample.




### How  does Data size impact the accuracy of KNN (by Surprise)?

Now we are trying to test how this model changes by the input data size.


![png](https://ws4.sinaimg.cn/large/006tNbRwly1fx0dev2tzhj30aw07qaai.jpg)


As the plot showing, the larger the sample size, the less MAE and RMSE.  But the MAE and RMSE of train set becomes larger as sample size increasing. 

The model overfits the train data when sample size is small. 

### How does Sample size impact the run-time of KNN (by Surprise)?


![png](https://ws4.sinaimg.cn/large/006tNbRwly1fx0deda9dcj30az07qt8y.jpg)


The fitting time increases monotonically as sample size getting larger.

## Coverage

We have 610 users, 193609 items and 100836 ratings.


![png](https://ws4.sinaimg.cn/large/006tNbRwly1fx0dee6mlcj30fe07q0t3.jpg)


## Conclusions on KNN:

* The MAE and RMSE is not bad if we choose a larger data set.
* KNN is easy to implement and produce reasonable prediction quality. However, there are some drawback of this approach:

     * cold-start problem
     * It can't deal with sparse data, meaning it's hard to find users that have rated the same items.
     * It tends to recommend popular items.


# Model-Based Collaborative Filtering
## NMF(Self-Implementation)

## Evaluate NMF (Self-Implementation)

### Fitting time vs. latent dimensions


![png](https://ws4.sinaimg.cn/large/006tNbRwly1fx0dekbah7j30aq07r0sv.jpg)


The higher the latent dimensions, the slower the fitting time of the model since the model gets more complex.

### Mean_Absolute _Error (MAE) & Root Mean Squared Error (RMSE)
#### Primary accuracy metric : MAE


![png](https://ws2.sinaimg.cn/large/006tNbRwly1fx0deemmtdj30az07qt8z.jpg)


MAE first decreases as latent dimensions increase. Then MAE increases with the increment of latent dimensions. 

The lowest MAE occurs at latent dimension = 12

#### Secondary accuracy metric: RMSE


![png](https://ws4.sinaimg.cn/large/006tNbRwly1fx0deagz0aj30b607q3yu.jpg)


The trend of RMSE by latent dimensions is similar with MAE. But the RMSE are lower at both latent dimension =2 and =12 than other values of latent dimension. 

### How does Sample size impact the accuracy of NMF?


![png](https://ws4.sinaimg.cn/large/006tNbRwly1fx0deiigzoj30at07qgm1.jpg)


When sample size is small, the model overfit the train data. 

### How does Data size impact the run-time of NMF?


![png](https://ws4.sinaimg.cn/large/006tNbRwly1fx0de5kub8j30at07qaa9.jpg)


As the sample size increases, the model is getting more complex. 

### Conclusions:
* The average MAE of test data is around 0.67, which is similar with the results from KNN.
* However, NMF can capture the multi cause confounding factors that influences the rating scores.



# SVD by surprise

## Evaluate SVD by surprise

### Fitting time vs. hyper-parameters


![png](https://ws3.sinaimg.cn/large/006tNbRwly1fx0de8mn0zj30ap07edg3.jpg)


As the plot showing, there is no pattern of relationships between fitting time and learning rate at a fixed regularization. The SVD model's fitting time has no strong relations with the learning rate and regularization.

### Mean_Absolute _Error (MAE) & Root Mean Squared Error (RMSE)
#### primary accuracy metric : MAE


![png](https://ws1.sinaimg.cn/large/006tNbRwly1fx0de9jhtij30av07ewep.jpg)


As we can clearly see in the plot, increasing learning rate causes lower MAE on test data at each level of regularization. The heavier weight of the regularization, the lower the MAE.

#### secondary accuracy metric : RMSE


![png](https://ws4.sinaimg.cn/large/006tNbRwly1fx0debfferj30ao07e3yp.jpg)


The trend of RMSE is similar with MAE. RMSE goes down as more regularization is enforced.

### How does Data size impact the accuracy of SVD?


![png](https://ws4.sinaimg.cn/large/006tNbRwly1fx0de7p5uzj30at07qaai.jpg)


The model overfits the training data very easily when the training set is small. 
MAE and RMSE is getting smaller when sample size increases.

### How does Data size impact the run-time of SVD?


![png](https://ws4.sinaimg.cn/large/006tNbRwly1fx0deccxsrj30aq07q0sx.jpg)


The smaller the sample size, the faster the model fits. 

## Coverage


![png](https://ws2.sinaimg.cn/large/006tNbRwly1fx0de6yr3nj30fe07qq3c.jpg)


### Conclusions on SVD model:
#### Effect of hyper-parameters:
* Running(fitting) time: The learning rate and regularization does not affect the fitting time but sample size does.
* SVD model tends to overfit train data when sample size is small.
* MAE and RMSE goes down as more weights on regularization and under less learning rates.
#### Drawbacks of SVD：
* Large number of free parameters which makes finding a good set of parameters that will work good for all cases is very hard.




# Conclusions:

### Factors that matter in a recommendation algorithms in HW2:
#### * Accuracy: 
       * It matters that the accuracy of a recommender is good, since we wouldn't like the users receives a recommendation that he don't like, which would cause the reduction of engagement of users.
#### * Fitting time:
       * In a real world project, the dataset is usually large. It's significant that the fitting time is as efficient as possible without hurt of performance.

#### * The best parameters:
       * In order to have good performance, we need to train the model by finding a good set of parameters.
       * For KNN, the best neighbor size is 
       * For SVD, the 
       * For NMF


#### In order to make business decision on choosing a recommender, we need to leverage these three factors to choose our models.

* Accuracy: The average MAE of KNN, NMF, and SVD in this case are all around 0.67.
* Fitting time: 

      When sample size is small (20000) : The fitting time of KNN and SVD are faster than NMF.
      When sample size gets larger (100000) : The fitting time of NMF are less than other two models.
* Hyper-parameters:
  ​    SVD has lots of free parameters. If we are facing a large dataset, it will take lots of time and efforts to find a set of parameters that best fit the model. 
  ​    For KNN, since the dataset we use is small, the MAE or RMSE does not change much when neighbor size gets larger. For a real world problem with a large or a sparse dataset, it's hard to find users that have rated the same items.
  ​    

