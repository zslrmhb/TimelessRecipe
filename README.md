# TimelessRecipe

by Hongbin Miao

---

## Introduction

> Introduction: I enjoy cooking and think it is a rewarding process. So, I would like to explore and test out different recipes in these dataset. In particular, I want to see what make a high-rating recipe distiguish from a low-rating one.

> Question: Do recipes with 5-star rating tend to be more difficult to make than recipes with 1-star rating? (In terms of minutes, n_steps and n_ingredients)

> Dataset Info:
    >> 83781 rows, 13 columns
    >> Columns of interests: *name*, *minutes*, *n_steps*, *steps*, *n_ingredients*, *ingredients*, *avg_rating*

---

## Cleaning and EDA

### Data Cleaning

- For the purpose of my question, I decide to focus on the following columns: *name*, *minutes*, *n_steps*, *steps*, *n_ingredients*, *ingredients*, *avg_rating*.

- *minutes*: there are some minutes that are unreasonably large, such as that of larger than 600 minutes. So, I instead keep the minutes value that are within the 99th percentile, and replace anything else with nan.

- *n_steps* and *steps*: To make sure "n_steps" is consistent with "steps", I transformed "steps" into a list and let the length of the list be the value in "n_steps".

- *n_ingredients* and *ingredients*: To make sure "n_ingredients" is consistent with "ingredients", I transformed "ingredients" into a list and let the length of the list be the value in "n_ingredients".

- *avg_rating*: for the purpose of my question, I divided the average rating equally to 5 ranks.

- *name*: No change made 

| name                                 |   minutes |   n_steps | steps                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |   n_ingredients | ingredients                                                                                                                                                                                                                                                       |   avg_rating |   rank |
|:-------------------------------------|----------:|----------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------:|-------:|
| 1 brownies in the world    best ever |        40 |        10 | ["'heat the oven to 350f and arrange the rack in the middle'", "'line an 8-by-8-inch glass baking dish with aluminum foil'", "'combine chocolate and butter in a medium saucepan and cook over medium-low heat ", 'stirring frequently ', "until evenly melted'", "'remove from heat and let cool to room temperature'", "'combine eggs ", 'sugar ', 'cocoa powder ', 'vanilla extract ', 'espresso ', "and salt in a large bowl and briefly stir until just evenly incorporated'", "'add cooled chocolate and mix until uniform in color'", "'add flour and stir until just incorporated'", "'transfer batter to the prepared baking dish'", "'bake until a tester inserted in the center of the brownies comes out clean ", "about 25 to 30 minutes'", "'remove from the oven and cool completely before cutting'"]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |               9 | ["'bittersweet chocolate'", "'unsalted butter'", "'eggs'", "'granulated sugar'", "'unsweetened cocoa powder'", "'vanilla extract'", "'brewed espresso'", "'kosher salt'", "'all-purpose flour'"]                                                                  |            4 |      4 |
| 1 in canada chocolate chip cookies   |        45 |        12 | ["'pre-heat oven the 350 degrees f'", "'in a mixing bowl ", "sift together the flours and baking powder'", "'set aside'", "'in another mixing bowl ", 'blend together the sugars ', 'margarine ', "and salt until light and fluffy'", "'add the eggs ", 'water ', "and vanilla to the margarine / sugar mixture and mix together until well combined'", "'add in the flour mixture to the wet ingredients and blend until combined'", "'scrape down the sides of the bowl and add the chocolate chips'", "'mix until combined'", "'scrape down the sides to the bowl again'", "'using an ice cream scoop ", "scoop evenly rounded balls of dough and place of cookie sheet about 1 - 2 inches apart to allow for spreading during baking'", "'bake for 10 - 15 minutes or until golden brown on the outside and soft & chewy in the center'", "'serve hot and enjoy !'"]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |              11 | ["'white sugar'", "'brown sugar'", "'salt'", "'margarine'", "'eggs'", "'vanilla'", "'water'", "'all-purpose flour'", "'whole wheat flour'", "'baking soda'", "'chocolate chips'"]                                                                                 |            5 |      5 |
| 412 broccoli casserole               |        40 |         6 | ["'preheat oven to 350 degrees'", "'spray a 2 quart baking dish with cooking spray ", "set aside'", "'in a large bowl mix together broccoli ", 'soup ', 'one cup of cheese ', 'garlic powder ', 'pepper ', 'salt ', 'milk ', '1 cup of french onions ', "and soy sauce'", "'pour into baking dish ", "sprinkle remaining cheese over top'", "'bake for 25 minutes or until cheese is lightly browned'", "'sprinkle with rest of french fried onions and bake until onions are browned and cheese is bubbly ", "about 10 more minutes'"]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |               9 | ["'frozen broccoli cuts'", "'cream of chicken soup'", "'sharp cheddar cheese'", "'garlic powder'", "'ground black pepper'", "'salt'", "'milk'", "'soy sauce'", "'french-fried onions'"]                                                                           |            5 |      5 |
| millionaire pound cake               |       120 |         7 | ["'freheat the oven to 300 degrees'", "'grease a 10-inch tube pan with butter ", 'dust the bottom and sides with flour ', "and set aside'", "'in a large mixing bowl ", 'cream the butter and sugar with an electric mixer and add the eggs one at a time ', "beating after each addition'", "'alternately add the flour and milk ", "stirring till the batter is smooth'", "'add the two extracts and stir till well blended'", "'scrape the batter into the prepared pan and bake till a cake tester or knife blade inserted in the center comes out clean ", "about 1 1 / 2 hours'", "'cool the cake in the pan on a rack for 5 minutes ", "then turn it out on the rack to cool completely'"]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |               7 | ["'butter'", "'sugar'", "'eggs'", "'all-purpose flour'", "'whole milk'", "'pure vanilla extract'", "'almond extract'"]                                                                                                                                            |            5 |      5 |
| 2000 meatloaf                        |        90 |        17 | ["'pan fry bacon ", "and set aside on a paper towel to absorb excess grease'", "'mince yellow onion ", 'red bell pepper ', "and add to your mixing bowl'", "'chop garlic and set aside'", "'put 1tbsp olive oil into a saut pan ", 'along with chopped garlic ', "teaspoons white pepper and a pinch of kosher salt'", "'bring to a medium heat to sweat your garlic'", "'preheat oven to 350f'", "'coarsely chop your baby spinach add to your heated pan ", "stir frequently for approximately 5 min to wilt'", "'add your spinach to the mixing bowl'", "'chop your now cooled bacon ", "and add it to the mixing bowl'", "'add your meatloaf mix to the bowl ", "with one egg and mix till thoroughly combined'", "'add your goat cheese ", 'one egg ', "1 / 8 tsp white pepper and 1 / 8 tsp of kosher salt and mix till thoroughly combined'", "'transfer to a 9x5 meatloaf pan ", "and cook for 60 min or until the internal temperature is at least 160f'", "'let stand for 5min'", "'melt 1tbsp unsalted butter into a frying pan ", "and cook up to three eggs at a time'", "'crack each egg into a separate dish ", 'in order to prevent egg shells from reaching the pan ', "then add salt and pepper to taste'", "'wait until the egg whites are firm looking ", "but slightly runny on top before flipping your eggs'", "'after flipping ", "wait 10~20 seconds before removing each egg and placing it over your slices of meatloaf'"] |              13 | ["'meatloaf mixture'", "'unsmoked bacon'", "'goat cheese'", "'unsalted butter'", "'eggs'", "'baby spinach'", "'yellow onion'", "'red bell pepper'", "'simply potatoes shredded hash browns'", "'fresh garlic'", "'kosher salt'", "'white pepper'", "'olive oil'"] |            5 |      5 |




### Univariate Analysis

<iframe src="assets/mins_dist.html" width=800 height=600 frameBorder=0></iframe>

> Most of the recipe ranges between 0-49 minutes, and the number of recipes decreased drastically as the number of minutes increased.


### Bivariate Analysis

<iframe src="assets/nsteps_mins.html" width=800 height=600 frameBorder=0></iframe>

> Most of the recipe ranges between 20-39 minutes and 9-10 steps (as with the brightest spots in the graph). We can see a slight positive correlation between minutes and n_steps, but this only limited to a specific range of minutes and n_steps.

### Interesting Aggregates

|   rank |   ('min', 'minutes') |   ('min', 'n_ingredients') |   ('min', 'n_steps') |   ('median', 'minutes') |   ('median', 'n_ingredients') |   ('median', 'n_steps') |   ('mean', 'minutes') |   ('mean', 'n_ingredients') |   ('mean', 'n_steps') |   ('max', 'minutes') |   ('max', 'n_ingredients') |   ('max', 'n_steps') |
|-------:|---------------------:|---------------------------:|---------------------:|------------------------:|------------------------------:|------------------------:|----------------------:|----------------------------:|----------------------:|---------------------:|---------------------------:|---------------------:|
|      1 |                    1 |                          2 |                    1 |                      40 |                             9 |                      10 |               64.3355 |                     9.06568 |               11.1764 |                  725 |                         24 |                   46 |
|      2 |                    1 |                          2 |                    1 |                      40 |                             9 |                      10 |               68.3903 |                     9.22721 |               11.2091 |                  675 |                         27 |                   48 |
|      3 |                    1 |                          2 |                    1 |                      40 |                             9 |                       9 |               66.317  |                     9.13899 |               10.5774 |                  680 |                         29 |                   88 |
|      4 |                    1 |                          2 |                    1 |                      40 |                             9 |                       9 |               62.6745 |                     9.37778 |               10.617  |                  730 |                         29 |                   81 |
|      5 |                    0 |                          1 |                    1 |                      35 |                             9 |                       9 |               58.4573 |                     9.21448 |               10.7634 |                  730 |                         37 |                  100 |


> We can see that although the n_steps and n_ingredients of rank-5 recipes is greater than those of rank-1 recipes, but average minutes of rank-5 recipes is smaller than that of rank-1 recipes.
---

## Assessment of Missingness

### NMAR Analysis
> The **description** column will be NMAR since the some users might not want to provide description for their recipe.

> The **review** column will be **NMAR** since the user might not want to review the recipe. However, we can perform permutation test to see if the **review** column depends on **rating**, since lower rating will more likely have user-review, and that could make the **review** column **MAR**.

### Missingness Dependency
<iframe src="assets/not_missing_des.html" width=800 height=600 frameBorder=0></iframe>

<iframe src="assets/missing_des.html" width=800 height=600 frameBorder=0></iframe>

> I want to see the missingess dependency of *description* to *n_ingredients*, *avg_rating* and *minutes*.
> Through permutation test, I find out that the missingness of *description* depends on *n_ingredients* and do not depend on *avg_rating* and *minutes*.

> p-value: 
>> n_ingredients: 0.00
>> avg_rating: 0.08
>> minutes: 0.65

> significance level: 5%
>Test Statistic: Absolute difference in group mean

---

## Hypothesis Testing

> **Rank**: I divided the average ratings into 5 groups equally

> **Null Hypothesis**: Recipe with rank-5 generally take less time to make than recipe with rank-1.

> **Alternative Hypothesis**: Recipe with rank-1 rating generally take less time to make than recipe with rank-5 rating.

> **Test Statistic**: Unsigned Difference in average time (minutes) between recipes with rank-5 rating and those of rank-1 rating.

> **significance level**: 5%

> **Resulting p-value**: 0.51

> **Conclusion**: Failed to reject the null hypothesis