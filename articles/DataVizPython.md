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


```python```



## Scatterplots

- show relationships between multiple variables
- helps you find outliners

## Bar graphs

- help compare numeric values
- good for comparing multiple values

## Data Aggregation / sampling

- using mean, percentiles
- evaluating samples multiple times







## Useful links & credits
- [📄 "Begin"](afgafgadgads)



Thanks for reading my article! Feel free to leave any feedback! 


<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
