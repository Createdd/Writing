# Implement linear regression in React

[<img src="https://images.unsplash.com/photo-1456081101716-74e616ab23d8?auto=format&fit=crop&w=1510&q=80&ixid=dW5zcGxhc2guY29tOzs7Ozs%3D">](
https://unsplash.com/photos/wpi3sDUrSEk)
Photo by Dmitry Ratushny on Unsplash - https://unsplash.com/photos/wpi3sDUrSEk

Linear regression is one of the first concepts you have to get your head around when you start with machine learning. In a simple linear regression, scores are predicted on one variable from the scores on a second variable. Very simple and powerful. Here I implemented the concept with React and visualized it with React-vis. Enjoy

[Open Source Code on Github](https://github.com/DDCreationStudios/logisticRegression/tree/feature/forArticle) (Be aware that this is only a branch of the project I am working on)

The result can be seen here: https://ddcreationstudios.github.io/logisticRegression/ 


## 📄 Table of contents


---
>“Control of consciousness determines the quality of life.” ― Mihaly Csikszentmihalyi
---


![gif](https://camo.githubusercontent.com/8702cf6f8016bc06f20490036fa028e065cf38cf/687474703a2f2f672e7265636f726469742e636f2f647271577035393139352e676966)

## On logistic regression 

> Logistic regression is a statistical analysis method used to predict a data value based on prior observations of a data set. A logistic regression model predicts a dependent data variable by analyzing the relationship between one or more existing independent variables.

## Used data

Here I have used public available data from Austria. In this example the number of marriages of all people living in Salzburg (a city in Austria) are gathered over time. It allows to show differences in age, years, wifes or husbands.

## Implementation frameworks

For creating the web application I used React with the create-react-app boilerplate.
Visualization is done with Uber's React-vis library. It integrates nicely with a React app and allows a fast development of charts and plots. The regression calculation is done with Regression.js, a library for calculating the actual regression line and additional information.

## Code walkthrough

The `index.js` provides the entry for the app. It renders `App.js`, which renders the following:

```jsx
render() {
    return (
      <div className="App">
        <header className="App-header">
          <img src={logo} className="App-logo" alt="logo" />
        </header>
        <h5>Marriages in Salzburg over time</h5>
        <Plot
          regression={this.state.regression}
          data={prepareData(this.state.age)}
        />
        <div className="fixed-action-btn">
          <a className="btn-floating btn-large waves-effect waves-light red">
            {this.renderRegressionInfo()}
          </a>
        </div>

        <ControlPanel
          switchAge={arg => this.switchAge(arg)}
          calcRegression={this.renderRegression}
        />
        {this.state.regression ? (
          <div>
            Prediction for 2020:{" "}
            {calculateRegression(prepareData(this.state.age)).prediction[1]}
          </div>
        ) : (
          ""
        )}
        <Footer />
      </div>
    );
  }
```






---

Thanks for reading my article! Feel free to leave any feedback! 

---

<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
