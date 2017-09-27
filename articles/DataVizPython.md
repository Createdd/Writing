# Introducing Data Visualization in Python

[<img src="https://images.unsplash.com/photo-1495639867387-5423d6811583?dpr=1&auto=compress,format&fit=crop&w=2550&h=&q=80&cs=tinysrgb&crop=">](
https://unsplash.com/photos/y3FkHW1cyBE)
Photo by Arif Wahid on Unsplash - https://unsplash.com/photos/y3FkHW1cyBE


[➡️ Github Repo is available here ⬅️](https://github.com/DDCreationStudios/pythonDataVis)


## 📄 Table of contents


---
>"To accomplish great things we must first dream, then visualize, then plan... believe... act!" - Alfred A. Montapert
---

## Python and it's eco system.

- Python as a solid established programming language
- Has many libraries (especially in the field of science and data visualization)
- Matplotlib (data visualization library)
- Pandas (for importing and processing data)
- Jupyter (interactive Python Notebook)
- Anaconda as package manager for Python

Draw a chart:
```python
import pandas as pd
from matplotlib import pyplot as plt

data = pd.read_csv('countries.csv')


austria = data[data.country == 'Austria']
plt.plot(austria.year, austria.gdpPerCapita)
plt.title('GDP per Capita of Austria')
plt.show()
```

## Distribution Data with Histograms

Histograms help you understand the distribution of a numeric value in a way that you cannot with mean or median alone.


```python
data2007 = data[data.year == 2007]
asia2007 = data2007[data2007.continent == 'Asia']
europe2007 = data2007[data2007.continent == 'Europe']

plt.subplot(211)
plt.title('Comparing GDP of EU and Asia in 2007')
plt.hist(asia2007.gdpPerCapita, 30, edgecolor='black')
plt.ylabel('Asia')
plt.subplot(212)
plt.hist(europe2007.gdpPerCapita, 30, edgecolor='black')
plt.ylabel('Europe')
plt.show()
```






## Time Series / Line Charts

- shows trend of over time
- test a hypothesis on a variety of conditions
- reduced misinterpretation of data


```python
us = data[data.country == 'United States']
china = data[data.country == 'China']

plt.plot(us.year, us.gdpPerCapita)
plt.plot(china.year, china.gdpPerCapita)
plt.legend(['United States', 'China'])
plt.xlabel('year')
plt.ylabel('GDP per capita')
plt.show()

usGrowth = us.gdpPerCapita / us.gdpPerCapita.iloc[0] * 100
chinaGrowth = china.gdpPerCapita / china.gdpPerCapita.iloc[0] * 100

plt.plot(us.year, usGrowth)
plt.plot(china.year, chinaGrowth)
plt.legend(['United States', 'China'])
plt.xlabel('year')
plt.ylabel('GDP growth per capita')
plt.show()
```



## Scatterplots

- show relationships between multiple variables
- helps you find outliners

```python
import numpy as np

plt.scatter(data2007.gdpPerCapita, data2007.lifeExpectancy)
plt.title('GDP per capita and life expectancy in 2007')
plt.xlabel('GDP per capita')
plt.ylabel('Life expectancy')
plt.show()

plt.scatter(np.log10(data2007.gdpPerCapita), data2007.lifeExpectancy)
plt.title('GDP per capita and life expectancy in 2007')
plt.xlabel('GDP per capita - log10')
plt.ylabel('Life expectancy')
plt.show()

yearsSorted = sorted(set(data.year))

for aYear in yearsSorted:
    dataYear = data[data.year == aYear]
    plt.scatter(dataYear.gdpPerCapita, dataYear.lifeExpectancy, 5)
    plt.title(aYear)
    plt.xlim(0,60000)
    plt.ylim(25, 85)
    plt.xlabel('GDP per capita')
    plt.ylabel('Life expectancy')
    plt.show()


for aYear in yearsSorted:
    dataYear = data[data.year == aYear]
    plt.scatter(np.log10(dataYear.gdpPerCapita), dataYear.lifeExpectancy, 5)
    plt.title(aYear)
    plt.xlim(2,5)
    plt.ylim(25, 85)
    plt.xlabel('GDP per capita - log10')
    plt.ylabel('Life expectancy')
    plt.show()

```



## Bar graphs

- help compare numeric values
- good for comparing multiple values



```python
top10 = data2007.sort_values('population', ascending=False).head(10)

x = range(10)
plt.bar(x, top10.population / 10**6)
plt.xticks(x, top10.country, rotation='vertical')
plt.title('10 most populous countries')
plt.ylabel('Population in mil')
plt.show()
```


## How to handle too much data?

- using mean, percentiles
- evaluating samples multiple times




## Useful links & credits


[![pluralsight logo](https://www.pluralsight.com/content/dam/pluralsight/newsroom/brand-assets/logos/pluralsight-logo-hor-color-1@2x.png)](https://www.pluralsight.com/)

See a in-depth tutorial on [Pluralsight](https://www.pluralsight.com/).



Thanks for reading my article! Feel free to leave any feedback! 


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
