# McDonald_Menu_Nutritional_Analysis - Documentation
Documentation:


PROJECT NAME:  McDonald's Menu Nutritional Analysis

Problem statement:
In today's world, there is a prevalent trend of widespread consumption of junk food among people of all ages. Junk food, characterized by its high levels of refined sugars, unhealthy fats, and low nutritional value, poses significant health risks to individuals who regularly consume it. This dietary habit contributes to rising rates of obesity, diabetes, cardiovascular diseases, and other lifestyle-related health conditions.
Purpose of the Project : 
	The purpose of this project is to analyze the nutritional content of McDonald's menu items. By conducting a detailed examination of calorie counts and nutrition facts, this analysis aims to provide valuable insights into the health implications of consuming McDonald's products. 
	This project seeks to offer transparency to consumers regarding the nutritional value of menu items and to assist McDonald's in identifying opportunities to promote healthier choices within their menu offerings.

Source of Data:
	Data is collected from Knowledge hut upgrade prism portal and the link of dataset is given below:
Link: https://knowledgehutglobalmy.sharepoint.com/personal/lsstorage_knowledgehut_com/_layouts/15/onedrive.aspx?id=%2Fpersonal%2Flsstorage%5Fknowledgehut%5Fcom%2FDocuments%2F62%5FData%20Analyst%20Bootcamp%20Capstone%20Projects%2FNutrical%20Dataset&ga=1





Following steps are taken below for data analysis:

Import necessary Libraries :
	 Numpy as np
	 Pandas as pd
	 Matplotlib.pyplot as plt
	 Seaborn as sns

Data Preprocessing:
a)	Import and loaded the dataset: 
                                                       Pd.read csv  function used to import and load the dataset                                                                                                                                                              and name of dataframe is given “data”.

b)	Information of dataset: 
1)	By using shape function on dataframe we get information about dataframe that we have 260 rows and 24 columns.
 e.g data.shape

2)	By using Info() function on dataframe we get information about datatype of columns and using value_counts() on it we got to know that there are 18 columns of int64, 3 columns of float64 and 3 columns are categorical data type. e.g  1) data.info()  2) data.dtypes.value_counts()


c)	Checked Missing values: 
3)	Isna() function used to check that our dataframe contains any missing values or  not and we found our dataframe does not contains any missing values.
e.g data.isna().sum()



d)	Data cleaning:  
Observation: 
1) All columns data types are correct, except Serving Size column because it supposed to be int64, not object data type. 
2) Most of the nutrients have a column of percentage daily need but Sugars, Protein, and Calorie does not have percentage daily needs column so we are going to add Sugars, Protein, and Calories column in percentage daily needs.
Action: If we read how all data write in Serving Size, there are several weight/volume units to describe the menus. That is Ounce (oz), Fluid Ounce (fl oz), Gram (g) and millilitre (ml). Most of the data use an ounce or gram unit for food and fluid oz for a drink, but some data like 1% Low Fat Milk Jug and Fat- Free Chocolate Milk Jug items use millilitre unit. So we're going to transform all unit to gram unit, and for data who didn't provide mass unit (like a fluid ounce or millilitre), we're going to use the density of milk (Only milk item who didn't have mass unit) for millilitre and then for fluid once we're going to use the density of pure water.
3) After normalized Serving Size column, let's add Sugars, Protein, and Calories column in percentage daily needs unit.                                                                            As a guide: i) An average man needs 2,500 kcal(calories) a day.                                                                                                                                                                                                                              ii)An average man needs 30gm sugar a day.                                                                        iii)An average man needs 50gm protein a day.

Conclusion:  After the dataset has been checked and cleaned. Now the dataset is ready to use and we can start dive into our dataset for Data Exploration.

e)	Data Exploration: 
                                Now we used describe function to overview the data and it gives the  count, mean , standard deviation, min, 25%, 50%, 75%, and max of all columns which has numerical value and it is very handy.


NOTE: Now we will explore the data as per the requirement.


1)	Question: Now we will find out Count, Min, Max, Sum, and Mean of calories column by category wise.
Action: In this we had formed new dataframe by the name of by_category and in this we had   calculated the count, Min, Max, Sum, Mean of calories by category wise and forming new columns i.e category, calorie(min) , calorie(max), calorie(sum), calorie(mean).
Functions used are: groupby, min(), max(), mean(), sum(), value_counts()
Conclusion: 
1) Average maximum calories and Max. calories per item which came from Chicken & Fish category.
2) Min. calories per item come from "Breakfast" and "Beverages" category.

2)	Question: Now we will visualize "by_category" dataframe, to get which category has the maximum no. of items and max. avg. max. colories
Action: “plt.subplots”  is used to visualize the "Total Items in Each Category" and "Avg. total Calories in Each Category"

Conclusion: 
1) "Coffee & Tea" has max. no. of items which is 36.5% of total no. of items but it stands 4th(fourth) in avg. clories per item i.e 15.2%
 2) "Chicken & Fish" has max. Average colorie per item despite of it has fourth most (4th) total no. of items i.e 10.4%

3)	Question: Let's see how the correlation of calories and nutrients with   the help of Heatmap plot
Action: In this we had created a new dataframe by the name of “Nutrition” and it contains all the columns which have our dataframe and then correlation function used to find the correlation between every column with each other.
 Conclusion: 
1) From the above figure, we can conclude that Calories has the highest correlation with Fat. It means more fat in a menu implies that more calories are present in the menu. followed by Protein in second place (0.79) and Carbohydrates in third place (0.78). 
2) Besides the correlation with the calories, there's a high correlation score in another feature, for example the correlation between Sodium and Iron (0.87), and Sodium between Protein is (0.87).

4)	Question: Identify menu items with highest and lowest calorie.
Action:  In this question we had formed new data frame by the name of item_calorie in which it has 3 columns from our dataframe i.e data and columns are “category”,”Item” and ”Calories”, after that sort_values function is applied on this column and we have set ascending= False. Then min() and max() function is applied on this dataframe and we got the item which have maximum calories and minimum calories.
Conclusion:
Max calorie item: "Chicken McNuggets (40 piece)"
Min calorie items:  And there are many items which having Minimum calorie counts i.e calorie = 0 , so we will show in catrgory wise.
for Eg. In "Coffee & Tea" category 
 1)"Coffee (Small)"
2)"Iced Tea (Child)" 
 3)"Iced Tea (Large)" 
 4)"Iced Tea (Medium)"
 5)"Iced Tea (Small)"
 6)"Coffee (Large)"
 7)"Coffee (Medium)"
 
 In "Beverages" 
 1)"Dasani Water Bottle"
 2)"Diet Dr Pepper (Medium)"	
 3)"Diet Dr Pepper (Child)"	
 4)"Diet Dr Pepper (Large)"	
 5)"Diet Dr Pepper (Small)"	
 6)"Diet Coke (Child)"	
 7)"Diet Coke (Large)"	
 8)"Diet Coke (Medium)"	
 9)"Diet Coke (Small)"
 
5)	Question: Identify which menu item is healthy based on the each nutritonal content.
Action: 1) To find out which menu item is healthy, we will filter out on the basis of min. and max. intake of each nutritional content for average healthy person.
2) we will first filtered out menu items on first nutritional content then we will take that dataframe further and filtered out on the basis of 2nd nutritional content and similarly we will take that dataframe which is generated from 2nd nutritional content and filtered out on basis of 3rd nutritional content and this process we will continues till we will filtered out on all nutritional content of our dataframe containing and finally we will conclude from this which food is healthy.
Conditions:   i) Saturated Fat (% Daily Value) < 10 
                        ii) Cholesterol (% Daily Value) < 20
                        iii)  Dietary Fiber (% Daily Value) >= 9
                        iv) Iron (% Daily Value)  > 5 
                        v) Vitamin C (% Daily Value) > 7
                       vi)  Vitamin A (% Daily Value) >= 10
                       vii) Calcium (% Daily Value)  > 10

Conclusion:
 By filtering out from all nutrional content the "PREMIUM SOUTHWEST SALAD (WITHOUT CHICKEN)" is the "HEALTHIEST" food item among 260 items and it comes from "SALAD" category.

6)	 Question: Now we will find out the less healthy menu item from our dataset.
Action: The main filtering column will be Saturated Fat (% Daily Value) and Cholesterol (% Daily Value) because it causes the heart related diseases i.e Heart attack
Conditions:   The item which have maximum Saturated Fat (% Daily Value and Cholesterol (% Daily Value) is considered to be less healthy.




Conclusion:
1)	"Big Breakfast with Hotcakes (Regular Biscuit)" and "Big Breakfast with Hotcakes (Large Biscuit)" has the highest cholestrol value out of 260 items which is 575 and it will be "LESS HEALTHY" menu item on the basis of cholestrol.
2)	"McFlurry with M&M’s Candies (Medium)" has the highest Saturated Fat (% Daily Value) out of 260 items which is 102 and it will be "LESS HEALTHY" menu item on the basis of Saturated Fat (%Daily Value).

7)	 Question:Now we will check which nutrient contents have an outlier?
Action:  I am using the subplot of three i.e three nutrient columns in one subplot,  so it is easy from appearance perpestive and it will formed 7 subplots and using boxplot to detect outliers, so there will be 21 boxplot will formed.
Conclusion:
Based on the visualization, the below variables have outliers:
Calories, Calories from Fat, Total Fat, Total Fat (% Daily Value), Trans Fat, Cholesterol , Cholesterol (% Daily Value), Sodium, Sodium (% Daily Value), Carbohydrates, Carbohydrates (% Daily Value), Dietary Fiber (% Daily Value), Sugars, Protein, Vitamin A (% Daily Value), Vitamin C (% Daily Value),                Calcium (% Daily Value) and Iron (% Daily Value)              

Based on the visualization, the below variables do not have outliers:
Saturated Fat, Dietary Fiber and Saturated Fat (% Daily Value)      



8)	Question: Identify which category and menu item has the highest nutrient content 
1)	we will find out first category wise that which category has the highest nutrient content then we will find out menu wise for each nutrient content.
2)	Now we will used pivot_table function for every nutritional content and find out maximum value for that nutrient content category wise and item wise.
Conclusion:
a)	 Vitamin A (% Daily Value) :

Category: "SALADS" has the highest "Vitamin A (% Daily Value)" among all the category.

Item:  "Premium Bacon Ranch Salad (without Chicken)", "Premium Southwest Salad with Crispy Chicken" and "Premium Southwest Salad with Grilled Chicken" has the highest "Vitamin A (% Daily Value)" out of 260 items and it comes under "salads" category.
b)	Vitamin C (% Daily Value) :
Category: "Salad” has the highest Average "Vitamin C(% Daily Value)"  among all catrgory.
Item:  "Minute Maid Orange Juice (Large)" has highest "Vitamin C (% Daily Value)" out of 260 items and it comes under "Beverages" category.
c)	Calcium (% Daily Value) :
Category: "Smoothies and shakes" has the highest "Calcium(% Daily Value)" among all the category.
Item:  "Strawberry Shake (Large)" and "McFlurry with M&M’s Candies (Medium)" has the highest "Calcium(% Daily Value)" out of 260 items and it comes under "Smoothies & Shakes" category.

d)	Iron (% Daily Value) :
Category: "Beef and pork" has the highest 'Iron (% Daily Value)' among all the category.
Item:   "Big Breakfast with Hotcakes (Regular Biscuit)" and "Big Breakfast with Hotcakes (Large Biscuit)" has highest "Iron (% Daily Value)" out of 260 items and it comes under "Breakfast" category.
e)	Cholestrol :
Category: "Breakfast" has the highest "Cholestrol" among all the category.
Item:   "Big Breakfast with Hotcakes (Regular Biscuit)" and "Big Breakfast with Hotcakes (Large Biscuit)" has the highest "Cholestrol" value.
f)	Protein: 
Category: "chicken and fish" has the highest 'Protein' among all the category.
Item:    "Chicken McNuggets (40 piece)" has highest "Protein" out of 260 items and it comes under "chicken & Fish" category
g)	Dietary Fiber (% Daily Value) :
Category: "salads" has the highest 'Dietary Fiber(% Daily Value)' among all the category.
Item:     "Big Breakfast with Hotcakes (Large Biscuit)","Big Breakfast with Hotcakes and Egg Whites (Large Biscuit)" comes under "Breakfast" category and "Premium Southwest Salad with Crispy Chicken" and "Premium Southwest Salad with Grilled Chicken" comes under "Salads" category which has highest "Protein" out of 260 items.


h)	Carbohydrates (% Daily Value) : 
Category: "Smoothies & shakes" has the highest 'Carbohydrates (% Daily Value)' among all the category.
Item:     "Strawberry Shake (Large)" and "Chocolate Shake (Large)" has highest "Carbohydrates (% Daily Value)" out of 260 items.

i)	Sodium (% Daily Value): 
Category: "chicken & fish" has the highest 'Sodium (% Daily Value)' among all the category.
Item:  "Chicken McNuggets (40 piece)" has "Sodium (% Daily Value)" of 150 which is highest out of 260 items.

j)	 Saturated Fat (% Daily Value):
Category: "Breakfast" has the highest "Saturated Fat (% Daily Value)" among all the category.
Item:   "McFlurry with M&M’s Candies (Medium)" has "Saturated Fat (% Daily Value)" of 102 which is highest out of 260 items.

9)	Question: Compare nutritional characteristic of different food categories.
Action:   i am comparing nutritional characteristic of "Salads" and "Desserts" category. We are going to compare the Mean, Min, Max and Standard deviation of these two categories by using describe function.
Conclusion:
From above result we can easily compare the values of each nutritional content. for e.g Mean calorie of salads is greater than desserts. similarly we can compare any nutritional content of above two category.


IMPORTANT INSIGHTS:
1)	"Coffee & Tea" category has maximum number of items which is 36.5% of total no. of items and that much number of items of particular one category should not be their and it should be reduced.
2)	 There are about 16 items which having Zero calories and just because a food is lower in calories doesn't mean it makes a better choice than higher calorie foods. Your body needs adequate calories on a daily basis to function optimally and help you feel your best. It's not a good idea to choose foods based simply on their calorie content.
3)	The "PREMIUM SOUTHWEST SALAD (WITHOUT CHICKEN)" is the "HEALTHIEST" food item among 260 items and it comes from "SALAD" category and salad category has only 6 items and it should be increased because it is a healthy diet.
4)	"Big Breakfast with Hotcakes (Regular Biscuit)" and "Big Breakfast with Hotcakes (Large Biscuit)" has the highest cholestrol value and "McFlurry with M&M’s Candies (Medium)" has the highest Saturated Fat (% Daily Value) out of 260 items and this items are "LESS HEALTHY" and it should be removed from menu items list because it may cause heart related problems i.e Heart attack.
