# pythondatascience
My DataScience Python Learning
### Pandas read_csv command param usage
- pd.read_csv(url, **skiprows=no.ofrowstoskip**)
- pd.read_csv(url, skiprows=1, **sep="\tor\nor,""**)

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
### Bivariate analysis
```
#use of pandas crosstab, div, axis=0, sum(1).astype('float'), plt.bar(stacked=True)
genderbivariatedata = pd.crosstab(train_csv["Gender"], train_csv["Loan_Status"])
genderbivariatedata.plot.bar()
genderbivariatedata.plot.bar(stacked=True)
genderbivariatedata.div(genderbivariatedata.sum(1).astype(float), axis=0).plot.bar(stacked=True)
```

```
#use of pd.cut to form bins and groups
bin = [0, 2500, 4000, 6000, 8000]
groups = ['low','average','high','very high']
train_csv['bindata'] = pd.cut(train_csv['ApplicantIncome'],bin, labels=groups)
bivardata = pd.crosstab(train_csv['bindata'], train_csv['Loan_Status'])
bivardata.div(bivardata.sum(1).astype('float'), axis=0).plot.bar(stacked=True)
```
```
#use of drop amd replace
train_csv=train_csv.drop(['bindata'], axis=1)
train_csv['dependents'].replace('3+',3, inplace=1)
```
```
#use of correlation and heatmap
matrix = train_csv.corr()
sns.heatmap(matrix, vmax=0.8, square=True, cmap="BuPu")
```
### sklearn usage
- from sklearn.**datasets** import datasetname
- ``` from sklearn.datasets import load_breast_cancer ```
- **return_X_y=True** => parameter to return the features and response variable only
- ``` features, target = load_breast_cancer(reaturn_X_y=True) ```
