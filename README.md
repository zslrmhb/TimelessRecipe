# TimelessRecipe

by Hongbin Miao

---

## Introduction

> Introduction: 

> Question: Does recipe with 5-star rating tend to be more difficult to make than recipe with 1-star rating? (In terms of minutes, n_steps and n_ingredients)
---

## Cleaning and EDA

### Data Cleaning


### Univariate Analysis

<iframe src="TimelessRecipe/assets/mins_dist.html" width=800 height=600 frameBorder=0></iframe>

### Bivariate Analysis

### Interesting Aggregates

---

## Assessment of Missingness

### NMAR Analysis
> The **description** column will be NMAR since the some users might not want to provide description for their recipe.

> The **review** column will be **NMAR** since the user might not want to review the recipe. However, we can perform permutation test to see if the **review** column depends on **rating**, since lower rating will more likely have user-review, and that could make the **review** column **MAR**.

### Missingness Dependency



---

## Hypothesis Testing

> **Null Hypothesis**: Recipe with 5-star rating generally take less time to make than recipe with 1-star rating.

> **Alternative Hypothesis**: Recipe with 1-star rating generally take less time to make than recipe with 5-star rating.

> **Test Statistic**: Different in average time (minutes) between recipes with 5-star rating and those of 1-star rating.

> **significance level**: 5%

> **Resulting p-value**: 0.468

> **Conclusion**: Failed to reject the null hypothesis