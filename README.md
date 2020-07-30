# Zomato data exploration
## by Adham Gad


## Dataset

This dataset is provided by Zomato, and can be downloaded from [here](https://www.kaggle.com/shrutimehta/zomato-restaurants-data), it contains restaurants info, cuisines, prices and ratings. 
Originally the dataset contained 9551 rows and 20 features, I removed some features that will not be used in this analysis these features are country_code, address, locality_verbose, longitude, latitude, and some redundant features aggregate_rating, rating_color and one feature which contained only one value switch_to_order_menu
leaving us with 13 features
Also
* Tidied the columns, removing spaces replacing them with underscores, also lowercasing them
* Changed ratings and price_range variables to categorical
* Represented restaurant_id as a string to avoid any numerical operations on it

In the middle of the exploration phase I had to do extra wrangling steps for cuisines analysis, I had to make a copy of the same data but tailored to cuisines, this is due to the fact that the cuisines column contained multiple cuisines for the same restaurant stored in the same cell, this would be a hassle to explore, I exploded these rows into multiple rows with one cuisine per row, also stripped the values out of any spaces to as I found some duplicates later in the analysis



## Summary of Findings

average_cost_for_two distribution is skewed to the right, nothing was strange with this skewness generally it represented some overpriced restaurants and it was useful later in the analysis i was able to identify high value and low value restaurants.

Also votes variable had a right skewed distribution, I had to log transform the values in order to take a further look at how the data was distributed and found out that it had many peaks, also for ratings analysis we may have to drop any restaurants with votes less than 10 votes for example, as there are many restaurants with only one, 5, 7 votes which is not that reliable, but it's more of a business decision we may decide to factor out any ratings having less than 100 votes for example, for this analysis I kept all ratings.

Restaurants in this dataset are mainly located in four areas, here's from top to bottom, New Delhi, Gurgaon, Noida, Faridabad

price_range is the categorical alternative of average_cost_for_two, as we go higher in cost per two we enter a higher price range, with 4 the highest

As you go higher in ratings the number of votes increase, there was something interesting though, the number of votes for Poor rating was low for all restaurants except one with very large number of votes this restaurant was The Wine Company with around 2400 votes rated as Poor

There is a positive correlation between restaurants price range and ratings
* Same correlation between restaurants average cost for two and ratings, this suggests the fact the more restaurants charge for their service the more the quality will be better and that's why people give higher ratings
* Outliers in average cost for two column allowed us to extract low and high value for money restaurants."Chicane" & "Nostalgia at 1911 Brasserie - The Imperial" restaurants have the low value for money. "Orient Express - Taj Palace Hotel" & "Masala Library"  restaurant have high value for money 

Restaurants with online delivery or table bookings tend to have higher ratings

Satyaniketan has a high proportion of cafes compared to other places

North Indian and chinese cuisines have pretty similar price ranges.
* Italian and Continental cuisines are also similar in price ranges, they tend to be of higher quality/price
* Fast Food and South Indian have similar price ranges they tend to be at medium - low category
* Bakery and Desserts have similar price ranges they tend to be at medium - low category but more on the low end
* Mughlai tend to be in the medium price range territory
* Apparently South indian cuisine tend to be more cheaper than North indian cuisine

Italian and continental restaurants also tend to be rated higher than other restaurants, probably justifying the higher price range.
Apparently the Italian cuisine is a very good cuisine, as it has highly rated restaurants with less price ranges & Continental cuisine have a few overpriced poor cuisines this is apparent in the multivariate analysis

New Delhi have large number of restraunts, with the most wide distribution of prices in every cuisine, also having some highly priced restaurants in many cuisines
* Faridabad have around 80% of it's restaurants rated as Average, also most of it's restaurants fall under the low price category
* Gurgaon have a high proportion of it's restaurnants between Good & Excellent but it doesn't have the same number of restaurants like New Delhi nor that wide distribution of prices, but it comes second


## Key Insights for Presentation

For this presentation i want to divide it into two main sections representing my two main target variables, ratings and cuisines and how they are related to restaurant prices. First I will start by introducing ratings variable then how cost per two variable is distributed, then will show the correlation between restaurant costs and their ratings, will also add how cost outliers compared to restaurant ratings were used to show high and low value restaurants.

Will then introduce top 10 cuisines in our dataset that will be further used in our analysis, then will show how different cuisines fall into similar price categories

The final step is to merge all together and show the relation between ratings and restaurant costs per each cuisine 
