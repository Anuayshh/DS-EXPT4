# Ex-04-Multivariate-Analysis

## AIM:
To perform Multivariate EDA on the given data set.

## EXPLANATION:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM:
Step1:Import the built libraries required to perform EDA and outlier removal.

Step2:Read the given csv file.

Step3:Convert the file into a dataframe and get information of the data.

Step4:Return the objects containing counts of unique values using (value_counts()).

Step5:Plot the counts in the form of Histogram or Bar Graph.

Step6:Use seaborn the bar graph comparison of data can be viewed.

Step7:Find the pairwise correlation of all columns in the dataframe.corr()

Step8:Save the final data set into the file.

## PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

dt = pd.read_csv('/content/titanic_dataset.csv')

dt

dt.info()

dt.set_index("PassengerId",inplace=True)

dt.shape

dt.describe()

dt.nunique()

dt["Survived"].value_counts()

per = (dt["Survived"].value_counts()/dt.shape[0]*100).round(2)

per

sns.countplot(data=dt,x="Survived")

dt

dt.Pclass.unique()

dt.rename(columns = {'Sex':'Gender'}, inplace = True)
dt

sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5, aspect=.7)

sns.catplot(x='Survived',hue = "Gender",data = dt,kind = "count")

fig, ax1 = plt.subplots(figsize=(8,5))
graph = sns.countplot(ax=ax1,data=dt,x="Survived",hue="Pclass",palette="rainbow")
graph.set_xticklabels(graph.get_xticklabels())
for p in graph.patches:
  height = p.get_height()
  graph.text(p.get_x()+p.get_width()/2, height + 20.8,height,ha="left")

dt.boxplot(column="Age",by="Survived")

sns.scatterplot(x = dt["Age"],y = dt["Fare"])

fig, ax1 = plt.subplots(figsize = (8,5))
pt = sns.boxplot(ax = ax1,x = 'Pclass',y = 'Age', hue='Gender',data=dt)

sns.catplot(data=dt,col="Survived",x="Gender",hue ="Pclass",kind = "count")

g = sns.catplot(data=dt,col="Survived",x="Gender",hue ="Pclass",kind = "count",legend=True)
g.fig.set_size_inches(8,5)
g.fig.subplots_adjust(top=0.81,right=0.86)
ax = g.facet_axis(0,0)
for p in ax.patches:
  ax.text(p.get_x()- 0.01,p.get_height() * 1.02,'{0:.1f}'.format(p.get_height()),color='red',rotation='horizontal',size='small')

## Co-relation
corr = dt.corr()
sns.heatmap(corr,annot=True)

sns.pairplot(dt)
```
## OUTPUT:
![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/cbf2c30d-adcc-4ff4-b73a-c84a965f00d7)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/807bd6cd-817b-48e2-b6db-ff7db4f6c6ce)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/27b7abd3-7f0a-4d7c-b6d5-16d4e527f1a3)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/0b6357c9-7692-4af0-8703-a6870814090c)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/f0c0c3cd-7b00-44c1-9d6e-56e4087c1520)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/db1c8dae-f7e5-468c-958d-d309a080e9d8)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/03ee04ff-f199-46f9-9f10-738717fc3d26)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/3cc8f74e-c371-4044-9402-f703d2392faa)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/f870ea2b-1f81-412c-b157-7edb0fd8ec6e)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/007ab120-55f4-4eb2-ad77-bb8c19e81643)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/303942d7-f7ea-4882-9663-d6590e87269b)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/f1075358-f6f7-40d0-a629-adbb9b31c72c)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/2044ee74-c2fa-45b3-87f8-b493b13596f4)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/23deb7ab-fea6-4a59-abd6-e6735bc9308a)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/082cdb0b-e96a-4f48-9c54-6668b664681b)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/7e131ea7-50a6-4873-bb31-22ed1f0e87be)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/ef9ffcf4-4d72-4a3d-a93e-7acba9171533)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/5a90d3d6-018b-4070-8e1f-939ea83417ab)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/6a69a63c-0e16-4611-a086-caf5c880097e)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/37b1636c-8cf6-4178-9f72-2ae37d8662d3)

![image](https://github.com/Anuayshh/DS-EXPT4/assets/127651217/6874c3eb-73c8-4030-8877-811202ce0ccd)

## RESULT:
Thus the program to perform EDA on the given data set is successfully executed.




































