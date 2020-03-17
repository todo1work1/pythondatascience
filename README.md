# pythondatascience
My DataScience Python Learning
### Use of Pandas, matplotlib seaborn
```
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

trainds = pd.read_csv(traindatasetpath)
trainds.shape
trainds.describe
trainds.dtypes # to get datatype of each column
trainds.columns # to get column name
trainds['colname'].value_counts() # to get different values available in this column
trainds['colname'].value_counts(normalize=True) # to get different values available in this column in percentage
trainds['colname'].value_counts(normalize=True).plot.bar() #bar plot of the distribution of values of column
trainds['colname'].value_counts(normalize=True).plot.bar(title="Titleofplot") #bar plot of the distribution of values of column

plt.figure(1)
plt.subplot(rowcolumnsindex) # plt.subplot(121)
plt.show()

sns.distplot(trainds['colname']) # will plot distribution of values in this column if all are not null
df = trainds.dropna() #removing null values
sns.distplot(df['colname'])

trainds.boxplot(column='colname', by='othercolumn') #box plot of colname group by other columns
```
