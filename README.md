## Traveling to Paris, France? How to get the biggest bang from your buck using Airbnb.


TO DO : INSERT LINK TO BLOG POST, PROOFREAD, ADD IN R2 score from RF prediction.

__Project Motivation__
There are more than 50,000 Airbnb listings in Paris, France (at the time of this analysis) spread across Paris’ 20 unique neighborhoods (or districts). The number of listings by room type and property type can be overwhelming for a traveler using Airbnb to determine which listings would be considered **best value** options.     

To inform future travelers to Paris who may use Airbnb to find lodging this analysis:
1. Provides a summary overview of price by `district` and `room_type`   
2. Determines which user selectable options are most influential to listing price (`adjusted_price`)  
3. Suggests an overall **best value** option founded on insight gained from the data  

__Major questions answered in the analysis__
1.	What is the breakdown of listings by room type?  
2.	How much does an Airbnb cost by district and room type?   
3.	Does superhost status influence listing price?  
4.	Of user options on the Airbnb website, which selection most strongly influences the price of a listing?   

__Summary of Methods__
I used publicly available [datasets](http://insideAirbnb.com/get-the-data.html) on Paris, France Airbnb listings to answer the above questions. I applied some cleaning/feature engineering steps to optimize the data for the analysis, visualization, and modeling steps. These included:  

1.	Changing data types of select variables
2.  Inferring missing values for beds, bedrooms, and bathrooms columns
3. Engineering `weekday`, `month`, and `year` from a date
4. Engineering columns (`has_wifi`, `has_washer`, `has_elevator`, `has_dryer`) based on the amenities string
5. Splitting the testing and training data using  `random_seed = 42` and `test_size=0.3`
5. One-hot encoding categorical variables in the features dataset supplied to the `RandomForestRegression()` machine learning algorithm

I also parsed the Arrondissements table from the [Arrondissements of Paris Wikipedia page](https://en.wikipedia.org/wiki/Arrondissements_of_Paris) to assign a district number based on `neighborhood_cleansed` column. This was done to better inform consumers of this analysis as major travel resources frequently list tourist destinations by district number rather than by neighborhood name.

I used the scikit RandomForestRegression function to apply a RandomForest algorithm to the dataset.

__Summary of Results__
1. There are more than 50,000 Airbnb listings in Paris; the majority of them are entire apartments, houses, or condos. A remaining small proportion are private rooms. Less than 1% are shared spaces.   

2. The most expensive district (based on median listing price) is the 8th district. Generally, entire apartments are the most expensive regardless of district and shared rooms are least expensive. Private rooms are nearly as much as entire apartments within the most expensive districts whereas within moderately priced districts, median price of private rooms generally fall within the middle price range between entire apartments and shared rooms.   

3. The three most influential predictors of price were user selected neighborhood, superhost status, and room type.   

4. My suggestion for best value is to search for a private room within the 8th district. While the price of a private room is nearly as much as an entire room or apartment the private rooms are frequently loft spaces or part of a duplex that are much nicer than entire apartments listed at the same price. The private rooms in this district generally have private bathrooms but do share a common entrance space or outdoor living space.   

__Link to public post on this project__
I have summarized my analysis on these data in a blog post that you can read here. **INSERT LINK**  

__Python Version and Package Requirements__
This analysis was performed using Python Version 2.7.15.  

* pandas==0.23.1
* numpy==1.15.0
* seaborn==0.9.0
* matplotlib==2.2.3
* scikit-learn==0.19.1
* Unidecode==1.1.0


__Files in Repository__
1. Data Folder - *listings.csv*, *calendar.csv*, and *paris_districts.csv*.  
2. Main Jupyter Notebook
3. Figures Folder - figures produced by the analysis
