# Video Game Sales with Ratings Data Analysis using R
The goal of this project is to analyze the video game sales data and gain insights into the market trends, top-selling games, and factors that affect the sales of video games. This analysis will help in making informed decisions about game development, marketing, and sales strategies

## The dataset for this project has been taken from the URL link:
[Video Game Sales with Ratings](https://www.kaggle.com/datasets/rush4ratio/video-game-sales-with-ratings)

## Data Cleaning
**1. Deleting Unwanted Columns**<br>
Code to set the working directory and read the date in R Studio
```
> setwd("C:/Users/Hemalatha/Music/College/Semester 3/5250/R Project/Data")
> data_videogamesales<-read.csv("Video_Games_Sales.csv")
> View(data_videogamesales)
```
Code to delete the column in R Studio
```
> delete_column1<-data_videogamesales[,2:ncol(data_videogamesales)]
> View(delete_column1)
```

**2. Splitting the column**<br>
Installing tidyr package
```
> install.packages("tidyr")

```
Code to split the column in R Studio
```
> dates_columnsplit<-separate(data_videogamesales,Date_of_Release,c("Month","Date","Year"),sep="/")
> View(dates_columnsplit)
```

**3. Merging two columns**<br>
Code to merge two columns in R Studio
```
> combine_data_column<-unite(delete_column1,Publisher_and_Developer,Publisher, 
Developer, sep=" / ")
> View(combine_data_column)
```

## Data Analysis and Visualizations
**1. Which game genres have gained the most popularity in the gaming community?** 
```
> View(data_videogamesales)
> b<-ggplot(data_videogamesales, aes(x="Genre", fill=Genre))+geom_bar()
> b+geom_bar()
> ggplot(data_videogamesales, aes(Genre))+geom_bar()+coord_flip()
> ggplot(data_videogamesales, aes(Genre, fill=Genre))+geom_bar()+coord_flip()
```
![bar chart](https://user-images.githubusercontent.com/122247029/229645879-b92b51b5-bbd9-451f-b78e-b4790ce8f218.PNG) <br>

**2. How have “Video games” evolved since their inception in the 1980s?** 
```
>  ggplot(data_videogamesales, aes(Year_of_Release)) + geom_histogram(binwidth=0.5) 
```
![histogram](https://user-images.githubusercontent.com/122247029/229645885-5746cc05-474f-4791-9620-3add064632ea.PNG)<br>

**3 How did the games generate revenue globally during their evolution as an industry??** 
```
> ggplot(data_videogamesales, aes(Year_of_Release, Global_Sales)) + geom_line()
```
![line chart](https://user-images.githubusercontent.com/122247029/229645888-6552a491-48a0-4c11-8972-c68a9cf6b737.PNG)<br>

