# Check data claims yourself with python - an example

![](https://lh3.googleusercontent.com/lFdZHvalxv9OEoU0xlGpvncXR5UQGGXdATfgcxGBYOZMw1Ly6QI73g_BiV7xXQRLguLjoTIhlvba4Cz5sXX-YqiXlnyXFiuhjm8=s0?ref=0xc36b01231a8f857b8751431c8011b09130ef92ec)


*AI created art by Author. [See on Opensea as NFT](https://opensea.io/accounts/createdd?ref=0xc36b01231a8f857b8751431c8011b09130ef92ec) inspired by [Eberhard Gross](https://unsplash.com/@eberhardgross)*


# Table of Contents

- [Check data claims yourself with python - an example](#check-data-claims-yourself-with-python---an-example)
- [Table of Contents](#table-of-contents)
- [Intro](#intro)
- [Links to results](#links-to-results)
- [Data Preparation](#data-preparation)
- [Plotly and regression lines](#plotly-and-regression-lines)
  - [PLotting data and polynomial regression](#plotting-data-and-polynomial-regression)
  - [Adding slope  of a certain point of the regression line](#adding-slope--of-a-certain-point-of-the-regression-line)
- [Animations with plotly](#animations-with-plotly)
- [Conclusion](#conclusion)
- [Disclaimer](#disclaimer)
- [About](#about)


# Intro

Public media is using data visualization more and more often.

Especially in times of the pandemic various charts and interpretations of data have been used to back up arguments.

As a business law graduate and data scientist I was always curious and sceptic about some numbers and visualizations that are portrayed in public media but also online.

In this article I show you a quick analysis of covid deaths in Austria to explore some curiosity I had. I couldn't believe some of the numbers I saw on public television and wanted to check it for myself.

I encourage you to do the same. There has never been a time where it was easier to check certain claims with analysis tools yourself.

For my analysis I used

- **Austrai's public datasets** for raw data
- **python** for programming
- **jupyter** notebook for documentation and exploration
- **pandas / numpy** library for data manipulation
- **plotly** for data visualization
- **Github** for deplyoment of code and static rendering
- **streamlit** as interactive webapp


In this article I will just pick a few things that I think are worth to be elaborated a bit more. Feel free to comment if you need more elaboration on something.


# Links to results

- Github Repo: https://github.com/Createdd/covid_analysis
- Notebook published: https://createdd.github.io/covid_analysis/
- Explanation video:
- Timelapse video:


# Data Preparation

For the data preparation it is important to understand that,

- data quality is very important
- there always needs to be some sort of pre-processing

In this case my raw data comes from a official goverment side. This means that is shall be deemed trustworthy in the eyes of the responsible department of the government but also that there might not be any proper explanation on where the data comes from and how it is collected.

In this analysis there was no special extraordinary preparation step. I did some manipulation of the formats, like changing to datetime format and created new specific columns for further usage. In the final step I merged the two used datasets and removed outliers by determining quantile thresholds.


https://jovian.ml/createdd/covid-analysis-charts-ipynb/v/1&cellId=37

# Plotly and regression lines

I want to show how easily you can integrate regression lines (from sklearn) into your plotly visualization. Because apart from the nice visualization itself, it is important to combine different datapoints in one chart. A perfect example is a regression line. And furthermore, adding a slope of the regression line.

 ## PLotting data and polynomial regression

 This can be achieved quite easily by

calculating the new points for the line

https://jovian.ml/createdd/covid-analysis-charts-ipynb/v/1&cellId=52

and then adding the line in the existing chart


https://jovian.ml/createdd/covid-analysis-charts-ipynb/v/1&cellId=53

So, merely adding `add_traces` does a great job.

However, now we want to do something more complex, namley adding the slope of a certain point of the regression line.

## Adding slope  of a certain point of the regression line

This was not so trivial to implement because you first need to understand how polynomial regressions work and then you also need to draw a nice looking tangent line. In fact, there hasn't been any impleemnation so far and that is why created an own answer for it on [Stackoverflow](https://stackoverflow.com/questions/72802695/how-can-i-add-the-slope-of-a-specific-point-in-a-polynomial-line-in-plotly/72802696#72802696) as well.

In the end it looks like that

![](https://i.stack.imgur.com/jx7we.png)

The code looks like that:

https://jovian.ml/createdd/covid-analysis-charts-ipynb/v/1&cellId=56

https://jovian.ml/createdd/covid-analysis-charts-ipynb/v/1&cellId=58

https://jovian.ml/createdd/covid-analysis-charts-ipynb/v/1&cellId=59


The heart of the implementation are those lines

```
fitted_params = np.polyfit(np.arange(0, len(y)), y, poly_degree )

polynomials = np.poly1d(fitted_params)

derivatives = np.polyder(polynomials)

y_value_at_point = polynomials(x).flatten()

slope_at_point = np.polyval(derivatives, np.arange(0, len(y)))
```

Those nice numpy functions allow you to calculate the numbers that are used to draw the tangent lines.


# Animations with plotly

The last, step was an animation within plotly. An animation that shows the movement of the tangent line.

Something like this:

![](https://camo.githubusercontent.com/17fb361b0529766bc9dc133eac10f41d4616c9a71bbe18a73cb1351da0234620/68747470733a2f2f6d656469612e67697068792e636f6d2f6d656469612f327346553977746c47416663696868746c492f67697068792e676966)


The code of that is the following

https://jovian.ml/createdd/covid-analysis-charts-ipynb/v/1&cellId=67


What is tricky to udnerstand here is, that
- first you need to add the data points and regression line as normal graph objects in plotly (traces).
- the tangent lines need to be calculated and stored as a dictionary through the timeline
- then you need to add the frames additionally to the data traces and the plotly layout
- the plotly layout also covers the config for the slider and the buttons
- note, that you need to calculate the slider steps similar to the frames within each step through the timeline

# Conclusion

Finally, it was easy to see and understand for me how the pandemic affected the death rates in Austria.

I achieved this by using open source data and open source tools.

I encourage you to do the same and check the quality of data and their visualizations you see in the media.


# Disclaimer

I am not associated with any of the services I use in this article.

I do not consider myself an expert. I merely document things besides doing other things. Therefore the content does not represent the quality of any of my professional work, nor does it fully reflect my view on things. If you have the feeling that I am missing important steps or neglected something, consider pointing it out in the comment section or get in touch with me.

This was written on **9.7.2022**.
I cannot monitor all of my articles. There is a high probability that when you read this article the tips are outdated and the processes have changed.

I am always happy for constructive input and how to improve.


---

# About

Daniel is an artist, entrepreneur, software developer, and business law graduate. His knowledge and interests currently revolve around programming machine learning applications and all their related aspects. To the core, he considers himself a problem solver of complex environments, which is reflected in his various projects.


![You can support me on https://www.buymeacoffee.com/createdd](/2020/assets/template_2020-09-25-22-32-52.png)
You can support me on https://www.buymeacoffee.com/createdd or with crypto https://etherdonation.com/d?to=0xC36b01231a8F857B8751431c8011b09130ef92eC


![picture of myself](https://avatars2.githubusercontent.com/u/22077628?s=460&v=4)

-> subscribe here on https://medium.com/subscribe/@createdd or read more on medium
-> https://medium.com/@createdd/membership


**Connect on:**

- [Allmylinks](https://allmylinks.com/createdd)

Direct:
- [LinkedIn](https://www.linkedin.com/in/createdd)
- [Github](https://github.com/Createdd)
- [Medium](https://medium.com/@createdd)
- [Twitter](https://twitter.com/_createdd)
- [Instagram](https://www.instagram.com/create.dd/)
- [createdd.com](https://www.createdd.com/)

Art-related:
- [Open Sea](https://opensea.io/accounts/createdd?ref=0xc36b01231a8f857b8751431c8011b09130ef92ec)
- [Instagram/art_and_ai](https://www.instagram.com/art_and_ai/)
- [Rarible](https://app.rarible.com/createdd/collectibles)
- [Known Origin](https://knownorigin.io/profile/0xC36b01231a8F857B8751431c8011b09130ef92eC)
- [Medium/the-art-of-art](https://medium.com/the-art-of-art)
- [Devian Art](https://www.deviantart.com/createdd1010/)

<!-- Written by Daniel Deutsch -->


