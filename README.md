# Ex-07-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# CODE :
### NAME : D.VINITHA NAIDU
### REG NO. : 212222230175

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/Superstore.csv",encoding="ISO-8859-1")
df
df.isnull.sum()
df.info()
df.describe()

sns.lineplot(x="Segment",y="Sales",data=df,marker='o')
plt.title("Segment vs Sales")
plt.xticks(rotation = 90)
plt.show()

sns.barplot(x="Segment",y="Sales",data=df)
plt.xticks(rotation = 90)
plt.show()
Which City has Highest profit?

df.shape
df1 = df[(df.Profit >= 60)]
df1.shape

plt.figure(figsize=(30,8))
states=df1.loc[:,["City","Profit"]]
states=states.groupby(by=["City"]).sum().sort_values(by="Profit")
sns.barplot(x=states.index,y="Profit",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("City")
plt.ylabel=("Profit")
plt.show()

sns.barplot(x="Ship Mode",y="Profit",data=df)
plt.show()

sns.lineplot(x="Ship Mode",y="Profit",data=df)
plt.show()
states=df.loc[:,["Region","Sales"]]
states=states.groupby(by=["Region"]).sum().sort_values(by="Sales")
sns.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("Region")
plt.ylabel=("Sales")
plt.show()

df.groupby(['Region']).sum().plot(kind='pie', y='Sales',figsize=(6,9),pctdistance=1.7,labeldistance=1.2)

df["Sales"].corr(df["Profit"])

df_corr = df.copy()
df_corr = df_corr[["Sales","Profit"]]
df_corr.corr()

sns.pairplot(df_corr, kind="scatter")
plt.show()

grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
ax.legend()
plt.show()

grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('City')
ax.set_ylabel('Value')
ax.legend()
plt.show()

grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('State')
ax.set_ylabel('Value')
ax.legend()
plt.show()


grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])
fig, ax = plt.subplots()
pivot_data.plot(kind='bar', ax=ax)
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
plt.legend(title='Ship Mode')
plt.show()


grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])
sns.set_style("whitegrid")
sns.set_palette("Set1")
pivot_data.plot(kind='bar', stacked=True, figsize=(10, 5))
plt.xlabel('Segment - Ship Mode')
plt.ylabel('Value')
plt.legend(title='Region')
plt.show()
```

# OUPUT :
![image](https://github.com/VinithaNaidu/Ex-08-Data-Visualization-/assets/121166004/507a3fb1-9e1d-40cc-a36c-da7e491ca3bf)
![image](https://github.com/VinithaNaidu/Ex-08-Data-Visualization-/assets/121166004/1677a2e6-f11c-4073-ab40-47bbcca14db8)
![image](https://github.com/VinithaNaidu/Ex-08-Data-Visualization-/assets/121166004/11ae1602-08ae-41f1-81be-ec71eea165f5)
![image](https://github.com/VinithaNaidu/Ex-08-Data-Visualization-/assets/121166004/45517166-80e0-409d-aad3-a5c83a58c79d)
## Which Segment has Highest sales?
![image](https://github.com/VinithaNaidu/Ex-08-Data-Visualization-/assets/121166004/d8b97eb7-7ceb-45bb-9d67-db458dc39759)
![image](https://github.com/VinithaNaidu/Ex-08-Data-Visualization-/assets/121166004/4fb9f346-4ee5-4a84-83d1-aaec48ee0ec5)
## Which City has Highest profit?
![image](https://github.com/VinithaNaidu/Ex-08-Data-Visualization-/assets/121166004/831acbc9-18b0-4118-8629-1165cafe25e9)
## Which ship mode is profitable?
![image](https://github.com/VinithaNaidu/Ex-08-Data-Visualization-/assets/121166004/d773cc73-1dae-48df-bcf0-be2647db70b1)
## Sales of the product based on region
![image](https://github.com/VinithaNaidu/Ex-08-Data-Visualization-/assets/121166004/f188b2f7-a7a2-47d1-915b-74d05582a091)
## Find the relation between sales and profit
![image](https://github.com/VinithaNaidu/Ex-08-Data-Visualization-/assets/121166004/5d3b9c7f-840c-4a7f-bced-24889b8330f9)
## Find the relation between sales and profit based on the following category.
![image](https://github.com/VinithaNaidu/Ex-08-Data-Visualization-/assets/121166004/bcdc4326-828e-4864-a7bd-2e78fd45660f)
![image](https://github.com/VinithaNaidu/Ex-08-Data-Visualization-/assets/121166004/5b935ab8-7c46-4b8e-ba3b-e51527f705ae)
![image](https://github.com/VinithaNaidu/Ex-08-Data-Visualization-/assets/121166004/b40fa785-609c-493b-a66a-2502a87c9c72)
![image](https://github.com/VinithaNaidu/Ex-08-Data-Visualization-/assets/121166004/51ec9787-52b5-4db6-b21a-38097f6baa38)
![image](https://github.com/VinithaNaidu/Ex-08-Data-Visualization-/assets/121166004/c3874877-561c-4973-af98-5a91fbbe21fc)
![image](https://github.com/VinithaNaidu/Ex-08-Data-Visualization-/assets/121166004/1ba16325-90cf-40b0-a337-ee1a0c00b1c3)
## Result:
Thus, Data Visualization is performed on the given dataset and save the data to a file.




