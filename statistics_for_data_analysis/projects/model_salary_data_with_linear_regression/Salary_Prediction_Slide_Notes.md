## Data Description Slides

### slide 3
The Dataset

373 employee records consisting of:
- Age
- Gender
- Education Level
- Job Title
- Years of Experience
- Salary

Dataset Clean Up

The dataset was free from any corrupt records. To prepare the data for analysis, only a couple of minor adjustments were required.

Dataset Cleaning Operations:
- 2 empty rows were removed
- a record with an very low salary value ($350.00) was flagged as an outlier and removed. The next lowest salary was $30,000.00

## slide 4
### distributions
- age
- years of experience

## slide 5
- gender
- education level

## slide 6
- job title flag
  - explain flags


## slide 7
### Correlations to Salary

- salary vs years of experience scatterplot
- salary vs age scatterplot


## slide 8
- salary vs male, female, bachelors, masters, phd boxplot
- mean salary: male, female table
- mean salary: bachelors, masters, phd table

| Gender | Mean Salary | Mean Salary vs Male |
| --- | --- | --- |
| Male | $104,404.15 | -- |
| Female | $97,011.17 | -$7392.97 |

| Education Level | Mean Salary | Mean Salary vs Bachelors |
| --- | --- | --- |
| Bachelors | $75,089.69 | -- |
| Masters | $129,795.92 | +$54,706.23 |
| PhD | $157,843.14 | +$82,753.45 |


## Regression Results

[Share the regression output associated with your linear model, identify which variables are statistically significant in their relationship with salary, remove variables from the model that are not statistically significant, identify how well the model fits the data]
[You may expand this to as many slides as you need]

### slide 9
Salary Linear Regression: Significant Variables

Preliminary linear regression to identify statistically significant variables
female, bachelors columns omitted from regression as baseline variables. Job title flag variables do not require a baseline as they are linearly independent.

variable,p-value
male,0.0000
years_experience,0.0000
masters,0.0000
phd,0.0000
is_director,0.0000
is_junior,0.0885
is_senior,0.0000
is_manager,0.0207
is_analyst,0.8460
is_engineer,0.5013

Statistically insignificant variables:

omitting insignificant predictor variables (p-value > 0.05):
variable,p-value
is_junior,0.0885
is_analyst,0.8460
is_engineer,0.5013

### slide 2
Salary Linear Regression: Years of Experience Multicollinearity

There could be multicollinearity between years_experience and some of the predictor variables:

is_director
is_senior
is_manager
masters
phd

show violin plots
A `True` value in all but `is_manager` has a distribution that is noticeably shifted toward higher `years_experience` values


### slide 3
Linear regression of years_experience and these suspected variables indicated all show statistically significant relationships to variance of years_experience

However, a variance inflation factor test did not show any of the variables passing the > 10 inflation factor threshold. This suggests that our regression model would not be improved if we removed them.

| suspected variable | coef | p-value | VIF | omit from regression? |
| --- | --- | --- | --- | --- |
| `masters` | 2.6187 | < 0.001 | 1.462968 | no |
| `phd` | 7.2576 | < 0.001 | 1.650073 | no |
| `is_director` | 11.5747 | < 0.001 | 2.251962 | no |
| `is_senior` | 3.7267 | < 0.001 | 1.468272 | no |
| `is_manager` | 2.7672 | < 0.001 | 1.166135 | no |


### slide 4
Salary Linear Regression: Results

The model returned an R-squared value of 0.916 indicating a good fit, explaining 91.6% of the variance of salary

R-squared:                       0.916

                       coef    std err          t      P>|t|      [0.025      0.975]
------------------------------------------------------------------------------------
intercept         2.907e+04   1660.594     17.505      0.000    2.58e+04    3.23e+04
male              7848.8370   1466.075      5.354      0.000    4965.796    1.07e+04
years_experience  5081.2555    175.297     28.987      0.000    4736.533    5425.978
masters           1.397e+04   2008.268      6.958      0.000       1e+04    1.79e+04
phd               2.314e+04   2728.306      8.480      0.000    1.78e+04    2.85e+04
is_director       2.505e+04   3461.875      7.237      0.000    1.82e+04    3.19e+04
is_senior         1.435e+04   1799.292      7.973      0.000    1.08e+04    1.79e+04
is_manager        4174.9452   1801.474      2.318      0.021     632.342    7717.549





## Interpretation and Next Steps

### slide 1
what are the most powerful predictors

### slide 2
what are the "cheapest" combinations of experience + education




