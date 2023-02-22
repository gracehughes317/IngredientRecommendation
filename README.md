# IngredientRecommendation

## Abstract

The purpose of this project is to to use Graph machine learning to pair different food that will work well together. This is to me, and all other chefs in the world, an interesting problem to solve because making food requires a good amount of creativity. You have to know what foods go well with others in order to make a successful dish. However, if you're just starting out or your mind doesn't work that way, it can be very difficult to stray from the recipe or make your own. 

I went into this project with the idea that if you have a list of foods, attributes of those foods, and recipes that feature those foods, it is possible to determine other foods that will go well with one you input. In the notebook, I found all the data, did the preprocessing and graph setup, and determined the best way to get food recommendations. The results of this lab were satisfactory, however there's not a fantastic way to measure how good "subjective" recommendations are.

## Introduction

The most prevalent use of graph ML is to find connections between different nodes and use those connections to introduce new ideas (recommendation algorithms, PageRank, etc.) Of these algorithms, most cater to applications in healthcare, advertising, and other commercial uses, but I wanted to do something different. I spend a lot of my free time experimenting in the kitchen and challenging myself to try new things, so this project aims to serve that purpose.

## Methods

To find ingredient recommendations, I started with three datasets: Food.csv, Content.csv, and RAW_Recipes.csv. The food dataset contains a list of 1,000+ individual foods with various attributes about that food. The content dataset, from the same database as food, had more information about what each ingredient is made up of. Lastly, the recipes dataset contains a collection of 180,000+ recipes, with their ingredients listed for each. 

Using the above data, I created a graph to track all of the ingredients and their connections. The graph used has five different node types: Food, Group, Recipe, Food Part, and Source Type. Edges between the foods and each node type were added based on if that food had a connection to it (featured in that recipe, apart of that food group etc.). With this data inputted, the graph is able to represent how different ingredients are connected to one another, whether they are both from the same food part or are featured in the same recipe. 

Then, to numerically determine if two ingredients belong together, a recommendation algorithm using the adamic adar index to find the closest related nodes. This index was created in 2003 to determine links in social networks, however it works well within a recommendation algorithm.

## Results

Since results for a recommendation system are very difficult to validate objectively, I opted to do a sort of smoke test on the results. To do this, I looked at the recommendations for the first 20 nodes and inspected what results it gave. Most of the ingredients made complete sense, and none of them were completely out of the blue, so I can say with some certainty that the recomendations are accurate.

For example, here are the results for papaya, leek, and chicken:
| Input | Top Recommendations |
| --- | --- | 
| Papaya | Mango, Sugar, Honey, Banana, Lime <br> Olive Oil, Pineapple, Red Onion, Lemon, Strawberry | 
| Leek | Olive Oil, Butter, Carrot, Garlic, Pepper, <br> Parmesean, Parsley, Eggs, Flour, Sour Cream |
| Chicken | Butter, Olive Oil, Pepper, Garlic, Flour, <br> Soy Sauce, Sour Cream, Parmesean, Parsley, Sugar|

The only ingredients I found a bit off at first glance were the olive oil for papaya and sugar for chicken. After doing a little digging, I found that olive oil and papaya go together in savory/sweet salsas, and sugar goes with chicken when you're breading and frying it. 


## Conclusions

My hypothesis for this lab was that if I had a list of ingredients and various attributes that could connect them, that I could use that information to create a list of ingredient recommendations. The results of the experiment were promising - all of the outputs make sense for the inputted food. Originally, I had wanted to use more of the ingredient attributes to make recommendations based soley on their properties. With the available data, however, this feat would likely require me to draft my own dataset. I'm still happy with this scaled-back version, so overall this lab was a success.
