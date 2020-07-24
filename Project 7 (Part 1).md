### Welcome to another lesson on Data Analysis / Data Science using the amazing Libraries in Python { Numpy, Pandas & Matplotlib }.

### This is part of sharing my learning and growth process on this career path. And also, to hope that this will encourage you to keep doing things right, even if it means doing it poorly till you gain mastery of it.

### In this lesson, I'll be working with IMDB Movies Dataset which is readily available online for public access.

### This Dataset contains 3 Sheets, and we're going to work on the 3 of them, by cleaning, exploring, analyzing, deriving insights and making visual plots as the case may require,


# So, Let's Get Started !!!

### The first step will be to import the required Libraries which is required for the task.

### These include Numpy, Pandas and Matplotlib. Remember to include "%matplotlib inline" . This will enable your plots to display in Jupyter Notebook. Skipping this step will require you to type plt.show() after every plotting code.


```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
%matplotlib inline
```

### Now, import the first sheet of the excel file and read the first lines of the Dataset.

#### Note the use of .T on the head() function. This is just an optional method to ensure the Dataset is Transposed and the full view is obtained


```python
file = pd.read_excel("movies.xls")
file.head().T
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Title</td>
      <td>Intolerance: Love's Struggle Throughout the Ages</td>
      <td>Over the Hill to the Poorhouse</td>
      <td>The Big Parade</td>
      <td>Metropolis</td>
      <td>Pandora's Box</td>
    </tr>
    <tr>
      <td>Year</td>
      <td>1916</td>
      <td>1920</td>
      <td>1925</td>
      <td>1927</td>
      <td>1929</td>
    </tr>
    <tr>
      <td>Genres</td>
      <td>Drama|History|War</td>
      <td>Crime|Drama</td>
      <td>Drama|Romance|War</td>
      <td>Drama|Sci-Fi</td>
      <td>Crime|Drama|Romance</td>
    </tr>
    <tr>
      <td>Language</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>German</td>
      <td>German</td>
    </tr>
    <tr>
      <td>Country</td>
      <td>USA</td>
      <td>USA</td>
      <td>USA</td>
      <td>Germany</td>
      <td>Germany</td>
    </tr>
    <tr>
      <td>Content Rating</td>
      <td>Not Rated</td>
      <td>NaN</td>
      <td>Not Rated</td>
      <td>Not Rated</td>
      <td>Not Rated</td>
    </tr>
    <tr>
      <td>Duration</td>
      <td>123</td>
      <td>110</td>
      <td>151</td>
      <td>145</td>
      <td>110</td>
    </tr>
    <tr>
      <td>Aspect Ratio</td>
      <td>1.33</td>
      <td>1.33</td>
      <td>1.33</td>
      <td>1.33</td>
      <td>1.33</td>
    </tr>
    <tr>
      <td>Budget</td>
      <td>385907</td>
      <td>100000</td>
      <td>245000</td>
      <td>6e+06</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>Gross Earnings</td>
      <td>NaN</td>
      <td>3e+06</td>
      <td>NaN</td>
      <td>26435</td>
      <td>9950</td>
    </tr>
    <tr>
      <td>Director</td>
      <td>D.W. Griffith</td>
      <td>Harry F. Millarde</td>
      <td>King Vidor</td>
      <td>Fritz Lang</td>
      <td>Georg Wilhelm Pabst</td>
    </tr>
    <tr>
      <td>Actor 1</td>
      <td>Lillian Gish</td>
      <td>Stephen Carr</td>
      <td>John Gilbert</td>
      <td>Brigitte Helm</td>
      <td>Louise Brooks</td>
    </tr>
    <tr>
      <td>Actor 2</td>
      <td>Mae Marsh</td>
      <td>Johnnie Walker</td>
      <td>Renée Adorée</td>
      <td>Gustav Fröhlich</td>
      <td>Francis Lederer</td>
    </tr>
    <tr>
      <td>Actor 3</td>
      <td>Walter Long</td>
      <td>Mary Carr</td>
      <td>Claire Adams</td>
      <td>Rudolf Klein-Rogge</td>
      <td>Fritz Kortner</td>
    </tr>
    <tr>
      <td>Facebook Likes - Director</td>
      <td>204</td>
      <td>0</td>
      <td>54</td>
      <td>756</td>
      <td>21</td>
    </tr>
    <tr>
      <td>Facebook Likes - Actor 1</td>
      <td>436</td>
      <td>2</td>
      <td>81</td>
      <td>136</td>
      <td>426</td>
    </tr>
    <tr>
      <td>Facebook Likes - Actor 2</td>
      <td>22</td>
      <td>2</td>
      <td>12</td>
      <td>23</td>
      <td>20</td>
    </tr>
    <tr>
      <td>Facebook Likes - Actor 3</td>
      <td>9</td>
      <td>0</td>
      <td>6</td>
      <td>18</td>
      <td>3</td>
    </tr>
    <tr>
      <td>Facebook Likes - cast Total</td>
      <td>481</td>
      <td>4</td>
      <td>108</td>
      <td>203</td>
      <td>455</td>
    </tr>
    <tr>
      <td>Facebook likes - Movie</td>
      <td>691</td>
      <td>0</td>
      <td>226</td>
      <td>12000</td>
      <td>926</td>
    </tr>
    <tr>
      <td>Facenumber in posters</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <td>User Votes</td>
      <td>10718</td>
      <td>5</td>
      <td>4849</td>
      <td>111841</td>
      <td>7431</td>
    </tr>
    <tr>
      <td>Reviews by Users</td>
      <td>88</td>
      <td>1</td>
      <td>45</td>
      <td>413</td>
      <td>84</td>
    </tr>
    <tr>
      <td>Reviews by Crtiics</td>
      <td>69</td>
      <td>1</td>
      <td>48</td>
      <td>260</td>
      <td>71</td>
    </tr>
    <tr>
      <td>IMDB Score</td>
      <td>8</td>
      <td>4.8</td>
      <td>8.3</td>
      <td>8.3</td>
      <td>8</td>
    </tr>
  </tbody>
</table>
</div>



### Now, import the second sheet of the Excel File and read the first 5 lines of the Dataset


```python
file1 = pd.read_excel("movies.xls", sheet_name = 1)
file1.head().T
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Title</td>
      <td>102 Dalmatians</td>
      <td>28 Days</td>
      <td>3 Strikes</td>
      <td>Aberdeen</td>
      <td>All the Pretty Horses</td>
    </tr>
    <tr>
      <td>Year</td>
      <td>2000</td>
      <td>2000</td>
      <td>2000</td>
      <td>2000</td>
      <td>2000</td>
    </tr>
    <tr>
      <td>Genres</td>
      <td>Adventure|Comedy|Family</td>
      <td>Comedy|Drama</td>
      <td>Comedy</td>
      <td>Drama</td>
      <td>Drama|Romance|Western</td>
    </tr>
    <tr>
      <td>Language</td>
      <td>English</td>
      <td>English</td>
      <td>English</td>
      <td>English</td>
      <td>English</td>
    </tr>
    <tr>
      <td>Country</td>
      <td>USA</td>
      <td>USA</td>
      <td>USA</td>
      <td>UK</td>
      <td>USA</td>
    </tr>
    <tr>
      <td>Content Rating</td>
      <td>G</td>
      <td>PG-13</td>
      <td>R</td>
      <td>NaN</td>
      <td>PG-13</td>
    </tr>
    <tr>
      <td>Duration</td>
      <td>100</td>
      <td>103</td>
      <td>82</td>
      <td>106</td>
      <td>220</td>
    </tr>
    <tr>
      <td>Aspect Ratio</td>
      <td>1.85</td>
      <td>1.37</td>
      <td>1.85</td>
      <td>1.85</td>
      <td>2.35</td>
    </tr>
    <tr>
      <td>Budget</td>
      <td>8.5e+07</td>
      <td>4.3e+07</td>
      <td>6e+06</td>
      <td>6.5e+06</td>
      <td>5.7e+07</td>
    </tr>
    <tr>
      <td>Gross Earnings</td>
      <td>6.69416e+07</td>
      <td>3.70355e+07</td>
      <td>9.82134e+06</td>
      <td>64148</td>
      <td>1.55271e+07</td>
    </tr>
    <tr>
      <td>Director</td>
      <td>Kevin Lima</td>
      <td>Betty Thomas</td>
      <td>DJ Pooh</td>
      <td>Hans Petter Moland</td>
      <td>Billy Bob Thornton</td>
    </tr>
    <tr>
      <td>Actor 1</td>
      <td>Ioan Gruffudd</td>
      <td>Steve Buscemi</td>
      <td>Mo'Nique</td>
      <td>Charlotte Rampling</td>
      <td>Matt Damon</td>
    </tr>
    <tr>
      <td>Actor 2</td>
      <td>Eric Idle</td>
      <td>Viggo Mortensen</td>
      <td>Mike Epps</td>
      <td>Sara-Marie Maltha</td>
      <td>Henry Thomas</td>
    </tr>
    <tr>
      <td>Actor 3</td>
      <td>Jim Carter</td>
      <td>Elizabeth Perkins</td>
      <td>Faizon Love</td>
      <td>Stellan Skarsgård</td>
      <td>Sam Shepard</td>
    </tr>
    <tr>
      <td>Facebook Likes - Director</td>
      <td>36</td>
      <td>84</td>
      <td>69</td>
      <td>19</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Facebook Likes - Actor 1</td>
      <td>2000</td>
      <td>12000</td>
      <td>939</td>
      <td>844</td>
      <td>13000</td>
    </tr>
    <tr>
      <td>Facebook Likes - Actor 2</td>
      <td>795</td>
      <td>10000</td>
      <td>706</td>
      <td>2</td>
      <td>861</td>
    </tr>
    <tr>
      <td>Facebook Likes - Actor 3</td>
      <td>439</td>
      <td>664</td>
      <td>585</td>
      <td>0</td>
      <td>820</td>
    </tr>
    <tr>
      <td>Facebook Likes - cast Total</td>
      <td>4182</td>
      <td>23864</td>
      <td>3354</td>
      <td>846</td>
      <td>15006</td>
    </tr>
    <tr>
      <td>Facebook likes - Movie</td>
      <td>372</td>
      <td>0</td>
      <td>118</td>
      <td>260</td>
      <td>652</td>
    </tr>
    <tr>
      <td>Facenumber in posters</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>2</td>
    </tr>
    <tr>
      <td>User Votes</td>
      <td>26413</td>
      <td>34597</td>
      <td>1415</td>
      <td>2601</td>
      <td>11388</td>
    </tr>
    <tr>
      <td>Reviews by Users</td>
      <td>77</td>
      <td>194</td>
      <td>10</td>
      <td>35</td>
      <td>183</td>
    </tr>
    <tr>
      <td>Reviews by Crtiics</td>
      <td>84</td>
      <td>116</td>
      <td>22</td>
      <td>28</td>
      <td>85</td>
    </tr>
    <tr>
      <td>IMDB Score</td>
      <td>4.8</td>
      <td>6</td>
      <td>4</td>
      <td>7.3</td>
      <td>5.8</td>
    </tr>
  </tbody>
</table>
</div>



### Now, import the third sheet of the excel file and read the first 5 lines of the Dataset


```python
file2 = pd.read_excel("movies.xls", sheet_name = 2)
file2.head().T
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Title</td>
      <td>127 Hours</td>
      <td>3 Backyards</td>
      <td>3</td>
      <td>8: The Mormon Proposition</td>
      <td>A Turtle's Tale: Sammy's Adventures</td>
    </tr>
    <tr>
      <td>Year</td>
      <td>2010</td>
      <td>2010</td>
      <td>2010</td>
      <td>2010</td>
      <td>2010</td>
    </tr>
    <tr>
      <td>Genres</td>
      <td>Adventure|Biography|Drama|Thriller</td>
      <td>Drama</td>
      <td>Comedy|Drama|Romance</td>
      <td>Documentary</td>
      <td>Adventure|Animation|Family</td>
    </tr>
    <tr>
      <td>Language</td>
      <td>English</td>
      <td>English</td>
      <td>German</td>
      <td>English</td>
      <td>English</td>
    </tr>
    <tr>
      <td>Country</td>
      <td>USA</td>
      <td>USA</td>
      <td>Germany</td>
      <td>USA</td>
      <td>France</td>
    </tr>
    <tr>
      <td>Content Rating</td>
      <td>R</td>
      <td>R</td>
      <td>Unrated</td>
      <td>R</td>
      <td>PG</td>
    </tr>
    <tr>
      <td>Duration</td>
      <td>94</td>
      <td>88</td>
      <td>119</td>
      <td>80</td>
      <td>88</td>
    </tr>
    <tr>
      <td>Aspect Ratio</td>
      <td>1.85</td>
      <td>NaN</td>
      <td>2.35</td>
      <td>1.78</td>
      <td>2.35</td>
    </tr>
    <tr>
      <td>Budget</td>
      <td>1.8e+07</td>
      <td>300000</td>
      <td>NaN</td>
      <td>2.5e+06</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>Gross Earnings</td>
      <td>1.83295e+07</td>
      <td>NaN</td>
      <td>59774</td>
      <td>99851</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>Director</td>
      <td>Danny Boyle</td>
      <td>Eric Mendelsohn</td>
      <td>Tom Tykwer</td>
      <td>Reed Cowan</td>
      <td>Ben Stassen</td>
    </tr>
    <tr>
      <td>Actor 1</td>
      <td>James Franco</td>
      <td>Embeth Davidtz</td>
      <td>Devid Striesow</td>
      <td>Dustin Lance Black</td>
      <td>Ed Begley Jr.</td>
    </tr>
    <tr>
      <td>Actor 2</td>
      <td>Treat Williams</td>
      <td>Edie Falco</td>
      <td>Sebastian Schipper</td>
      <td>Emily Pearson</td>
      <td>Jenny McCarthy</td>
    </tr>
    <tr>
      <td>Actor 3</td>
      <td>Kate Burton</td>
      <td>Kathryn Erbe</td>
      <td>Sophie Rois</td>
      <td>Gavin Newsom</td>
      <td>Stacy Keach</td>
    </tr>
    <tr>
      <td>Facebook Likes - Director</td>
      <td>0</td>
      <td>5</td>
      <td>670</td>
      <td>0</td>
      <td>4</td>
    </tr>
    <tr>
      <td>Facebook Likes - Actor 1</td>
      <td>11000</td>
      <td>795</td>
      <td>24</td>
      <td>191</td>
      <td>783</td>
    </tr>
    <tr>
      <td>Facebook Likes - Actor 2</td>
      <td>642</td>
      <td>659</td>
      <td>20</td>
      <td>12</td>
      <td>749</td>
    </tr>
    <tr>
      <td>Facebook Likes - Actor 3</td>
      <td>223</td>
      <td>301</td>
      <td>9</td>
      <td>5</td>
      <td>602</td>
    </tr>
    <tr>
      <td>Facebook Likes - cast Total</td>
      <td>11984</td>
      <td>1884</td>
      <td>69</td>
      <td>210</td>
      <td>3874</td>
    </tr>
    <tr>
      <td>Facebook likes - Movie</td>
      <td>63000</td>
      <td>92</td>
      <td>2000</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Facenumber in posters</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
    </tr>
    <tr>
      <td>User Votes</td>
      <td>279179</td>
      <td>554</td>
      <td>4212</td>
      <td>1138</td>
      <td>5385</td>
    </tr>
    <tr>
      <td>Reviews by Users</td>
      <td>440</td>
      <td>23</td>
      <td>18</td>
      <td>30</td>
      <td>22</td>
    </tr>
    <tr>
      <td>Reviews by Crtiics</td>
      <td>450</td>
      <td>20</td>
      <td>76</td>
      <td>28</td>
      <td>56</td>
    </tr>
    <tr>
      <td>IMDB Score</td>
      <td>7.6</td>
      <td>5.2</td>
      <td>6.8</td>
      <td>7.1</td>
      <td>6.1</td>
    </tr>
  </tbody>
</table>
</div>



### Now that the 3 sheets in the Excel File have been imported and read, you can proceed to further actions like joining the 3 files together into a single Dataset.

### But before then, confirm the state of these datasets so that you will know if further actions on the datasets are successful


```python
print(file.shape)
print(file1.shape)
print(file2.shape)
```

    (1338, 25)
    (2100, 25)
    (1604, 25)


### You can as well confirm if the column names for each of the files or Dataset are equal. Doing this now will avoid complications when you want to join the 3 Datasets together.

### Moreover, there's no harm in double-checking the status of the Dataset


```python
for A,B,C in zip(file.columns, file1.columns, file2.columns):
    if A == B == C:
        print(True)
        print(A,'=',B,'=',C,"\n")
    else:
        print(False)
```

    True
    Title = Title = Title 
    
    True
    Year = Year = Year 
    
    True
    Genres = Genres = Genres 
    
    True
    Language = Language = Language 
    
    True
    Country = Country = Country 
    
    True
    Content Rating = Content Rating = Content Rating 
    
    True
    Duration = Duration = Duration 
    
    True
    Aspect Ratio = Aspect Ratio = Aspect Ratio 
    
    True
    Budget = Budget = Budget 
    
    True
    Gross Earnings = Gross Earnings = Gross Earnings 
    
    True
    Director = Director = Director 
    
    True
    Actor 1 = Actor 1 = Actor 1 
    
    True
    Actor 2 = Actor 2 = Actor 2 
    
    True
    Actor 3 = Actor 3 = Actor 3 
    
    True
    Facebook Likes - Director = Facebook Likes - Director = Facebook Likes - Director 
    
    True
    Facebook Likes - Actor 1 = Facebook Likes - Actor 1 = Facebook Likes - Actor 1 
    
    True
    Facebook Likes - Actor 2 = Facebook Likes - Actor 2 = Facebook Likes - Actor 2 
    
    True
    Facebook Likes - Actor 3 = Facebook Likes - Actor 3 = Facebook Likes - Actor 3 
    
    True
    Facebook Likes - cast Total = Facebook Likes - cast Total = Facebook Likes - cast Total 
    
    True
    Facebook likes - Movie = Facebook likes - Movie = Facebook likes - Movie 
    
    True
    Facenumber in posters = Facenumber in posters = Facenumber in posters 
    
    True
    User Votes = User Votes = User Votes 
    
    True
    Reviews by Users = Reviews by Users = Reviews by Users 
    
    True
    Reviews by Crtiics = Reviews by Crtiics = Reviews by Crtiics 
    
    True
    IMDB Score = IMDB Score = IMDB Score 
    


### Now, it's time to join the 3 files together. Here, the pd.concat() will be utilized. 


```python
dataset = pd.concat([file, file1, file2])
print(dataset.shape)
dataset.head()
```

    (5042, 25)





<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Year</th>
      <th>Genres</th>
      <th>Language</th>
      <th>Country</th>
      <th>Content Rating</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>...</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>Intolerance: Love's Struggle Throughout the Ages</td>
      <td>1916.0</td>
      <td>Drama|History|War</td>
      <td>NaN</td>
      <td>USA</td>
      <td>Not Rated</td>
      <td>123.0</td>
      <td>1.33</td>
      <td>385907.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>436.0</td>
      <td>22.0</td>
      <td>9.0</td>
      <td>481</td>
      <td>691</td>
      <td>1.0</td>
      <td>10718</td>
      <td>88.0</td>
      <td>69.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <td>1</td>
      <td>Over the Hill to the Poorhouse</td>
      <td>1920.0</td>
      <td>Crime|Drama</td>
      <td>NaN</td>
      <td>USA</td>
      <td>NaN</td>
      <td>110.0</td>
      <td>1.33</td>
      <td>100000.0</td>
      <td>3000000.0</td>
      <td>...</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>4</td>
      <td>0</td>
      <td>1.0</td>
      <td>5</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>4.8</td>
    </tr>
    <tr>
      <td>2</td>
      <td>The Big Parade</td>
      <td>1925.0</td>
      <td>Drama|Romance|War</td>
      <td>NaN</td>
      <td>USA</td>
      <td>Not Rated</td>
      <td>151.0</td>
      <td>1.33</td>
      <td>245000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>81.0</td>
      <td>12.0</td>
      <td>6.0</td>
      <td>108</td>
      <td>226</td>
      <td>0.0</td>
      <td>4849</td>
      <td>45.0</td>
      <td>48.0</td>
      <td>8.3</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Metropolis</td>
      <td>1927.0</td>
      <td>Drama|Sci-Fi</td>
      <td>German</td>
      <td>Germany</td>
      <td>Not Rated</td>
      <td>145.0</td>
      <td>1.33</td>
      <td>6000000.0</td>
      <td>26435.0</td>
      <td>...</td>
      <td>136.0</td>
      <td>23.0</td>
      <td>18.0</td>
      <td>203</td>
      <td>12000</td>
      <td>1.0</td>
      <td>111841</td>
      <td>413.0</td>
      <td>260.0</td>
      <td>8.3</td>
    </tr>
    <tr>
      <td>4</td>
      <td>Pandora's Box</td>
      <td>1929.0</td>
      <td>Crime|Drama|Romance</td>
      <td>German</td>
      <td>Germany</td>
      <td>Not Rated</td>
      <td>110.0</td>
      <td>1.33</td>
      <td>NaN</td>
      <td>9950.0</td>
      <td>...</td>
      <td>426.0</td>
      <td>20.0</td>
      <td>3.0</td>
      <td>455</td>
      <td>926</td>
      <td>1.0</td>
      <td>7431</td>
      <td>84.0</td>
      <td>71.0</td>
      <td>8.0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 25 columns</p>
</div>



### How are you sure that what you've done is correct ?

### You can write a small code to confirm the authenticity of the last step 

### Remember when dealing with data, you cannot be overbearing as double-checking is concerned. Any mistake in the handling of data will affect all your actions and results across-the-board. And in most cases than not, it's a flawed outcome.


```python
print("The index size of file is :",len(file.index),"\n")
print("The index size of file1 is :",len(file1.index),"\n")
print("The index size o file2 is :",len(file2.index),"\n")
print("The index size of the combined dataset is :",len(file1) + len(file) + len(file2))
print("The index size of dataset is :",len(dataset.index))
```

    The index size of file is : 1338 
    
    The index size of file1 is : 2100 
    
    The index size o file2 is : 1604 
    
    The index size of the combined dataset is : 5042
    The index size of dataset is : 5042


### And just a simple process like the one displayed below can save you tons of stress that might arise later because you didn't double-check


```python
combined_dataset = len(file.index) + len(file1.index) + len(file2.index)
if len(dataset.index) == combined_dataset :
    print("Your concatenation process is correct. You can Proceed")
else :
    print("Your Concatenation process has some erroei. Kindly rectify it before you proceed")
```

    Your concatenation process is correct. You can Proceed


### And now that this process is confirmed accurate, you can proceed to get familiar with the dadaset that you will now be working with.

### Check its Statistical details, its attributes and all other necessary things that will give you a fair idea of the dataset


```python
dataset.shape
```




    (5042, 25)




```python
dataset.size
```




    126050




```python
dataset.dtypes
```




    Title                           object
    Year                           float64
    Genres                          object
    Language                        object
    Country                         object
    Content Rating                  object
    Duration                       float64
    Aspect Ratio                   float64
    Budget                         float64
    Gross Earnings                 float64
    Director                        object
    Actor 1                         object
    Actor 2                         object
    Actor 3                         object
    Facebook Likes - Director      float64
    Facebook Likes - Actor 1       float64
    Facebook Likes - Actor 2       float64
    Facebook Likes - Actor 3       float64
    Facebook Likes - cast Total      int64
    Facebook likes - Movie           int64
    Facenumber in posters          float64
    User Votes                       int64
    Reviews by Users               float64
    Reviews by Crtiics             float64
    IMDB Score                     float64
    dtype: object




```python
pd.value_counts(dataset.dtypes)
```




    float64    13
    object      9
    int64       3
    dtype: int64




```python
dataset.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 5042 entries, 0 to 1603
    Data columns (total 25 columns):
    Title                          5042 non-null object
    Year                           4935 non-null float64
    Genres                         5042 non-null object
    Language                       5031 non-null object
    Country                        5038 non-null object
    Content Rating                 4740 non-null object
    Duration                       5028 non-null float64
    Aspect Ratio                   4714 non-null float64
    Budget                         4551 non-null float64
    Gross Earnings                 4159 non-null float64
    Director                       4938 non-null object
    Actor 1                        5035 non-null object
    Actor 2                        5029 non-null object
    Actor 3                        5020 non-null object
    Facebook Likes - Director      4938 non-null float64
    Facebook Likes - Actor 1       5035 non-null float64
    Facebook Likes - Actor 2       5029 non-null float64
    Facebook Likes - Actor 3       5020 non-null float64
    Facebook Likes - cast Total    5042 non-null int64
    Facebook likes - Movie         5042 non-null int64
    Facenumber in posters          5029 non-null float64
    User Votes                     5042 non-null int64
    Reviews by Users               5022 non-null float64
    Reviews by Crtiics             4993 non-null float64
    IMDB Score                     5042 non-null float64
    dtypes: float64(13), int64(3), object(9)
    memory usage: 846.9+ KB


### From the above details using the info() attribute of the dataset, it's observed that the index column of the dataset is not well labeled.

### It's necessary to check it out and correct it accordingly

### Even though this could've been corrected when the 3 datasets were concatenated, ( because pd.concat takes the "ignore_index" parameter), it's not too much of hassle to correct that below with just 1 or 2 lines of code(s)

### That will be corrected below and check again


```python
new_index = range(0,5042)
dataset.index = new_index
dataset.index
```




    RangeIndex(start=0, stop=5042, step=1)




```python
dataset.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 5042 entries, 0 to 5041
    Data columns (total 25 columns):
    Title                          5042 non-null object
    Year                           4935 non-null float64
    Genres                         5042 non-null object
    Language                       5031 non-null object
    Country                        5038 non-null object
    Content Rating                 4740 non-null object
    Duration                       5028 non-null float64
    Aspect Ratio                   4714 non-null float64
    Budget                         4551 non-null float64
    Gross Earnings                 4159 non-null float64
    Director                       4938 non-null object
    Actor 1                        5035 non-null object
    Actor 2                        5029 non-null object
    Actor 3                        5020 non-null object
    Facebook Likes - Director      4938 non-null float64
    Facebook Likes - Actor 1       5035 non-null float64
    Facebook Likes - Actor 2       5029 non-null float64
    Facebook Likes - Actor 3       5020 non-null float64
    Facebook Likes - cast Total    5042 non-null int64
    Facebook likes - Movie         5042 non-null int64
    Facenumber in posters          5029 non-null float64
    User Votes                     5042 non-null int64
    Reviews by Users               5022 non-null float64
    Reviews by Crtiics             4993 non-null float64
    IMDB Score                     5042 non-null float64
    dtypes: float64(13), int64(3), object(9)
    memory usage: 807.6+ KB



```python
dataset.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>Facebook Likes - Director</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>count</td>
      <td>4935.000000</td>
      <td>5028.000000</td>
      <td>4714.000000</td>
      <td>4.551000e+03</td>
      <td>4.159000e+03</td>
      <td>4938.000000</td>
      <td>5035.000000</td>
      <td>5029.000000</td>
      <td>5020.000000</td>
      <td>5042.000000</td>
      <td>5042.000000</td>
      <td>5029.000000</td>
      <td>5.042000e+03</td>
      <td>5022.000000</td>
      <td>4993.000000</td>
      <td>5042.000000</td>
    </tr>
    <tr>
      <td>mean</td>
      <td>2002.470517</td>
      <td>107.201074</td>
      <td>2.220403</td>
      <td>3.975262e+07</td>
      <td>4.846841e+07</td>
      <td>686.621709</td>
      <td>6561.323932</td>
      <td>1652.080533</td>
      <td>645.009761</td>
      <td>9700.959143</td>
      <td>7527.457160</td>
      <td>1.371446</td>
      <td>8.368475e+04</td>
      <td>272.770808</td>
      <td>140.194272</td>
      <td>6.442007</td>
    </tr>
    <tr>
      <td>std</td>
      <td>12.474599</td>
      <td>25.197441</td>
      <td>1.385113</td>
      <td>2.061149e+08</td>
      <td>6.845299e+07</td>
      <td>2813.602405</td>
      <td>15021.977635</td>
      <td>4042.774685</td>
      <td>1665.041728</td>
      <td>18165.101925</td>
      <td>19322.070537</td>
      <td>2.013683</td>
      <td>1.384940e+05</td>
      <td>377.982886</td>
      <td>121.601675</td>
      <td>1.125189</td>
    </tr>
    <tr>
      <td>min</td>
      <td>1916.000000</td>
      <td>7.000000</td>
      <td>1.180000</td>
      <td>2.180000e+02</td>
      <td>1.620000e+02</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>5.000000e+00</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.600000</td>
    </tr>
    <tr>
      <td>25%</td>
      <td>1999.000000</td>
      <td>93.000000</td>
      <td>1.850000</td>
      <td>6.000000e+06</td>
      <td>5.340988e+06</td>
      <td>7.000000</td>
      <td>614.500000</td>
      <td>281.000000</td>
      <td>133.000000</td>
      <td>1411.250000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>8.599250e+03</td>
      <td>65.000000</td>
      <td>50.000000</td>
      <td>5.800000</td>
    </tr>
    <tr>
      <td>50%</td>
      <td>2005.000000</td>
      <td>103.000000</td>
      <td>2.350000</td>
      <td>2.000000e+07</td>
      <td>2.551750e+07</td>
      <td>49.000000</td>
      <td>988.000000</td>
      <td>595.000000</td>
      <td>371.500000</td>
      <td>3091.000000</td>
      <td>166.000000</td>
      <td>1.000000</td>
      <td>3.437100e+04</td>
      <td>156.000000</td>
      <td>110.000000</td>
      <td>6.600000</td>
    </tr>
    <tr>
      <td>75%</td>
      <td>2011.000000</td>
      <td>118.000000</td>
      <td>2.350000</td>
      <td>4.500000e+07</td>
      <td>6.230944e+07</td>
      <td>194.750000</td>
      <td>11000.000000</td>
      <td>918.000000</td>
      <td>636.000000</td>
      <td>13758.750000</td>
      <td>3000.000000</td>
      <td>2.000000</td>
      <td>9.634700e+04</td>
      <td>326.000000</td>
      <td>195.000000</td>
      <td>7.200000</td>
    </tr>
    <tr>
      <td>max</td>
      <td>2016.000000</td>
      <td>511.000000</td>
      <td>16.000000</td>
      <td>1.221550e+10</td>
      <td>7.605058e+08</td>
      <td>23000.000000</td>
      <td>640000.000000</td>
      <td>137000.000000</td>
      <td>23000.000000</td>
      <td>656730.000000</td>
      <td>349000.000000</td>
      <td>43.000000</td>
      <td>1.689764e+06</td>
      <td>5060.000000</td>
      <td>813.000000</td>
      <td>9.500000</td>
    </tr>
  </tbody>
</table>
</div>



### Okay, time to check up for duplicate values. And whatever the outcome is will be treated accordingly


```python
dataset.duplicated().sum()
```




    45



### From the above results, there's and indication that there's a total of 45 duplicate values in the dataset.

### Instead of just taking that blindly, why not let's dig deeper to actually


```python
dup_values = dataset[dataset.duplicated()]
dup_values
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Year</th>
      <th>Genres</th>
      <th>Language</th>
      <th>Country</th>
      <th>Content Rating</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>...</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>131</td>
      <td>Night of the Living Dead</td>
      <td>1968.0</td>
      <td>Drama|Horror|Mystery</td>
      <td>English</td>
      <td>USA</td>
      <td>Unrated</td>
      <td>96.0</td>
      <td>1.85</td>
      <td>114000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>125.0</td>
      <td>108.0</td>
      <td>56.0</td>
      <td>403</td>
      <td>0</td>
      <td>5.0</td>
      <td>87978</td>
      <td>580.0</td>
      <td>284.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <td>167</td>
      <td>The French Connection</td>
      <td>1971.0</td>
      <td>Action|Crime|Drama|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>104.0</td>
      <td>1.85</td>
      <td>1800000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>813.0</td>
      <td>165.0</td>
      <td>109.0</td>
      <td>1196</td>
      <td>0</td>
      <td>0.0</td>
      <td>82476</td>
      <td>280.0</td>
      <td>138.0</td>
      <td>7.8</td>
    </tr>
    <tr>
      <td>237</td>
      <td>Halloween</td>
      <td>1978.0</td>
      <td>Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>101.0</td>
      <td>2.35</td>
      <td>300000.0</td>
      <td>47000000.0</td>
      <td>...</td>
      <td>2000.0</td>
      <td>742.0</td>
      <td>598.0</td>
      <td>4400</td>
      <td>12000</td>
      <td>0.0</td>
      <td>157857</td>
      <td>1191.0</td>
      <td>318.0</td>
      <td>7.9</td>
    </tr>
    <tr>
      <td>296</td>
      <td>History of the World: Part I</td>
      <td>1981.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>92.0</td>
      <td>2.35</td>
      <td>11000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>898.0</td>
      <td>842.0</td>
      <td>3931</td>
      <td>0</td>
      <td>0.0</td>
      <td>36559</td>
      <td>131.0</td>
      <td>48.0</td>
      <td>6.9</td>
    </tr>
    <tr>
      <td>321</td>
      <td>Cat People</td>
      <td>1982.0</td>
      <td>Fantasy|Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>93.0</td>
      <td>1.85</td>
      <td>18000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>783.0</td>
      <td>782.0</td>
      <td>697.0</td>
      <td>3700</td>
      <td>0</td>
      <td>1.0</td>
      <td>14193</td>
      <td>106.0</td>
      <td>130.0</td>
      <td>6.1</td>
    </tr>
    <tr>
      <td>381</td>
      <td>Footloose</td>
      <td>1984.0</td>
      <td>Drama|Music|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>107.0</td>
      <td>1.85</td>
      <td>8200000.0</td>
      <td>80000000.0</td>
      <td>...</td>
      <td>967.0</td>
      <td>455.0</td>
      <td>304.0</td>
      <td>1962</td>
      <td>0</td>
      <td>0.0</td>
      <td>51459</td>
      <td>113.0</td>
      <td>60.0</td>
      <td>6.5</td>
    </tr>
    <tr>
      <td>498</td>
      <td>Dangerous Liaisons</td>
      <td>1988.0</td>
      <td>Drama|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>119.0</td>
      <td>1.85</td>
      <td>14000000.0</td>
      <td>34700000.0</td>
      <td>...</td>
      <td>18000.0</td>
      <td>17000.0</td>
      <td>418.0</td>
      <td>35501</td>
      <td>0</td>
      <td>2.0</td>
      <td>52846</td>
      <td>143.0</td>
      <td>51.0</td>
      <td>7.7</td>
    </tr>
    <tr>
      <td>579</td>
      <td>Total Recall</td>
      <td>1990.0</td>
      <td>Action|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>113.0</td>
      <td>1.85</td>
      <td>65000000.0</td>
      <td>119412921.0</td>
      <td>...</td>
      <td>605.0</td>
      <td>308.0</td>
      <td>217.0</td>
      <td>1441</td>
      <td>0</td>
      <td>0.0</td>
      <td>240241</td>
      <td>391.0</td>
      <td>196.0</td>
      <td>7.5</td>
    </tr>
    <tr>
      <td>851</td>
      <td>Hamlet</td>
      <td>1996.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>UK</td>
      <td>PG-13</td>
      <td>150.0</td>
      <td>2.20</td>
      <td>18000000.0</td>
      <td>4414535.0</td>
      <td>...</td>
      <td>597.0</td>
      <td>591.0</td>
      <td>401.0</td>
      <td>1645</td>
      <td>0</td>
      <td>0.0</td>
      <td>30618</td>
      <td>224.0</td>
      <td>85.0</td>
      <td>7.8</td>
    </tr>
    <tr>
      <td>1011</td>
      <td>The Full Monty</td>
      <td>1997.0</td>
      <td>Comedy|Drama|Music</td>
      <td>English</td>
      <td>UK</td>
      <td>R</td>
      <td>91.0</td>
      <td>1.85</td>
      <td>3500000.0</td>
      <td>45857453.0</td>
      <td>...</td>
      <td>1000.0</td>
      <td>891.0</td>
      <td>121.0</td>
      <td>2323</td>
      <td>0</td>
      <td>3.0</td>
      <td>82232</td>
      <td>174.0</td>
      <td>122.0</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>1139</td>
      <td>The Love Letter</td>
      <td>1998.0</td>
      <td>Fantasy|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>Unrated</td>
      <td>99.0</td>
      <td>1.33</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>393.0</td>
      <td>224.0</td>
      <td>2166</td>
      <td>515</td>
      <td>1.0</td>
      <td>1465</td>
      <td>56.0</td>
      <td>NaN</td>
      <td>7.4</td>
    </tr>
    <tr>
      <td>1449</td>
      <td>Snatch</td>
      <td>2000.0</td>
      <td>Comedy|Crime</td>
      <td>English</td>
      <td>UK</td>
      <td>R</td>
      <td>104.0</td>
      <td>1.85</td>
      <td>6000000.0</td>
      <td>30093107.0</td>
      <td>...</td>
      <td>26000.0</td>
      <td>11000.0</td>
      <td>1000.0</td>
      <td>39175</td>
      <td>27000</td>
      <td>6.0</td>
      <td>600996</td>
      <td>726.0</td>
      <td>151.0</td>
      <td>8.3</td>
    </tr>
    <tr>
      <td>1463</td>
      <td>The Claim</td>
      <td>2000.0</td>
      <td>Drama|Romance|Western</td>
      <td>English</td>
      <td>UK</td>
      <td>R</td>
      <td>115.0</td>
      <td>2.35</td>
      <td>20000000.0</td>
      <td>403932.0</td>
      <td>...</td>
      <td>14000.0</td>
      <td>900.0</td>
      <td>887.0</td>
      <td>17104</td>
      <td>141</td>
      <td>4.0</td>
      <td>5254</td>
      <td>92.0</td>
      <td>71.0</td>
      <td>6.5</td>
    </tr>
    <tr>
      <td>1561</td>
      <td>From Hell</td>
      <td>2001.0</td>
      <td>Horror|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>122.0</td>
      <td>2.35</td>
      <td>35000000.0</td>
      <td>31598308.0</td>
      <td>...</td>
      <td>40000.0</td>
      <td>1000.0</td>
      <td>140.0</td>
      <td>41636</td>
      <td>0</td>
      <td>1.0</td>
      <td>124765</td>
      <td>541.0</td>
      <td>208.0</td>
      <td>6.8</td>
    </tr>
    <tr>
      <td>1618</td>
      <td>O</td>
      <td>2001.0</td>
      <td>Drama|Romance|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>95.0</td>
      <td>1.85</td>
      <td>5000000.0</td>
      <td>16017403.0</td>
      <td>...</td>
      <td>1000.0</td>
      <td>835.0</td>
      <td>697.0</td>
      <td>3300</td>
      <td>0</td>
      <td>2.0</td>
      <td>17333</td>
      <td>153.0</td>
      <td>92.0</td>
      <td>6.2</td>
    </tr>
    <tr>
      <td>1660</td>
      <td>The Fast and the Furious</td>
      <td>2001.0</td>
      <td>Action|Crime|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>106.0</td>
      <td>2.35</td>
      <td>38000000.0</td>
      <td>144512310.0</td>
      <td>...</td>
      <td>23000.0</td>
      <td>14000.0</td>
      <td>4000.0</td>
      <td>45327</td>
      <td>14000</td>
      <td>2.0</td>
      <td>272223</td>
      <td>988.0</td>
      <td>187.0</td>
      <td>6.7</td>
    </tr>
    <tr>
      <td>1721</td>
      <td>Big Fat Liar</td>
      <td>2002.0</td>
      <td>Adventure|Comedy|Family</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>88.0</td>
      <td>1.85</td>
      <td>15000000.0</td>
      <td>47811275.0</td>
      <td>...</td>
      <td>934.0</td>
      <td>927.0</td>
      <td>799.0</td>
      <td>3707</td>
      <td>896</td>
      <td>1.0</td>
      <td>29008</td>
      <td>99.0</td>
      <td>69.0</td>
      <td>5.4</td>
    </tr>
    <tr>
      <td>1744</td>
      <td>Crossroads</td>
      <td>2002.0</td>
      <td>Comedy|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>93.0</td>
      <td>1.85</td>
      <td>12000000.0</td>
      <td>37188667.0</td>
      <td>...</td>
      <td>1000.0</td>
      <td>188.0</td>
      <td>135.0</td>
      <td>1531</td>
      <td>0</td>
      <td>1.0</td>
      <td>34219</td>
      <td>578.0</td>
      <td>111.0</td>
      <td>3.3</td>
    </tr>
    <tr>
      <td>1778</td>
      <td>Hero</td>
      <td>2002.0</td>
      <td>Action|Adventure|History</td>
      <td>Mandarin</td>
      <td>China</td>
      <td>PG-13</td>
      <td>80.0</td>
      <td>2.35</td>
      <td>31000000.0</td>
      <td>84961.0</td>
      <td>...</td>
      <td>5000.0</td>
      <td>643.0</td>
      <td>576.0</td>
      <td>6229</td>
      <td>0</td>
      <td>4.0</td>
      <td>149414</td>
      <td>841.0</td>
      <td>283.0</td>
      <td>7.9</td>
    </tr>
    <tr>
      <td>1849</td>
      <td>Stealing Harvard</td>
      <td>2002.0</td>
      <td>Comedy|Crime</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>85.0</td>
      <td>1.85</td>
      <td>25000000.0</td>
      <td>13973532.0</td>
      <td>...</td>
      <td>985.0</td>
      <td>637.0</td>
      <td>455.0</td>
      <td>3065</td>
      <td>215</td>
      <td>1.0</td>
      <td>11211</td>
      <td>92.0</td>
      <td>52.0</td>
      <td>5.1</td>
    </tr>
    <tr>
      <td>2118</td>
      <td>Crash</td>
      <td>2004.0</td>
      <td>Crime|Drama|Thriller</td>
      <td>English</td>
      <td>Germany</td>
      <td>R</td>
      <td>115.0</td>
      <td>2.35</td>
      <td>6500000.0</td>
      <td>54557348.0</td>
      <td>...</td>
      <td>3000.0</td>
      <td>912.0</td>
      <td>911.0</td>
      <td>5732</td>
      <td>18000</td>
      <td>0.0</td>
      <td>361169</td>
      <td>1624.0</td>
      <td>287.0</td>
      <td>7.9</td>
    </tr>
    <tr>
      <td>2232</td>
      <td>The Alamo</td>
      <td>2004.0</td>
      <td>Drama|History|War|Western</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>137.0</td>
      <td>2.35</td>
      <td>107000000.0</td>
      <td>22406362.0</td>
      <td>...</td>
      <td>2000.0</td>
      <td>973.0</td>
      <td>877.0</td>
      <td>5780</td>
      <td>701</td>
      <td>0.0</td>
      <td>16832</td>
      <td>267.0</td>
      <td>106.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <td>2282</td>
      <td>Wicker Park</td>
      <td>2004.0</td>
      <td>Drama|Mystery|Romance|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>114.0</td>
      <td>2.35</td>
      <td>30000000.0</td>
      <td>12831121.0</td>
      <td>...</td>
      <td>489.0</td>
      <td>93.0</td>
      <td>40.0</td>
      <td>679</td>
      <td>0</td>
      <td>0.0</td>
      <td>44979</td>
      <td>298.0</td>
      <td>98.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <td>2707</td>
      <td>The Illusionist</td>
      <td>2006.0</td>
      <td>Drama|Mystery|Romance|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>110.0</td>
      <td>1.85</td>
      <td>16000000.0</td>
      <td>39825798.0</td>
      <td>...</td>
      <td>3000.0</td>
      <td>979.0</td>
      <td>96.0</td>
      <td>4210</td>
      <td>15000</td>
      <td>3.0</td>
      <td>295375</td>
      <td>645.0</td>
      <td>236.0</td>
      <td>7.6</td>
    </tr>
    <tr>
      <td>2757</td>
      <td>A Dog's Breakfast</td>
      <td>2007.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>Canada</td>
      <td>NaN</td>
      <td>88.0</td>
      <td>1.78</td>
      <td>120000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>847.0</td>
      <td>686.0</td>
      <td>405.0</td>
      <td>2364</td>
      <td>377</td>
      <td>2.0</td>
      <td>3262</td>
      <td>46.0</td>
      <td>8.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <td>2791</td>
      <td>Death at a Funeral</td>
      <td>2007.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>87.0</td>
      <td>1.85</td>
      <td>9000000.0</td>
      <td>8579684.0</td>
      <td>...</td>
      <td>22000.0</td>
      <td>557.0</td>
      <td>548.0</td>
      <td>24324</td>
      <td>0</td>
      <td>0.0</td>
      <td>89547</td>
      <td>199.0</td>
      <td>168.0</td>
      <td>7.4</td>
    </tr>
    <tr>
      <td>3192</td>
      <td>A Woman, a Gun and a Noodle Shop</td>
      <td>2009.0</td>
      <td>Comedy|Drama</td>
      <td>Mandarin</td>
      <td>China</td>
      <td>R</td>
      <td>95.0</td>
      <td>2.35</td>
      <td>NaN</td>
      <td>190666.0</td>
      <td>...</td>
      <td>9.0</td>
      <td>4.0</td>
      <td>3.0</td>
      <td>18</td>
      <td>784</td>
      <td>1.0</td>
      <td>2410</td>
      <td>20.0</td>
      <td>101.0</td>
      <td>5.7</td>
    </tr>
    <tr>
      <td>3272</td>
      <td>Halloween II</td>
      <td>2009.0</td>
      <td>Horror</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>119.0</td>
      <td>1.85</td>
      <td>15000000.0</td>
      <td>33386128.0</td>
      <td>...</td>
      <td>908.0</td>
      <td>764.0</td>
      <td>593.0</td>
      <td>3226</td>
      <td>3000</td>
      <td>0.0</td>
      <td>36372</td>
      <td>491.0</td>
      <td>220.0</td>
      <td>4.9</td>
    </tr>
    <tr>
      <td>3555</td>
      <td>My Soul to Take</td>
      <td>2010.0</td>
      <td>Horror|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>107.0</td>
      <td>2.35</td>
      <td>25000000.0</td>
      <td>14637490.0</td>
      <td>...</td>
      <td>798.0</td>
      <td>374.0</td>
      <td>255.0</td>
      <td>2537</td>
      <td>0</td>
      <td>2.0</td>
      <td>16411</td>
      <td>136.0</td>
      <td>160.0</td>
      <td>4.8</td>
    </tr>
    <tr>
      <td>4049</td>
      <td>The Avengers</td>
      <td>2012.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>173.0</td>
      <td>1.85</td>
      <td>220000000.0</td>
      <td>623279547.0</td>
      <td>...</td>
      <td>26000.0</td>
      <td>21000.0</td>
      <td>19000.0</td>
      <td>87697</td>
      <td>123000</td>
      <td>3.0</td>
      <td>995415</td>
      <td>1722.0</td>
      <td>703.0</td>
      <td>8.1</td>
    </tr>
    <tr>
      <td>4082</td>
      <td>The Possession</td>
      <td>2012.0</td>
      <td>Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>92.0</td>
      <td>2.35</td>
      <td>14000000.0</td>
      <td>49122319.0</td>
      <td>...</td>
      <td>941.0</td>
      <td>459.0</td>
      <td>309.0</td>
      <td>2348</td>
      <td>17000</td>
      <td>0.0</td>
      <td>47169</td>
      <td>162.0</td>
      <td>264.0</td>
      <td>5.9</td>
    </tr>
    <tr>
      <td>4088</td>
      <td>The Twilight Saga: Breaking Dawn - Part 2</td>
      <td>2012.0</td>
      <td>Adventure|Drama|Fantasy|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>115.0</td>
      <td>2.35</td>
      <td>120000000.0</td>
      <td>292298923.0</td>
      <td>...</td>
      <td>21000.0</td>
      <td>17000.0</td>
      <td>12000.0</td>
      <td>59177</td>
      <td>65000</td>
      <td>3.0</td>
      <td>185394</td>
      <td>329.0</td>
      <td>322.0</td>
      <td>5.5</td>
    </tr>
    <tr>
      <td>4335</td>
      <td>Trance</td>
      <td>2013.0</td>
      <td>Crime|Drama|Mystery|Thriller</td>
      <td>English</td>
      <td>UK</td>
      <td>R</td>
      <td>101.0</td>
      <td>2.35</td>
      <td>20000000.0</td>
      <td>2319187.0</td>
      <td>...</td>
      <td>3000.0</td>
      <td>1000.0</td>
      <td>888.0</td>
      <td>5056</td>
      <td>23000</td>
      <td>0.0</td>
      <td>92640</td>
      <td>212.0</td>
      <td>393.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <td>4443</td>
      <td>Hercules</td>
      <td>2014.0</td>
      <td>Action|Adventure</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>101.0</td>
      <td>2.35</td>
      <td>100000000.0</td>
      <td>72660029.0</td>
      <td>...</td>
      <td>12000.0</td>
      <td>3000.0</td>
      <td>467.0</td>
      <td>16235</td>
      <td>21000</td>
      <td>0.0</td>
      <td>115687</td>
      <td>269.0</td>
      <td>245.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <td>4467</td>
      <td>Left Behind</td>
      <td>2014.0</td>
      <td>Action|Drama|Fantasy|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>110.0</td>
      <td>2.35</td>
      <td>16000000.0</td>
      <td>13998282.0</td>
      <td>...</td>
      <td>12000.0</td>
      <td>1000.0</td>
      <td>734.0</td>
      <td>15044</td>
      <td>31000</td>
      <td>1.0</td>
      <td>24854</td>
      <td>374.0</td>
      <td>169.0</td>
      <td>3.1</td>
    </tr>
    <tr>
      <td>4538</td>
      <td>The Calling</td>
      <td>2014.0</td>
      <td>Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>108.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>2000.0</td>
      <td>1000.0</td>
      <td>826.0</td>
      <td>4385</td>
      <td>0</td>
      <td>2.0</td>
      <td>6025</td>
      <td>28.0</td>
      <td>48.0</td>
      <td>5.8</td>
    </tr>
    <tr>
      <td>4588</td>
      <td>Unbroken</td>
      <td>2014.0</td>
      <td>Biography|Drama|Sport|War</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>137.0</td>
      <td>2.35</td>
      <td>65000000.0</td>
      <td>115603980.0</td>
      <td>...</td>
      <td>769.0</td>
      <td>698.0</td>
      <td>465.0</td>
      <td>2938</td>
      <td>35000</td>
      <td>0.0</td>
      <td>103589</td>
      <td>351.0</td>
      <td>322.0</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>4669</td>
      <td>Fantastic Four</td>
      <td>2015.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>100.0</td>
      <td>2.35</td>
      <td>120000000.0</td>
      <td>56114221.0</td>
      <td>...</td>
      <td>596.0</td>
      <td>360.0</td>
      <td>78.0</td>
      <td>1261</td>
      <td>41000</td>
      <td>3.0</td>
      <td>110486</td>
      <td>695.0</td>
      <td>369.0</td>
      <td>4.3</td>
    </tr>
    <tr>
      <td>4674</td>
      <td>Forsaken</td>
      <td>2015.0</td>
      <td>Drama|Western</td>
      <td>English</td>
      <td>Canada</td>
      <td>R</td>
      <td>90.0</td>
      <td>2.35</td>
      <td>11000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>2000.0</td>
      <td>1000.0</td>
      <td>720.0</td>
      <td>4142</td>
      <td>0</td>
      <td>1.0</td>
      <td>4693</td>
      <td>49.0</td>
      <td>45.0</td>
      <td>6.3</td>
    </tr>
    <tr>
      <td>4721</td>
      <td>Pan</td>
      <td>2015.0</td>
      <td>Adventure|Family|Fantasy</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>111.0</td>
      <td>2.35</td>
      <td>150000000.0</td>
      <td>34964818.0</td>
      <td>...</td>
      <td>20000.0</td>
      <td>548.0</td>
      <td>394.0</td>
      <td>21393</td>
      <td>24000</td>
      <td>4.0</td>
      <td>39956</td>
      <td>186.0</td>
      <td>256.0</td>
      <td>5.8</td>
    </tr>
    <tr>
      <td>4819</td>
      <td>Victor Frankenstein</td>
      <td>2015.0</td>
      <td>Drama|Horror|Sci-Fi|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>110.0</td>
      <td>2.35</td>
      <td>40000000.0</td>
      <td>5773519.0</td>
      <td>...</td>
      <td>11000.0</td>
      <td>1000.0</td>
      <td>287.0</td>
      <td>12876</td>
      <td>11000</td>
      <td>2.0</td>
      <td>28618</td>
      <td>91.0</td>
      <td>159.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <td>4838</td>
      <td>Bad Moms</td>
      <td>2016.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>100.0</td>
      <td>NaN</td>
      <td>20000000.0</td>
      <td>55461307.0</td>
      <td>...</td>
      <td>15000.0</td>
      <td>1000.0</td>
      <td>851.0</td>
      <td>18786</td>
      <td>18000</td>
      <td>9.0</td>
      <td>4654</td>
      <td>46.0</td>
      <td>81.0</td>
      <td>6.7</td>
    </tr>
    <tr>
      <td>4863</td>
      <td>Godzilla Resurgence</td>
      <td>2016.0</td>
      <td>Action|Adventure|Drama|Horror|Sci-Fi</td>
      <td>Japanese</td>
      <td>Japan</td>
      <td>NaN</td>
      <td>120.0</td>
      <td>2.35</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>544.0</td>
      <td>106.0</td>
      <td>12.0</td>
      <td>699</td>
      <td>0</td>
      <td>0.0</td>
      <td>374</td>
      <td>13.0</td>
      <td>1.0</td>
      <td>8.2</td>
    </tr>
    <tr>
      <td>4917</td>
      <td>The Legend of Tarzan</td>
      <td>2016.0</td>
      <td>Action|Adventure|Drama|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>110.0</td>
      <td>2.35</td>
      <td>180000000.0</td>
      <td>124051759.0</td>
      <td>...</td>
      <td>11000.0</td>
      <td>10000.0</td>
      <td>103.0</td>
      <td>21175</td>
      <td>29000</td>
      <td>2.0</td>
      <td>42372</td>
      <td>239.0</td>
      <td>248.0</td>
      <td>6.6</td>
    </tr>
    <tr>
      <td>4998</td>
      <td>Saving Grace</td>
      <td>NaN</td>
      <td>Drama|Fantasy</td>
      <td>English</td>
      <td>USA</td>
      <td>TV-MA</td>
      <td>60.0</td>
      <td>1.78</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>1000.0</td>
      <td>904.0</td>
      <td>5203</td>
      <td>634</td>
      <td>1.0</td>
      <td>3852</td>
      <td>47.0</td>
      <td>9.0</td>
      <td>7.5</td>
    </tr>
  </tbody>
</table>
<p>45 rows × 25 columns</p>
</div>



### Now that you have the duplicate values, from my experience, i will say don't just take it as it is presented. You can dig a little deeper. This way, you'll be double sure of what to delete and what to retain.

### So, why not write a little code and display the duplicate values. That way, you can visualize and make informed decisions


```python
create = []
for num in dup_values.index:
    create.append(num-1)
    create.append(num)
    create.append(num+1)
create
```




    [130,
     131,
     132,
     166,
     167,
     168,
     236,
     237,
     238,
     295,
     296,
     297,
     320,
     321,
     322,
     380,
     381,
     382,
     497,
     498,
     499,
     578,
     579,
     580,
     850,
     851,
     852,
     1010,
     1011,
     1012,
     1138,
     1139,
     1140,
     1448,
     1449,
     1450,
     1462,
     1463,
     1464,
     1560,
     1561,
     1562,
     1617,
     1618,
     1619,
     1659,
     1660,
     1661,
     1720,
     1721,
     1722,
     1743,
     1744,
     1745,
     1777,
     1778,
     1779,
     1848,
     1849,
     1850,
     2117,
     2118,
     2119,
     2231,
     2232,
     2233,
     2281,
     2282,
     2283,
     2706,
     2707,
     2708,
     2756,
     2757,
     2758,
     2790,
     2791,
     2792,
     3191,
     3192,
     3193,
     3271,
     3272,
     3273,
     3554,
     3555,
     3556,
     4048,
     4049,
     4050,
     4081,
     4082,
     4083,
     4087,
     4088,
     4089,
     4334,
     4335,
     4336,
     4442,
     4443,
     4444,
     4466,
     4467,
     4468,
     4537,
     4538,
     4539,
     4587,
     4588,
     4589,
     4668,
     4669,
     4670,
     4673,
     4674,
     4675,
     4720,
     4721,
     4722,
     4818,
     4819,
     4820,
     4837,
     4838,
     4839,
     4862,
     4863,
     4864,
     4916,
     4917,
     4918,
     4997,
     4998,
     4999]




```python
dup_show = dataset.iloc[create]
display(dup_show[ :45 ])
display(dup_show[45:91])
display(dup_show[91: ])
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Year</th>
      <th>Genres</th>
      <th>Language</th>
      <th>Country</th>
      <th>Content Rating</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>...</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>130</td>
      <td>Night of the Living Dead</td>
      <td>1968.0</td>
      <td>Drama|Horror|Mystery</td>
      <td>English</td>
      <td>USA</td>
      <td>Unrated</td>
      <td>96.0</td>
      <td>1.85</td>
      <td>114000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>125.0</td>
      <td>108.0</td>
      <td>56.0</td>
      <td>403</td>
      <td>0</td>
      <td>5.0</td>
      <td>87978</td>
      <td>580.0</td>
      <td>284.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <td>131</td>
      <td>Night of the Living Dead</td>
      <td>1968.0</td>
      <td>Drama|Horror|Mystery</td>
      <td>English</td>
      <td>USA</td>
      <td>Unrated</td>
      <td>96.0</td>
      <td>1.85</td>
      <td>114000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>125.0</td>
      <td>108.0</td>
      <td>56.0</td>
      <td>403</td>
      <td>0</td>
      <td>5.0</td>
      <td>87978</td>
      <td>580.0</td>
      <td>284.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <td>132</td>
      <td>Oliver!</td>
      <td>1968.0</td>
      <td>Drama|Family|Musical</td>
      <td>English</td>
      <td>UK</td>
      <td>G</td>
      <td>153.0</td>
      <td>2.35</td>
      <td>10000000.0</td>
      <td>16800000.0</td>
      <td>...</td>
      <td>695.0</td>
      <td>275.0</td>
      <td>139.0</td>
      <td>1593</td>
      <td>0</td>
      <td>1.0</td>
      <td>25303</td>
      <td>138.0</td>
      <td>56.0</td>
      <td>7.5</td>
    </tr>
    <tr>
      <td>166</td>
      <td>The French Connection</td>
      <td>1971.0</td>
      <td>Action|Crime|Drama|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>104.0</td>
      <td>1.85</td>
      <td>1800000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>813.0</td>
      <td>165.0</td>
      <td>109.0</td>
      <td>1196</td>
      <td>0</td>
      <td>0.0</td>
      <td>82476</td>
      <td>280.0</td>
      <td>138.0</td>
      <td>7.8</td>
    </tr>
    <tr>
      <td>167</td>
      <td>The French Connection</td>
      <td>1971.0</td>
      <td>Action|Crime|Drama|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>104.0</td>
      <td>1.85</td>
      <td>1800000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>813.0</td>
      <td>165.0</td>
      <td>109.0</td>
      <td>1196</td>
      <td>0</td>
      <td>0.0</td>
      <td>82476</td>
      <td>280.0</td>
      <td>138.0</td>
      <td>7.8</td>
    </tr>
    <tr>
      <td>168</td>
      <td>The Night Visitor</td>
      <td>1971.0</td>
      <td>Crime|Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>GP</td>
      <td>106.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>440.0</td>
      <td>98.0</td>
      <td>13.0</td>
      <td>564</td>
      <td>65</td>
      <td>1.0</td>
      <td>544</td>
      <td>19.0</td>
      <td>14.0</td>
      <td>6.8</td>
    </tr>
    <tr>
      <td>236</td>
      <td>Halloween</td>
      <td>1978.0</td>
      <td>Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>101.0</td>
      <td>2.35</td>
      <td>300000.0</td>
      <td>47000000.0</td>
      <td>...</td>
      <td>2000.0</td>
      <td>742.0</td>
      <td>598.0</td>
      <td>4400</td>
      <td>12000</td>
      <td>0.0</td>
      <td>157857</td>
      <td>1191.0</td>
      <td>318.0</td>
      <td>7.9</td>
    </tr>
    <tr>
      <td>237</td>
      <td>Halloween</td>
      <td>1978.0</td>
      <td>Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>101.0</td>
      <td>2.35</td>
      <td>300000.0</td>
      <td>47000000.0</td>
      <td>...</td>
      <td>2000.0</td>
      <td>742.0</td>
      <td>598.0</td>
      <td>4400</td>
      <td>12000</td>
      <td>0.0</td>
      <td>157857</td>
      <td>1191.0</td>
      <td>318.0</td>
      <td>7.9</td>
    </tr>
    <tr>
      <td>238</td>
      <td>Halloween</td>
      <td>1978.0</td>
      <td>Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>101.0</td>
      <td>2.35</td>
      <td>300000.0</td>
      <td>47000000.0</td>
      <td>...</td>
      <td>2000.0</td>
      <td>742.0</td>
      <td>598.0</td>
      <td>4400</td>
      <td>12000</td>
      <td>0.0</td>
      <td>157863</td>
      <td>1191.0</td>
      <td>318.0</td>
      <td>7.9</td>
    </tr>
    <tr>
      <td>295</td>
      <td>History of the World: Part I</td>
      <td>1981.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>92.0</td>
      <td>2.35</td>
      <td>11000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>898.0</td>
      <td>842.0</td>
      <td>3931</td>
      <td>0</td>
      <td>0.0</td>
      <td>36559</td>
      <td>131.0</td>
      <td>48.0</td>
      <td>6.9</td>
    </tr>
    <tr>
      <td>296</td>
      <td>History of the World: Part I</td>
      <td>1981.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>92.0</td>
      <td>2.35</td>
      <td>11000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>898.0</td>
      <td>842.0</td>
      <td>3931</td>
      <td>0</td>
      <td>0.0</td>
      <td>36559</td>
      <td>131.0</td>
      <td>48.0</td>
      <td>6.9</td>
    </tr>
    <tr>
      <td>297</td>
      <td>Inchon</td>
      <td>1981.0</td>
      <td>Drama|History|War</td>
      <td>English</td>
      <td>South Korea</td>
      <td>PG</td>
      <td>140.0</td>
      <td>2.35</td>
      <td>48000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>623.0</td>
      <td>522.0</td>
      <td>2704</td>
      <td>115</td>
      <td>1.0</td>
      <td>491</td>
      <td>16.0</td>
      <td>10.0</td>
      <td>2.7</td>
    </tr>
    <tr>
      <td>320</td>
      <td>Cat People</td>
      <td>1982.0</td>
      <td>Fantasy|Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>93.0</td>
      <td>1.85</td>
      <td>18000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>783.0</td>
      <td>782.0</td>
      <td>697.0</td>
      <td>3700</td>
      <td>0</td>
      <td>1.0</td>
      <td>14193</td>
      <td>106.0</td>
      <td>130.0</td>
      <td>6.1</td>
    </tr>
    <tr>
      <td>321</td>
      <td>Cat People</td>
      <td>1982.0</td>
      <td>Fantasy|Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>93.0</td>
      <td>1.85</td>
      <td>18000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>783.0</td>
      <td>782.0</td>
      <td>697.0</td>
      <td>3700</td>
      <td>0</td>
      <td>1.0</td>
      <td>14193</td>
      <td>106.0</td>
      <td>130.0</td>
      <td>6.1</td>
    </tr>
    <tr>
      <td>322</td>
      <td>Class of 1984</td>
      <td>1982.0</td>
      <td>Action|Crime|Drama|Thriller</td>
      <td>English</td>
      <td>Canada</td>
      <td>R</td>
      <td>98.0</td>
      <td>1.85</td>
      <td>4300000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>595.0</td>
      <td>251.0</td>
      <td>129.0</td>
      <td>1105</td>
      <td>934</td>
      <td>4.0</td>
      <td>6549</td>
      <td>75.0</td>
      <td>101.0</td>
      <td>6.6</td>
    </tr>
    <tr>
      <td>380</td>
      <td>Footloose</td>
      <td>1984.0</td>
      <td>Drama|Music|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>107.0</td>
      <td>1.85</td>
      <td>8200000.0</td>
      <td>80000000.0</td>
      <td>...</td>
      <td>967.0</td>
      <td>455.0</td>
      <td>304.0</td>
      <td>1962</td>
      <td>0</td>
      <td>0.0</td>
      <td>51459</td>
      <td>113.0</td>
      <td>60.0</td>
      <td>6.5</td>
    </tr>
    <tr>
      <td>381</td>
      <td>Footloose</td>
      <td>1984.0</td>
      <td>Drama|Music|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>107.0</td>
      <td>1.85</td>
      <td>8200000.0</td>
      <td>80000000.0</td>
      <td>...</td>
      <td>967.0</td>
      <td>455.0</td>
      <td>304.0</td>
      <td>1962</td>
      <td>0</td>
      <td>0.0</td>
      <td>51459</td>
      <td>113.0</td>
      <td>60.0</td>
      <td>6.5</td>
    </tr>
    <tr>
      <td>382</td>
      <td>Friday the 13th: The Final Chapter</td>
      <td>1984.0</td>
      <td>Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>97.0</td>
      <td>1.85</td>
      <td>1800000.0</td>
      <td>32600000.0</td>
      <td>...</td>
      <td>158.0</td>
      <td>84.0</td>
      <td>74.0</td>
      <td>467</td>
      <td>0</td>
      <td>0.0</td>
      <td>29488</td>
      <td>326.0</td>
      <td>166.0</td>
      <td>5.9</td>
    </tr>
    <tr>
      <td>497</td>
      <td>Dangerous Liaisons</td>
      <td>1988.0</td>
      <td>Drama|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>119.0</td>
      <td>1.85</td>
      <td>14000000.0</td>
      <td>34700000.0</td>
      <td>...</td>
      <td>18000.0</td>
      <td>17000.0</td>
      <td>418.0</td>
      <td>35501</td>
      <td>0</td>
      <td>2.0</td>
      <td>52846</td>
      <td>143.0</td>
      <td>51.0</td>
      <td>7.7</td>
    </tr>
    <tr>
      <td>498</td>
      <td>Dangerous Liaisons</td>
      <td>1988.0</td>
      <td>Drama|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>119.0</td>
      <td>1.85</td>
      <td>14000000.0</td>
      <td>34700000.0</td>
      <td>...</td>
      <td>18000.0</td>
      <td>17000.0</td>
      <td>418.0</td>
      <td>35501</td>
      <td>0</td>
      <td>2.0</td>
      <td>52846</td>
      <td>143.0</td>
      <td>51.0</td>
      <td>7.7</td>
    </tr>
    <tr>
      <td>499</td>
      <td>Die Hard</td>
      <td>1988.0</td>
      <td>Action|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>131.0</td>
      <td>2.35</td>
      <td>28000000.0</td>
      <td>81350242.0</td>
      <td>...</td>
      <td>25000.0</td>
      <td>13000.0</td>
      <td>541.0</td>
      <td>40585</td>
      <td>25000</td>
      <td>0.0</td>
      <td>592582</td>
      <td>722.0</td>
      <td>233.0</td>
      <td>8.2</td>
    </tr>
    <tr>
      <td>578</td>
      <td>Total Recall</td>
      <td>1990.0</td>
      <td>Action|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>113.0</td>
      <td>1.85</td>
      <td>65000000.0</td>
      <td>119412921.0</td>
      <td>...</td>
      <td>605.0</td>
      <td>308.0</td>
      <td>217.0</td>
      <td>1441</td>
      <td>0</td>
      <td>0.0</td>
      <td>240241</td>
      <td>391.0</td>
      <td>196.0</td>
      <td>7.5</td>
    </tr>
    <tr>
      <td>579</td>
      <td>Total Recall</td>
      <td>1990.0</td>
      <td>Action|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>113.0</td>
      <td>1.85</td>
      <td>65000000.0</td>
      <td>119412921.0</td>
      <td>...</td>
      <td>605.0</td>
      <td>308.0</td>
      <td>217.0</td>
      <td>1441</td>
      <td>0</td>
      <td>0.0</td>
      <td>240241</td>
      <td>391.0</td>
      <td>196.0</td>
      <td>7.5</td>
    </tr>
    <tr>
      <td>580</td>
      <td>Tremors</td>
      <td>1990.0</td>
      <td>Comedy|Horror|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>96.0</td>
      <td>1.85</td>
      <td>11000000.0</td>
      <td>16667084.0</td>
      <td>...</td>
      <td>651.0</td>
      <td>610.0</td>
      <td>536.0</td>
      <td>3119</td>
      <td>11000</td>
      <td>0.0</td>
      <td>90070</td>
      <td>248.0</td>
      <td>132.0</td>
      <td>7.1</td>
    </tr>
    <tr>
      <td>850</td>
      <td>Hamlet</td>
      <td>1996.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>UK</td>
      <td>PG-13</td>
      <td>150.0</td>
      <td>2.20</td>
      <td>18000000.0</td>
      <td>4414535.0</td>
      <td>...</td>
      <td>597.0</td>
      <td>591.0</td>
      <td>401.0</td>
      <td>1645</td>
      <td>0</td>
      <td>0.0</td>
      <td>30618</td>
      <td>224.0</td>
      <td>85.0</td>
      <td>7.8</td>
    </tr>
    <tr>
      <td>851</td>
      <td>Hamlet</td>
      <td>1996.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>UK</td>
      <td>PG-13</td>
      <td>150.0</td>
      <td>2.20</td>
      <td>18000000.0</td>
      <td>4414535.0</td>
      <td>...</td>
      <td>597.0</td>
      <td>591.0</td>
      <td>401.0</td>
      <td>1645</td>
      <td>0</td>
      <td>0.0</td>
      <td>30618</td>
      <td>224.0</td>
      <td>85.0</td>
      <td>7.8</td>
    </tr>
    <tr>
      <td>852</td>
      <td>Happy Gilmore</td>
      <td>1996.0</td>
      <td>Comedy|Sport</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>92.0</td>
      <td>1.85</td>
      <td>12000000.0</td>
      <td>38624000.0</td>
      <td>...</td>
      <td>11000.0</td>
      <td>503.0</td>
      <td>491.0</td>
      <td>13162</td>
      <td>0</td>
      <td>1.0</td>
      <td>156143</td>
      <td>289.0</td>
      <td>77.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <td>1010</td>
      <td>The Full Monty</td>
      <td>1997.0</td>
      <td>Comedy|Drama|Music</td>
      <td>English</td>
      <td>UK</td>
      <td>R</td>
      <td>91.0</td>
      <td>1.85</td>
      <td>3500000.0</td>
      <td>45857453.0</td>
      <td>...</td>
      <td>1000.0</td>
      <td>891.0</td>
      <td>121.0</td>
      <td>2323</td>
      <td>0</td>
      <td>3.0</td>
      <td>82232</td>
      <td>174.0</td>
      <td>122.0</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>1011</td>
      <td>The Full Monty</td>
      <td>1997.0</td>
      <td>Comedy|Drama|Music</td>
      <td>English</td>
      <td>UK</td>
      <td>R</td>
      <td>91.0</td>
      <td>1.85</td>
      <td>3500000.0</td>
      <td>45857453.0</td>
      <td>...</td>
      <td>1000.0</td>
      <td>891.0</td>
      <td>121.0</td>
      <td>2323</td>
      <td>0</td>
      <td>3.0</td>
      <td>82232</td>
      <td>174.0</td>
      <td>122.0</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>1012</td>
      <td>The Game</td>
      <td>1997.0</td>
      <td>Drama|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>129.0</td>
      <td>2.35</td>
      <td>50000000.0</td>
      <td>48265581.0</td>
      <td>...</td>
      <td>495.0</td>
      <td>294.0</td>
      <td>283.0</td>
      <td>1397</td>
      <td>25000</td>
      <td>1.0</td>
      <td>261069</td>
      <td>506.0</td>
      <td>157.0</td>
      <td>7.8</td>
    </tr>
    <tr>
      <td>1138</td>
      <td>The Love Letter</td>
      <td>1998.0</td>
      <td>Fantasy|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>Unrated</td>
      <td>99.0</td>
      <td>1.33</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>393.0</td>
      <td>224.0</td>
      <td>2166</td>
      <td>515</td>
      <td>1.0</td>
      <td>1465</td>
      <td>56.0</td>
      <td>NaN</td>
      <td>7.4</td>
    </tr>
    <tr>
      <td>1139</td>
      <td>The Love Letter</td>
      <td>1998.0</td>
      <td>Fantasy|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>Unrated</td>
      <td>99.0</td>
      <td>1.33</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>393.0</td>
      <td>224.0</td>
      <td>2166</td>
      <td>515</td>
      <td>1.0</td>
      <td>1465</td>
      <td>56.0</td>
      <td>NaN</td>
      <td>7.4</td>
    </tr>
    <tr>
      <td>1140</td>
      <td>The Magic Sword: Quest for Camelot</td>
      <td>1998.0</td>
      <td>Adventure|Animation|Comedy|Drama|Family|Fantas...</td>
      <td>English</td>
      <td>USA</td>
      <td>G</td>
      <td>86.0</td>
      <td>1.85</td>
      <td>40000000.0</td>
      <td>22717758.0</td>
      <td>...</td>
      <td>10000.0</td>
      <td>908.0</td>
      <td>795.0</td>
      <td>14275</td>
      <td>0</td>
      <td>0.0</td>
      <td>11156</td>
      <td>67.0</td>
      <td>34.0</td>
      <td>6.2</td>
    </tr>
    <tr>
      <td>1448</td>
      <td>Snatch</td>
      <td>2000.0</td>
      <td>Comedy|Crime</td>
      <td>English</td>
      <td>UK</td>
      <td>R</td>
      <td>104.0</td>
      <td>1.85</td>
      <td>6000000.0</td>
      <td>30093107.0</td>
      <td>...</td>
      <td>26000.0</td>
      <td>11000.0</td>
      <td>1000.0</td>
      <td>39175</td>
      <td>27000</td>
      <td>6.0</td>
      <td>600996</td>
      <td>726.0</td>
      <td>151.0</td>
      <td>8.3</td>
    </tr>
    <tr>
      <td>1449</td>
      <td>Snatch</td>
      <td>2000.0</td>
      <td>Comedy|Crime</td>
      <td>English</td>
      <td>UK</td>
      <td>R</td>
      <td>104.0</td>
      <td>1.85</td>
      <td>6000000.0</td>
      <td>30093107.0</td>
      <td>...</td>
      <td>26000.0</td>
      <td>11000.0</td>
      <td>1000.0</td>
      <td>39175</td>
      <td>27000</td>
      <td>6.0</td>
      <td>600996</td>
      <td>726.0</td>
      <td>151.0</td>
      <td>8.3</td>
    </tr>
    <tr>
      <td>1450</td>
      <td>Snow Day</td>
      <td>2000.0</td>
      <td>Adventure|Comedy|Family</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>89.0</td>
      <td>1.85</td>
      <td>13000000.0</td>
      <td>60008303.0</td>
      <td>...</td>
      <td>571.0</td>
      <td>442.0</td>
      <td>329.0</td>
      <td>2241</td>
      <td>0</td>
      <td>1.0</td>
      <td>9285</td>
      <td>91.0</td>
      <td>42.0</td>
      <td>4.9</td>
    </tr>
    <tr>
      <td>1462</td>
      <td>The Claim</td>
      <td>2000.0</td>
      <td>Drama|Romance|Western</td>
      <td>English</td>
      <td>UK</td>
      <td>R</td>
      <td>115.0</td>
      <td>2.35</td>
      <td>20000000.0</td>
      <td>403932.0</td>
      <td>...</td>
      <td>14000.0</td>
      <td>900.0</td>
      <td>887.0</td>
      <td>17104</td>
      <td>141</td>
      <td>4.0</td>
      <td>5254</td>
      <td>92.0</td>
      <td>71.0</td>
      <td>6.5</td>
    </tr>
    <tr>
      <td>1463</td>
      <td>The Claim</td>
      <td>2000.0</td>
      <td>Drama|Romance|Western</td>
      <td>English</td>
      <td>UK</td>
      <td>R</td>
      <td>115.0</td>
      <td>2.35</td>
      <td>20000000.0</td>
      <td>403932.0</td>
      <td>...</td>
      <td>14000.0</td>
      <td>900.0</td>
      <td>887.0</td>
      <td>17104</td>
      <td>141</td>
      <td>4.0</td>
      <td>5254</td>
      <td>92.0</td>
      <td>71.0</td>
      <td>6.5</td>
    </tr>
    <tr>
      <td>1464</td>
      <td>The Contender</td>
      <td>2000.0</td>
      <td>Drama|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>126.0</td>
      <td>1.85</td>
      <td>20000000.0</td>
      <td>17804273.0</td>
      <td>...</td>
      <td>12000.0</td>
      <td>10000.0</td>
      <td>883.0</td>
      <td>25660</td>
      <td>1000</td>
      <td>0.0</td>
      <td>20449</td>
      <td>370.0</td>
      <td>136.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <td>1560</td>
      <td>From Hell</td>
      <td>2001.0</td>
      <td>Horror|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>122.0</td>
      <td>2.35</td>
      <td>35000000.0</td>
      <td>31598308.0</td>
      <td>...</td>
      <td>40000.0</td>
      <td>1000.0</td>
      <td>140.0</td>
      <td>41636</td>
      <td>0</td>
      <td>1.0</td>
      <td>124765</td>
      <td>541.0</td>
      <td>208.0</td>
      <td>6.8</td>
    </tr>
    <tr>
      <td>1561</td>
      <td>From Hell</td>
      <td>2001.0</td>
      <td>Horror|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>122.0</td>
      <td>2.35</td>
      <td>35000000.0</td>
      <td>31598308.0</td>
      <td>...</td>
      <td>40000.0</td>
      <td>1000.0</td>
      <td>140.0</td>
      <td>41636</td>
      <td>0</td>
      <td>1.0</td>
      <td>124765</td>
      <td>541.0</td>
      <td>208.0</td>
      <td>6.8</td>
    </tr>
    <tr>
      <td>1562</td>
      <td>Get Over It</td>
      <td>2001.0</td>
      <td>Comedy|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>87.0</td>
      <td>2.35</td>
      <td>22000000.0</td>
      <td>11560259.0</td>
      <td>...</td>
      <td>15000.0</td>
      <td>4000.0</td>
      <td>869.0</td>
      <td>22485</td>
      <td>0</td>
      <td>1.0</td>
      <td>15617</td>
      <td>180.0</td>
      <td>63.0</td>
      <td>5.8</td>
    </tr>
    <tr>
      <td>1617</td>
      <td>O</td>
      <td>2001.0</td>
      <td>Drama|Romance|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>95.0</td>
      <td>1.85</td>
      <td>5000000.0</td>
      <td>16017403.0</td>
      <td>...</td>
      <td>1000.0</td>
      <td>835.0</td>
      <td>697.0</td>
      <td>3300</td>
      <td>0</td>
      <td>2.0</td>
      <td>17333</td>
      <td>153.0</td>
      <td>92.0</td>
      <td>6.2</td>
    </tr>
    <tr>
      <td>1618</td>
      <td>O</td>
      <td>2001.0</td>
      <td>Drama|Romance|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>95.0</td>
      <td>1.85</td>
      <td>5000000.0</td>
      <td>16017403.0</td>
      <td>...</td>
      <td>1000.0</td>
      <td>835.0</td>
      <td>697.0</td>
      <td>3300</td>
      <td>0</td>
      <td>2.0</td>
      <td>17333</td>
      <td>153.0</td>
      <td>92.0</td>
      <td>6.2</td>
    </tr>
    <tr>
      <td>1619</td>
      <td>Ocean's Eleven</td>
      <td>2001.0</td>
      <td>Crime|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>116.0</td>
      <td>2.35</td>
      <td>85000000.0</td>
      <td>183405771.0</td>
      <td>...</td>
      <td>11000.0</td>
      <td>1000.0</td>
      <td>471.0</td>
      <td>13028</td>
      <td>0</td>
      <td>4.0</td>
      <td>402645</td>
      <td>845.0</td>
      <td>186.0</td>
      <td>7.8</td>
    </tr>
  </tbody>
</table>
<p>45 rows × 25 columns</p>
</div>



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Year</th>
      <th>Genres</th>
      <th>Language</th>
      <th>Country</th>
      <th>Content Rating</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>...</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1659</td>
      <td>The Fast and the Furious</td>
      <td>2001.0</td>
      <td>Action|Crime|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>106.0</td>
      <td>2.35</td>
      <td>38000000.0</td>
      <td>144512310.0</td>
      <td>...</td>
      <td>23000.0</td>
      <td>14000.0</td>
      <td>4000.0</td>
      <td>45327</td>
      <td>14000</td>
      <td>2.0</td>
      <td>272223</td>
      <td>988.0</td>
      <td>187.0</td>
      <td>6.7</td>
    </tr>
    <tr>
      <td>1660</td>
      <td>The Fast and the Furious</td>
      <td>2001.0</td>
      <td>Action|Crime|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>106.0</td>
      <td>2.35</td>
      <td>38000000.0</td>
      <td>144512310.0</td>
      <td>...</td>
      <td>23000.0</td>
      <td>14000.0</td>
      <td>4000.0</td>
      <td>45327</td>
      <td>14000</td>
      <td>2.0</td>
      <td>272223</td>
      <td>988.0</td>
      <td>187.0</td>
      <td>6.7</td>
    </tr>
    <tr>
      <td>1661</td>
      <td>The Fast and the Furious</td>
      <td>2001.0</td>
      <td>Action|Crime|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>106.0</td>
      <td>2.35</td>
      <td>38000000.0</td>
      <td>144512310.0</td>
      <td>...</td>
      <td>23000.0</td>
      <td>14000.0</td>
      <td>4000.0</td>
      <td>45327</td>
      <td>14000</td>
      <td>2.0</td>
      <td>272227</td>
      <td>988.0</td>
      <td>187.0</td>
      <td>6.7</td>
    </tr>
    <tr>
      <td>1720</td>
      <td>Big Fat Liar</td>
      <td>2002.0</td>
      <td>Adventure|Comedy|Family</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>88.0</td>
      <td>1.85</td>
      <td>15000000.0</td>
      <td>47811275.0</td>
      <td>...</td>
      <td>934.0</td>
      <td>927.0</td>
      <td>799.0</td>
      <td>3707</td>
      <td>896</td>
      <td>1.0</td>
      <td>29008</td>
      <td>99.0</td>
      <td>69.0</td>
      <td>5.4</td>
    </tr>
    <tr>
      <td>1721</td>
      <td>Big Fat Liar</td>
      <td>2002.0</td>
      <td>Adventure|Comedy|Family</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>88.0</td>
      <td>1.85</td>
      <td>15000000.0</td>
      <td>47811275.0</td>
      <td>...</td>
      <td>934.0</td>
      <td>927.0</td>
      <td>799.0</td>
      <td>3707</td>
      <td>896</td>
      <td>1.0</td>
      <td>29008</td>
      <td>99.0</td>
      <td>69.0</td>
      <td>5.4</td>
    </tr>
    <tr>
      <td>1722</td>
      <td>Big Trouble</td>
      <td>2002.0</td>
      <td>Comedy|Crime|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>74.0</td>
      <td>1.85</td>
      <td>40000000.0</td>
      <td>7262288.0</td>
      <td>...</td>
      <td>11000.0</td>
      <td>1000.0</td>
      <td>865.0</td>
      <td>13917</td>
      <td>892</td>
      <td>2.0</td>
      <td>17307</td>
      <td>186.0</td>
      <td>87.0</td>
      <td>6.5</td>
    </tr>
    <tr>
      <td>1743</td>
      <td>Crossroads</td>
      <td>2002.0</td>
      <td>Comedy|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>93.0</td>
      <td>1.85</td>
      <td>12000000.0</td>
      <td>37188667.0</td>
      <td>...</td>
      <td>1000.0</td>
      <td>188.0</td>
      <td>135.0</td>
      <td>1531</td>
      <td>0</td>
      <td>1.0</td>
      <td>34219</td>
      <td>578.0</td>
      <td>111.0</td>
      <td>3.3</td>
    </tr>
    <tr>
      <td>1744</td>
      <td>Crossroads</td>
      <td>2002.0</td>
      <td>Comedy|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>93.0</td>
      <td>1.85</td>
      <td>12000000.0</td>
      <td>37188667.0</td>
      <td>...</td>
      <td>1000.0</td>
      <td>188.0</td>
      <td>135.0</td>
      <td>1531</td>
      <td>0</td>
      <td>1.0</td>
      <td>34219</td>
      <td>578.0</td>
      <td>111.0</td>
      <td>3.3</td>
    </tr>
    <tr>
      <td>1745</td>
      <td>Cypher</td>
      <td>2002.0</td>
      <td>Mystery|Romance|Sci-Fi|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>95.0</td>
      <td>1.85</td>
      <td>7500000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>686.0</td>
      <td>327.0</td>
      <td>280.0</td>
      <td>1501</td>
      <td>0</td>
      <td>2.0</td>
      <td>27052</td>
      <td>124.0</td>
      <td>82.0</td>
      <td>6.8</td>
    </tr>
    <tr>
      <td>1777</td>
      <td>Hero</td>
      <td>2002.0</td>
      <td>Action|Adventure|History</td>
      <td>Mandarin</td>
      <td>China</td>
      <td>PG-13</td>
      <td>80.0</td>
      <td>2.35</td>
      <td>31000000.0</td>
      <td>84961.0</td>
      <td>...</td>
      <td>5000.0</td>
      <td>643.0</td>
      <td>576.0</td>
      <td>6229</td>
      <td>0</td>
      <td>4.0</td>
      <td>149414</td>
      <td>841.0</td>
      <td>283.0</td>
      <td>7.9</td>
    </tr>
    <tr>
      <td>1778</td>
      <td>Hero</td>
      <td>2002.0</td>
      <td>Action|Adventure|History</td>
      <td>Mandarin</td>
      <td>China</td>
      <td>PG-13</td>
      <td>80.0</td>
      <td>2.35</td>
      <td>31000000.0</td>
      <td>84961.0</td>
      <td>...</td>
      <td>5000.0</td>
      <td>643.0</td>
      <td>576.0</td>
      <td>6229</td>
      <td>0</td>
      <td>4.0</td>
      <td>149414</td>
      <td>841.0</td>
      <td>283.0</td>
      <td>7.9</td>
    </tr>
    <tr>
      <td>1779</td>
      <td>Hey Arnold! The Movie</td>
      <td>2002.0</td>
      <td>Adventure|Animation|Comedy|Family</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>76.0</td>
      <td>1.85</td>
      <td>3000000.0</td>
      <td>13684949.0</td>
      <td>...</td>
      <td>1000.0</td>
      <td>811.0</td>
      <td>636.0</td>
      <td>3752</td>
      <td>227</td>
      <td>0.0</td>
      <td>4564</td>
      <td>43.0</td>
      <td>33.0</td>
      <td>5.9</td>
    </tr>
    <tr>
      <td>1848</td>
      <td>Stealing Harvard</td>
      <td>2002.0</td>
      <td>Comedy|Crime</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>85.0</td>
      <td>1.85</td>
      <td>25000000.0</td>
      <td>13973532.0</td>
      <td>...</td>
      <td>985.0</td>
      <td>637.0</td>
      <td>455.0</td>
      <td>3065</td>
      <td>215</td>
      <td>1.0</td>
      <td>11211</td>
      <td>92.0</td>
      <td>52.0</td>
      <td>5.1</td>
    </tr>
    <tr>
      <td>1849</td>
      <td>Stealing Harvard</td>
      <td>2002.0</td>
      <td>Comedy|Crime</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>85.0</td>
      <td>1.85</td>
      <td>25000000.0</td>
      <td>13973532.0</td>
      <td>...</td>
      <td>985.0</td>
      <td>637.0</td>
      <td>455.0</td>
      <td>3065</td>
      <td>215</td>
      <td>1.0</td>
      <td>11211</td>
      <td>92.0</td>
      <td>52.0</td>
      <td>5.1</td>
    </tr>
    <tr>
      <td>1850</td>
      <td>Stolen Summer</td>
      <td>2002.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>91.0</td>
      <td>1.85</td>
      <td>1500000.0</td>
      <td>119841.0</td>
      <td>...</td>
      <td>954.0</td>
      <td>767.0</td>
      <td>597.0</td>
      <td>3901</td>
      <td>304</td>
      <td>1.0</td>
      <td>2419</td>
      <td>55.0</td>
      <td>31.0</td>
      <td>6.5</td>
    </tr>
    <tr>
      <td>2117</td>
      <td>Crash</td>
      <td>2004.0</td>
      <td>Crime|Drama|Thriller</td>
      <td>English</td>
      <td>Germany</td>
      <td>R</td>
      <td>115.0</td>
      <td>2.35</td>
      <td>6500000.0</td>
      <td>54557348.0</td>
      <td>...</td>
      <td>3000.0</td>
      <td>912.0</td>
      <td>911.0</td>
      <td>5732</td>
      <td>18000</td>
      <td>0.0</td>
      <td>361169</td>
      <td>1624.0</td>
      <td>287.0</td>
      <td>7.9</td>
    </tr>
    <tr>
      <td>2118</td>
      <td>Crash</td>
      <td>2004.0</td>
      <td>Crime|Drama|Thriller</td>
      <td>English</td>
      <td>Germany</td>
      <td>R</td>
      <td>115.0</td>
      <td>2.35</td>
      <td>6500000.0</td>
      <td>54557348.0</td>
      <td>...</td>
      <td>3000.0</td>
      <td>912.0</td>
      <td>911.0</td>
      <td>5732</td>
      <td>18000</td>
      <td>0.0</td>
      <td>361169</td>
      <td>1624.0</td>
      <td>287.0</td>
      <td>7.9</td>
    </tr>
    <tr>
      <td>2119</td>
      <td>D.E.B.S.</td>
      <td>2004.0</td>
      <td>Action|Comedy|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>91.0</td>
      <td>2.35</td>
      <td>3500000.0</td>
      <td>96793.0</td>
      <td>...</td>
      <td>4000.0</td>
      <td>756.0</td>
      <td>660.0</td>
      <td>6380</td>
      <td>1000</td>
      <td>3.0</td>
      <td>12188</td>
      <td>135.0</td>
      <td>50.0</td>
      <td>5.3</td>
    </tr>
    <tr>
      <td>2231</td>
      <td>The Alamo</td>
      <td>2004.0</td>
      <td>Drama|History|War|Western</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>137.0</td>
      <td>2.35</td>
      <td>107000000.0</td>
      <td>22406362.0</td>
      <td>...</td>
      <td>2000.0</td>
      <td>973.0</td>
      <td>877.0</td>
      <td>5780</td>
      <td>701</td>
      <td>0.0</td>
      <td>16832</td>
      <td>267.0</td>
      <td>106.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <td>2232</td>
      <td>The Alamo</td>
      <td>2004.0</td>
      <td>Drama|History|War|Western</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>137.0</td>
      <td>2.35</td>
      <td>107000000.0</td>
      <td>22406362.0</td>
      <td>...</td>
      <td>2000.0</td>
      <td>973.0</td>
      <td>877.0</td>
      <td>5780</td>
      <td>701</td>
      <td>0.0</td>
      <td>16832</td>
      <td>267.0</td>
      <td>106.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <td>2233</td>
      <td>The Aviator</td>
      <td>2004.0</td>
      <td>Biography|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>170.0</td>
      <td>2.35</td>
      <td>110000000.0</td>
      <td>102608827.0</td>
      <td>...</td>
      <td>29000.0</td>
      <td>3000.0</td>
      <td>827.0</td>
      <td>34582</td>
      <td>0</td>
      <td>0.0</td>
      <td>264318</td>
      <td>799.0</td>
      <td>267.0</td>
      <td>7.5</td>
    </tr>
    <tr>
      <td>2281</td>
      <td>Wicker Park</td>
      <td>2004.0</td>
      <td>Drama|Mystery|Romance|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>114.0</td>
      <td>2.35</td>
      <td>30000000.0</td>
      <td>12831121.0</td>
      <td>...</td>
      <td>489.0</td>
      <td>93.0</td>
      <td>40.0</td>
      <td>679</td>
      <td>0</td>
      <td>0.0</td>
      <td>44979</td>
      <td>298.0</td>
      <td>98.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <td>2282</td>
      <td>Wicker Park</td>
      <td>2004.0</td>
      <td>Drama|Mystery|Romance|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>114.0</td>
      <td>2.35</td>
      <td>30000000.0</td>
      <td>12831121.0</td>
      <td>...</td>
      <td>489.0</td>
      <td>93.0</td>
      <td>40.0</td>
      <td>679</td>
      <td>0</td>
      <td>0.0</td>
      <td>44979</td>
      <td>298.0</td>
      <td>98.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <td>2283</td>
      <td>Wimbledon</td>
      <td>2004.0</td>
      <td>Comedy|Romance|Sport</td>
      <td>English</td>
      <td>UK</td>
      <td>PG-13</td>
      <td>98.0</td>
      <td>2.35</td>
      <td>31000000.0</td>
      <td>16831505.0</td>
      <td>...</td>
      <td>4000.0</td>
      <td>4000.0</td>
      <td>663.0</td>
      <td>9330</td>
      <td>0</td>
      <td>1.0</td>
      <td>51842</td>
      <td>173.0</td>
      <td>129.0</td>
      <td>6.3</td>
    </tr>
    <tr>
      <td>2706</td>
      <td>The Illusionist</td>
      <td>2006.0</td>
      <td>Drama|Mystery|Romance|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>110.0</td>
      <td>1.85</td>
      <td>16000000.0</td>
      <td>39825798.0</td>
      <td>...</td>
      <td>3000.0</td>
      <td>979.0</td>
      <td>96.0</td>
      <td>4210</td>
      <td>15000</td>
      <td>3.0</td>
      <td>295375</td>
      <td>645.0</td>
      <td>236.0</td>
      <td>7.6</td>
    </tr>
    <tr>
      <td>2707</td>
      <td>The Illusionist</td>
      <td>2006.0</td>
      <td>Drama|Mystery|Romance|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>110.0</td>
      <td>1.85</td>
      <td>16000000.0</td>
      <td>39825798.0</td>
      <td>...</td>
      <td>3000.0</td>
      <td>979.0</td>
      <td>96.0</td>
      <td>4210</td>
      <td>15000</td>
      <td>3.0</td>
      <td>295375</td>
      <td>645.0</td>
      <td>236.0</td>
      <td>7.6</td>
    </tr>
    <tr>
      <td>2708</td>
      <td>The Lake House</td>
      <td>2006.0</td>
      <td>Drama|Fantasy|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>99.0</td>
      <td>2.35</td>
      <td>40000000.0</td>
      <td>52320979.0</td>
      <td>...</td>
      <td>18000.0</td>
      <td>426.0</td>
      <td>211.0</td>
      <td>18693</td>
      <td>0</td>
      <td>0.0</td>
      <td>114321</td>
      <td>548.0</td>
      <td>175.0</td>
      <td>6.8</td>
    </tr>
    <tr>
      <td>2756</td>
      <td>A Dog's Breakfast</td>
      <td>2007.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>Canada</td>
      <td>NaN</td>
      <td>88.0</td>
      <td>1.78</td>
      <td>120000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>847.0</td>
      <td>686.0</td>
      <td>405.0</td>
      <td>2364</td>
      <td>377</td>
      <td>2.0</td>
      <td>3262</td>
      <td>46.0</td>
      <td>8.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <td>2757</td>
      <td>A Dog's Breakfast</td>
      <td>2007.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>Canada</td>
      <td>NaN</td>
      <td>88.0</td>
      <td>1.78</td>
      <td>120000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>847.0</td>
      <td>686.0</td>
      <td>405.0</td>
      <td>2364</td>
      <td>377</td>
      <td>2.0</td>
      <td>3262</td>
      <td>46.0</td>
      <td>8.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <td>2758</td>
      <td>A Mighty Heart</td>
      <td>2007.0</td>
      <td>Biography|Drama|History|Thriller|War</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>108.0</td>
      <td>2.35</td>
      <td>16000000.0</td>
      <td>9172810.0</td>
      <td>...</td>
      <td>11000.0</td>
      <td>883.0</td>
      <td>254.0</td>
      <td>12178</td>
      <td>923</td>
      <td>0.0</td>
      <td>24150</td>
      <td>118.0</td>
      <td>190.0</td>
      <td>6.7</td>
    </tr>
    <tr>
      <td>2790</td>
      <td>Death at a Funeral</td>
      <td>2007.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>87.0</td>
      <td>1.85</td>
      <td>9000000.0</td>
      <td>8579684.0</td>
      <td>...</td>
      <td>22000.0</td>
      <td>557.0</td>
      <td>548.0</td>
      <td>24324</td>
      <td>0</td>
      <td>0.0</td>
      <td>89547</td>
      <td>199.0</td>
      <td>168.0</td>
      <td>7.4</td>
    </tr>
    <tr>
      <td>2791</td>
      <td>Death at a Funeral</td>
      <td>2007.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>87.0</td>
      <td>1.85</td>
      <td>9000000.0</td>
      <td>8579684.0</td>
      <td>...</td>
      <td>22000.0</td>
      <td>557.0</td>
      <td>548.0</td>
      <td>24324</td>
      <td>0</td>
      <td>0.0</td>
      <td>89547</td>
      <td>199.0</td>
      <td>168.0</td>
      <td>7.4</td>
    </tr>
    <tr>
      <td>2792</td>
      <td>Death Sentence</td>
      <td>2007.0</td>
      <td>Action|Crime|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>111.0</td>
      <td>2.35</td>
      <td>20000000.0</td>
      <td>9525276.0</td>
      <td>...</td>
      <td>856.0</td>
      <td>742.0</td>
      <td>725.0</td>
      <td>3309</td>
      <td>0</td>
      <td>0.0</td>
      <td>60156</td>
      <td>299.0</td>
      <td>166.0</td>
      <td>6.8</td>
    </tr>
    <tr>
      <td>3191</td>
      <td>A Woman, a Gun and a Noodle Shop</td>
      <td>2009.0</td>
      <td>Comedy|Drama</td>
      <td>Mandarin</td>
      <td>China</td>
      <td>R</td>
      <td>95.0</td>
      <td>2.35</td>
      <td>NaN</td>
      <td>190666.0</td>
      <td>...</td>
      <td>9.0</td>
      <td>4.0</td>
      <td>3.0</td>
      <td>18</td>
      <td>784</td>
      <td>1.0</td>
      <td>2410</td>
      <td>20.0</td>
      <td>101.0</td>
      <td>5.7</td>
    </tr>
    <tr>
      <td>3192</td>
      <td>A Woman, a Gun and a Noodle Shop</td>
      <td>2009.0</td>
      <td>Comedy|Drama</td>
      <td>Mandarin</td>
      <td>China</td>
      <td>R</td>
      <td>95.0</td>
      <td>2.35</td>
      <td>NaN</td>
      <td>190666.0</td>
      <td>...</td>
      <td>9.0</td>
      <td>4.0</td>
      <td>3.0</td>
      <td>18</td>
      <td>784</td>
      <td>1.0</td>
      <td>2410</td>
      <td>20.0</td>
      <td>101.0</td>
      <td>5.7</td>
    </tr>
    <tr>
      <td>3193</td>
      <td>Adam</td>
      <td>2009.0</td>
      <td>Drama|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>99.0</td>
      <td>2.35</td>
      <td>NaN</td>
      <td>2277396.0</td>
      <td>...</td>
      <td>828.0</td>
      <td>390.0</td>
      <td>194.0</td>
      <td>1936</td>
      <td>0</td>
      <td>0.0</td>
      <td>29239</td>
      <td>70.0</td>
      <td>122.0</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>3271</td>
      <td>Halloween II</td>
      <td>2009.0</td>
      <td>Horror</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>119.0</td>
      <td>1.85</td>
      <td>15000000.0</td>
      <td>33386128.0</td>
      <td>...</td>
      <td>908.0</td>
      <td>764.0</td>
      <td>593.0</td>
      <td>3226</td>
      <td>3000</td>
      <td>0.0</td>
      <td>36372</td>
      <td>491.0</td>
      <td>220.0</td>
      <td>4.9</td>
    </tr>
    <tr>
      <td>3272</td>
      <td>Halloween II</td>
      <td>2009.0</td>
      <td>Horror</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>119.0</td>
      <td>1.85</td>
      <td>15000000.0</td>
      <td>33386128.0</td>
      <td>...</td>
      <td>908.0</td>
      <td>764.0</td>
      <td>593.0</td>
      <td>3226</td>
      <td>3000</td>
      <td>0.0</td>
      <td>36372</td>
      <td>491.0</td>
      <td>220.0</td>
      <td>4.9</td>
    </tr>
    <tr>
      <td>3273</td>
      <td>Hannah Montana: The Movie</td>
      <td>2009.0</td>
      <td>Comedy|Drama|Family|Music|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>G</td>
      <td>102.0</td>
      <td>1.85</td>
      <td>30000000.0</td>
      <td>79566871.0</td>
      <td>...</td>
      <td>1000.0</td>
      <td>1000.0</td>
      <td>635.0</td>
      <td>4516</td>
      <td>0</td>
      <td>2.0</td>
      <td>31760</td>
      <td>140.0</td>
      <td>131.0</td>
      <td>4.2</td>
    </tr>
    <tr>
      <td>3554</td>
      <td>My Soul to Take</td>
      <td>2010.0</td>
      <td>Horror|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>107.0</td>
      <td>2.35</td>
      <td>25000000.0</td>
      <td>14637490.0</td>
      <td>...</td>
      <td>798.0</td>
      <td>374.0</td>
      <td>255.0</td>
      <td>2537</td>
      <td>0</td>
      <td>2.0</td>
      <td>16411</td>
      <td>136.0</td>
      <td>160.0</td>
      <td>4.8</td>
    </tr>
    <tr>
      <td>3555</td>
      <td>My Soul to Take</td>
      <td>2010.0</td>
      <td>Horror|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>107.0</td>
      <td>2.35</td>
      <td>25000000.0</td>
      <td>14637490.0</td>
      <td>...</td>
      <td>798.0</td>
      <td>374.0</td>
      <td>255.0</td>
      <td>2537</td>
      <td>0</td>
      <td>2.0</td>
      <td>16411</td>
      <td>136.0</td>
      <td>160.0</td>
      <td>4.8</td>
    </tr>
    <tr>
      <td>3556</td>
      <td>Nanny McPhee Returns</td>
      <td>2010.0</td>
      <td>Comedy|Family|Fantasy</td>
      <td>English</td>
      <td>UK</td>
      <td>PG</td>
      <td>109.0</td>
      <td>2.35</td>
      <td>35000000.0</td>
      <td>28995450.0</td>
      <td>...</td>
      <td>287.0</td>
      <td>175.0</td>
      <td>167.0</td>
      <td>855</td>
      <td>0</td>
      <td>5.0</td>
      <td>19230</td>
      <td>59.0</td>
      <td>97.0</td>
      <td>6.1</td>
    </tr>
    <tr>
      <td>4048</td>
      <td>The Avengers</td>
      <td>2012.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>173.0</td>
      <td>1.85</td>
      <td>220000000.0</td>
      <td>623279547.0</td>
      <td>...</td>
      <td>26000.0</td>
      <td>21000.0</td>
      <td>19000.0</td>
      <td>87697</td>
      <td>123000</td>
      <td>3.0</td>
      <td>995415</td>
      <td>1722.0</td>
      <td>703.0</td>
      <td>8.1</td>
    </tr>
    <tr>
      <td>4049</td>
      <td>The Avengers</td>
      <td>2012.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>173.0</td>
      <td>1.85</td>
      <td>220000000.0</td>
      <td>623279547.0</td>
      <td>...</td>
      <td>26000.0</td>
      <td>21000.0</td>
      <td>19000.0</td>
      <td>87697</td>
      <td>123000</td>
      <td>3.0</td>
      <td>995415</td>
      <td>1722.0</td>
      <td>703.0</td>
      <td>8.1</td>
    </tr>
    <tr>
      <td>4050</td>
      <td>The Bourne Legacy</td>
      <td>2012.0</td>
      <td>Action|Adventure|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>135.0</td>
      <td>2.35</td>
      <td>125000000.0</td>
      <td>113165635.0</td>
      <td>...</td>
      <td>10000.0</td>
      <td>826.0</td>
      <td>602.0</td>
      <td>12175</td>
      <td>31000</td>
      <td>0.0</td>
      <td>229823</td>
      <td>504.0</td>
      <td>436.0</td>
      <td>6.7</td>
    </tr>
    <tr>
      <td>4081</td>
      <td>The Possession</td>
      <td>2012.0</td>
      <td>Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>92.0</td>
      <td>2.35</td>
      <td>14000000.0</td>
      <td>49122319.0</td>
      <td>...</td>
      <td>941.0</td>
      <td>459.0</td>
      <td>309.0</td>
      <td>2348</td>
      <td>17000</td>
      <td>0.0</td>
      <td>47169</td>
      <td>162.0</td>
      <td>264.0</td>
      <td>5.9</td>
    </tr>
  </tbody>
</table>
<p>46 rows × 25 columns</p>
</div>



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Year</th>
      <th>Genres</th>
      <th>Language</th>
      <th>Country</th>
      <th>Content Rating</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>...</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>4082</td>
      <td>The Possession</td>
      <td>2012.0</td>
      <td>Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>92.0</td>
      <td>2.35</td>
      <td>14000000.0</td>
      <td>49122319.0</td>
      <td>...</td>
      <td>941.0</td>
      <td>459.0</td>
      <td>309.0</td>
      <td>2348</td>
      <td>17000</td>
      <td>0.0</td>
      <td>47169</td>
      <td>162.0</td>
      <td>264.0</td>
      <td>5.9</td>
    </tr>
    <tr>
      <td>4083</td>
      <td>The Raven</td>
      <td>2012.0</td>
      <td>Crime|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>110.0</td>
      <td>2.35</td>
      <td>26000000.0</td>
      <td>16005978.0</td>
      <td>...</td>
      <td>771.0</td>
      <td>570.0</td>
      <td>427.0</td>
      <td>2356</td>
      <td>35000</td>
      <td>1.0</td>
      <td>72886</td>
      <td>190.0</td>
      <td>265.0</td>
      <td>6.4</td>
    </tr>
    <tr>
      <td>4087</td>
      <td>The Twilight Saga: Breaking Dawn - Part 2</td>
      <td>2012.0</td>
      <td>Adventure|Drama|Fantasy|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>115.0</td>
      <td>2.35</td>
      <td>120000000.0</td>
      <td>292298923.0</td>
      <td>...</td>
      <td>21000.0</td>
      <td>17000.0</td>
      <td>12000.0</td>
      <td>59177</td>
      <td>65000</td>
      <td>3.0</td>
      <td>185394</td>
      <td>329.0</td>
      <td>322.0</td>
      <td>5.5</td>
    </tr>
    <tr>
      <td>4088</td>
      <td>The Twilight Saga: Breaking Dawn - Part 2</td>
      <td>2012.0</td>
      <td>Adventure|Drama|Fantasy|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>115.0</td>
      <td>2.35</td>
      <td>120000000.0</td>
      <td>292298923.0</td>
      <td>...</td>
      <td>21000.0</td>
      <td>17000.0</td>
      <td>12000.0</td>
      <td>59177</td>
      <td>65000</td>
      <td>3.0</td>
      <td>185394</td>
      <td>329.0</td>
      <td>322.0</td>
      <td>5.5</td>
    </tr>
    <tr>
      <td>4089</td>
      <td>The Vow</td>
      <td>2012.0</td>
      <td>Drama|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>104.0</td>
      <td>2.35</td>
      <td>30000000.0</td>
      <td>125014030.0</td>
      <td>...</td>
      <td>17000.0</td>
      <td>359.0</td>
      <td>281.0</td>
      <td>18322</td>
      <td>32000</td>
      <td>0.0</td>
      <td>145852</td>
      <td>164.0</td>
      <td>214.0</td>
      <td>6.8</td>
    </tr>
    <tr>
      <td>4334</td>
      <td>Trance</td>
      <td>2013.0</td>
      <td>Crime|Drama|Mystery|Thriller</td>
      <td>English</td>
      <td>UK</td>
      <td>R</td>
      <td>101.0</td>
      <td>2.35</td>
      <td>20000000.0</td>
      <td>2319187.0</td>
      <td>...</td>
      <td>3000.0</td>
      <td>1000.0</td>
      <td>888.0</td>
      <td>5056</td>
      <td>23000</td>
      <td>0.0</td>
      <td>92640</td>
      <td>212.0</td>
      <td>393.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <td>4335</td>
      <td>Trance</td>
      <td>2013.0</td>
      <td>Crime|Drama|Mystery|Thriller</td>
      <td>English</td>
      <td>UK</td>
      <td>R</td>
      <td>101.0</td>
      <td>2.35</td>
      <td>20000000.0</td>
      <td>2319187.0</td>
      <td>...</td>
      <td>3000.0</td>
      <td>1000.0</td>
      <td>888.0</td>
      <td>5056</td>
      <td>23000</td>
      <td>0.0</td>
      <td>92640</td>
      <td>212.0</td>
      <td>393.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <td>4336</td>
      <td>Treachery</td>
      <td>2013.0</td>
      <td>Drama|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>67.0</td>
      <td>NaN</td>
      <td>625000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>260000.0</td>
      <td>21000.0</td>
      <td>2000.0</td>
      <td>283939</td>
      <td>0</td>
      <td>5.0</td>
      <td>344</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>3.9</td>
    </tr>
    <tr>
      <td>4442</td>
      <td>Hercules</td>
      <td>2014.0</td>
      <td>Action|Adventure</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>101.0</td>
      <td>2.35</td>
      <td>100000000.0</td>
      <td>72660029.0</td>
      <td>...</td>
      <td>12000.0</td>
      <td>3000.0</td>
      <td>467.0</td>
      <td>16235</td>
      <td>21000</td>
      <td>0.0</td>
      <td>115687</td>
      <td>269.0</td>
      <td>245.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <td>4443</td>
      <td>Hercules</td>
      <td>2014.0</td>
      <td>Action|Adventure</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>101.0</td>
      <td>2.35</td>
      <td>100000000.0</td>
      <td>72660029.0</td>
      <td>...</td>
      <td>12000.0</td>
      <td>3000.0</td>
      <td>467.0</td>
      <td>16235</td>
      <td>21000</td>
      <td>0.0</td>
      <td>115687</td>
      <td>269.0</td>
      <td>245.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <td>4444</td>
      <td>Hidden Away</td>
      <td>2014.0</td>
      <td>Drama|Romance</td>
      <td>Spanish</td>
      <td>Spain</td>
      <td>Unrated</td>
      <td>96.0</td>
      <td>2.35</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>90.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>90</td>
      <td>68</td>
      <td>0.0</td>
      <td>955</td>
      <td>7.0</td>
      <td>9.0</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>4466</td>
      <td>Left Behind</td>
      <td>2014.0</td>
      <td>Action|Drama|Fantasy|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>110.0</td>
      <td>2.35</td>
      <td>16000000.0</td>
      <td>13998282.0</td>
      <td>...</td>
      <td>12000.0</td>
      <td>1000.0</td>
      <td>734.0</td>
      <td>15044</td>
      <td>31000</td>
      <td>1.0</td>
      <td>24854</td>
      <td>374.0</td>
      <td>169.0</td>
      <td>3.1</td>
    </tr>
    <tr>
      <td>4467</td>
      <td>Left Behind</td>
      <td>2014.0</td>
      <td>Action|Drama|Fantasy|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>110.0</td>
      <td>2.35</td>
      <td>16000000.0</td>
      <td>13998282.0</td>
      <td>...</td>
      <td>12000.0</td>
      <td>1000.0</td>
      <td>734.0</td>
      <td>15044</td>
      <td>31000</td>
      <td>1.0</td>
      <td>24854</td>
      <td>374.0</td>
      <td>169.0</td>
      <td>3.1</td>
    </tr>
    <tr>
      <td>4468</td>
      <td>Let's Be Cops</td>
      <td>2014.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>104.0</td>
      <td>1.85</td>
      <td>17000000.0</td>
      <td>82389560.0</td>
      <td>...</td>
      <td>839.0</td>
      <td>756.0</td>
      <td>613.0</td>
      <td>3627</td>
      <td>14000</td>
      <td>1.0</td>
      <td>106820</td>
      <td>147.0</td>
      <td>129.0</td>
      <td>6.5</td>
    </tr>
    <tr>
      <td>4537</td>
      <td>The Calling</td>
      <td>2014.0</td>
      <td>Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>108.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>2000.0</td>
      <td>1000.0</td>
      <td>826.0</td>
      <td>4385</td>
      <td>0</td>
      <td>2.0</td>
      <td>6025</td>
      <td>28.0</td>
      <td>48.0</td>
      <td>5.8</td>
    </tr>
    <tr>
      <td>4538</td>
      <td>The Calling</td>
      <td>2014.0</td>
      <td>Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>108.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>2000.0</td>
      <td>1000.0</td>
      <td>826.0</td>
      <td>4385</td>
      <td>0</td>
      <td>2.0</td>
      <td>6025</td>
      <td>28.0</td>
      <td>48.0</td>
      <td>5.8</td>
    </tr>
    <tr>
      <td>4539</td>
      <td>The Equalizer</td>
      <td>2014.0</td>
      <td>Action|Crime|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>132.0</td>
      <td>2.35</td>
      <td>55000000.0</td>
      <td>101530738.0</td>
      <td>...</td>
      <td>18000.0</td>
      <td>17000.0</td>
      <td>683.0</td>
      <td>37605</td>
      <td>56000</td>
      <td>0.0</td>
      <td>229574</td>
      <td>436.0</td>
      <td>292.0</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>4587</td>
      <td>Unbroken</td>
      <td>2014.0</td>
      <td>Biography|Drama|Sport|War</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>137.0</td>
      <td>2.35</td>
      <td>65000000.0</td>
      <td>115603980.0</td>
      <td>...</td>
      <td>769.0</td>
      <td>698.0</td>
      <td>465.0</td>
      <td>2938</td>
      <td>35000</td>
      <td>0.0</td>
      <td>103589</td>
      <td>351.0</td>
      <td>322.0</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>4588</td>
      <td>Unbroken</td>
      <td>2014.0</td>
      <td>Biography|Drama|Sport|War</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>137.0</td>
      <td>2.35</td>
      <td>65000000.0</td>
      <td>115603980.0</td>
      <td>...</td>
      <td>769.0</td>
      <td>698.0</td>
      <td>465.0</td>
      <td>2938</td>
      <td>35000</td>
      <td>0.0</td>
      <td>103589</td>
      <td>351.0</td>
      <td>322.0</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>4589</td>
      <td>Unfriended</td>
      <td>2014.0</td>
      <td>Horror|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>83.0</td>
      <td>1.85</td>
      <td>1000000.0</td>
      <td>31537320.0</td>
      <td>...</td>
      <td>707.0</td>
      <td>305.0</td>
      <td>142.0</td>
      <td>1565</td>
      <td>13000</td>
      <td>0.0</td>
      <td>44329</td>
      <td>309.0</td>
      <td>270.0</td>
      <td>5.7</td>
    </tr>
    <tr>
      <td>4668</td>
      <td>Fantastic Four</td>
      <td>2015.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>100.0</td>
      <td>2.35</td>
      <td>120000000.0</td>
      <td>56114221.0</td>
      <td>...</td>
      <td>596.0</td>
      <td>360.0</td>
      <td>78.0</td>
      <td>1261</td>
      <td>41000</td>
      <td>3.0</td>
      <td>110486</td>
      <td>695.0</td>
      <td>369.0</td>
      <td>4.3</td>
    </tr>
    <tr>
      <td>4669</td>
      <td>Fantastic Four</td>
      <td>2015.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>100.0</td>
      <td>2.35</td>
      <td>120000000.0</td>
      <td>56114221.0</td>
      <td>...</td>
      <td>596.0</td>
      <td>360.0</td>
      <td>78.0</td>
      <td>1261</td>
      <td>41000</td>
      <td>3.0</td>
      <td>110486</td>
      <td>695.0</td>
      <td>369.0</td>
      <td>4.3</td>
    </tr>
    <tr>
      <td>4670</td>
      <td>Fear Clinic</td>
      <td>2015.0</td>
      <td>Horror</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>95.0</td>
      <td>2.35</td>
      <td>1000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>677.0</td>
      <td>366.0</td>
      <td>253.0</td>
      <td>1825</td>
      <td>936</td>
      <td>0.0</td>
      <td>6256</td>
      <td>19.0</td>
      <td>39.0</td>
      <td>5.2</td>
    </tr>
    <tr>
      <td>4673</td>
      <td>Forsaken</td>
      <td>2015.0</td>
      <td>Drama|Western</td>
      <td>English</td>
      <td>Canada</td>
      <td>R</td>
      <td>90.0</td>
      <td>2.35</td>
      <td>11000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>2000.0</td>
      <td>1000.0</td>
      <td>720.0</td>
      <td>4142</td>
      <td>0</td>
      <td>1.0</td>
      <td>4693</td>
      <td>49.0</td>
      <td>45.0</td>
      <td>6.3</td>
    </tr>
    <tr>
      <td>4674</td>
      <td>Forsaken</td>
      <td>2015.0</td>
      <td>Drama|Western</td>
      <td>English</td>
      <td>Canada</td>
      <td>R</td>
      <td>90.0</td>
      <td>2.35</td>
      <td>11000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>2000.0</td>
      <td>1000.0</td>
      <td>720.0</td>
      <td>4142</td>
      <td>0</td>
      <td>1.0</td>
      <td>4693</td>
      <td>49.0</td>
      <td>45.0</td>
      <td>6.3</td>
    </tr>
    <tr>
      <td>4675</td>
      <td>Freeheld</td>
      <td>2015.0</td>
      <td>Biography|Drama|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>103.0</td>
      <td>1.85</td>
      <td>7000000.0</td>
      <td>532988.0</td>
      <td>...</td>
      <td>7000.0</td>
      <td>1000.0</td>
      <td>935.0</td>
      <td>9660</td>
      <td>0</td>
      <td>0.0</td>
      <td>5863</td>
      <td>25.0</td>
      <td>133.0</td>
      <td>6.5</td>
    </tr>
    <tr>
      <td>4720</td>
      <td>Pan</td>
      <td>2015.0</td>
      <td>Adventure|Family|Fantasy</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>111.0</td>
      <td>2.35</td>
      <td>150000000.0</td>
      <td>34964818.0</td>
      <td>...</td>
      <td>20000.0</td>
      <td>548.0</td>
      <td>394.0</td>
      <td>21393</td>
      <td>24000</td>
      <td>4.0</td>
      <td>39956</td>
      <td>186.0</td>
      <td>256.0</td>
      <td>5.8</td>
    </tr>
    <tr>
      <td>4721</td>
      <td>Pan</td>
      <td>2015.0</td>
      <td>Adventure|Family|Fantasy</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>111.0</td>
      <td>2.35</td>
      <td>150000000.0</td>
      <td>34964818.0</td>
      <td>...</td>
      <td>20000.0</td>
      <td>548.0</td>
      <td>394.0</td>
      <td>21393</td>
      <td>24000</td>
      <td>4.0</td>
      <td>39956</td>
      <td>186.0</td>
      <td>256.0</td>
      <td>5.8</td>
    </tr>
    <tr>
      <td>4722</td>
      <td>Pan</td>
      <td>2015.0</td>
      <td>Adventure|Family|Fantasy</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>111.0</td>
      <td>2.35</td>
      <td>150000000.0</td>
      <td>34964818.0</td>
      <td>...</td>
      <td>20000.0</td>
      <td>559.0</td>
      <td>394.0</td>
      <td>21404</td>
      <td>24000</td>
      <td>4.0</td>
      <td>39975</td>
      <td>186.0</td>
      <td>256.0</td>
      <td>5.8</td>
    </tr>
    <tr>
      <td>4818</td>
      <td>Victor Frankenstein</td>
      <td>2015.0</td>
      <td>Drama|Horror|Sci-Fi|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>110.0</td>
      <td>2.35</td>
      <td>40000000.0</td>
      <td>5773519.0</td>
      <td>...</td>
      <td>11000.0</td>
      <td>1000.0</td>
      <td>287.0</td>
      <td>12876</td>
      <td>11000</td>
      <td>2.0</td>
      <td>28618</td>
      <td>91.0</td>
      <td>159.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <td>4819</td>
      <td>Victor Frankenstein</td>
      <td>2015.0</td>
      <td>Drama|Horror|Sci-Fi|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>110.0</td>
      <td>2.35</td>
      <td>40000000.0</td>
      <td>5773519.0</td>
      <td>...</td>
      <td>11000.0</td>
      <td>1000.0</td>
      <td>287.0</td>
      <td>12876</td>
      <td>11000</td>
      <td>2.0</td>
      <td>28618</td>
      <td>91.0</td>
      <td>159.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <td>4820</td>
      <td>Victor Frankenstein</td>
      <td>2015.0</td>
      <td>Drama|Horror|Sci-Fi|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>110.0</td>
      <td>2.35</td>
      <td>40000000.0</td>
      <td>5773519.0</td>
      <td>...</td>
      <td>11000.0</td>
      <td>1000.0</td>
      <td>287.0</td>
      <td>12876</td>
      <td>11000</td>
      <td>2.0</td>
      <td>28621</td>
      <td>91.0</td>
      <td>159.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <td>4837</td>
      <td>Bad Moms</td>
      <td>2016.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>100.0</td>
      <td>NaN</td>
      <td>20000000.0</td>
      <td>55461307.0</td>
      <td>...</td>
      <td>15000.0</td>
      <td>1000.0</td>
      <td>851.0</td>
      <td>18786</td>
      <td>18000</td>
      <td>9.0</td>
      <td>4654</td>
      <td>46.0</td>
      <td>81.0</td>
      <td>6.7</td>
    </tr>
    <tr>
      <td>4838</td>
      <td>Bad Moms</td>
      <td>2016.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>100.0</td>
      <td>NaN</td>
      <td>20000000.0</td>
      <td>55461307.0</td>
      <td>...</td>
      <td>15000.0</td>
      <td>1000.0</td>
      <td>851.0</td>
      <td>18786</td>
      <td>18000</td>
      <td>9.0</td>
      <td>4654</td>
      <td>46.0</td>
      <td>81.0</td>
      <td>6.7</td>
    </tr>
    <tr>
      <td>4839</td>
      <td>Batman v Superman: Dawn of Justice</td>
      <td>2016.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>183.0</td>
      <td>2.35</td>
      <td>250000000.0</td>
      <td>330249062.0</td>
      <td>...</td>
      <td>15000.0</td>
      <td>4000.0</td>
      <td>2000.0</td>
      <td>24450</td>
      <td>197000</td>
      <td>0.0</td>
      <td>371639</td>
      <td>3018.0</td>
      <td>673.0</td>
      <td>6.9</td>
    </tr>
    <tr>
      <td>4862</td>
      <td>Godzilla Resurgence</td>
      <td>2016.0</td>
      <td>Action|Adventure|Drama|Horror|Sci-Fi</td>
      <td>Japanese</td>
      <td>Japan</td>
      <td>NaN</td>
      <td>120.0</td>
      <td>2.35</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>544.0</td>
      <td>106.0</td>
      <td>12.0</td>
      <td>699</td>
      <td>0</td>
      <td>0.0</td>
      <td>374</td>
      <td>13.0</td>
      <td>1.0</td>
      <td>8.2</td>
    </tr>
    <tr>
      <td>4863</td>
      <td>Godzilla Resurgence</td>
      <td>2016.0</td>
      <td>Action|Adventure|Drama|Horror|Sci-Fi</td>
      <td>Japanese</td>
      <td>Japan</td>
      <td>NaN</td>
      <td>120.0</td>
      <td>2.35</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>544.0</td>
      <td>106.0</td>
      <td>12.0</td>
      <td>699</td>
      <td>0</td>
      <td>0.0</td>
      <td>374</td>
      <td>13.0</td>
      <td>1.0</td>
      <td>8.2</td>
    </tr>
    <tr>
      <td>4864</td>
      <td>Hail, Caesar!</td>
      <td>2016.0</td>
      <td>Comedy|Mystery</td>
      <td>English</td>
      <td>UK</td>
      <td>PG-13</td>
      <td>106.0</td>
      <td>1.85</td>
      <td>22000000.0</td>
      <td>29997095.0</td>
      <td>...</td>
      <td>19000.0</td>
      <td>17000.0</td>
      <td>1000.0</td>
      <td>38494</td>
      <td>23000</td>
      <td>5.0</td>
      <td>60926</td>
      <td>302.0</td>
      <td>423.0</td>
      <td>6.4</td>
    </tr>
    <tr>
      <td>4916</td>
      <td>The Legend of Tarzan</td>
      <td>2016.0</td>
      <td>Action|Adventure|Drama|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>110.0</td>
      <td>2.35</td>
      <td>180000000.0</td>
      <td>124051759.0</td>
      <td>...</td>
      <td>11000.0</td>
      <td>10000.0</td>
      <td>103.0</td>
      <td>21175</td>
      <td>29000</td>
      <td>2.0</td>
      <td>42372</td>
      <td>239.0</td>
      <td>248.0</td>
      <td>6.6</td>
    </tr>
    <tr>
      <td>4917</td>
      <td>The Legend of Tarzan</td>
      <td>2016.0</td>
      <td>Action|Adventure|Drama|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>110.0</td>
      <td>2.35</td>
      <td>180000000.0</td>
      <td>124051759.0</td>
      <td>...</td>
      <td>11000.0</td>
      <td>10000.0</td>
      <td>103.0</td>
      <td>21175</td>
      <td>29000</td>
      <td>2.0</td>
      <td>42372</td>
      <td>239.0</td>
      <td>248.0</td>
      <td>6.6</td>
    </tr>
    <tr>
      <td>4918</td>
      <td>The Little Ponderosa Zoo</td>
      <td>2016.0</td>
      <td>Family</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>84.0</td>
      <td>16.00</td>
      <td>500000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>385.0</td>
      <td>169.0</td>
      <td>53.0</td>
      <td>683</td>
      <td>9</td>
      <td>2.0</td>
      <td>15</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>5.2</td>
    </tr>
    <tr>
      <td>4997</td>
      <td>Saving Grace</td>
      <td>NaN</td>
      <td>Drama|Fantasy</td>
      <td>English</td>
      <td>USA</td>
      <td>TV-MA</td>
      <td>60.0</td>
      <td>1.78</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>1000.0</td>
      <td>904.0</td>
      <td>5203</td>
      <td>634</td>
      <td>1.0</td>
      <td>3852</td>
      <td>47.0</td>
      <td>9.0</td>
      <td>7.5</td>
    </tr>
    <tr>
      <td>4998</td>
      <td>Saving Grace</td>
      <td>NaN</td>
      <td>Drama|Fantasy</td>
      <td>English</td>
      <td>USA</td>
      <td>TV-MA</td>
      <td>60.0</td>
      <td>1.78</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>1000.0</td>
      <td>904.0</td>
      <td>5203</td>
      <td>634</td>
      <td>1.0</td>
      <td>3852</td>
      <td>47.0</td>
      <td>9.0</td>
      <td>7.5</td>
    </tr>
    <tr>
      <td>4999</td>
      <td>Scream: The TV Series</td>
      <td>NaN</td>
      <td>Crime|Drama|Horror|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>TV-14</td>
      <td>45.0</td>
      <td>16.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>460.0</td>
      <td>292.0</td>
      <td>260.0</td>
      <td>2380</td>
      <td>0</td>
      <td>0.0</td>
      <td>18058</td>
      <td>68.0</td>
      <td>20.0</td>
      <td>7.3</td>
    </tr>
  </tbody>
</table>
<p>44 rows × 25 columns</p>
</div>



```python
display(dup_show.duplicated().sum())
display(dataset.duplicated().sum())
```


    45



    45


### Now, it's confirmed. The duplicate values in the original dataset is the same as the one in the extracted dataset.

### This is not a waste of time for the following reasons.

## 1. It'll build your skills working and digging deeper into data

## 2. You'll be sure of what you're doing
## 3. You can visualize the data and see for yourself how the duplicate values look like. In my experience, duplicate values are either directly before or after the original version of it. In this case, both situation are present. That's experience which you'll never get if you fail to dive deep enough.

## So, for what it's worth, you should do this once in a while as time permits

### Now, you can drop the duplicate values contained in the original dataset and check again.

### After that, you can continue with other processes


```python
dataset.drop_duplicates(inplace = True)
dataset.duplicated().sum()
```




    0



### Here we are. Now it's time to check for missing values.

### Some rigorous work will be done here, so fasten your seatbelt tight.

### I'm just kidding about that but pay attention to this part. It's a very important aspect of data preparation (Science) process


```python
not_missing = dataset.notna().sum()
not_missing
```




    Title                          4997
    Year                           4891
    Genres                         4997
    Language                       4986
    Country                        4993
    Content Rating                 4697
    Duration                       4983
    Aspect Ratio                   4671
    Budget                         4511
    Gross Earnings                 4124
    Director                       4894
    Actor 1                        4990
    Actor 2                        4984
    Actor 3                        4975
    Facebook Likes - Director      4894
    Facebook Likes - Actor 1       4990
    Facebook Likes - Actor 2       4984
    Facebook Likes - Actor 3       4975
    Facebook Likes - cast Total    4997
    Facebook likes - Movie         4997
    Facenumber in posters          4984
    User Votes                     4997
    Reviews by Users               4977
    Reviews by Crtiics             4949
    IMDB Score                     4997
    dtype: int64



### As some random values of duplicated dataset has been deleted, the index of the dataset would have been altered. Check this again and correct it accordingly


```python
display(len(dataset.index))
#The total length of the index in the dataset is 4997. Now, the index should be reconfigured accordingly
new_index1 = range(0,4997)
dataset.index = new_index1
dataset.index
```


    4997





    RangeIndex(start=0, stop=4997, step=1)




```python
missing_values = dataset.isnull().sum()
missing_values
```




    Title                            0
    Year                           106
    Genres                           0
    Language                        11
    Country                          4
    Content Rating                 300
    Duration                        14
    Aspect Ratio                   326
    Budget                         486
    Gross Earnings                 873
    Director                       103
    Actor 1                          7
    Actor 2                         13
    Actor 3                         22
    Facebook Likes - Director      103
    Facebook Likes - Actor 1         7
    Facebook Likes - Actor 2        13
    Facebook Likes - Actor 3        22
    Facebook Likes - cast Total      0
    Facebook likes - Movie           0
    Facenumber in posters           13
    User Votes                       0
    Reviews by Users                20
    Reviews by Crtiics              48
    IMDB Score                       0
    dtype: int64




```python
for column, percent in zip(dataset.columns, missing_values) :
    if percent > 0 :
        print(column,":", percent)
```

    Year : 106
    Language : 11
    Country : 4
    Content Rating : 300
    Duration : 14
    Aspect Ratio : 326
    Budget : 486
    Gross Earnings : 873
    Director : 103
    Actor 1 : 7
    Actor 2 : 13
    Actor 3 : 22
    Facebook Likes - Director : 103
    Facebook Likes - Actor 1 : 7
    Facebook Likes - Actor 2 : 13
    Facebook Likes - Actor 3 : 22
    Facenumber in posters : 13
    Reviews by Users : 20
    Reviews by Crtiics : 48



```python
outcome = []
for M,N in zip(missing_values,not_missing) :
    outcome.append((M/(M+N)*100))
for P,Q,R in zip(dataset.columns, outcome, missing_values) :
    if Q > 0 :
        print(P,"=>",R,"=>",Q,"%")
 
```

    Year => 106 => 2.1212727636581947 %
    Language => 11 => 0.22013207924754855 %
    Country => 4 => 0.08004802881729037 %
    Content Rating => 300 => 6.0036021612967785 %
    Duration => 14 => 0.2801681008605163 %
    Aspect Ratio => 326 => 6.523914348609165 %
    Budget => 486 => 9.72583550130078 %
    Gross Earnings => 873 => 17.470482289373624 %
    Director => 103 => 2.061236742045227 %
    Actor 1 => 7 => 0.14008405043025815 %
    Actor 2 => 13 => 0.2601560936561937 %
    Actor 3 => 22 => 0.4402641584950971 %
    Facebook Likes - Director => 103 => 2.061236742045227 %
    Facebook Likes - Actor 1 => 7 => 0.14008405043025815 %
    Facebook Likes - Actor 2 => 13 => 0.2601560936561937 %
    Facebook Likes - Actor 3 => 22 => 0.4402641584950971 %
    Facenumber in posters => 13 => 0.2601560936561937 %
    Reviews by Users => 20 => 0.40024014408645187 %
    Reviews by Crtiics => 48 => 0.9605763458074845 %


### This seems a little more clear. It's very much easier to see the columns that has null values, the number of null values it contains and the percentage of the total values of the column which the null values represent.

### When it comes to treating null values, there are many approach to it and how to treat it varies according to the situation.

### Some of the condition is the quantity of the missing values we're talking about.

### Is the value not recorded or it does not exist.

### Whatever the condition is determines what you do and how you do it.

### In this case, each column will be scrutinized separately, anf depending on what is revealed, the appropriate approach will be applied accordingly.


```python
dataset[dataset.Year.isnull()].index
```




    Int64Index([4891, 4892, 4893, 4894, 4895, 4896, 4897, 4898, 4899, 4900,
                ...
                4987, 4988, 4989, 4990, 4991, 4992, 4993, 4994, 4995, 4996],
               dtype='int64', length=106)



### The code above indicates the positions of the null values. They're towards the end of the dataset. Now we'll call it out, to have a visual clue


```python
display(dataset[4540:4600])
display(dataset[4780:4801])
display(dataset[4840 : 4900])
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Year</th>
      <th>Genres</th>
      <th>Language</th>
      <th>Country</th>
      <th>Content Rating</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>...</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>4540</td>
      <td>The Water Diviner</td>
      <td>2014.0</td>
      <td>Drama|War</td>
      <td>English</td>
      <td>Australia</td>
      <td>R</td>
      <td>111.0</td>
      <td>2.35</td>
      <td>22500000.0</td>
      <td>4190530.0</td>
      <td>...</td>
      <td>523.0</td>
      <td>468.0</td>
      <td>234.0</td>
      <td>1795</td>
      <td>18000</td>
      <td>0.0</td>
      <td>53341</td>
      <td>185.0</td>
      <td>183.0</td>
      <td>7.1</td>
    </tr>
    <tr>
      <td>4541</td>
      <td>They Came Together</td>
      <td>2014.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>83.0</td>
      <td>1.85</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>3000.0</td>
      <td>1000.0</td>
      <td>975.0</td>
      <td>7191</td>
      <td>0</td>
      <td>2.0</td>
      <td>16987</td>
      <td>85.0</td>
      <td>98.0</td>
      <td>5.5</td>
    </tr>
    <tr>
      <td>4542</td>
      <td>Think Like a Man Too</td>
      <td>2014.0</td>
      <td>Comedy|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>106.0</td>
      <td>2.35</td>
      <td>24000000.0</td>
      <td>65182182.0</td>
      <td>...</td>
      <td>966.0</td>
      <td>807.0</td>
      <td>676.0</td>
      <td>4830</td>
      <td>3000</td>
      <td>8.0</td>
      <td>15310</td>
      <td>38.0</td>
      <td>52.0</td>
      <td>5.7</td>
    </tr>
    <tr>
      <td>4543</td>
      <td>This Is Where I Leave You</td>
      <td>2014.0</td>
      <td>Comedy|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>103.0</td>
      <td>2.35</td>
      <td>19800000.0</td>
      <td>34290142.0</td>
      <td>...</td>
      <td>2000.0</td>
      <td>1000.0</td>
      <td>949.0</td>
      <td>4662</td>
      <td>14000</td>
      <td>8.0</td>
      <td>54242</td>
      <td>145.0</td>
      <td>156.0</td>
      <td>6.6</td>
    </tr>
    <tr>
      <td>4544</td>
      <td>Tiger Orange</td>
      <td>2014.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>Unrated</td>
      <td>75.0</td>
      <td>1.78</td>
      <td>100000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>267.0</td>
      <td>87.0</td>
      <td>46.0</td>
      <td>488</td>
      <td>182</td>
      <td>2.0</td>
      <td>683</td>
      <td>8.0</td>
      <td>13.0</td>
      <td>6.8</td>
    </tr>
    <tr>
      <td>4545</td>
      <td>Top Five</td>
      <td>2014.0</td>
      <td>Comedy|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>102.0</td>
      <td>2.35</td>
      <td>12000000.0</td>
      <td>25277561.0</td>
      <td>...</td>
      <td>3000.0</td>
      <td>966.0</td>
      <td>555.0</td>
      <td>5592</td>
      <td>0</td>
      <td>10.0</td>
      <td>21672</td>
      <td>93.0</td>
      <td>161.0</td>
      <td>6.5</td>
    </tr>
    <tr>
      <td>4546</td>
      <td>Top Spin</td>
      <td>2014.0</td>
      <td>Documentary</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>80.0</td>
      <td>NaN</td>
      <td>150000.0</td>
      <td>5858.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>116</td>
      <td>0.0</td>
      <td>260</td>
      <td>2.0</td>
      <td>18.0</td>
      <td>7.1</td>
    </tr>
    <tr>
      <td>4547</td>
      <td>Transcendence</td>
      <td>2014.0</td>
      <td>Drama|Mystery|Romance|Sci-Fi|Thriller</td>
      <td>English</td>
      <td>UK</td>
      <td>PG-13</td>
      <td>119.0</td>
      <td>2.35</td>
      <td>100000000.0</td>
      <td>23014504.0</td>
      <td>...</td>
      <td>40000.0</td>
      <td>11000.0</td>
      <td>968.0</td>
      <td>54031</td>
      <td>37000</td>
      <td>1.0</td>
      <td>172707</td>
      <td>462.0</td>
      <td>355.0</td>
      <td>6.3</td>
    </tr>
    <tr>
      <td>4548</td>
      <td>Transformers: Age of Extinction</td>
      <td>2014.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>165.0</td>
      <td>2.35</td>
      <td>210000000.0</td>
      <td>245428137.0</td>
      <td>...</td>
      <td>974.0</td>
      <td>956.0</td>
      <td>808.0</td>
      <td>3988</td>
      <td>56000</td>
      <td>2.0</td>
      <td>242420</td>
      <td>918.0</td>
      <td>378.0</td>
      <td>5.7</td>
    </tr>
    <tr>
      <td>4549</td>
      <td>Trash</td>
      <td>2014.0</td>
      <td>Adventure|Crime|Drama|Mystery|Thriller</td>
      <td>Portuguese</td>
      <td>UK</td>
      <td>R</td>
      <td>114.0</td>
      <td>2.35</td>
      <td>NaN</td>
      <td>10230.0</td>
      <td>...</td>
      <td>585.0</td>
      <td>68.0</td>
      <td>14.0</td>
      <td>679</td>
      <td>0</td>
      <td>0.0</td>
      <td>14437</td>
      <td>26.0</td>
      <td>101.0</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>4550</td>
      <td>Tusk</td>
      <td>2014.0</td>
      <td>Comedy|Drama|Horror</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>102.0</td>
      <td>2.35</td>
      <td>3000000.0</td>
      <td>1821983.0</td>
      <td>...</td>
      <td>40000.0</td>
      <td>3000.0</td>
      <td>387.0</td>
      <td>43810</td>
      <td>20000</td>
      <td>0.0</td>
      <td>31089</td>
      <td>261.0</td>
      <td>254.0</td>
      <td>5.4</td>
    </tr>
    <tr>
      <td>4551</td>
      <td>Unbroken</td>
      <td>2014.0</td>
      <td>Biography|Drama|Sport|War</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>137.0</td>
      <td>2.35</td>
      <td>65000000.0</td>
      <td>115603980.0</td>
      <td>...</td>
      <td>769.0</td>
      <td>698.0</td>
      <td>465.0</td>
      <td>2938</td>
      <td>35000</td>
      <td>0.0</td>
      <td>103589</td>
      <td>351.0</td>
      <td>322.0</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>4552</td>
      <td>Unfriended</td>
      <td>2014.0</td>
      <td>Horror|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>83.0</td>
      <td>1.85</td>
      <td>1000000.0</td>
      <td>31537320.0</td>
      <td>...</td>
      <td>707.0</td>
      <td>305.0</td>
      <td>142.0</td>
      <td>1565</td>
      <td>13000</td>
      <td>0.0</td>
      <td>44329</td>
      <td>309.0</td>
      <td>270.0</td>
      <td>5.7</td>
    </tr>
    <tr>
      <td>4553</td>
      <td>United Passions</td>
      <td>2014.0</td>
      <td>Drama|History|Sport</td>
      <td>English</td>
      <td>France</td>
      <td>Not Rated</td>
      <td>110.0</td>
      <td>2.35</td>
      <td>24000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>922.0</td>
      <td>919.0</td>
      <td>432.0</td>
      <td>2725</td>
      <td>0</td>
      <td>4.0</td>
      <td>3279</td>
      <td>22.0</td>
      <td>7.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <td>4554</td>
      <td>Unsullied</td>
      <td>2014.0</td>
      <td>Action|Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>93.0</td>
      <td>2.35</td>
      <td>1500000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>393.0</td>
      <td>191.0</td>
      <td>56.0</td>
      <td>792</td>
      <td>307</td>
      <td>1.0</td>
      <td>95</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>5.5</td>
    </tr>
    <tr>
      <td>4555</td>
      <td>Viy</td>
      <td>2014.0</td>
      <td>Adventure|Fantasy|Mystery|Thriller</td>
      <td>Russian</td>
      <td>Russia</td>
      <td>NaN</td>
      <td>107.0</td>
      <td>1.85</td>
      <td>26000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>65.0</td>
      <td>48.0</td>
      <td>1166</td>
      <td>0</td>
      <td>1.0</td>
      <td>3170</td>
      <td>18.0</td>
      <td>25.0</td>
      <td>5.4</td>
    </tr>
    <tr>
      <td>4556</td>
      <td>When the Game Stands Tall</td>
      <td>2014.0</td>
      <td>Drama|Family|Sport</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>115.0</td>
      <td>1.85</td>
      <td>15000000.0</td>
      <td>30127963.0</td>
      <td>...</td>
      <td>116.0</td>
      <td>110.0</td>
      <td>100.0</td>
      <td>525</td>
      <td>0</td>
      <td>0.0</td>
      <td>12596</td>
      <td>64.0</td>
      <td>50.0</td>
      <td>6.7</td>
    </tr>
    <tr>
      <td>4557</td>
      <td>While We're Young</td>
      <td>2014.0</td>
      <td>Comedy|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>97.0</td>
      <td>1.85</td>
      <td>10000000.0</td>
      <td>7574066.0</td>
      <td>...</td>
      <td>6000.0</td>
      <td>139.0</td>
      <td>64.0</td>
      <td>6322</td>
      <td>0</td>
      <td>2.0</td>
      <td>30325</td>
      <td>96.0</td>
      <td>270.0</td>
      <td>6.3</td>
    </tr>
    <tr>
      <td>4558</td>
      <td>Whiplash</td>
      <td>2014.0</td>
      <td>Drama|Music</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>107.0</td>
      <td>2.40</td>
      <td>3300000.0</td>
      <td>13092000.0</td>
      <td>...</td>
      <td>24000.0</td>
      <td>970.0</td>
      <td>535.0</td>
      <td>26495</td>
      <td>129000</td>
      <td>0.0</td>
      <td>399138</td>
      <td>731.0</td>
      <td>535.0</td>
      <td>8.5</td>
    </tr>
    <tr>
      <td>4559</td>
      <td>Wicked Blood</td>
      <td>2014.0</td>
      <td>Action|Crime|Drama|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>Not Rated</td>
      <td>92.0</td>
      <td>1.85</td>
      <td>3500000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>2000.0</td>
      <td>660.0</td>
      <td>597.0</td>
      <td>3854</td>
      <td>482</td>
      <td>2.0</td>
      <td>1928</td>
      <td>10.0</td>
      <td>7.0</td>
      <td>5.4</td>
    </tr>
    <tr>
      <td>4560</td>
      <td>Wild</td>
      <td>2014.0</td>
      <td>Adventure|Biography|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>115.0</td>
      <td>2.35</td>
      <td>15000000.0</td>
      <td>37877959.0</td>
      <td>...</td>
      <td>2000.0</td>
      <td>820.0</td>
      <td>612.0</td>
      <td>4896</td>
      <td>38000</td>
      <td>1.0</td>
      <td>86664</td>
      <td>252.0</td>
      <td>349.0</td>
      <td>7.1</td>
    </tr>
    <tr>
      <td>4561</td>
      <td>Winter's Tale</td>
      <td>2014.0</td>
      <td>Drama|Fantasy|Mystery|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>118.0</td>
      <td>2.35</td>
      <td>60000000.0</td>
      <td>22451.0</td>
      <td>...</td>
      <td>20000.0</td>
      <td>882.0</td>
      <td>778.0</td>
      <td>22447</td>
      <td>17000</td>
      <td>0.0</td>
      <td>41288</td>
      <td>126.0</td>
      <td>189.0</td>
      <td>6.2</td>
    </tr>
    <tr>
      <td>4562</td>
      <td>Wish I Was Here</td>
      <td>2014.0</td>
      <td>Comedy|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>106.0</td>
      <td>2.35</td>
      <td>6000000.0</td>
      <td>3588432.0</td>
      <td>...</td>
      <td>17000.0</td>
      <td>1000.0</td>
      <td>379.0</td>
      <td>18947</td>
      <td>0</td>
      <td>4.0</td>
      <td>29341</td>
      <td>93.0</td>
      <td>149.0</td>
      <td>6.7</td>
    </tr>
    <tr>
      <td>4563</td>
      <td>Wolves</td>
      <td>2014.0</td>
      <td>Action|Horror</td>
      <td>English</td>
      <td>France</td>
      <td>R</td>
      <td>91.0</td>
      <td>2.35</td>
      <td>18000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>11000.0</td>
      <td>918.0</td>
      <td>413.0</td>
      <td>13545</td>
      <td>0</td>
      <td>2.0</td>
      <td>5693</td>
      <td>34.0</td>
      <td>59.0</td>
      <td>5.3</td>
    </tr>
    <tr>
      <td>4564</td>
      <td>X-Men: Days of Future Past</td>
      <td>2014.0</td>
      <td>Action|Adventure|Fantasy|Sci-Fi|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>149.0</td>
      <td>2.35</td>
      <td>200000000.0</td>
      <td>233914986.0</td>
      <td>...</td>
      <td>34000.0</td>
      <td>22000.0</td>
      <td>20000.0</td>
      <td>91434</td>
      <td>82000</td>
      <td>7.0</td>
      <td>514125</td>
      <td>752.0</td>
      <td>539.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <td>4565</td>
      <td>Z Storm</td>
      <td>2014.0</td>
      <td>Action|Crime</td>
      <td>Cantonese</td>
      <td>Hong Kong</td>
      <td>NaN</td>
      <td>92.0</td>
      <td>2.35</td>
      <td>7000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>91.0</td>
      <td>82.0</td>
      <td>4.0</td>
      <td>198</td>
      <td>55</td>
      <td>1.0</td>
      <td>383</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>5.3</td>
    </tr>
    <tr>
      <td>4566</td>
      <td>#Horror</td>
      <td>2015.0</td>
      <td>Drama|Horror|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>Not Rated</td>
      <td>101.0</td>
      <td>NaN</td>
      <td>1500000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>501.0</td>
      <td>418.0</td>
      <td>56.0</td>
      <td>1044</td>
      <td>750</td>
      <td>1.0</td>
      <td>1547</td>
      <td>42.0</td>
      <td>35.0</td>
      <td>3.3</td>
    </tr>
    <tr>
      <td>4567</td>
      <td>10 Days in a Madhouse</td>
      <td>2015.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>111.0</td>
      <td>1.85</td>
      <td>12000000.0</td>
      <td>14616.0</td>
      <td>...</td>
      <td>1000.0</td>
      <td>445.0</td>
      <td>247.0</td>
      <td>2059</td>
      <td>26000</td>
      <td>1.0</td>
      <td>314</td>
      <td>10.0</td>
      <td>1.0</td>
      <td>7.5</td>
    </tr>
    <tr>
      <td>4568</td>
      <td>90 Minutes in Heaven</td>
      <td>2015.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>121.0</td>
      <td>2.35</td>
      <td>5000000.0</td>
      <td>4700361.0</td>
      <td>...</td>
      <td>4000.0</td>
      <td>849.0</td>
      <td>473.0</td>
      <td>6617</td>
      <td>0</td>
      <td>0.0</td>
      <td>2047</td>
      <td>29.0</td>
      <td>12.0</td>
      <td>4.6</td>
    </tr>
    <tr>
      <td>4569</td>
      <td>A Tale of Three Cities</td>
      <td>2015.0</td>
      <td>Drama</td>
      <td>Chinese</td>
      <td>China</td>
      <td>NaN</td>
      <td>130.0</td>
      <td>2.35</td>
      <td>12000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>215.0</td>
      <td>27.0</td>
      <td>2.0</td>
      <td>244</td>
      <td>4</td>
      <td>1.0</td>
      <td>117</td>
      <td>6.0</td>
      <td>6.0</td>
      <td>6.2</td>
    </tr>
    <tr>
      <td>4570</td>
      <td>A Warrior's Tail</td>
      <td>2015.0</td>
      <td>Adventure|Animation|Fantasy</td>
      <td>Russian</td>
      <td>Russia</td>
      <td>NaN</td>
      <td>85.0</td>
      <td>NaN</td>
      <td>30000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>114.0</td>
      <td>35.0</td>
      <td>21.0</td>
      <td>229</td>
      <td>161</td>
      <td>1.0</td>
      <td>393</td>
      <td>7.0</td>
      <td>5.0</td>
      <td>4.1</td>
    </tr>
    <tr>
      <td>4571</td>
      <td>Abandoned</td>
      <td>2015.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>New Zealand</td>
      <td>NaN</td>
      <td>86.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>42.0</td>
      <td>40.0</td>
      <td>3.0</td>
      <td>90</td>
      <td>213</td>
      <td>5.0</td>
      <td>333</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>6.3</td>
    </tr>
    <tr>
      <td>4572</td>
      <td>Accidental Love</td>
      <td>2015.0</td>
      <td>Comedy|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>100.0</td>
      <td>1.85</td>
      <td>26000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>15000.0</td>
      <td>980.0</td>
      <td>816.0</td>
      <td>19068</td>
      <td>0</td>
      <td>5.0</td>
      <td>5006</td>
      <td>28.0</td>
      <td>56.0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <td>4573</td>
      <td>Adulterers</td>
      <td>2015.0</td>
      <td>Crime|Drama|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>91.0</td>
      <td>2.35</td>
      <td>750000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>696.0</td>
      <td>320.0</td>
      <td>137.0</td>
      <td>1210</td>
      <td>158</td>
      <td>3.0</td>
      <td>514</td>
      <td>1.0</td>
      <td>8.0</td>
      <td>4.9</td>
    </tr>
    <tr>
      <td>4574</td>
      <td>Aloha</td>
      <td>2015.0</td>
      <td>Comedy|Drama|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>105.0</td>
      <td>1.85</td>
      <td>37000000.0</td>
      <td>20991497.0</td>
      <td>...</td>
      <td>15000.0</td>
      <td>14000.0</td>
      <td>13000.0</td>
      <td>44037</td>
      <td>11000</td>
      <td>1.0</td>
      <td>39778</td>
      <td>172.0</td>
      <td>138.0</td>
      <td>5.4</td>
    </tr>
    <tr>
      <td>4575</td>
      <td>Aloha</td>
      <td>2015.0</td>
      <td>Comedy|Drama|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>105.0</td>
      <td>1.85</td>
      <td>37000000.0</td>
      <td>20991497.0</td>
      <td>...</td>
      <td>15000.0</td>
      <td>14000.0</td>
      <td>13000.0</td>
      <td>44037</td>
      <td>11000</td>
      <td>1.0</td>
      <td>39782</td>
      <td>172.0</td>
      <td>138.0</td>
      <td>5.4</td>
    </tr>
    <tr>
      <td>4576</td>
      <td>Alvin and the Chipmunks: The Road Chip</td>
      <td>2015.0</td>
      <td>Adventure|Animation|Comedy|Family|Fantasy|Music</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>92.0</td>
      <td>1.85</td>
      <td>90000000.0</td>
      <td>85884815.0</td>
      <td>...</td>
      <td>35000.0</td>
      <td>1000.0</td>
      <td>1000.0</td>
      <td>38450</td>
      <td>0</td>
      <td>0.0</td>
      <td>9418</td>
      <td>53.0</td>
      <td>70.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <td>4577</td>
      <td>America Is Still the Place</td>
      <td>2015.0</td>
      <td>History</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>90.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>970.0</td>
      <td>812.0</td>
      <td>569.0</td>
      <td>3359</td>
      <td>337</td>
      <td>0.0</td>
      <td>22</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7.5</td>
    </tr>
    <tr>
      <td>4578</td>
      <td>American Hero</td>
      <td>2015.0</td>
      <td>Action|Comedy|Drama|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>86.0</td>
      <td>NaN</td>
      <td>990000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>489.0</td>
      <td>207.0</td>
      <td>175.0</td>
      <td>1278</td>
      <td>549</td>
      <td>2.0</td>
      <td>2706</td>
      <td>23.0</td>
      <td>16.0</td>
      <td>4.9</td>
    </tr>
    <tr>
      <td>4579</td>
      <td>Animal Kingdom: Let's go Ape</td>
      <td>2015.0</td>
      <td>Adventure|Animation|Comedy|Family</td>
      <td>French</td>
      <td>France</td>
      <td>NaN</td>
      <td>101.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>326.0</td>
      <td>152.0</td>
      <td>6.0</td>
      <td>488</td>
      <td>161</td>
      <td>0.0</td>
      <td>590</td>
      <td>5.0</td>
      <td>9.0</td>
      <td>4.9</td>
    </tr>
    <tr>
      <td>4580</td>
      <td>Anomalisa</td>
      <td>2015.0</td>
      <td>Animation|Comedy|Drama|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>90.0</td>
      <td>2.35</td>
      <td>8000000.0</td>
      <td>3442820.0</td>
      <td>...</td>
      <td>1000.0</td>
      <td>442.0</td>
      <td>0.0</td>
      <td>1442</td>
      <td>0</td>
      <td>0.0</td>
      <td>31489</td>
      <td>140.0</td>
      <td>328.0</td>
      <td>7.3</td>
    </tr>
    <tr>
      <td>4581</td>
      <td>Antarctic Edge: 70° South</td>
      <td>2015.0</td>
      <td>Adventure|Documentary</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>72.0</td>
      <td>NaN</td>
      <td>150000.0</td>
      <td>4914.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>215</td>
      <td>0.0</td>
      <td>123</td>
      <td>2.0</td>
      <td>5.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <td>4582</td>
      <td>Ant-Man</td>
      <td>2015.0</td>
      <td>Action|Adventure|Comedy|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>117.0</td>
      <td>1.85</td>
      <td>130000000.0</td>
      <td>180191634.0</td>
      <td>...</td>
      <td>2000.0</td>
      <td>2000.0</td>
      <td>680.0</td>
      <td>5730</td>
      <td>61000</td>
      <td>6.0</td>
      <td>313866</td>
      <td>549.0</td>
      <td>517.0</td>
      <td>7.4</td>
    </tr>
    <tr>
      <td>4583</td>
      <td>Area 51</td>
      <td>2015.0</td>
      <td>Horror|Sci-Fi|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>91.0</td>
      <td>NaN</td>
      <td>5000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>46.0</td>
      <td>21.0</td>
      <td>14.0</td>
      <td>117</td>
      <td>0</td>
      <td>0.0</td>
      <td>7888</td>
      <td>55.0</td>
      <td>56.0</td>
      <td>4.2</td>
    </tr>
    <tr>
      <td>4584</td>
      <td>Avengers: Age of Ultron</td>
      <td>2015.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>141.0</td>
      <td>2.35</td>
      <td>250000000.0</td>
      <td>458991599.0</td>
      <td>...</td>
      <td>26000.0</td>
      <td>21000.0</td>
      <td>19000.0</td>
      <td>92000</td>
      <td>118000</td>
      <td>4.0</td>
      <td>462669</td>
      <td>1117.0</td>
      <td>635.0</td>
      <td>7.5</td>
    </tr>
    <tr>
      <td>4585</td>
      <td>AWOL-72</td>
      <td>2015.0</td>
      <td>Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>82.0</td>
      <td>NaN</td>
      <td>3000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>904.0</td>
      <td>779.0</td>
      <td>648.0</td>
      <td>4092</td>
      <td>398</td>
      <td>4.0</td>
      <td>520</td>
      <td>8.0</td>
      <td>6.0</td>
      <td>3.9</td>
    </tr>
    <tr>
      <td>4586</td>
      <td>Baahubali: The Beginning</td>
      <td>2015.0</td>
      <td>Action|Adventure|Drama|Fantasy|War</td>
      <td>Telugu</td>
      <td>India</td>
      <td>NaN</td>
      <td>159.0</td>
      <td>1.85</td>
      <td>18026148.0</td>
      <td>6498000.0</td>
      <td>...</td>
      <td>218.0</td>
      <td>133.0</td>
      <td>72.0</td>
      <td>554</td>
      <td>21000</td>
      <td>1.0</td>
      <td>62756</td>
      <td>410.0</td>
      <td>44.0</td>
      <td>8.4</td>
    </tr>
    <tr>
      <td>4587</td>
      <td>Bizarre</td>
      <td>2015.0</td>
      <td>Drama|Musical|Romance</td>
      <td>English</td>
      <td>France</td>
      <td>Unrated</td>
      <td>98.0</td>
      <td>1.78</td>
      <td>500000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>19.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>19</td>
      <td>114</td>
      <td>0.0</td>
      <td>569</td>
      <td>1.0</td>
      <td>9.0</td>
      <td>4.3</td>
    </tr>
    <tr>
      <td>4588</td>
      <td>Black Mass</td>
      <td>2015.0</td>
      <td>Biography|Crime|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>123.0</td>
      <td>2.35</td>
      <td>53000000.0</td>
      <td>62563543.0</td>
      <td>...</td>
      <td>40000.0</td>
      <td>19000.0</td>
      <td>3000.0</td>
      <td>63769</td>
      <td>44000</td>
      <td>7.0</td>
      <td>115216</td>
      <td>289.0</td>
      <td>391.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <td>4589</td>
      <td>Blackhat</td>
      <td>2015.0</td>
      <td>Action|Crime|Drama|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>133.0</td>
      <td>2.35</td>
      <td>70000000.0</td>
      <td>7097125.0</td>
      <td>...</td>
      <td>26000.0</td>
      <td>326.0</td>
      <td>301.0</td>
      <td>28129</td>
      <td>11000</td>
      <td>1.0</td>
      <td>38983</td>
      <td>207.0</td>
      <td>261.0</td>
      <td>5.4</td>
    </tr>
    <tr>
      <td>4590</td>
      <td>Bleeding Hearts</td>
      <td>2015.0</td>
      <td>Horror</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>100.0</td>
      <td>NaN</td>
      <td>1200000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>498.0</td>
      <td>350.0</td>
      <td>312.0</td>
      <td>1810</td>
      <td>242</td>
      <td>1.0</td>
      <td>71</td>
      <td>2.0</td>
      <td>7.0</td>
      <td>4.2</td>
    </tr>
    <tr>
      <td>4591</td>
      <td>Bridge of Spies</td>
      <td>2015.0</td>
      <td>Drama|History|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>142.0</td>
      <td>2.35</td>
      <td>40000000.0</td>
      <td>72306065.0</td>
      <td>...</td>
      <td>15000.0</td>
      <td>535.0</td>
      <td>423.0</td>
      <td>16944</td>
      <td>55000</td>
      <td>0.0</td>
      <td>178118</td>
      <td>355.0</td>
      <td>459.0</td>
      <td>7.6</td>
    </tr>
    <tr>
      <td>4592</td>
      <td>Broken Horses</td>
      <td>2015.0</td>
      <td>Action|Crime|Drama|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>101.0</td>
      <td>2.35</td>
      <td>15000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>892.0</td>
      <td>355.0</td>
      <td>277.0</td>
      <td>2055</td>
      <td>0</td>
      <td>0.0</td>
      <td>1554</td>
      <td>20.0</td>
      <td>22.0</td>
      <td>5.7</td>
    </tr>
    <tr>
      <td>4593</td>
      <td>Brooklyn</td>
      <td>2015.0</td>
      <td>Drama|Romance</td>
      <td>English</td>
      <td>UK</td>
      <td>PG-13</td>
      <td>111.0</td>
      <td>1.85</td>
      <td>11000000.0</td>
      <td>38317535.0</td>
      <td>...</td>
      <td>838.0</td>
      <td>55.0</td>
      <td>54.0</td>
      <td>995</td>
      <td>36000</td>
      <td>1.0</td>
      <td>73249</td>
      <td>212.0</td>
      <td>351.0</td>
      <td>7.5</td>
    </tr>
    <tr>
      <td>4594</td>
      <td>Brotherly Love</td>
      <td>2015.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>89.0</td>
      <td>1.85</td>
      <td>1900000.0</td>
      <td>444044.0</td>
      <td>...</td>
      <td>628.0</td>
      <td>606.0</td>
      <td>585.0</td>
      <td>4249</td>
      <td>1000</td>
      <td>6.0</td>
      <td>744</td>
      <td>19.0</td>
      <td>10.0</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>4595</td>
      <td>Burnt</td>
      <td>2015.0</td>
      <td>Comedy|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>101.0</td>
      <td>2.35</td>
      <td>20000000.0</td>
      <td>13650738.0</td>
      <td>...</td>
      <td>14000.0</td>
      <td>1000.0</td>
      <td>580.0</td>
      <td>16926</td>
      <td>25000</td>
      <td>1.0</td>
      <td>61360</td>
      <td>129.0</td>
      <td>175.0</td>
      <td>6.6</td>
    </tr>
    <tr>
      <td>4596</td>
      <td>By the Sea</td>
      <td>2015.0</td>
      <td>Drama|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>122.0</td>
      <td>2.35</td>
      <td>10000000.0</td>
      <td>531009.0</td>
      <td>...</td>
      <td>11000.0</td>
      <td>11000.0</td>
      <td>188.0</td>
      <td>22319</td>
      <td>0</td>
      <td>0.0</td>
      <td>7976</td>
      <td>61.0</td>
      <td>131.0</td>
      <td>5.3</td>
    </tr>
    <tr>
      <td>4597</td>
      <td>Captive</td>
      <td>2015.0</td>
      <td>Crime|Drama|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>97.0</td>
      <td>1.85</td>
      <td>2000000.0</td>
      <td>2557668.0</td>
      <td>...</td>
      <td>1000.0</td>
      <td>426.0</td>
      <td>349.0</td>
      <td>2739</td>
      <td>0</td>
      <td>1.0</td>
      <td>3911</td>
      <td>22.0</td>
      <td>39.0</td>
      <td>5.3</td>
    </tr>
    <tr>
      <td>4598</td>
      <td>Censored Voices</td>
      <td>2015.0</td>
      <td>Documentary|History</td>
      <td>Hebrew</td>
      <td>Israel</td>
      <td>NaN</td>
      <td>84.0</td>
      <td>1.78</td>
      <td>450000.0</td>
      <td>34151.0</td>
      <td>...</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3</td>
      <td>111</td>
      <td>0.0</td>
      <td>186</td>
      <td>3.0</td>
      <td>23.0</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>4599</td>
      <td>Chain of Command</td>
      <td>2015.0</td>
      <td>Action|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>88.0</td>
      <td>1.33</td>
      <td>5000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>2000.0</td>
      <td>872.0</td>
      <td>6.0</td>
      <td>2886</td>
      <td>358</td>
      <td>3.0</td>
      <td>801</td>
      <td>14.0</td>
      <td>11.0</td>
      <td>3.5</td>
    </tr>
  </tbody>
</table>
<p>60 rows × 25 columns</p>
</div>



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Year</th>
      <th>Genres</th>
      <th>Language</th>
      <th>Country</th>
      <th>Content Rating</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>...</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>4780</td>
      <td>Walter</td>
      <td>2015.0</td>
      <td>Comedy|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>94.0</td>
      <td>NaN</td>
      <td>700000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>956.0</td>
      <td>945.0</td>
      <td>912.0</td>
      <td>4767</td>
      <td>0</td>
      <td>2.0</td>
      <td>1432</td>
      <td>19.0</td>
      <td>10.0</td>
      <td>5.3</td>
    </tr>
    <tr>
      <td>4781</td>
      <td>We Are Your Friends</td>
      <td>2015.0</td>
      <td>Drama|Music|Romance</td>
      <td>English</td>
      <td>UK</td>
      <td>R</td>
      <td>96.0</td>
      <td>1.85</td>
      <td>2000000.0</td>
      <td>3590010.0</td>
      <td>...</td>
      <td>804.0</td>
      <td>625.0</td>
      <td>328.0</td>
      <td>3013</td>
      <td>0</td>
      <td>0.0</td>
      <td>20885</td>
      <td>60.0</td>
      <td>158.0</td>
      <td>6.1</td>
    </tr>
    <tr>
      <td>4782</td>
      <td>Western Religion</td>
      <td>2015.0</td>
      <td>Adventure|Drama|Fantasy|Thriller|Western</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>105.0</td>
      <td>NaN</td>
      <td>250000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>814.0</td>
      <td>755.0</td>
      <td>494.0</td>
      <td>2970</td>
      <td>244</td>
      <td>0.0</td>
      <td>146</td>
      <td>4.0</td>
      <td>5.0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <td>4783</td>
      <td>Wild Card</td>
      <td>2015.0</td>
      <td>Action|Crime|Drama|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>92.0</td>
      <td>2.35</td>
      <td>30000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>26000.0</td>
      <td>947.0</td>
      <td>700.0</td>
      <td>29773</td>
      <td>0</td>
      <td>0.0</td>
      <td>36487</td>
      <td>114.0</td>
      <td>130.0</td>
      <td>5.6</td>
    </tr>
    <tr>
      <td>4784</td>
      <td>Wind Walkers</td>
      <td>2015.0</td>
      <td>Action|Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>93.0</td>
      <td>NaN</td>
      <td>2000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>708.0</td>
      <td>571.0</td>
      <td>485.0</td>
      <td>2870</td>
      <td>135</td>
      <td>NaN</td>
      <td>133</td>
      <td>2.0</td>
      <td>27.0</td>
      <td>3.6</td>
    </tr>
    <tr>
      <td>4785</td>
      <td>Windsor Drive</td>
      <td>2015.0</td>
      <td>Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>90.0</td>
      <td>NaN</td>
      <td>100000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>806.0</td>
      <td>487.0</td>
      <td>3336</td>
      <td>312</td>
      <td>1.0</td>
      <td>169</td>
      <td>6.0</td>
      <td>7.0</td>
      <td>3.2</td>
    </tr>
    <tr>
      <td>4786</td>
      <td>Woman in Gold</td>
      <td>2015.0</td>
      <td>Biography|Drama|History</td>
      <td>English</td>
      <td>UK</td>
      <td>PG-13</td>
      <td>109.0</td>
      <td>2.35</td>
      <td>11000000.0</td>
      <td>33305037.0</td>
      <td>...</td>
      <td>16000.0</td>
      <td>638.0</td>
      <td>553.0</td>
      <td>17866</td>
      <td>34000</td>
      <td>2.0</td>
      <td>33856</td>
      <td>147.0</td>
      <td>203.0</td>
      <td>7.3</td>
    </tr>
    <tr>
      <td>4787</td>
      <td>Zipper</td>
      <td>2015.0</td>
      <td>Drama|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>103.0</td>
      <td>2.35</td>
      <td>4500000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>1000.0</td>
      <td>842.0</td>
      <td>3408</td>
      <td>987</td>
      <td>0.0</td>
      <td>4091</td>
      <td>20.0</td>
      <td>35.0</td>
      <td>5.7</td>
    </tr>
    <tr>
      <td>4788</td>
      <td>10 Cloverfield Lane</td>
      <td>2016.0</td>
      <td>Drama|Horror|Mystery|Sci-Fi|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>104.0</td>
      <td>2.35</td>
      <td>15000000.0</td>
      <td>71897215.0</td>
      <td>...</td>
      <td>14000.0</td>
      <td>338.0</td>
      <td>82.0</td>
      <td>14504</td>
      <td>33000</td>
      <td>0.0</td>
      <td>126893</td>
      <td>440.0</td>
      <td>411.0</td>
      <td>7.3</td>
    </tr>
    <tr>
      <td>4789</td>
      <td>13 Hours</td>
      <td>2016.0</td>
      <td>Action|Drama|Thriller|War</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>144.0</td>
      <td>2.35</td>
      <td>50000000.0</td>
      <td>52822418.0</td>
      <td>...</td>
      <td>769.0</td>
      <td>726.0</td>
      <td>681.0</td>
      <td>3580</td>
      <td>44000</td>
      <td>0.0</td>
      <td>47764</td>
      <td>219.0</td>
      <td>204.0</td>
      <td>7.4</td>
    </tr>
    <tr>
      <td>4790</td>
      <td>A Beginner's Guide to Snuff</td>
      <td>2016.0</td>
      <td>Comedy|Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>87.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>467.0</td>
      <td>258.0</td>
      <td>165.0</td>
      <td>1270</td>
      <td>8</td>
      <td>0.0</td>
      <td>13</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8.7</td>
    </tr>
    <tr>
      <td>4791</td>
      <td>Airlift</td>
      <td>2016.0</td>
      <td>Action|Drama|History|Thriller|War</td>
      <td>Hindi</td>
      <td>India</td>
      <td>NaN</td>
      <td>130.0</td>
      <td>2.35</td>
      <td>4400000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>85.0</td>
      <td>26.0</td>
      <td>12.0</td>
      <td>151</td>
      <td>10000</td>
      <td>1.0</td>
      <td>30977</td>
      <td>178.0</td>
      <td>39.0</td>
      <td>8.5</td>
    </tr>
    <tr>
      <td>4792</td>
      <td>Alice Through the Looking Glass</td>
      <td>2016.0</td>
      <td>Adventure|Family|Fantasy</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>113.0</td>
      <td>1.85</td>
      <td>170000000.0</td>
      <td>76846624.0</td>
      <td>...</td>
      <td>40000.0</td>
      <td>25000.0</td>
      <td>11000.0</td>
      <td>80806</td>
      <td>30000</td>
      <td>1.0</td>
      <td>21352</td>
      <td>131.0</td>
      <td>218.0</td>
      <td>6.4</td>
    </tr>
    <tr>
      <td>4793</td>
      <td>Allegiant</td>
      <td>2016.0</td>
      <td>Action|Adventure|Mystery|Sci-Fi|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>120.0</td>
      <td>2.35</td>
      <td>110000000.0</td>
      <td>66002193.0</td>
      <td>...</td>
      <td>6000.0</td>
      <td>5000.0</td>
      <td>943.0</td>
      <td>12452</td>
      <td>12000</td>
      <td>3.0</td>
      <td>44296</td>
      <td>144.0</td>
      <td>181.0</td>
      <td>5.8</td>
    </tr>
    <tr>
      <td>4794</td>
      <td>Alleluia! The Devil's Carnival</td>
      <td>2016.0</td>
      <td>Horror|Musical</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>97.0</td>
      <td>1.78</td>
      <td>500000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>636.0</td>
      <td>456.0</td>
      <td>303.0</td>
      <td>2438</td>
      <td>707</td>
      <td>5.0</td>
      <td>259</td>
      <td>20.0</td>
      <td>10.0</td>
      <td>7.4</td>
    </tr>
    <tr>
      <td>4795</td>
      <td>Antibirth</td>
      <td>2016.0</td>
      <td>Horror</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>94.0</td>
      <td>NaN</td>
      <td>3500000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>677.0</td>
      <td>442.0</td>
      <td>2406</td>
      <td>89</td>
      <td>1.0</td>
      <td>63</td>
      <td>2.0</td>
      <td>10.0</td>
      <td>6.3</td>
    </tr>
    <tr>
      <td>4796</td>
      <td>Bad Moms</td>
      <td>2016.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>100.0</td>
      <td>NaN</td>
      <td>20000000.0</td>
      <td>55461307.0</td>
      <td>...</td>
      <td>15000.0</td>
      <td>1000.0</td>
      <td>851.0</td>
      <td>18786</td>
      <td>18000</td>
      <td>9.0</td>
      <td>4654</td>
      <td>46.0</td>
      <td>81.0</td>
      <td>6.7</td>
    </tr>
    <tr>
      <td>4797</td>
      <td>Batman v Superman: Dawn of Justice</td>
      <td>2016.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>183.0</td>
      <td>2.35</td>
      <td>250000000.0</td>
      <td>330249062.0</td>
      <td>...</td>
      <td>15000.0</td>
      <td>4000.0</td>
      <td>2000.0</td>
      <td>24450</td>
      <td>197000</td>
      <td>0.0</td>
      <td>371639</td>
      <td>3018.0</td>
      <td>673.0</td>
      <td>6.9</td>
    </tr>
    <tr>
      <td>4798</td>
      <td>Ben-Hur</td>
      <td>2016.0</td>
      <td>Adventure|Drama|History</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>141.0</td>
      <td>2.35</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>11000.0</td>
      <td>745.0</td>
      <td>635.0</td>
      <td>13379</td>
      <td>0</td>
      <td>2.0</td>
      <td>57</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>6.1</td>
    </tr>
    <tr>
      <td>4799</td>
      <td>Ben-Hur</td>
      <td>2016.0</td>
      <td>Adventure|Drama|History</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>141.0</td>
      <td>2.35</td>
      <td>100000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>11000.0</td>
      <td>744.0</td>
      <td>635.0</td>
      <td>13390</td>
      <td>0</td>
      <td>2.0</td>
      <td>62</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>6.1</td>
    </tr>
    <tr>
      <td>4800</td>
      <td>Ben-Hur</td>
      <td>2016.0</td>
      <td>Adventure|Drama|History</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>141.0</td>
      <td>2.35</td>
      <td>100000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>11000.0</td>
      <td>744.0</td>
      <td>635.0</td>
      <td>13391</td>
      <td>0</td>
      <td>2.0</td>
      <td>67</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>6.0</td>
    </tr>
  </tbody>
</table>
<p>21 rows × 25 columns</p>
</div>



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Year</th>
      <th>Genres</th>
      <th>Language</th>
      <th>Country</th>
      <th>Content Rating</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>...</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>4840</td>
      <td>Money Monster</td>
      <td>2016.0</td>
      <td>Crime|Drama|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>98.0</td>
      <td>2.35</td>
      <td>27000000.0</td>
      <td>41008532.0</td>
      <td>...</td>
      <td>8000.0</td>
      <td>698.0</td>
      <td>638.0</td>
      <td>10894</td>
      <td>0</td>
      <td>1.0</td>
      <td>19611</td>
      <td>103.0</td>
      <td>268.0</td>
      <td>6.7</td>
    </tr>
    <tr>
      <td>4841</td>
      <td>Mr. Church</td>
      <td>2016.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>104.0</td>
      <td>2.35</td>
      <td>8000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>502.0</td>
      <td>206.0</td>
      <td>189.0</td>
      <td>1546</td>
      <td>205</td>
      <td>0.0</td>
      <td>63</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <td>4842</td>
      <td>My Big Fat Greek Wedding 2</td>
      <td>2016.0</td>
      <td>Comedy|Family|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>94.0</td>
      <td>2.35</td>
      <td>18000000.0</td>
      <td>59573085.0</td>
      <td>...</td>
      <td>567.0</td>
      <td>312.0</td>
      <td>261.0</td>
      <td>2259</td>
      <td>19000</td>
      <td>10.0</td>
      <td>13562</td>
      <td>103.0</td>
      <td>156.0</td>
      <td>6.1</td>
    </tr>
    <tr>
      <td>4843</td>
      <td>Neighbors 2: Sorority Rising</td>
      <td>2016.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>92.0</td>
      <td>2.35</td>
      <td>35000000.0</td>
      <td>55291815.0</td>
      <td>...</td>
      <td>17000.0</td>
      <td>329.0</td>
      <td>190.0</td>
      <td>17860</td>
      <td>0</td>
      <td>0.0</td>
      <td>28041</td>
      <td>111.0</td>
      <td>177.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <td>4844</td>
      <td>Nerve</td>
      <td>2016.0</td>
      <td>Adventure|Crime|Mystery|Sci-Fi|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>96.0</td>
      <td>NaN</td>
      <td>20000000.0</td>
      <td>28876924.0</td>
      <td>...</td>
      <td>646.0</td>
      <td>441.0</td>
      <td>374.0</td>
      <td>1780</td>
      <td>0</td>
      <td>0.0</td>
      <td>4303</td>
      <td>35.0</td>
      <td>86.0</td>
      <td>7.1</td>
    </tr>
    <tr>
      <td>4845</td>
      <td>Now You See Me 2</td>
      <td>2016.0</td>
      <td>Action|Adventure|Comedy|Crime|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>129.0</td>
      <td>2.35</td>
      <td>90000000.0</td>
      <td>64685359.0</td>
      <td>...</td>
      <td>11000.0</td>
      <td>11000.0</td>
      <td>886.0</td>
      <td>23031</td>
      <td>15000</td>
      <td>6.0</td>
      <td>40862</td>
      <td>139.0</td>
      <td>196.0</td>
      <td>6.9</td>
    </tr>
    <tr>
      <td>4846</td>
      <td>Operation Chromite</td>
      <td>2016.0</td>
      <td>Action|Drama|History|War</td>
      <td>English</td>
      <td>South Korea</td>
      <td>NaN</td>
      <td>115.0</td>
      <td>NaN</td>
      <td>12620000.0</td>
      <td>31662.0</td>
      <td>...</td>
      <td>14000.0</td>
      <td>81.0</td>
      <td>29.0</td>
      <td>14133</td>
      <td>139</td>
      <td>1.0</td>
      <td>90</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>6.8</td>
    </tr>
    <tr>
      <td>4847</td>
      <td>Our Kind of Traitor</td>
      <td>2016.0</td>
      <td>Thriller</td>
      <td>English</td>
      <td>UK</td>
      <td>R</td>
      <td>108.0</td>
      <td>2.35</td>
      <td>NaN</td>
      <td>3108216.0</td>
      <td>...</td>
      <td>150.0</td>
      <td>104.0</td>
      <td>100.0</td>
      <td>540</td>
      <td>0</td>
      <td>2.0</td>
      <td>2587</td>
      <td>21.0</td>
      <td>134.0</td>
      <td>6.4</td>
    </tr>
    <tr>
      <td>4848</td>
      <td>Pete's Dragon</td>
      <td>2016.0</td>
      <td>Adventure|Family|Fantasy</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>102.0</td>
      <td>2.35</td>
      <td>65000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>3000.0</td>
      <td>424.0</td>
      <td>190.0</td>
      <td>3691</td>
      <td>21000</td>
      <td>0.0</td>
      <td>408</td>
      <td>6.0</td>
      <td>78.0</td>
      <td>7.3</td>
    </tr>
    <tr>
      <td>4849</td>
      <td>Pride and Prejudice and Zombies</td>
      <td>2016.0</td>
      <td>Action|Horror|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>108.0</td>
      <td>2.35</td>
      <td>28000000.0</td>
      <td>10907291.0</td>
      <td>...</td>
      <td>2000.0</td>
      <td>860.0</td>
      <td>845.0</td>
      <td>4710</td>
      <td>73000</td>
      <td>0.0</td>
      <td>23775</td>
      <td>134.0</td>
      <td>225.0</td>
      <td>5.8</td>
    </tr>
    <tr>
      <td>4850</td>
      <td>Race</td>
      <td>2016.0</td>
      <td>Biography|Drama|Sport</td>
      <td>English</td>
      <td>Canada</td>
      <td>PG-13</td>
      <td>134.0</td>
      <td>2.35</td>
      <td>NaN</td>
      <td>19097994.0</td>
      <td>...</td>
      <td>882.0</td>
      <td>845.0</td>
      <td>388.0</td>
      <td>2410</td>
      <td>0</td>
      <td>0.0</td>
      <td>11744</td>
      <td>49.0</td>
      <td>125.0</td>
      <td>7.1</td>
    </tr>
    <tr>
      <td>4851</td>
      <td>Restoration</td>
      <td>2016.0</td>
      <td>Horror</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>92.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>662.0</td>
      <td>290.0</td>
      <td>161.0</td>
      <td>1498</td>
      <td>378</td>
      <td>0.0</td>
      <td>436</td>
      <td>6.0</td>
      <td>15.0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <td>4852</td>
      <td>Ride Along 2</td>
      <td>2016.0</td>
      <td>Action|Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>102.0</td>
      <td>2.35</td>
      <td>40000000.0</td>
      <td>90835030.0</td>
      <td>...</td>
      <td>2000.0</td>
      <td>874.0</td>
      <td>655.0</td>
      <td>5178</td>
      <td>0</td>
      <td>0.0</td>
      <td>28621</td>
      <td>58.0</td>
      <td>119.0</td>
      <td>5.9</td>
    </tr>
    <tr>
      <td>4853</td>
      <td>Risen</td>
      <td>2016.0</td>
      <td>Action|Adventure|Drama|Mystery</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>107.0</td>
      <td>2.35</td>
      <td>20000000.0</td>
      <td>36874745.0</td>
      <td>...</td>
      <td>141.0</td>
      <td>76.0</td>
      <td>47.0</td>
      <td>389</td>
      <td>21000</td>
      <td>2.0</td>
      <td>12276</td>
      <td>117.0</td>
      <td>122.0</td>
      <td>6.3</td>
    </tr>
    <tr>
      <td>4854</td>
      <td>Rodeo Girl</td>
      <td>2016.0</td>
      <td>Family</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>108.0</td>
      <td>NaN</td>
      <td>500000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>466.0</td>
      <td>431.0</td>
      <td>317.0</td>
      <td>1628</td>
      <td>0</td>
      <td>2.0</td>
      <td>62</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>5.7</td>
    </tr>
    <tr>
      <td>4855</td>
      <td>Sausage Party</td>
      <td>2016.0</td>
      <td>Adventure|Animation|Comedy|Fantasy</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>89.0</td>
      <td>1.85</td>
      <td>19000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>11000.0</td>
      <td>4000.0</td>
      <td>365.0</td>
      <td>15795</td>
      <td>13000</td>
      <td>0.0</td>
      <td>3302</td>
      <td>14.0</td>
      <td>65.0</td>
      <td>7.5</td>
    </tr>
    <tr>
      <td>4856</td>
      <td>Star Trek Beyond</td>
      <td>2016.0</td>
      <td>Action|Adventure|Sci-Fi|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>122.0</td>
      <td>2.35</td>
      <td>185000000.0</td>
      <td>130468626.0</td>
      <td>...</td>
      <td>998.0</td>
      <td>119.0</td>
      <td>105.0</td>
      <td>1327</td>
      <td>30000</td>
      <td>4.0</td>
      <td>53607</td>
      <td>432.0</td>
      <td>322.0</td>
      <td>7.5</td>
    </tr>
    <tr>
      <td>4857</td>
      <td>Suicide Squad</td>
      <td>2016.0</td>
      <td>Action|Adventure|Comedy|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>123.0</td>
      <td>2.35</td>
      <td>175000000.0</td>
      <td>161087183.0</td>
      <td>...</td>
      <td>10000.0</td>
      <td>336.0</td>
      <td>329.0</td>
      <td>11287</td>
      <td>80000</td>
      <td>8.0</td>
      <td>118992</td>
      <td>971.0</td>
      <td>418.0</td>
      <td>6.9</td>
    </tr>
    <tr>
      <td>4858</td>
      <td>Teenage Mutant Ninja Turtles: Out of the Shadows</td>
      <td>2016.0</td>
      <td>Action|Adventure|Comedy|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>112.0</td>
      <td>2.35</td>
      <td>135000000.0</td>
      <td>81638674.0</td>
      <td>...</td>
      <td>5000.0</td>
      <td>833.0</td>
      <td>799.0</td>
      <td>8306</td>
      <td>12000</td>
      <td>NaN</td>
      <td>17533</td>
      <td>115.0</td>
      <td>181.0</td>
      <td>6.3</td>
    </tr>
    <tr>
      <td>4859</td>
      <td>The 5th Wave</td>
      <td>2016.0</td>
      <td>Action|Adventure|Sci-Fi|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>112.0</td>
      <td>2.35</td>
      <td>38000000.0</td>
      <td>34912982.0</td>
      <td>...</td>
      <td>17000.0</td>
      <td>1000.0</td>
      <td>724.0</td>
      <td>19974</td>
      <td>14000</td>
      <td>0.0</td>
      <td>55617</td>
      <td>266.0</td>
      <td>194.0</td>
      <td>5.2</td>
    </tr>
    <tr>
      <td>4860</td>
      <td>The Angry Birds Movie</td>
      <td>2016.0</td>
      <td>Action|Animation|Comedy|Family</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>97.0</td>
      <td>1.85</td>
      <td>73000000.0</td>
      <td>107225164.0</td>
      <td>...</td>
      <td>22000.0</td>
      <td>1000.0</td>
      <td>415.0</td>
      <td>24350</td>
      <td>14000</td>
      <td>0.0</td>
      <td>27130</td>
      <td>126.0</td>
      <td>141.0</td>
      <td>6.3</td>
    </tr>
    <tr>
      <td>4861</td>
      <td>The BFG</td>
      <td>2016.0</td>
      <td>Adventure|Family|Fantasy</td>
      <td>English</td>
      <td>UK</td>
      <td>PG</td>
      <td>117.0</td>
      <td>2.35</td>
      <td>140000000.0</td>
      <td>52792307.0</td>
      <td>...</td>
      <td>535.0</td>
      <td>400.0</td>
      <td>358.0</td>
      <td>1950</td>
      <td>27000</td>
      <td>0.0</td>
      <td>12572</td>
      <td>106.0</td>
      <td>252.0</td>
      <td>6.8</td>
    </tr>
    <tr>
      <td>4862</td>
      <td>The Birth of a Nation</td>
      <td>2016.0</td>
      <td>Biography|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>120.0</td>
      <td>2.35</td>
      <td>10000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>990.0</td>
      <td>664.0</td>
      <td>400.0</td>
      <td>3525</td>
      <td>0</td>
      <td>1.0</td>
      <td>1197</td>
      <td>8.0</td>
      <td>21.0</td>
      <td>5.4</td>
    </tr>
    <tr>
      <td>4863</td>
      <td>The Boss</td>
      <td>2016.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>99.0</td>
      <td>1.85</td>
      <td>29000000.0</td>
      <td>63034755.0</td>
      <td>...</td>
      <td>22000.0</td>
      <td>779.0</td>
      <td>265.0</td>
      <td>23562</td>
      <td>0</td>
      <td>1.0</td>
      <td>16984</td>
      <td>96.0</td>
      <td>154.0</td>
      <td>5.3</td>
    </tr>
    <tr>
      <td>4864</td>
      <td>The Boy</td>
      <td>2016.0</td>
      <td>Horror|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>97.0</td>
      <td>2.35</td>
      <td>10000000.0</td>
      <td>35794166.0</td>
      <td>...</td>
      <td>4000.0</td>
      <td>334.0</td>
      <td>130.0</td>
      <td>4687</td>
      <td>20000</td>
      <td>0.0</td>
      <td>35654</td>
      <td>155.0</td>
      <td>159.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <td>4865</td>
      <td>The Conjuring 2</td>
      <td>2016.0</td>
      <td>Horror|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>134.0</td>
      <td>2.35</td>
      <td>40000000.0</td>
      <td>102310175.0</td>
      <td>...</td>
      <td>1000.0</td>
      <td>575.0</td>
      <td>336.0</td>
      <td>2676</td>
      <td>40000</td>
      <td>0.0</td>
      <td>64989</td>
      <td>279.0</td>
      <td>300.0</td>
      <td>7.8</td>
    </tr>
    <tr>
      <td>4866</td>
      <td>The Dog Lover</td>
      <td>2016.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>101.0</td>
      <td>2.35</td>
      <td>2000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>301.0</td>
      <td>256.0</td>
      <td>2419</td>
      <td>724</td>
      <td>NaN</td>
      <td>162</td>
      <td>8.0</td>
      <td>9.0</td>
      <td>4.8</td>
    </tr>
    <tr>
      <td>4867</td>
      <td>The Finest Hours</td>
      <td>2016.0</td>
      <td>Action|Drama|History|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>117.0</td>
      <td>2.35</td>
      <td>NaN</td>
      <td>27550735.0</td>
      <td>...</td>
      <td>788.0</td>
      <td>562.0</td>
      <td>531.0</td>
      <td>3524</td>
      <td>12000</td>
      <td>0.0</td>
      <td>27481</td>
      <td>113.0</td>
      <td>178.0</td>
      <td>6.8</td>
    </tr>
    <tr>
      <td>4868</td>
      <td>The Forest</td>
      <td>2016.0</td>
      <td>Horror|Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>93.0</td>
      <td>1.85</td>
      <td>10000000.0</td>
      <td>26583369.0</td>
      <td>...</td>
      <td>533.0</td>
      <td>35.0</td>
      <td>4.0</td>
      <td>578</td>
      <td>10000</td>
      <td>1.0</td>
      <td>20837</td>
      <td>127.0</td>
      <td>185.0</td>
      <td>4.8</td>
    </tr>
    <tr>
      <td>4869</td>
      <td>The Huntsman: Winter's War</td>
      <td>2016.0</td>
      <td>Action|Adventure|Drama|Fantasy</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>120.0</td>
      <td>2.35</td>
      <td>115000000.0</td>
      <td>47952020.0</td>
      <td>...</td>
      <td>26000.0</td>
      <td>11000.0</td>
      <td>9000.0</td>
      <td>46719</td>
      <td>16000</td>
      <td>2.0</td>
      <td>37750</td>
      <td>134.0</td>
      <td>231.0</td>
      <td>6.1</td>
    </tr>
    <tr>
      <td>4870</td>
      <td>The Infiltrator</td>
      <td>2016.0</td>
      <td>Biography|Crime|Drama|Thriller</td>
      <td>English</td>
      <td>UK</td>
      <td>R</td>
      <td>127.0</td>
      <td>2.35</td>
      <td>25000000.0</td>
      <td>14946229.0</td>
      <td>...</td>
      <td>788.0</td>
      <td>423.0</td>
      <td>345.0</td>
      <td>2104</td>
      <td>0</td>
      <td>1.0</td>
      <td>2581</td>
      <td>29.0</td>
      <td>72.0</td>
      <td>7.3</td>
    </tr>
    <tr>
      <td>4871</td>
      <td>The Jungle Book</td>
      <td>2016.0</td>
      <td>Adventure|Drama|Family|Fantasy</td>
      <td>English</td>
      <td>UK</td>
      <td>PG</td>
      <td>106.0</td>
      <td>1.85</td>
      <td>175000000.0</td>
      <td>362645141.0</td>
      <td>...</td>
      <td>19000.0</td>
      <td>13000.0</td>
      <td>591.0</td>
      <td>32921</td>
      <td>65000</td>
      <td>0.0</td>
      <td>106072</td>
      <td>398.0</td>
      <td>370.0</td>
      <td>7.8</td>
    </tr>
    <tr>
      <td>4872</td>
      <td>The Jungle Book</td>
      <td>2016.0</td>
      <td>Adventure|Drama|Family|Fantasy</td>
      <td>English</td>
      <td>UK</td>
      <td>PG</td>
      <td>106.0</td>
      <td>1.85</td>
      <td>175000000.0</td>
      <td>362645141.0</td>
      <td>...</td>
      <td>19000.0</td>
      <td>13000.0</td>
      <td>591.0</td>
      <td>32921</td>
      <td>65000</td>
      <td>0.0</td>
      <td>106221</td>
      <td>398.0</td>
      <td>370.0</td>
      <td>7.8</td>
    </tr>
    <tr>
      <td>4873</td>
      <td>The Legend of Tarzan</td>
      <td>2016.0</td>
      <td>Action|Adventure|Drama|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>110.0</td>
      <td>2.35</td>
      <td>180000000.0</td>
      <td>124051759.0</td>
      <td>...</td>
      <td>11000.0</td>
      <td>10000.0</td>
      <td>103.0</td>
      <td>21175</td>
      <td>29000</td>
      <td>2.0</td>
      <td>42372</td>
      <td>239.0</td>
      <td>248.0</td>
      <td>6.6</td>
    </tr>
    <tr>
      <td>4874</td>
      <td>The Little Ponderosa Zoo</td>
      <td>2016.0</td>
      <td>Family</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>84.0</td>
      <td>16.00</td>
      <td>500000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>385.0</td>
      <td>169.0</td>
      <td>53.0</td>
      <td>683</td>
      <td>9</td>
      <td>2.0</td>
      <td>15</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>5.2</td>
    </tr>
    <tr>
      <td>4875</td>
      <td>The Masked Saint</td>
      <td>2016.0</td>
      <td>Action|Biography|Crime|Drama|Family|Fantasy</td>
      <td>English</td>
      <td>Canada</td>
      <td>PG-13</td>
      <td>105.0</td>
      <td>1.85</td>
      <td>3500000.0</td>
      <td>123777.0</td>
      <td>...</td>
      <td>426.0</td>
      <td>294.0</td>
      <td>131.0</td>
      <td>1043</td>
      <td>0</td>
      <td>0.0</td>
      <td>342</td>
      <td>15.0</td>
      <td>9.0</td>
      <td>4.7</td>
    </tr>
    <tr>
      <td>4876</td>
      <td>The Neon Demon</td>
      <td>2016.0</td>
      <td>Horror|Thriller</td>
      <td>English</td>
      <td>France</td>
      <td>R</td>
      <td>118.0</td>
      <td>2.35</td>
      <td>7000000.0</td>
      <td>1330827.0</td>
      <td>...</td>
      <td>18000.0</td>
      <td>860.0</td>
      <td>500.0</td>
      <td>19879</td>
      <td>0</td>
      <td>2.0</td>
      <td>9866</td>
      <td>73.0</td>
      <td>253.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <td>4877</td>
      <td>The Perfect Match</td>
      <td>2016.0</td>
      <td>Comedy|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>96.0</td>
      <td>NaN</td>
      <td>5000000.0</td>
      <td>9658370.0</td>
      <td>...</td>
      <td>927.0</td>
      <td>509.0</td>
      <td>503.0</td>
      <td>3552</td>
      <td>740</td>
      <td>6.0</td>
      <td>1180</td>
      <td>9.0</td>
      <td>12.0</td>
      <td>4.5</td>
    </tr>
    <tr>
      <td>4878</td>
      <td>The Purge: Election Year</td>
      <td>2016.0</td>
      <td>Action|Horror|Sci-Fi|Thriller</td>
      <td>English</td>
      <td>France</td>
      <td>R</td>
      <td>109.0</td>
      <td>2.35</td>
      <td>10000000.0</td>
      <td>78845130.0</td>
      <td>...</td>
      <td>798.0</td>
      <td>465.0</td>
      <td>393.0</td>
      <td>2480</td>
      <td>0</td>
      <td>1.0</td>
      <td>17596</td>
      <td>94.0</td>
      <td>165.0</td>
      <td>6.1</td>
    </tr>
    <tr>
      <td>4879</td>
      <td>The Secret Life of Pets</td>
      <td>2016.0</td>
      <td>Animation|Comedy|Family</td>
      <td>English</td>
      <td>Japan</td>
      <td>PG</td>
      <td>87.0</td>
      <td>1.85</td>
      <td>75000000.0</td>
      <td>323505540.0</td>
      <td>...</td>
      <td>1000.0</td>
      <td>904.0</td>
      <td>745.0</td>
      <td>4782</td>
      <td>36000</td>
      <td>0.0</td>
      <td>24407</td>
      <td>155.0</td>
      <td>165.0</td>
      <td>6.8</td>
    </tr>
    <tr>
      <td>4880</td>
      <td>The Shallows</td>
      <td>2016.0</td>
      <td>Drama|Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>86.0</td>
      <td>2.35</td>
      <td>17000000.0</td>
      <td>54257433.0</td>
      <td>...</td>
      <td>619.0</td>
      <td>350.0</td>
      <td>2.0</td>
      <td>971</td>
      <td>0</td>
      <td>0.0</td>
      <td>12983</td>
      <td>139.0</td>
      <td>186.0</td>
      <td>6.8</td>
    </tr>
    <tr>
      <td>4881</td>
      <td>The Veil</td>
      <td>2016.0</td>
      <td>Horror</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>93.0</td>
      <td>2.35</td>
      <td>4000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>763.0</td>
      <td>637.0</td>
      <td>359.0</td>
      <td>2651</td>
      <td>0</td>
      <td>2.0</td>
      <td>4146</td>
      <td>29.0</td>
      <td>39.0</td>
      <td>4.7</td>
    </tr>
    <tr>
      <td>4882</td>
      <td>The Wailing</td>
      <td>2016.0</td>
      <td>Fantasy|Horror|Mystery|Thriller</td>
      <td>Korean</td>
      <td>South Korea</td>
      <td>Not Rated</td>
      <td>156.0</td>
      <td>2.35</td>
      <td>NaN</td>
      <td>770629.0</td>
      <td>...</td>
      <td>45.0</td>
      <td>5.0</td>
      <td>0.0</td>
      <td>50</td>
      <td>0</td>
      <td>0.0</td>
      <td>2379</td>
      <td>24.0</td>
      <td>77.0</td>
      <td>7.7</td>
    </tr>
    <tr>
      <td>4883</td>
      <td>The Young Messiah</td>
      <td>2016.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>111.0</td>
      <td>2.35</td>
      <td>18500000.0</td>
      <td>6462576.0</td>
      <td>...</td>
      <td>241.0</td>
      <td>118.0</td>
      <td>107.0</td>
      <td>824</td>
      <td>0</td>
      <td>0.0</td>
      <td>1449</td>
      <td>30.0</td>
      <td>24.0</td>
      <td>5.4</td>
    </tr>
    <tr>
      <td>4884</td>
      <td>Triple 9</td>
      <td>2016.0</td>
      <td>Action|Crime|Drama|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>115.0</td>
      <td>2.35</td>
      <td>20000000.0</td>
      <td>12626905.0</td>
      <td>...</td>
      <td>14000.0</td>
      <td>12000.0</td>
      <td>968.0</td>
      <td>27214</td>
      <td>0</td>
      <td>3.0</td>
      <td>32567</td>
      <td>106.0</td>
      <td>214.0</td>
      <td>6.3</td>
    </tr>
    <tr>
      <td>4885</td>
      <td>Two Lovers and a Bear</td>
      <td>2016.0</td>
      <td>Drama|Romance</td>
      <td>English</td>
      <td>Canada</td>
      <td>NaN</td>
      <td>96.0</td>
      <td>2.35</td>
      <td>8700000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>149.0</td>
      <td>147.0</td>
      <td>63.0</td>
      <td>414</td>
      <td>187</td>
      <td>0.0</td>
      <td>33</td>
      <td>6.0</td>
      <td>6.0</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>4886</td>
      <td>Warcraft</td>
      <td>2016.0</td>
      <td>Action|Adventure|Fantasy</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>123.0</td>
      <td>2.35</td>
      <td>160000000.0</td>
      <td>46978995.0</td>
      <td>...</td>
      <td>3000.0</td>
      <td>716.0</td>
      <td>648.0</td>
      <td>5505</td>
      <td>89000</td>
      <td>0.0</td>
      <td>111609</td>
      <td>781.0</td>
      <td>275.0</td>
      <td>7.3</td>
    </tr>
    <tr>
      <td>4887</td>
      <td>Xi you ji zhi: Sun Wukong san da Baigu Jing</td>
      <td>2016.0</td>
      <td>Action|Adventure|Fantasy</td>
      <td>English</td>
      <td>China</td>
      <td>NaN</td>
      <td>119.0</td>
      <td>2.35</td>
      <td>68005000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>879.0</td>
      <td>107.0</td>
      <td>22.0</td>
      <td>1026</td>
      <td>426</td>
      <td>1.0</td>
      <td>1212</td>
      <td>9.0</td>
      <td>14.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <td>4888</td>
      <td>X-Men: Apocalypse</td>
      <td>2016.0</td>
      <td>Action|Adventure|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>144.0</td>
      <td>2.35</td>
      <td>178000000.0</td>
      <td>154985087.0</td>
      <td>...</td>
      <td>34000.0</td>
      <td>13000.0</td>
      <td>1000.0</td>
      <td>49684</td>
      <td>54000</td>
      <td>6.0</td>
      <td>148379</td>
      <td>622.0</td>
      <td>396.0</td>
      <td>7.3</td>
    </tr>
    <tr>
      <td>4889</td>
      <td>Yoga Hosers</td>
      <td>2016.0</td>
      <td>Comedy|Fantasy|Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>88.0</td>
      <td>NaN</td>
      <td>5000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>40000.0</td>
      <td>3000.0</td>
      <td>1000.0</td>
      <td>46115</td>
      <td>0</td>
      <td>7.0</td>
      <td>849</td>
      <td>4.0</td>
      <td>35.0</td>
      <td>4.8</td>
    </tr>
    <tr>
      <td>4890</td>
      <td>Zoolander 2</td>
      <td>2016.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>102.0</td>
      <td>2.35</td>
      <td>50000000.0</td>
      <td>28837115.0</td>
      <td>...</td>
      <td>14000.0</td>
      <td>8000.0</td>
      <td>1000.0</td>
      <td>24107</td>
      <td>28000</td>
      <td>4.0</td>
      <td>34964</td>
      <td>150.0</td>
      <td>226.0</td>
      <td>4.8</td>
    </tr>
    <tr>
      <td>4891</td>
      <td>10,000 B.C.</td>
      <td>NaN</td>
      <td>Comedy</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>22.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5</td>
      <td>0</td>
      <td>0.0</td>
      <td>6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>4892</td>
      <td>12 Monkeys</td>
      <td>NaN</td>
      <td>Adventure|Drama|Mystery|Sci-Fi|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>TV-14</td>
      <td>42.0</td>
      <td>16.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>757.0</td>
      <td>641.0</td>
      <td>442.0</td>
      <td>3309</td>
      <td>12000</td>
      <td>0.0</td>
      <td>20839</td>
      <td>56.0</td>
      <td>13.0</td>
      <td>7.6</td>
    </tr>
    <tr>
      <td>4893</td>
      <td>3rd Rock from the Sun</td>
      <td>NaN</td>
      <td>Comedy|Family|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>TV-PG</td>
      <td>60.0</td>
      <td>1.33</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>23000.0</td>
      <td>967.0</td>
      <td>501.0</td>
      <td>25160</td>
      <td>0</td>
      <td>4.0</td>
      <td>38383</td>
      <td>86.0</td>
      <td>22.0</td>
      <td>7.8</td>
    </tr>
    <tr>
      <td>4894</td>
      <td>A Touch of Frost</td>
      <td>NaN</td>
      <td>Crime|Drama|Mystery</td>
      <td>English</td>
      <td>UK</td>
      <td>NaN</td>
      <td>105.0</td>
      <td>1.33</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>325.0</td>
      <td>7.0</td>
      <td>5.0</td>
      <td>344</td>
      <td>361</td>
      <td>1.0</td>
      <td>4438</td>
      <td>33.0</td>
      <td>14.0</td>
      <td>7.8</td>
    </tr>
    <tr>
      <td>4895</td>
      <td>Anger Management</td>
      <td>NaN</td>
      <td>Comedy|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>22.0</td>
      <td>16.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>883.0</td>
      <td>701.0</td>
      <td>676.0</td>
      <td>4115</td>
      <td>0</td>
      <td>1.0</td>
      <td>26992</td>
      <td>54.0</td>
      <td>26.0</td>
      <td>6.7</td>
    </tr>
    <tr>
      <td>4896</td>
      <td>Animal Kingdom</td>
      <td>NaN</td>
      <td>Crime|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>60.0</td>
      <td>16.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>557.0</td>
      <td>551.0</td>
      <td>3026</td>
      <td>0</td>
      <td>0.0</td>
      <td>3673</td>
      <td>23.0</td>
      <td>8.0</td>
      <td>8.1</td>
    </tr>
    <tr>
      <td>4897</td>
      <td>Anne of Green Gables</td>
      <td>NaN</td>
      <td>Drama|Family</td>
      <td>English</td>
      <td>Canada</td>
      <td>TV-G</td>
      <td>199.0</td>
      <td>1.33</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>662.0</td>
      <td>517.0</td>
      <td>505.0</td>
      <td>2667</td>
      <td>0</td>
      <td>0.0</td>
      <td>14251</td>
      <td>74.0</td>
      <td>2.0</td>
      <td>8.4</td>
    </tr>
    <tr>
      <td>4898</td>
      <td>Arthur</td>
      <td>NaN</td>
      <td>Animation|Comedy|Family</td>
      <td>English</td>
      <td>Canada</td>
      <td>TV-Y</td>
      <td>30.0</td>
      <td>1.33</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>51.0</td>
      <td>21.0</td>
      <td>12.0</td>
      <td>108</td>
      <td>301</td>
      <td>0.0</td>
      <td>8495</td>
      <td>43.0</td>
      <td>3.0</td>
      <td>7.4</td>
    </tr>
    <tr>
      <td>4899</td>
      <td>Bewitched</td>
      <td>NaN</td>
      <td>Comedy|Family|Fantasy</td>
      <td>English</td>
      <td>USA</td>
      <td>TV-G</td>
      <td>25.0</td>
      <td>4.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>960.0</td>
      <td>474.0</td>
      <td>2614</td>
      <td>0</td>
      <td>1.0</td>
      <td>11427</td>
      <td>71.0</td>
      <td>31.0</td>
      <td>7.6</td>
    </tr>
  </tbody>
</table>
<p>60 rows × 25 columns</p>
</div>


### Look again through the trend of the results obtained above. There's a reason i extracted that much of info. Look throught the date column, that it's arranged in ascending order. This is a matter of unrecorded data, not that it doesn't exist. Moreover, the missing values in the Year column are from the 3rd sheet of the Excel file

### Assuming you contacted the source of your data and it confirmed the year of those movies as 2016. so fill in 2016 for the missing values in that column


```python
pd.value_counts(dataset.Year).sort_index()
```




    1916.0      1
    1920.0      1
    1925.0      1
    1927.0      1
    1929.0      2
             ... 
    2012.0    218
    2013.0    236
    2014.0    248
    2015.0    222
    2016.0    103
    Name: Year, Length: 91, dtype: int64




```python
dataset.Year.fillna(method = "ffill", inplace = True)
display(dataset.Year.isnull().sum())
```


    0



```python
null_lang = dataset[dataset.Language.isnull()]
null_lang
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Year</th>
      <th>Genres</th>
      <th>Language</th>
      <th>Country</th>
      <th>Content Rating</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>...</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>Intolerance: Love's Struggle Throughout the Ages</td>
      <td>1916.0</td>
      <td>Drama|History|War</td>
      <td>NaN</td>
      <td>USA</td>
      <td>Not Rated</td>
      <td>123.0</td>
      <td>1.33</td>
      <td>385907.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>436.0</td>
      <td>22.0</td>
      <td>9.0</td>
      <td>481</td>
      <td>691</td>
      <td>1.0</td>
      <td>10718</td>
      <td>88.0</td>
      <td>69.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <td>1</td>
      <td>Over the Hill to the Poorhouse</td>
      <td>1920.0</td>
      <td>Crime|Drama</td>
      <td>NaN</td>
      <td>USA</td>
      <td>NaN</td>
      <td>110.0</td>
      <td>1.33</td>
      <td>100000.0</td>
      <td>3000000.0</td>
      <td>...</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>4</td>
      <td>0</td>
      <td>1.0</td>
      <td>5</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>4.8</td>
    </tr>
    <tr>
      <td>2</td>
      <td>The Big Parade</td>
      <td>1925.0</td>
      <td>Drama|Romance|War</td>
      <td>NaN</td>
      <td>USA</td>
      <td>Not Rated</td>
      <td>151.0</td>
      <td>1.33</td>
      <td>245000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>81.0</td>
      <td>12.0</td>
      <td>6.0</td>
      <td>108</td>
      <td>226</td>
      <td>0.0</td>
      <td>4849</td>
      <td>45.0</td>
      <td>48.0</td>
      <td>8.3</td>
    </tr>
    <tr>
      <td>206</td>
      <td>Silent Movie</td>
      <td>1976.0</td>
      <td>Comedy|Romance</td>
      <td>NaN</td>
      <td>USA</td>
      <td>PG</td>
      <td>87.0</td>
      <td>1.85</td>
      <td>4400000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>898.0</td>
      <td>842.0</td>
      <td>753.0</td>
      <td>2951</td>
      <td>629</td>
      <td>0.0</td>
      <td>12666</td>
      <td>61.0</td>
      <td>39.0</td>
      <td>6.7</td>
    </tr>
    <tr>
      <td>2602</td>
      <td>Love's Abiding Joy</td>
      <td>2006.0</td>
      <td>Drama|Family|Western</td>
      <td>NaN</td>
      <td>USA</td>
      <td>PG</td>
      <td>87.0</td>
      <td>NaN</td>
      <td>3000000.0</td>
      <td>252726.0</td>
      <td>...</td>
      <td>702.0</td>
      <td>366.0</td>
      <td>331.0</td>
      <td>2715</td>
      <td>76</td>
      <td>0.0</td>
      <td>1289</td>
      <td>18.0</td>
      <td>5.0</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>2851</td>
      <td>September Dawn</td>
      <td>2007.0</td>
      <td>Drama|History|Romance|Western</td>
      <td>NaN</td>
      <td>USA</td>
      <td>R</td>
      <td>111.0</td>
      <td>1.85</td>
      <td>11000000.0</td>
      <td>1066555.0</td>
      <td>...</td>
      <td>482.0</td>
      <td>362.0</td>
      <td>258.0</td>
      <td>1526</td>
      <td>411</td>
      <td>0.0</td>
      <td>2618</td>
      <td>111.0</td>
      <td>43.0</td>
      <td>5.8</td>
    </tr>
    <tr>
      <td>4322</td>
      <td>A Fine Step</td>
      <td>2014.0</td>
      <td>Drama</td>
      <td>NaN</td>
      <td>USA</td>
      <td>PG</td>
      <td>111.0</td>
      <td>NaN</td>
      <td>1000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>657.0</td>
      <td>608.0</td>
      <td>426.0</td>
      <td>2677</td>
      <td>212</td>
      <td>0.0</td>
      <td>207</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>5.3</td>
    </tr>
    <tr>
      <td>4333</td>
      <td>Alpha and Omega 4: The Legend of the Saw Tooth...</td>
      <td>2014.0</td>
      <td>Action|Adventure|Animation|Comedy|Drama|Family...</td>
      <td>NaN</td>
      <td>USA</td>
      <td>NaN</td>
      <td>45.0</td>
      <td>NaN</td>
      <td>7000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>122.0</td>
      <td>35.0</td>
      <td>29.0</td>
      <td>236</td>
      <td>41</td>
      <td>0.0</td>
      <td>192</td>
      <td>6.0</td>
      <td>2.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <td>4831</td>
      <td>Kickboxer: Vengeance</td>
      <td>2016.0</td>
      <td>Action</td>
      <td>NaN</td>
      <td>USA</td>
      <td>NaN</td>
      <td>90.0</td>
      <td>NaN</td>
      <td>17000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>260000.0</td>
      <td>454.0</td>
      <td>354.0</td>
      <td>261818</td>
      <td>0</td>
      <td>5.0</td>
      <td>246</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>9.1</td>
    </tr>
    <tr>
      <td>4891</td>
      <td>10,000 B.C.</td>
      <td>2016.0</td>
      <td>Comedy</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>22.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5</td>
      <td>0</td>
      <td>0.0</td>
      <td>6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>4989</td>
      <td>Unforgettable</td>
      <td>2016.0</td>
      <td>Drama|Mystery</td>
      <td>NaN</td>
      <td>USA</td>
      <td>NaN</td>
      <td>60.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>654.0</td>
      <td>426.0</td>
      <td>405.0</td>
      <td>1906</td>
      <td>0</td>
      <td>1.0</td>
      <td>12854</td>
      <td>44.0</td>
      <td>14.0</td>
      <td>6.7</td>
    </tr>
  </tbody>
</table>
<p>11 rows × 25 columns</p>
</div>



### A higher percentage of the movies made in USA are in English Language. And upon confirming from the Data source, that's true except for only one.

### So, delete, that one and fill the language of the rest as english


```python
dataset.Language.fillna("English", inplace = True )
dataset.drop( [4891], inplace = True )
display(dataset.Language.isnull().sum())
```


    0



```python
null_country = dataset[dataset.Country.isnull()]
null_country
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Year</th>
      <th>Genres</th>
      <th>Language</th>
      <th>Country</th>
      <th>Content Rating</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>...</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>4368</td>
      <td>Dawn Patrol</td>
      <td>2014.0</td>
      <td>Drama|Thriller</td>
      <td>English</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>88.0</td>
      <td>2.35</td>
      <td>3500000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>795.0</td>
      <td>535.0</td>
      <td>322.0</td>
      <td>2497</td>
      <td>570</td>
      <td>0.0</td>
      <td>455</td>
      <td>13.0</td>
      <td>9.0</td>
      <td>4.8</td>
    </tr>
    <tr>
      <td>4923</td>
      <td>Gone, Baby, Gone</td>
      <td>2016.0</td>
      <td>Comedy|Drama|Reality-TV|Romance</td>
      <td>English</td>
      <td>NaN</td>
      <td>TV-14</td>
      <td>43.0</td>
      <td>1.33</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>341.0</td>
      <td>230.0</td>
      <td>211.0</td>
      <td>1462</td>
      <td>0</td>
      <td>1.0</td>
      <td>29</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.6</td>
    </tr>
    <tr>
      <td>4945</td>
      <td>Preacher</td>
      <td>2016.0</td>
      <td>Adventure|Drama|Fantasy|Mystery</td>
      <td>English</td>
      <td>NaN</td>
      <td>TV-MA</td>
      <td>60.0</td>
      <td>16.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>3000.0</td>
      <td>788.0</td>
      <td>648.0</td>
      <td>6034</td>
      <td>18000</td>
      <td>0.0</td>
      <td>22848</td>
      <td>85.0</td>
      <td>18.0</td>
      <td>8.3</td>
    </tr>
  </tbody>
</table>
<p>3 rows × 25 columns</p>
</div>



### The missing values for country corresponds to English under the language column. And upon confirmation from the data source, the missing values under Country column was confirmed to be "USA". So, fill it in appropriately.


```python
dataset.Country.fillna("USA", inplace = True)
display(dataset.Country.isnull().sum())
```


    0



```python
null_duration = dataset[dataset.Duration.isnull()]
null_duration
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Year</th>
      <th>Genres</th>
      <th>Language</th>
      <th>Country</th>
      <th>Content Rating</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>...</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1387</td>
      <td>Hum To Mohabbat Karega</td>
      <td>2000.0</td>
      <td>Action|Comedy|Romance|Thriller</td>
      <td>Hindi</td>
      <td>India</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>353.0</td>
      <td>89.0</td>
      <td>72.0</td>
      <td>613</td>
      <td>10</td>
      <td>2.0</td>
      <td>275</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>2.8</td>
    </tr>
    <tr>
      <td>2303</td>
      <td>Dil Jo Bhi Kahey...</td>
      <td>2005.0</td>
      <td>Romance</td>
      <td>English</td>
      <td>India</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>70000000.0</td>
      <td>129319.0</td>
      <td>...</td>
      <td>421.0</td>
      <td>96.0</td>
      <td>45.0</td>
      <td>622</td>
      <td>9</td>
      <td>4.0</td>
      <td>257</td>
      <td>4.0</td>
      <td>4.0</td>
      <td>5.1</td>
    </tr>
    <tr>
      <td>2689</td>
      <td>The Naked Ape</td>
      <td>2006.0</td>
      <td>Comedy|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>36.0</td>
      <td>15.0</td>
      <td>1077</td>
      <td>2</td>
      <td>0.0</td>
      <td>128</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>4.7</td>
    </tr>
    <tr>
      <td>3183</td>
      <td>Black Water Transit</td>
      <td>2009.0</td>
      <td>Crime|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>23000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>970.0</td>
      <td>856.0</td>
      <td>816.0</td>
      <td>3874</td>
      <td>26</td>
      <td>0.0</td>
      <td>219</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>3479</td>
      <td>Harry Potter and the Deathly Hallows: Part I</td>
      <td>2010.0</td>
      <td>Fantasy</td>
      <td>English</td>
      <td>UK</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>10000.0</td>
      <td>2000.0</td>
      <td>1000.0</td>
      <td>14719</td>
      <td>25</td>
      <td>1.0</td>
      <td>252</td>
      <td>2.0</td>
      <td>4.0</td>
      <td>6.4</td>
    </tr>
    <tr>
      <td>3530</td>
      <td>N-Secure</td>
      <td>2010.0</td>
      <td>Crime|Drama|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>NaN</td>
      <td>2.35</td>
      <td>NaN</td>
      <td>2592808.0</td>
      <td>...</td>
      <td>713.0</td>
      <td>607.0</td>
      <td>394.0</td>
      <td>3137</td>
      <td>588</td>
      <td>5.0</td>
      <td>548</td>
      <td>15.0</td>
      <td>5.0</td>
      <td>3.5</td>
    </tr>
    <tr>
      <td>3704</td>
      <td>Harry Potter and the Deathly Hallows: Part II</td>
      <td>2011.0</td>
      <td>Action|Fantasy</td>
      <td>English</td>
      <td>UK</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>10000.0</td>
      <td>570.0</td>
      <td>159.0</td>
      <td>11036</td>
      <td>40</td>
      <td>1.0</td>
      <td>381</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>7.5</td>
    </tr>
    <tr>
      <td>3996</td>
      <td>Should've Been Romeo</td>
      <td>2012.0</td>
      <td>Comedy|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>975.0</td>
      <td>900.0</td>
      <td>723.0</td>
      <td>4991</td>
      <td>35</td>
      <td>15.0</td>
      <td>38</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>6.7</td>
    </tr>
    <tr>
      <td>4113</td>
      <td>Barfi</td>
      <td>2013.0</td>
      <td>Comedy|Romance</td>
      <td>Kannada</td>
      <td>India</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>5</td>
      <td>2</td>
      <td>2.0</td>
      <td>57</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>7.1</td>
    </tr>
    <tr>
      <td>4371</td>
      <td>Destiny</td>
      <td>2014.0</td>
      <td>Action|Adventure|Fantasy|Sci-Fi</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>22000.0</td>
      <td>4000.0</td>
      <td>567.0</td>
      <td>26578</td>
      <td>1000</td>
      <td>0.0</td>
      <td>3089</td>
      <td>11.0</td>
      <td>4.0</td>
      <td>8.1</td>
    </tr>
    <tr>
      <td>4663</td>
      <td>Karachi se Lahore</td>
      <td>2015.0</td>
      <td>Comedy|Family</td>
      <td>Urdu</td>
      <td>Pakistan</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>7.0</td>
      <td>5.0</td>
      <td>4.0</td>
      <td>19</td>
      <td>259</td>
      <td>9.0</td>
      <td>876</td>
      <td>15.0</td>
      <td>6.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <td>4696</td>
      <td>Romantic Schemer</td>
      <td>2015.0</td>
      <td>Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>125000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>17.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>17</td>
      <td>0</td>
      <td>2.0</td>
      <td>172</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.1</td>
    </tr>
    <tr>
      <td>4992</td>
      <td>War &amp; Peace</td>
      <td>2016.0</td>
      <td>Drama|History|Romance|War</td>
      <td>English</td>
      <td>UK</td>
      <td>TV-14</td>
      <td>NaN</td>
      <td>16.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>888.0</td>
      <td>502.0</td>
      <td>4528</td>
      <td>11000</td>
      <td>1.0</td>
      <td>9277</td>
      <td>44.0</td>
      <td>10.0</td>
      <td>8.2</td>
    </tr>
    <tr>
      <td>4994</td>
      <td>Wolf Creek</td>
      <td>2016.0</td>
      <td>Drama|Horror|Thriller</td>
      <td>English</td>
      <td>Australia</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>511.0</td>
      <td>457.0</td>
      <td>206.0</td>
      <td>1617</td>
      <td>954</td>
      <td>0.0</td>
      <td>726</td>
      <td>6.0</td>
      <td>2.0</td>
      <td>7.1</td>
    </tr>
  </tbody>
</table>
<p>14 rows × 25 columns</p>
</div>



### After contacting your data supplier, assuming you're provided with the corresponding duration of the missing values. So, you'll fill it in accordingly. In this case, the missing values under Duration column will be filled with the column median value.


```python
duration_median = dataset.Duration.median()
dataset.Duration.fillna(duration_median, inplace = True )
display(dataset.Duration.isnull().sum())
```


    0



```python
null_actor1 = dataset[dataset["Actor 1"].isnull()]
null_actor1
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Year</th>
      <th>Genres</th>
      <th>Language</th>
      <th>Country</th>
      <th>Content Rating</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>...</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1513</td>
      <td>Ayurveda: Art of Being</td>
      <td>2001.0</td>
      <td>Documentary</td>
      <td>English</td>
      <td>India</td>
      <td>NaN</td>
      <td>102.0</td>
      <td>1.85</td>
      <td>300000.0</td>
      <td>16892.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>379</td>
      <td>0.0</td>
      <td>341</td>
      <td>12.0</td>
      <td>15.0</td>
      <td>7.6</td>
    </tr>
    <tr>
      <td>1817</td>
      <td>Sex with Strangers</td>
      <td>2002.0</td>
      <td>Documentary|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>105.0</td>
      <td>1.33</td>
      <td>NaN</td>
      <td>247740.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>51</td>
      <td>0.0</td>
      <td>285</td>
      <td>8.0</td>
      <td>12.0</td>
      <td>4.7</td>
    </tr>
    <tr>
      <td>2411</td>
      <td>The Blood of My Brother</td>
      <td>2005.0</td>
      <td>Documentary|War</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>90.0</td>
      <td>1.66</td>
      <td>120000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>14</td>
      <td>1.0</td>
      <td>102</td>
      <td>7.0</td>
      <td>12.0</td>
      <td>6.6</td>
    </tr>
    <tr>
      <td>3759</td>
      <td>Pink Ribbons, Inc.</td>
      <td>2011.0</td>
      <td>Documentary</td>
      <td>English</td>
      <td>Canada</td>
      <td>Not Rated</td>
      <td>97.0</td>
      <td>NaN</td>
      <td>1200000.0</td>
      <td>24784.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>5000</td>
      <td>0.0</td>
      <td>591</td>
      <td>10.0</td>
      <td>23.0</td>
      <td>7.4</td>
    </tr>
    <tr>
      <td>3819</td>
      <td>The Harvest/La Cosecha</td>
      <td>2011.0</td>
      <td>Documentary</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>80.0</td>
      <td>NaN</td>
      <td>560000.0</td>
      <td>2245.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>88</td>
      <td>0.0</td>
      <td>57</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>4251</td>
      <td>The Brain That Sings</td>
      <td>2013.0</td>
      <td>Documentary|Family</td>
      <td>Arabic</td>
      <td>United Arab Emirates</td>
      <td>NaN</td>
      <td>62.0</td>
      <td>NaN</td>
      <td>125000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>54</td>
      <td>1.0</td>
      <td>18</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8.2</td>
    </tr>
    <tr>
      <td>4611</td>
      <td>Counting</td>
      <td>2015.0</td>
      <td>Documentary</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>111.0</td>
      <td>1.78</td>
      <td>50000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>5</td>
      <td>0.0</td>
      <td>61</td>
      <td>1.0</td>
      <td>12.0</td>
      <td>6.0</td>
    </tr>
  </tbody>
</table>
<p>7 rows × 25 columns</p>
</div>



### Upon contacting the Data supplier, there's no provision for the missing values of Actor 1, Actor 2, Actor 3.

### The next  step will be to drop the missing values in those columns


```python
dataset.drop(null_actor1.index, inplace = True )
```


```python
null_actor2 = dataset[dataset["Actor 2"].isnull()]
null_actor2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Year</th>
      <th>Genres</th>
      <th>Language</th>
      <th>Country</th>
      <th>Content Rating</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>...</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>4102</td>
      <td>All Is Lost</td>
      <td>2013.0</td>
      <td>Action|Adventure|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>106.0</td>
      <td>2.35</td>
      <td>9000000.0</td>
      <td>6262942.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>18000</td>
      <td>0.0</td>
      <td>59545</td>
      <td>312.0</td>
      <td>346.0</td>
      <td>6.9</td>
    </tr>
    <tr>
      <td>4119</td>
      <td>Bending Steel</td>
      <td>2013.0</td>
      <td>Documentary</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>92.0</td>
      <td>16.00</td>
      <td>50000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>33</td>
      <td>0.0</td>
      <td>53</td>
      <td>10.0</td>
      <td>10.0</td>
      <td>7.9</td>
    </tr>
    <tr>
      <td>4598</td>
      <td>Censored Voices</td>
      <td>2015.0</td>
      <td>Documentary|History</td>
      <td>Hebrew</td>
      <td>Israel</td>
      <td>NaN</td>
      <td>84.0</td>
      <td>1.78</td>
      <td>450000.0</td>
      <td>34151.0</td>
      <td>...</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3</td>
      <td>111</td>
      <td>0.0</td>
      <td>186</td>
      <td>3.0</td>
      <td>23.0</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>4966</td>
      <td>The Bachelor</td>
      <td>2016.0</td>
      <td>Game-Show|Reality-TV|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>60.0</td>
      <td>NaN</td>
      <td>3000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>98.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>98</td>
      <td>141</td>
      <td>0.0</td>
      <td>4398</td>
      <td>33.0</td>
      <td>5.0</td>
      <td>2.9</td>
    </tr>
    <tr>
      <td>4996</td>
      <td>Yu-Gi-Oh! Duel Monsters</td>
      <td>2016.0</td>
      <td>Action|Adventure|Animation|Family|Fantasy</td>
      <td>Japanese</td>
      <td>Japan</td>
      <td>NaN</td>
      <td>24.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>124</td>
      <td>0.0</td>
      <td>12417</td>
      <td>51.0</td>
      <td>6.0</td>
      <td>7.0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 25 columns</p>
</div>




```python
dataset.drop(null_actor2.index, inplace = True )
```


```python
null_actor3 = dataset[dataset["Actor 3"].isnull()]
null_actor3
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Year</th>
      <th>Genres</th>
      <th>Language</th>
      <th>Country</th>
      <th>Content Rating</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>...</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>22</td>
      <td>Fantasia</td>
      <td>1940.0</td>
      <td>Animation|Family|Fantasy|Music</td>
      <td>English</td>
      <td>USA</td>
      <td>G</td>
      <td>120.0</td>
      <td>1.37</td>
      <td>2280000.0</td>
      <td>76400000.0</td>
      <td>...</td>
      <td>16.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>16</td>
      <td>3000</td>
      <td>0.0</td>
      <td>71321</td>
      <td>230.0</td>
      <td>99.0</td>
      <td>7.8</td>
    </tr>
    <tr>
      <td>162</td>
      <td>Pink Narcissus</td>
      <td>1971.0</td>
      <td>Drama|Fantasy</td>
      <td>English</td>
      <td>USA</td>
      <td>Not Rated</td>
      <td>65.0</td>
      <td>1.37</td>
      <td>27000.0</td>
      <td>8231.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>85</td>
      <td>1.0</td>
      <td>803</td>
      <td>16.0</td>
      <td>8.0</td>
      <td>6.7</td>
    </tr>
    <tr>
      <td>1678</td>
      <td>Winged Migration</td>
      <td>2001.0</td>
      <td>Documentary</td>
      <td>English</td>
      <td>France</td>
      <td>G</td>
      <td>81.0</td>
      <td>1.85</td>
      <td>160000000.0</td>
      <td>10762178.0</td>
      <td>...</td>
      <td>63.0</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>66</td>
      <td>1000</td>
      <td>0.0</td>
      <td>10369</td>
      <td>153.0</td>
      <td>100.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <td>1753</td>
      <td>Gerry</td>
      <td>2002.0</td>
      <td>Adventure|Drama|Mystery</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>103.0</td>
      <td>2.35</td>
      <td>3500000.0</td>
      <td>236266.0</td>
      <td>...</td>
      <td>13000.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>13000</td>
      <td>0</td>
      <td>0.0</td>
      <td>15104</td>
      <td>290.0</td>
      <td>103.0</td>
      <td>6.2</td>
    </tr>
    <tr>
      <td>2397</td>
      <td>Sisters in Law</td>
      <td>2005.0</td>
      <td>Documentary</td>
      <td>English</td>
      <td>Cameroon</td>
      <td>Not Rated</td>
      <td>104.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>32631.0</td>
      <td>...</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>2</td>
      <td>50</td>
      <td>1.0</td>
      <td>291</td>
      <td>8.0</td>
      <td>27.0</td>
      <td>7.5</td>
    </tr>
    <tr>
      <td>2499</td>
      <td>An Inconvenient Truth</td>
      <td>2006.0</td>
      <td>Documentary</td>
      <td>English</td>
      <td>USA</td>
      <td>PG</td>
      <td>96.0</td>
      <td>1.85</td>
      <td>NaN</td>
      <td>23808111.0</td>
      <td>...</td>
      <td>861.0</td>
      <td>68.0</td>
      <td>NaN</td>
      <td>929</td>
      <td>0</td>
      <td>0.0</td>
      <td>67654</td>
      <td>504.0</td>
      <td>372.0</td>
      <td>7.5</td>
    </tr>
    <tr>
      <td>2961</td>
      <td>Dolphins and Whales 3D: Tribes of the Ocean</td>
      <td>2008.0</td>
      <td>Adventure|Documentary|Short</td>
      <td>English</td>
      <td>UK</td>
      <td>NaN</td>
      <td>42.0</td>
      <td>1.78</td>
      <td>6000000.0</td>
      <td>7518876.0</td>
      <td>...</td>
      <td>844.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>844</td>
      <td>28</td>
      <td>0.0</td>
      <td>172</td>
      <td>5.0</td>
      <td>9.0</td>
      <td>6.5</td>
    </tr>
    <tr>
      <td>4696</td>
      <td>Romantic Schemer</td>
      <td>2015.0</td>
      <td>Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>103.0</td>
      <td>NaN</td>
      <td>125000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>17.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>17</td>
      <td>0</td>
      <td>2.0</td>
      <td>172</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.1</td>
    </tr>
    <tr>
      <td>4985</td>
      <td>The Streets of San Francisco</td>
      <td>2016.0</td>
      <td>Action|Crime|Drama|Mystery</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>120.0</td>
      <td>4.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>416.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>416</td>
      <td>533</td>
      <td>0.0</td>
      <td>3405</td>
      <td>13.0</td>
      <td>13.0</td>
      <td>7.3</td>
    </tr>
  </tbody>
</table>
<p>9 rows × 25 columns</p>
</div>




```python
dataset.drop(null_actor3.index, inplace = True )
```


```python
null_director = dataset[dataset["Facebook Likes - Director"].isnull()]
null_index = null_director.index
```

### Upon contacting the data supplier, you couldn't get concrete figures about the missing values for this column. So you decided to treat it with discretion. And as such, all the null values in this column will be deleted


```python
dataset.drop(null_index, inplace = True)
```


```python
null_user_review = dataset[dataset["Reviews by Users"].isnull()]
null_user_review
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Year</th>
      <th>Genres</th>
      <th>Language</th>
      <th>Country</th>
      <th>Content Rating</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>...</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2805</td>
      <td>Jesus People</td>
      <td>2007.0</td>
      <td>Comedy|Short</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>35.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>338.0</td>
      <td>219.0</td>
      <td>152.0</td>
      <td>968</td>
      <td>0</td>
      <td>5.0</td>
      <td>31</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.9</td>
    </tr>
    <tr>
      <td>2902</td>
      <td>The Touch</td>
      <td>2007.0</td>
      <td>Romance|Short</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>7.0</td>
      <td>1.85</td>
      <td>13000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>344.0</td>
      <td>281.0</td>
      <td>51.0</td>
      <td>726</td>
      <td>30</td>
      <td>0.0</td>
      <td>118</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.2</td>
    </tr>
    <tr>
      <td>2951</td>
      <td>Childless</td>
      <td>2008.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>90.0</td>
      <td>NaN</td>
      <td>1000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>618.0</td>
      <td>171.0</td>
      <td>1996</td>
      <td>3</td>
      <td>5.0</td>
      <td>33</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.1</td>
    </tr>
    <tr>
      <td>3183</td>
      <td>Black Water Transit</td>
      <td>2009.0</td>
      <td>Crime|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>103.0</td>
      <td>NaN</td>
      <td>23000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>970.0</td>
      <td>856.0</td>
      <td>816.0</td>
      <td>3874</td>
      <td>26</td>
      <td>0.0</td>
      <td>219</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7.2</td>
    </tr>
    <tr>
      <td>3448</td>
      <td>Death Calls</td>
      <td>2010.0</td>
      <td>Action|Adventure|Mystery|Romance|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>R</td>
      <td>90.0</td>
      <td>1.85</td>
      <td>290000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>466.0</td>
      <td>216.0</td>
      <td>99.0</td>
      <td>842</td>
      <td>16</td>
      <td>2.0</td>
      <td>30</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4.3</td>
    </tr>
    <tr>
      <td>4311</td>
      <td>Water &amp; Power</td>
      <td>2013.0</td>
      <td>Crime|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>Not Rated</td>
      <td>88.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>79043.0</td>
      <td>...</td>
      <td>601.0</td>
      <td>371.0</td>
      <td>359.0</td>
      <td>2241</td>
      <td>358</td>
      <td>0.0</td>
      <td>85</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.3</td>
    </tr>
    <tr>
      <td>4337</td>
      <td>Amidst the Devil's Wings</td>
      <td>2014.0</td>
      <td>Action|Crime|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>90.0</td>
      <td>NaN</td>
      <td>300000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>569.0</td>
      <td>553.0</td>
      <td>185.0</td>
      <td>1461</td>
      <td>17</td>
      <td>0.0</td>
      <td>28</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4.3</td>
    </tr>
    <tr>
      <td>4463</td>
      <td>Perfect Cowboy</td>
      <td>2014.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>109.0</td>
      <td>NaN</td>
      <td>200000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>270.0</td>
      <td>54.0</td>
      <td>26.0</td>
      <td>364</td>
      <td>65</td>
      <td>3.0</td>
      <td>8</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7.0</td>
    </tr>
    <tr>
      <td>4577</td>
      <td>America Is Still the Place</td>
      <td>2015.0</td>
      <td>History</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>90.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>970.0</td>
      <td>812.0</td>
      <td>569.0</td>
      <td>3359</td>
      <td>337</td>
      <td>0.0</td>
      <td>22</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7.5</td>
    </tr>
    <tr>
      <td>4673</td>
      <td>Me You and Five Bucks</td>
      <td>2015.0</td>
      <td>Comedy|Drama|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>93.0</td>
      <td>NaN</td>
      <td>1500000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>310.0</td>
      <td>228.0</td>
      <td>134.0</td>
      <td>771</td>
      <td>132</td>
      <td>1.0</td>
      <td>7</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7.6</td>
    </tr>
    <tr>
      <td>4700</td>
      <td>Running Forever</td>
      <td>2015.0</td>
      <td>Family</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>88.0</td>
      <td>NaN</td>
      <td>5000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>784.0</td>
      <td>763.0</td>
      <td>668.0</td>
      <td>3021</td>
      <td>49</td>
      <td>2.0</td>
      <td>8</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8.6</td>
    </tr>
    <tr>
      <td>4770</td>
      <td>To Be Frank, Sinatra at 100</td>
      <td>2015.0</td>
      <td>Documentary</td>
      <td>English</td>
      <td>UK</td>
      <td>NaN</td>
      <td>81.0</td>
      <td>NaN</td>
      <td>2000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>674.0</td>
      <td>27.0</td>
      <td>8.0</td>
      <td>712</td>
      <td>0</td>
      <td>0.0</td>
      <td>7</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7.4</td>
    </tr>
    <tr>
      <td>4790</td>
      <td>A Beginner's Guide to Snuff</td>
      <td>2016.0</td>
      <td>Comedy|Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>87.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>467.0</td>
      <td>258.0</td>
      <td>165.0</td>
      <td>1270</td>
      <td>8</td>
      <td>0.0</td>
      <td>13</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8.7</td>
    </tr>
    <tr>
      <td>4912</td>
      <td>Del 1 - Män som hatar kvinnor</td>
      <td>2016.0</td>
      <td>Action|Crime|Mystery|Thriller</td>
      <td>Swedish</td>
      <td>Sweden</td>
      <td>NaN</td>
      <td>88.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>690.0</td>
      <td>94.0</td>
      <td>75.0</td>
      <td>998</td>
      <td>22</td>
      <td>0.0</td>
      <td>335</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8.1</td>
    </tr>
    <tr>
      <td>4986</td>
      <td>Towering Inferno</td>
      <td>2016.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>Canada</td>
      <td>NaN</td>
      <td>65.0</td>
      <td>1.33</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>770.0</td>
      <td>179.0</td>
      <td>176.0</td>
      <td>1125</td>
      <td>0</td>
      <td>2.0</td>
      <td>10</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9.5</td>
    </tr>
  </tbody>
</table>
<p>15 rows × 25 columns</p>
</div>



###  The data supplier could not provide the missing values for this column, hence, the null values will be dropped


```python
dataset.drop(null_user_review.index, inplace = True)
```


```python
null_critic_review = dataset[dataset["Reviews by Crtiics"].isnull()]
null_critic_review
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Title</th>
      <th>Year</th>
      <th>Genres</th>
      <th>Language</th>
      <th>Country</th>
      <th>Content Rating</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>...</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>336</td>
      <td>The Ballad of Gregorio Cortez</td>
      <td>1982.0</td>
      <td>Western</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>105.0</td>
      <td>NaN</td>
      <td>1250000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>883.0</td>
      <td>655.0</td>
      <td>467.0</td>
      <td>3164</td>
      <td>32</td>
      <td>0.0</td>
      <td>39</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>7.1</td>
    </tr>
    <tr>
      <td>1128</td>
      <td>The Love Letter</td>
      <td>1998.0</td>
      <td>Fantasy|Romance</td>
      <td>English</td>
      <td>USA</td>
      <td>Unrated</td>
      <td>99.0</td>
      <td>1.33</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>393.0</td>
      <td>224.0</td>
      <td>2166</td>
      <td>515</td>
      <td>1.0</td>
      <td>1465</td>
      <td>56.0</td>
      <td>NaN</td>
      <td>7.4</td>
    </tr>
    <tr>
      <td>2127</td>
      <td>Guiana 1838</td>
      <td>2004.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>Unrated</td>
      <td>120.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>227241.0</td>
      <td>...</td>
      <td>12.0</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>15</td>
      <td>32</td>
      <td>0.0</td>
      <td>56</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>7.4</td>
    </tr>
    <tr>
      <td>2171</td>
      <td>On the Downlow</td>
      <td>2004.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>84.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>21.0</td>
      <td>20.0</td>
      <td>12.0</td>
      <td>62</td>
      <td>22</td>
      <td>2.0</td>
      <td>156</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>6.1</td>
    </tr>
    <tr>
      <td>2342</td>
      <td>Insomnia Manica</td>
      <td>2005.0</td>
      <td>Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>127.0</td>
      <td>1.33</td>
      <td>500000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2</td>
      <td>0</td>
      <td>0.0</td>
      <td>16</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>5.8</td>
    </tr>
    <tr>
      <td>2440</td>
      <td>The Mongol King</td>
      <td>2005.0</td>
      <td>Crime|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>84.0</td>
      <td>NaN</td>
      <td>3250.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>45.0</td>
      <td>44.0</td>
      <td>2.0</td>
      <td>93</td>
      <td>4</td>
      <td>0.0</td>
      <td>36</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>7.8</td>
    </tr>
    <tr>
      <td>2689</td>
      <td>The Naked Ape</td>
      <td>2006.0</td>
      <td>Comedy|Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>103.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>36.0</td>
      <td>15.0</td>
      <td>1077</td>
      <td>2</td>
      <td>0.0</td>
      <td>128</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>4.7</td>
    </tr>
    <tr>
      <td>2743</td>
      <td>Arnolds Park</td>
      <td>2007.0</td>
      <td>Mystery|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>103.0</td>
      <td>1.78</td>
      <td>600000.0</td>
      <td>23616.0</td>
      <td>...</td>
      <td>23.0</td>
      <td>20.0</td>
      <td>20.0</td>
      <td>85</td>
      <td>11</td>
      <td>4.0</td>
      <td>94</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>5.6</td>
    </tr>
    <tr>
      <td>3233</td>
      <td>Flying By</td>
      <td>2009.0</td>
      <td>Drama|Family|Music</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>90.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>695.0</td>
      <td>617.0</td>
      <td>483.0</td>
      <td>3217</td>
      <td>38</td>
      <td>6.0</td>
      <td>215</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>4.5</td>
    </tr>
    <tr>
      <td>3326</td>
      <td>Steppin: The Movie</td>
      <td>2009.0</td>
      <td>Comedy|Music</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>138.0</td>
      <td>NaN</td>
      <td>1000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>592.0</td>
      <td>207.0</td>
      <td>110.0</td>
      <td>1350</td>
      <td>41</td>
      <td>6.0</td>
      <td>293</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>3.4</td>
    </tr>
    <tr>
      <td>3339</td>
      <td>The Deported</td>
      <td>2009.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>90.0</td>
      <td>1.85</td>
      <td>3000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>1000.0</td>
      <td>975.0</td>
      <td>452.0</td>
      <td>3882</td>
      <td>54</td>
      <td>1.0</td>
      <td>62</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>6.2</td>
    </tr>
    <tr>
      <td>3508</td>
      <td>Lies in Plain Sight</td>
      <td>2010.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>USA</td>
      <td>TV-PG</td>
      <td>89.0</td>
      <td>1.78</td>
      <td>2100000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>919.0</td>
      <td>718.0</td>
      <td>650.0</td>
      <td>3873</td>
      <td>162</td>
      <td>1.0</td>
      <td>544</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>6.3</td>
    </tr>
    <tr>
      <td>3831</td>
      <td>The Ridges</td>
      <td>2011.0</td>
      <td>Drama|Horror|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>143.0</td>
      <td>NaN</td>
      <td>17350.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>720.0</td>
      <td>19.0</td>
      <td>8.0</td>
      <td>770</td>
      <td>33</td>
      <td>0.0</td>
      <td>125</td>
      <td>8.0</td>
      <td>NaN</td>
      <td>3.0</td>
    </tr>
    <tr>
      <td>3851</td>
      <td>We Have Your Husband</td>
      <td>2011.0</td>
      <td>Crime|Drama|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>TV-PG</td>
      <td>87.0</td>
      <td>1.78</td>
      <td>5000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>708.0</td>
      <td>699.0</td>
      <td>601.0</td>
      <td>3059</td>
      <td>58</td>
      <td>1.0</td>
      <td>216</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>5.5</td>
    </tr>
    <tr>
      <td>4094</td>
      <td>A True Story</td>
      <td>2013.0</td>
      <td>Comedy</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>96.0</td>
      <td>2.35</td>
      <td>45000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>948.0</td>
      <td>482.0</td>
      <td>281.0</td>
      <td>2058</td>
      <td>72</td>
      <td>5.0</td>
      <td>181</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>5.5</td>
    </tr>
    <tr>
      <td>4169</td>
      <td>Her Cry: La Llorona Investigation</td>
      <td>2013.0</td>
      <td>Horror</td>
      <td>English</td>
      <td>USA</td>
      <td>Not Rated</td>
      <td>89.0</td>
      <td>NaN</td>
      <td>60000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>5</td>
      <td>48</td>
      <td>0.0</td>
      <td>23</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>5.4</td>
    </tr>
    <tr>
      <td>4321</td>
      <td>8 Days</td>
      <td>2014.0</td>
      <td>Drama|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>90.0</td>
      <td>NaN</td>
      <td>2500000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>210.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>210</td>
      <td>224</td>
      <td>1.0</td>
      <td>44</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>6.9</td>
    </tr>
    <tr>
      <td>4361</td>
      <td>Butterfly Girl</td>
      <td>2014.0</td>
      <td>Documentary</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>78.0</td>
      <td>NaN</td>
      <td>180000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>88</td>
      <td>0.0</td>
      <td>27</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>8.7</td>
    </tr>
    <tr>
      <td>4435</td>
      <td>Light from the Darkroom</td>
      <td>2014.0</td>
      <td>Action|Drama|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>90.0</td>
      <td>NaN</td>
      <td>600000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>595.0</td>
      <td>412.0</td>
      <td>271.0</td>
      <td>1754</td>
      <td>9</td>
      <td>0.0</td>
      <td>6</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>8.0</td>
    </tr>
    <tr>
      <td>4471</td>
      <td>Rise of the Entrepreneur: The Search for a Bet...</td>
      <td>2014.0</td>
      <td>Documentary</td>
      <td>English</td>
      <td>USA</td>
      <td>G</td>
      <td>52.0</td>
      <td>NaN</td>
      <td>450000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>8.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>10</td>
      <td>460</td>
      <td>0.0</td>
      <td>78</td>
      <td>10.0</td>
      <td>NaN</td>
      <td>8.2</td>
    </tr>
    <tr>
      <td>4571</td>
      <td>Abandoned</td>
      <td>2015.0</td>
      <td>Drama</td>
      <td>English</td>
      <td>New Zealand</td>
      <td>NaN</td>
      <td>86.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>42.0</td>
      <td>40.0</td>
      <td>3.0</td>
      <td>90</td>
      <td>213</td>
      <td>5.0</td>
      <td>333</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>6.3</td>
    </tr>
    <tr>
      <td>4625</td>
      <td>Dutch Kills</td>
      <td>2015.0</td>
      <td>Crime|Drama|Thriller</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>90.0</td>
      <td>NaN</td>
      <td>25000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>313.0</td>
      <td>25.0</td>
      <td>9.0</td>
      <td>366</td>
      <td>33</td>
      <td>2.0</td>
      <td>57</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>4.8</td>
    </tr>
    <tr>
      <td>4643</td>
      <td>Growing Up Smith</td>
      <td>2015.0</td>
      <td>Comedy|Drama|Family</td>
      <td>English</td>
      <td>USA</td>
      <td>PG-13</td>
      <td>102.0</td>
      <td>1.85</td>
      <td>2000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>3000.0</td>
      <td>660.0</td>
      <td>259.0</td>
      <td>4320</td>
      <td>232</td>
      <td>NaN</td>
      <td>108</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>8.2</td>
    </tr>
    <tr>
      <td>4722</td>
      <td>Teeth and Blood</td>
      <td>2015.0</td>
      <td>Horror</td>
      <td>English</td>
      <td>USA</td>
      <td>NaN</td>
      <td>96.0</td>
      <td>16.00</td>
      <td>300000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>471.0</td>
      <td>320.0</td>
      <td>270.0</td>
      <td>1399</td>
      <td>85</td>
      <td>0.0</td>
      <td>24</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>4.3</td>
    </tr>
    <tr>
      <td>4822</td>
      <td>Hands of Stone</td>
      <td>2016.0</td>
      <td>Action|Biography|Drama|Sport</td>
      <td>English</td>
      <td>Panama</td>
      <td>R</td>
      <td>105.0</td>
      <td>NaN</td>
      <td>20000000.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>22000.0</td>
      <td>2000.0</td>
      <td>897.0</td>
      <td>27425</td>
      <td>0</td>
      <td>0.0</td>
      <td>178</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>7.2</td>
    </tr>
  </tbody>
</table>
<p>25 rows × 25 columns</p>
</div>



### The data supplier couldn't make provisions for the missing values in this column as well. Hence, it'll be dropped


```python
dataset.drop(null_critic_review.index, inplace = True)
```

### Both "Content Rating" and "Aspect Ratio" columns which have missing values will be dropped. The Data supplier  couldn't make provisions for the missing values in both cases


```python
null_content_rating = dataset[dataset["Content Rating"].isnull()]
dataset.drop(null_content_rating.index, inplace = True)
```


```python
null_aspect_ratio = dataset[dataset["Aspect Ratio"].isnull()]
dataset.drop(null_aspect_ratio.index, inplace = True)
```


```python
null_facenumbers = dataset[dataset["Facenumber in posters"].isnull()]
facenumbers_index = null_facenumbers.index
```

### When the data supplier was contacted for info on the missing values in this column, his response is a value equal to mean of the column. And the mean value for the column will be filled in for null values accordingly


```python
dataset["Facenumber in posters"].fillna(dataset["Facenumber in posters"].mean(), inplace = True)
```

### There are only 2 columns left containing null values. First we'll drop the Budget columns, so the null values in the "Gross Earnings column will be reduced. Next, we'll fill the remaining null values with the median values of the Gross Earning column


```python
print("Number of missing values in Gross Earnings\' column before deleting Budget Column :", dataset["Gross Earnings"].isnull().sum())
null_budget = dataset[dataset.Budget.isnull()]
dataset.drop(null_budget.index, inplace = True)
print("Number of missing values in Gross Earnings\' column after deleting Budget Column :", dataset["Gross Earnings"].isnull().sum())
```

    Number of missing values in Gross Earnings' column before deleting Budget Column : 461
    Number of missing values in Gross Earnings' column after deleting Budget Column : 404



```python
dataset["Gross Earnings"].fillna(dataset["Gross Earnings"].median(), inplace = True)
```

### Note  that most of the values dropped in this tutorial are for teaching or example sake. There's a certain values ( mostly, less than 10% of the total data ) that can be dropped. Any other scenario should be treated with great care. This will help you avoid the trap of losing valuable chunks of data.


```python
dataset.isna().sum()
```




    Title                          0
    Year                           0
    Genres                         0
    Language                       0
    Country                        0
    Content Rating                 0
    Duration                       0
    Aspect Ratio                   0
    Budget                         0
    Gross Earnings                 0
    Director                       0
    Actor 1                        0
    Actor 2                        0
    Actor 3                        0
    Facebook Likes - Director      0
    Facebook Likes - Actor 1       0
    Facebook Likes - Actor 2       0
    Facebook Likes - Actor 3       0
    Facebook Likes - cast Total    0
    Facebook likes - Movie         0
    Facenumber in posters          0
    User Votes                     0
    Reviews by Users               0
    Reviews by Crtiics             0
    IMDB Score                     0
    dtype: int64




```python
pd.value_counts(dataset["Facenumber in posters"])
```




    0.000000     1768
    1.000000     1046
    2.000000      592
    3.000000      314
    4.000000      174
    5.000000       84
    6.000000       58
    7.000000       34
    8.000000       33
    9.000000       11
    10.000000       8
    1.351131        8
    11.000000       5
    15.000000       4
    12.000000       4
    13.000000       2
    14.000000       1
    19.000000       1
    31.000000       1
    43.000000       1
    Name: Facenumber in posters, dtype: int64



### All the missing values in the dataset have been treated. The data is clean and is ready for further exploration and analysis.

### But this has been a fair lesson to wrap your head around and lay your hands on.

### This document will be saved into an excel file and the exploration, analysis and insights and visualization will be saved for the second part. Make sure to check it out


```python
dataset.index
```




    Int64Index([   0,    2,    3,    5,    6,    7,    8,    9,   10,   11,
                ...
                4876, 4878, 4879, 4880, 4881, 4883, 4884, 4886, 4888, 4890],
               dtype='int64', length=4149)



### The index column has been altered again as a result of data cleaning process. Let's rewrite it in an ordered manner


```python
final_index = range(1,4150)
dataset.index = final_index
dataset.index
```




    RangeIndex(start=1, stop=4150, step=1)




```python
dataset.shape
```




    (4149, 25)




```python
dataset.size
```




    103725




```python
dataset.dtypes
```




    Title                           object
    Year                           float64
    Genres                          object
    Language                        object
    Country                         object
    Content Rating                  object
    Duration                       float64
    Aspect Ratio                   float64
    Budget                         float64
    Gross Earnings                 float64
    Director                        object
    Actor 1                         object
    Actor 2                         object
    Actor 3                         object
    Facebook Likes - Director      float64
    Facebook Likes - Actor 1       float64
    Facebook Likes - Actor 2       float64
    Facebook Likes - Actor 3       float64
    Facebook Likes - cast Total      int64
    Facebook likes - Movie           int64
    Facenumber in posters          float64
    User Votes                       int64
    Reviews by Users               float64
    Reviews by Crtiics             float64
    IMDB Score                     float64
    dtype: object




```python
dataset.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 4149 entries, 1 to 4149
    Data columns (total 25 columns):
    Title                          4149 non-null object
    Year                           4149 non-null float64
    Genres                         4149 non-null object
    Language                       4149 non-null object
    Country                        4149 non-null object
    Content Rating                 4149 non-null object
    Duration                       4149 non-null float64
    Aspect Ratio                   4149 non-null float64
    Budget                         4149 non-null float64
    Gross Earnings                 4149 non-null float64
    Director                       4149 non-null object
    Actor 1                        4149 non-null object
    Actor 2                        4149 non-null object
    Actor 3                        4149 non-null object
    Facebook Likes - Director      4149 non-null float64
    Facebook Likes - Actor 1       4149 non-null float64
    Facebook Likes - Actor 2       4149 non-null float64
    Facebook Likes - Actor 3       4149 non-null float64
    Facebook Likes - cast Total    4149 non-null int64
    Facebook likes - Movie         4149 non-null int64
    Facenumber in posters          4149 non-null float64
    User Votes                     4149 non-null int64
    Reviews by Users               4149 non-null float64
    Reviews by Crtiics             4149 non-null float64
    IMDB Score                     4149 non-null float64
    dtypes: float64(13), int64(3), object(9)
    memory usage: 664.6+ KB



```python
dataset.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>Duration</th>
      <th>Aspect Ratio</th>
      <th>Budget</th>
      <th>Gross Earnings</th>
      <th>Facebook Likes - Director</th>
      <th>Facebook Likes - Actor 1</th>
      <th>Facebook Likes - Actor 2</th>
      <th>Facebook Likes - Actor 3</th>
      <th>Facebook Likes - cast Total</th>
      <th>Facebook likes - Movie</th>
      <th>Facenumber in posters</th>
      <th>User Votes</th>
      <th>Reviews by Users</th>
      <th>Reviews by Crtiics</th>
      <th>IMDB Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>count</td>
      <td>4149.000000</td>
      <td>4149.000000</td>
      <td>4149.000000</td>
      <td>4.149000e+03</td>
      <td>4.149000e+03</td>
      <td>4149.000000</td>
      <td>4149.000000</td>
      <td>4149.000000</td>
      <td>4149.000000</td>
      <td>4149.000000</td>
      <td>4149.000000</td>
      <td>4149.000000</td>
      <td>4.149000e+03</td>
      <td>4149.000000</td>
      <td>4149.000000</td>
      <td>4149.000000</td>
    </tr>
    <tr>
      <td>mean</td>
      <td>2001.688841</td>
      <td>109.782598</td>
      <td>2.113620</td>
      <td>4.242499e+07</td>
      <td>5.016976e+07</td>
      <td>785.356471</td>
      <td>7250.685466</td>
      <td>1859.320559</td>
      <td>714.560858</td>
      <td>10750.794167</td>
      <td>8651.721379</td>
      <td>1.355461</td>
      <td>9.782653e+04</td>
      <td>314.473126</td>
      <td>157.030369</td>
      <td>6.454857</td>
    </tr>
    <tr>
      <td>std</td>
      <td>12.482498</td>
      <td>22.707194</td>
      <td>0.558098</td>
      <td>2.153378e+08</td>
      <td>6.665142e+07</td>
      <td>3015.762769</td>
      <td>15111.639548</td>
      <td>4329.447726</td>
      <td>1778.491017</td>
      <td>18522.890707</td>
      <td>20755.105562</td>
      <td>2.016013</td>
      <td>1.470236e+05</td>
      <td>398.540618</td>
      <td>122.431401</td>
      <td>1.086413</td>
    </tr>
    <tr>
      <td>min</td>
      <td>1916.000000</td>
      <td>20.000000</td>
      <td>1.180000</td>
      <td>2.180000e+02</td>
      <td>1.620000e+02</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2.200000e+01</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.600000</td>
    </tr>
    <tr>
      <td>25%</td>
      <td>1998.000000</td>
      <td>95.000000</td>
      <td>1.850000</td>
      <td>8.000000e+06</td>
      <td>1.021401e+07</td>
      <td>10.000000</td>
      <td>692.000000</td>
      <td>342.000000</td>
      <td>172.000000</td>
      <td>1724.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.534500e+04</td>
      <td>96.000000</td>
      <td>67.000000</td>
      <td>5.800000</td>
    </tr>
    <tr>
      <td>50%</td>
      <td>2004.000000</td>
      <td>105.000000</td>
      <td>2.350000</td>
      <td>2.000000e+07</td>
      <td>2.997598e+07</td>
      <td>58.000000</td>
      <td>1000.000000</td>
      <td>649.000000</td>
      <td>410.000000</td>
      <td>3629.000000</td>
      <td>209.000000</td>
      <td>1.000000</td>
      <td>4.622100e+04</td>
      <td>192.000000</td>
      <td>127.000000</td>
      <td>6.600000</td>
    </tr>
    <tr>
      <td>75%</td>
      <td>2010.000000</td>
      <td>120.000000</td>
      <td>2.350000</td>
      <td>4.800000e+07</td>
      <td>6.065204e+07</td>
      <td>222.000000</td>
      <td>12000.000000</td>
      <td>960.000000</td>
      <td>664.000000</td>
      <td>15361.000000</td>
      <td>10000.000000</td>
      <td>2.000000</td>
      <td>1.156500e+05</td>
      <td>375.000000</td>
      <td>214.000000</td>
      <td>7.200000</td>
    </tr>
    <tr>
      <td>max</td>
      <td>2016.000000</td>
      <td>330.000000</td>
      <td>16.000000</td>
      <td>1.221550e+10</td>
      <td>7.605058e+08</td>
      <td>23000.000000</td>
      <td>640000.000000</td>
      <td>137000.000000</td>
      <td>23000.000000</td>
      <td>656730.000000</td>
      <td>349000.000000</td>
      <td>43.000000</td>
      <td>1.689764e+06</td>
      <td>5060.000000</td>
      <td>813.000000</td>
      <td>9.300000</td>
    </tr>
  </tbody>
</table>
</div>




```python
dataset.to_excel("movies_cleaned_for_part2.xlsx", index = False)
```

### So, this marks the end of another lesson in the process of Data Science using Python Libraries like Numpy, Pandas and Matplotlib.

### The simplest way to learn is by doing, so roll up your sleeves and get to work. Be encouraged no matter the progress you're making, keep doing it even if it means doing it poorly till you get it right.

### It's only a matter of some more practice before you actually get it right. With a little more of commitment, it'll all come naturally and you'll gain mastery of the process and system

### Till i bring another lesson your way,


# Happy Learning ! ! !


```python

```
