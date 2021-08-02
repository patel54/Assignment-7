# Assignment-7

Hello 

https://colab.research.google.com/drive/13KXQ2YY69OpAF3FQRsReHWUlW4SgACZZ

Read the summarize_data() and explain the difference between g and df.

we have seen the data to get a feel for it, we saw the spread of the desired variable MPG along the various discrete variables Model and Cylinders.

MPGs relation with discrete variables.

MPG distribution by number of cylinders.

[ ]
import pandas as pd

# the mpg data is used for demonstration
df = pd.read_csv("https://raw.githubusercontent.com/franklin-univ-data-science/data/master/mpg.csv")
df.head()
str(df)
print(df.head())
print(df.index)
print(df.columns)
df.shape
    mpg  cylinders  displacement  acceleration  model  origin
0  18.0          8         307.0          12.0     70       1
1  15.0          8         350.0          11.5     70       1
2  18.0          8         318.0          11.0     70       1
3  16.0          8         304.0          12.0     70       1
4  17.0          8         302.0          10.5     70       1
RangeIndex(start=0, stop=406, step=1)
Index(['mpg', 'cylinders', 'displacement', 'acceleration', 'model', 'origin'], dtype='object')
(406, 6)
[ ]
df.mpg.describe()
count    398.000000
mean      23.514573
std        7.815984
min        9.000000
25%       17.500000
50%       23.000000
75%       29.000000
max       46.600000
Name: mpg, dtype: float64
[ ]
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np
[ ]
def summarize_data(g):
  return(
    pd.Series({
      "avg_MPG": g.mpg.mean(),
      "min_MPG": g.mpg.min(),
      "max_MPG": g.mpg.max(),
      "sample_count": len(g),
      "mix": g.cylinders.sum()/df.cylinders.sum(),
    })
  )



Select the measure and dimention variables from your dataframe, apply the summarize_data() and modify as needed based on your preferences.
Using our seaborn tool we can look at mpg

[ ]
sns.distplot(df['mpg'])
print("Skewness: %f" % df['mpg'].skew())
print("Kurtosis: %f" % df['mpg'].kurt())

Write 1-3 paragraphs to explain the differences or challenges when you applied the function to your chosen dataframe.
The data consists of 406 observations and 6 attributes. Except Acceleration column, rest of the column values are right skewed. There are more number of ‘4’ cylinder cars than others. And, they also prove to have a better miles per gallon value. ‘8’ cylinder cars have the worst MPG values. There are not many ‘3’ and ‘5’ cylinder car observations. But, we can make a safe assumption that ‘8’ cylinder cars give poor MPG.

Most of ‘4’ cylinder cars have better HP along with MPG values. Most of ‘8’ cylinder cars have less HP along with worse MPG values. ‘1’ origin produces more of ‘6’ and ‘8’ cylinder cars.

The most important plot which gives us how the attributes are correlated. This visualization says that cylinders, displacement and weight values negatively impact mpg value. The cars have got better with mpg value along with years. This is understandable as the scientific and manufacturing process got better. And, according to assumption made, origin ‘3’ - have better mpg value.

Post your version of the above code on your GitHub account. Do not forget a README file with explanations.
