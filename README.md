# Movie-Scraping-and-Regression-Mode
The major goal is to predict a domestic total gross value by using a linear regression model

## 1. Objectives



In fact, the film industry is a significant player in the global economy.  In this project, I try to answer the question, which factors, if any, contribute to the success of films at the box office that will help business area.The major goal is to predict a domestic total gross value by using a linear regression model.The main objectives of this project are:

* Using BeautifulSoup to scrape web data (must have a good knowledge in the HTML)
* Using Statsmodels and Scikit-learn to build linear regression model
* Using power transformation to variables in order to create a better model
* Experiment between Lasso, Ridge, and Elastic Net to regularize the models (solve the overfitting problem)
* Utilizing cross validation to build better model during sampling process



## 2. Workflow
The following figure shows the workflow of Predicting Movie Domestic Total Gross 
![Image test](/images/project2-1.png)



### 2.1 Scraping the Data
The data scraping was one of the most time consuming parts of this project because it’s difficult to navigate through the nested tables (the HTML). However, BeautifulSoup made it quite simple to grab the HTML and parse through it.

In this project I scraped from [boxofficemojo](https://www.boxofficemojo.com), I decided to start by scraping top of all  movies relased in 2018 so that I could build out my model. When I looked at the [page](https://www.boxofficemojo.com/yearly/chart/?yr=2018&p=.htm) that includes all movies that released on 2018, as a first step, I noticed that I need to collect all linkes of all movies then  go into each movie to collect the needed information. A lot of [interesting information](https://www.boxofficemojo.com/movies/?id=grinch2017.htm) was captured in the table at the top of each movie page. The following figure is a smaple of the strategy of scraping movies.

![Image test](/images/project2-2.png)

At the end of this step, 879 movies and 8 features were collected.After that I saved all these information into CSV file.
The featuers are Title, Domestic_Total_Gross, Distributor, Release_Date,Runtime	Production_Budget, MPAA_Rating, and Genre.The following figure is a smaple of Movies dataset:

![Image test](/images/project2-3.png)


### 2.2 Data Cleaning and Feature Engineering

The next focus was to clean the data to build a better model. I started by importing the CSV file that I had created into my Python environment then I read this file using dataframes.Next, I worked with the variables to make sure that they were able to be processed by applied the following: 

* Turning the Release Date strings into datetime objects
* Turning the runtime string from "1 hr. 52 min." to minutes float format
* Getting the Month , Day of Year and Day form Release Date
* Dealing with categorical data such as Genre and MAPP Rating
* Drop the Null values
* Shuffling Data

Regarding dealing with categorical data I used One-Hot encoding with Genre feature and Ordinal with MAPP Rating feature

### 2.3 Model Building 
The following sections describe in details model building

#### 2.3.1 Pre-Model Building 

After data cleaning steps completed,then I start to building the linear regression models.Generally, before starting building the model we should check many things. First, I create an initial plot of Domestic_Total_Gross to look to the distribution. From the following figere the initial plot looks like normal distribution so there is no need to do the log transformation

![Image test](/images/project2-4.png)

I also created a residual plot to ensure if the residuals were more or less random.It's clear from the following figere the residual is ramdom error

![Image test](/images/project2-5.png)

To check the binary correlation between featuers I build a correlation matrix

![Image test](/images/project2-6.png)

#### 2.3.2 Model Selection Process

* Stage 1 :
BaseLine model: Validation R^2= 0.119
* Stage 2:
ElasticNet model: Validation R^2=0.281
* Final Model : 
Test r^2= 0.298


## 3. Results

After completing the analysis and visualization, using a linear regression model, a month feature influence prediction of the domestic total gross.Also, the results of the model shown that there was a significant relationship between a other genre such as action and domestic total gross.For future work, other features will be selected and improve model r^2.



## 4. Resource Description
For more details please viste [Project Resource](https://github.com/LubnaAlhenaki/Movie-Scraping-and-Regression-Mode). This repo contains the following:
* Movie2018 that contain the code file.
* Project-02 pdf file that describe the project in details.

Also I recommended [The determinants of box office performance in the film industry revisited](https://pdfs.semanticscholar.org/c960/7aaa7746ec9735a19d0ab2e524e53d20ab7f.pdf) scientific paper


