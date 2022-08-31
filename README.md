
# Chennai House Price Prediction

This project is regarding the Real estate transactions which are normally not very unmasked and it is difficult to know the fair price of houses. we can see that normally the real estate websites have the functionality to predict the prices of houses. This type of forecasts help both buyer and seller so they build houses accordingly or pridict a price for their houses. The model developed in this project helps people understand the feature importances and also sugests ideas on the relative features.


## Data Description
The data has 22 features. the target was Sales Price
which is obvious and the problem is a Supervised learning problem
and also the target is continues and its a regression problem we have dropped
features like commission and reg fee as its a part of sales price and dose not contribute
to prediction or we could add it to the sales price but we have removed.
### Features
'PRT_ID', 'AREA', 'INT_SQFT', 'DATE_SALE', 'DIST_MAINROAD', 'N_BEDROOM',
'N_BATHROOM', 'N_ROOM', 'SALE_COND', 'PARK_FACIL', 'DATE_BUILD',
'BUILDTYPE', 'UTILITY_AVAIL', 'STREET', 'MZZONE', 'QS_ROOMS',
'QS_BATHROOM', 'QS_BEDROOM', 'QS_OVERALL', 'REG_FEE', 'COMMIS',
'SALES_PRICE'.
### Intresting Feature

The Age of the building was calculated using DATE_SALE and DATE_BUILD.
and ploting the feature with sales prics we actully saw a line.
![Ageline](https://user-images.githubusercontent.com/98254459/187719189-46c105c1-f65d-44c1-aad1-e9e2e2aac6e9.png)
The Y axis is the sales price,
there is an inverse relationship, it has ups and downs
 but we can see the linear pattern .
 we also see 43 years old house with a very high price
 which explains the other features are more influensive also.
 we have tried to transform the data and the result is as follows.
![Age Transformation](https://user-images.githubusercontent.com/98254459/187720244-223f4407-c04d-45f7-a52d-41b04549b2fb.png)

No transformation was actully satisfying so we dropped the feature.



## Multi-Co-Linearity
The Matrix has actully helped us find the features that has a very strong corelation among other feature and not the target. 
this type of feature can be removed to stop the problems of poor prediction.

![colinearity](https://user-images.githubusercontent.com/98254459/187721350-21f43ef1-bb53-4c07-a9f0-ef05213a4354.png)

in the Multicolinearity we see that the 'Nrooms' has huge relation with int_sqft.
int_sqft is of 0.95 which will obslutely disturb the model.
we will also be useing the feature importance in the feature to find best feature if not we can actully have this piece of info in our model.


## ML
Since we cleaned all the data and were set to train the algorithm.
we started the prediction with Linear Regression.
### Linear Regression.
we have got a R2 score of 0.91.
that is already amazing for a basic model like Linear Regression.

To find the best features we used the formulae.

    (coeffecient * standard deviation(coeffecient))

![LinearregFeatures](https://user-images.githubusercontent.com/98254459/187724336-d1142c5c-dd85-4b19-bd3e-b1f445d33d44.png)

### KNN
The Knn model was able to go beond Linear Regression 
and the results were as follows:

        The best score obtained =  0.93
        The best Nearest Neighbors = 4 
        The best cross validation fold = 9

the results again was a satisfying one.

### Decision Tree.
The Decision Tree compleately showed off.
we can see the results are as follows

        The best score obtained =  0.97
        The best depth = 18 
        The best cross validation fold = 8
key features are...
![DTfeat](https://user-images.githubusercontent.com/98254459/187729204-e5bfa9f6-a264-444d-a7d2-e6b016983b77.png)

### Random Forest:
This model was a betterment from Decision Tree. as this is a combination of trees.
results were as follows:

        The best score obtained =  0.9858761603148314
        The best depth = 17
key features are...
![Randomforestfet](https://user-images.githubusercontent.com/98254459/187741928-31f130c2-dfa2-4590-8ef4-494ef96386b2.png)

### XG-Boost:
This was the best model of all and the advantagious part is that.
it learns from the mistakes.
and so is the result.

        The best score obtained =  0.9933069803189621
        The learning rate = 0.3
key features:
![XG-Boostfet](https://user-images.githubusercontent.com/98254459/187744773-b1329e42-7afc-4fa9-b99a-49de182227a2.png)


## Business Insights
This Section is were everyone is intrested in 
we have all models perfomed well so takeing common 
best features was the best idea.

based on that we have a few features selected...

    AREA                    0.233
    INT_SQFT                0.076
    BUILDTYPE_Commercial    0.068
    PARK_FACIL              0.059
    MZZONE                  0.059

#### AREA:

![business1](https://user-images.githubusercontent.com/98254459/187745838-c5487e8d-426e-4fa9-80b7-7e5f09900ecb.png)
Seller Insights:

* we see that the sqft are more in the KKnagar. the price is not good enough for the amount of space they are ready to offer.if we are a seller its not the best option to take.
* T-Nagar can offer us the best since its average price is still high. we should note that for less sqft we get more price.
* bulding a house in T nagar is best. but we should also note that the frequence is less as per our data, which means not many houses has been sold.
* in that case if we see chromepet sqft is less and also some houses have sold at very huge prices.
Buyer Insight:

* for a buyer the are should be more and the price should be less.
* if we see the graph we can sugest that for a medium buyer we can suggest Karampakkam because the area is in squire feet is in the center and the average price of the houses is at the lowest. and in no of houses sold even its in the second place.
* chromepet stands at the first place though interms of sale but karampakkam is the best.

#### Build Type

![business2](https://user-images.githubusercontent.com/98254459/187746910-35b51d92-088b-46d6-8549-d33826edbc69.png)

* we can clearly see that the comercial houses are priced high and yet people have equally purchased the houses among commercial and other build types.
* one best sugestion is to build commercial couses in chromepet. we can see that the buyers are also more and the price is also high.
* second option will be the karampakkam as we can see good buying rates.

#### Parking Fesility

![business3](https://user-images.githubusercontent.com/98254459/187747424-07a0ae7a-dd0f-4bba-bdf5-220259f3668f.png)

* we can see all areas with parking fesility has higher sales price
* yet our sugested place karampakkam has slaes never minding the parking fesility as a problem.
* in other places houses with parking fesility has sold more thatn the non parking ones.
* if chromepet is our option then we must think about it.

#### MZZONE

![business4](https://user-images.githubusercontent.com/98254459/187748041-6b5773b6-0bb7-4fd1-b8b9-e4c17c316cbf.png)

* we see that karampakkam has mostly evened ammount of all types of lands.
* to be specific residential medium and high density houses are less sold.
* chromepet has most of the houses sold to be residential low density houses.
* price wise in all areas residential medium density houses are highly priced.

#### Squire Feet 

![business5](https://user-images.githubusercontent.com/98254459/187748558-c8be9007-9f8f-42d5-b861-41d709fcd1c9.png)

* sales price for 500-1000 sqft houses. we see adyar has the highest still count wise chromepet stands tall and our karampakkam is 2nd. important point is we dont see other areas in 500 to 1000sqft. only 3 areas are avilable. which means we cannot make sales if we build such building in other ares.

* 1000-1500 sqft we see chromepet has higher sales.followed by karampakkam and others. price wise KKnagar is second and yet lowest at sales. nopoint in building. velacheri pricing has entered but we see very less count on houses sold. even in this range my best option would be chromepet or karampakkam

* 1500-2000 - this is were we see annanagar, velacheri and Tnagar makeing a lot of contribution were other areas went down. chromepet vanished actully. even karampakkam is not a best option here. we see that if sqft is more we can make very good sales in Tnagar(1st), Annanagar(2nd) and velachery(3rd)-for all lands avilability.

* 2000-2500sqft- it only for kknagar no other places has shown sales and prices are obviously high for residential mediumdensity buildings.
## Conclusion
we see that based on sqft the prices and sales has shown a lot of changes and meaningfull insights.

overall idea is if we are building houses under 1500 sqft. we see chromepet and karampakkam ruling.

if sqft is above 1500 we can see Tnagar, Annanagar and velachery.

if sqft is above 2000 then its only for kknagar.

