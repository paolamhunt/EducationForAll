# Data Visualizaton with Matplotlib

#### In this Section
- [Getting Started](#Getting-Started)
- [Line Plots](#Line-PLots)
- [Bar Chart](#Bar-Chart)
- [Pie Chart](#Pie-Chart)
- [Histogram](#Histogram)
- [Scatter Plot](#Scatter-Plot)
- [Box Plot](#Box-Plot)

---

I will mainly use [pandas.DataFrame.plot](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.plot.html) in most examples.

`DataFrame.plot(x=None, y=None, ax=None, subplots=False, figsize=None, use_index=True, title=None, legend=True)`

Each plot kind has a corresponding method on the DataFrame.plot accessor: `df.plot(kind=‘line’)` is equivalent to `df.plot.line()`.
Parameters:
- data : DataFrame
- x : label or position, default None
- y : label, position or list of label, positions, default None
- ax : matplotlib axes object, default None
- subplots : boolean, default False. Make separate subplots for each column
- figsize : a tuple (width, height) in inches
- title : string or list. Title to use for the plot
- legend : False/True/, default True
- stacked: False/True, default false

## Getting Started
For this section, I will be using the auto-mpg dataset. You can find it [here](/Basics_Intro/DataSets/mpg.csv):point_left:

Import modules into memory
~~~
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
~~~

Next, I will clean the data a little bit in order to start visualizing the data

~~~
auto = pd.read_csv('mpg.csv')
auto = auto.dropna() # drop the missing data
auto.shape
auto.index = auto.car # set car as index
auto.head() # display first 5 items of dataframe
~~~
[Back to Top](#In-this-Section)



## Line Plots
`DataFrame.plot.line(x=None, y=None)` allows plotting of one column versus another. `DataFrame.plot()` is equivalent to `DataFrame.plot.line()`. Here I use `DataFrame.plot.line()` for consistence with other plotting methods.

**x** : label or position, optional
- Allows plotting of one column versus another. If not specified, the index of the DataFrame is used.

**y** : label or position, optional
- Allows plotting of one column versus another. If not specified, all numerical columns are used.

### Line Plot of One Column
**Example**
~~~
# a simplest line plot. plot the mpg along the default index car names
auto.mpg.plot.line()
plt.show() # show the graph on screen

# add features to a graph such as title, figure size and axex labels	 
ax = auto.plot.line(x='model', 
                    y='mpg',
                    figsize=[10,5],
                    title='mpg',
                    legend=False )

# DataFrame.plot() function returns a matplotlib.axes.AxesSubplot object

# set the labels on that object called ax here.
ax.set_xlabel('Model Year') # add x label
ax.set_ylabel('mpg') # add y label

plt.savefig('mpg') # save the figure as mpg.png in the directory
plt.show()
~~~

### Line Plot of More Columns
**Example**
~~~
auto.plot(y=['acceleration','mpg'])
plt.show()

auto.plot(subplots=True,figsize=(5,10), y=['acceleration','mpg'])
# subplots=True will graph the two columns separately
plt.show()
~~~
[Back to Top](#In-this-Section)



## Bar Chart
A bar plot is a way of representing data where the length of the bars represents the magnitude/size of the feature/variables. Bar graphs usually represent numerical and categorical variables grouped in intervals.

`DataFrame.plot.bar(x=None, y=None)` shows the vertical bar plot.
`DataFrame.plot.barh(x=None, y=None)` shows the horizontal bar plot.

**x** : label or position, optional
- Allows plotting of one column versus another. If not specified, the index of the DataFrame is used.

**y** : label or position, optional
- Allows plotting of one column versus another. If not specified, all numerical columns are used.

### Bar Chart of One Column
**Example**
~~~
auto_selected = auto[(auto.cylinders==8) & (auto.mpg>20)]
auto_selected.shape
auto_selected = auto[(auto.cylinders==8) & (auto.mpg>20)] # select data with the two condistions
auto_selected =  auto_selected.drop(['weight','displacement','model'], axis=1) # delete some columns
auto_selected.index = ['car1','car2','car3','car4']
print(auto_selected.shape) # check the shape of the new data auto_selected
## (4, 6)

auto_selected.plot.bar(y='mpg')
# plot the bar chart of mpg along car names
plt.show()

auto_selected.plot.bar(y='mpg', rot=45)
#rot=45 means the index shows in 45 degree
plt.show()


auto_selected.plot.barh(y='mpg', rot=45)
#plot the horizontal bar chart
plt.show()
~~~

### Bar Chart of More Columns
**Example**
~~~
auto_selected.plot.bar()
# plot vertical bars for all numerical columns
# each numerical column is assigned a distinct color,
# and each row is nested in a group along the horizontal axis
plt.show()

auto_selected.plot.bar(subplots=True, rot=45, legend=False,figsize=(8,10))
# instead of nesting, the figure can be split by column with subplots=True.
plt.show()

auto_selected.plot.bar(stacked=True,rot=45)
# stacked=True means to stack the bars
plt.show()

auto_selected.plot.barh() # plot the horizontal bar chart
plt.show()
~~~

### Bar Chart (Histogram) of Categorical Columns
For a categorical column, we first use `Series.value_counts()` to count the frequency of each category. The resulting series of `Series.value_counts()` will be in descending order so that the first element is the most frequently-occurring element. Then plot the bar chart for the resulting series along the default resulting series index which is the names of the categories. The type of bar chart is actually the histogram of the categorical columns.

**Example**
~~~
plt.figure()
origin_country = auto.origin.value_counts()
# count the frequency of cars' origin
# name the resulting series as origin_country
print(origin_country)
## US    248
## Japan  79
## Europe 69
## Name: origin, dtype: int64

origin_country.plot.bar(figsize=(5,6), rot=45 ) # plot bar chart for the series origin_country
plt.show()
~~~
[Back to Top](#In-this-Section)



## Pie Chart
A pie chart helps show proportions and percentages between categories, by dividing a circle into proportional segments. Pie chart plot doesn’t allow negative values in Series or DataFrames.

### Pie Chart of One Column
The format is `Series.plot.pie()`.
**Example**
~~~
plt.figure()
origin_country.plot.pie(figsize=(5, 5),autopct='%1.2f%%', legend=False)
# a series pie chart
# autopct='%1.1f%%' formats the percentage to the tenth place.
# autopct='%1.2f%%' formats the percentage to the hundredths place
plt.show()

grouping_result = auto.groupby('origin').mean()
# group auto data by origin
# grouping_result is a data frame
print(grouping_result)
##           mpg  cylinders ...  acceleration  model
## origin                      ...                         
## Europe   27.947826 4.159420 ...     16.805797  75.855072
## Japan    30.450633 4.101266    ... 16.172152  77.443038
## US       20.079839   6.250000 ...     15.025806  75.616935
##
## [3 rows x 6 columns]
explode_list = [0, 0.1, 0]
grouping_result.plot.pie(y='mpg',figsize=(5, 5),autopct='%1.2f%%', legend=False, explode=explode_list)
# pie chart of one column in a data frame
# explode the pie chart to emphasize some slice by pasing in explode parameter.
plt.show()

#another way to plot pie chart of one column in a data frame
grouping_result.mpg.plot.pie(figsize=(5, 5),autopct='%1.2f%%', legend=False)
#pie chart of one column in a data frame
~~~

### Pie Chart of More Columns
`DataFrame.plot.pie(y=‘’)`: Here `y` must be given. If not provided, `subplots=True` argument must be passed. And `x` is defaulted to be the index.

**Example**
~~~
grouping_result.plot.pie(subplots=True,figsize=(15,5),autopct='%1.0f%%', legend=False)
# use figsize(length, width) to control the pie charts size
plt.show()

grouping_result.plot.pie(y=['mpg', 'weight'], subplots=True,figsize=(10, 5),autopct='%1.0f%%', legend=False)
# pie charts of selected columns
plt.show()
 
plt.close('all')
~~~
[Back to Top](#In-this-Section)



## Histogram
A histogram is a way of representing the frequency distribution of numeric dataset. The way it works is it partitions the x-axis into bins, assigns each data point in our dataset to a bin, and then counts the number of data points that have been assigned to each bin. So the y-axis is the frequency or the number of data points in each bin. Python offers a handful of different options for building and plotting histograms.


`Series.hist()` and `DataFrame.hist()` are two easy ways to plot histograms with Pandas. Now I will show you an example of a histogram with one column, and a histogram with more than one column.

### Histogram of One Column
**Example** 
~~~
# a simple histogram
plt.figure()
auto.mpg.hist()
plt.show()
 
plt.close()
# add features to the histogram
mpg = auto.mpg.hist(bins=20)
#plot 20 bins
mpg.set_xlabel('MPG') # add x label
mpg.set_ylabel('Frequency') # add y label
plt.show()
~~~

### Histogram of More Columns
**Example**
~~~
auto.hist(figsize=(8,10))
# histograms of all numerical columns in a data frame
plt.show()

auto.hist(column=['mpg', 'weight'], bins=20)
# histograms of selected columns in a data frame
# another way to plot histograms of selected columns
auto[['mpg', 'weight']].hist(bins=20)
plt.show()
~~~
[Back to Top](#In-this-Section)



## Scatter Plot
A scatter plot (2D) is a useful method of comparing variables against each other. Scatter plots look similar to line plots in that they both map independent and dependent variables on a 2D graph. While the datapoints are connected together by a line in a line plot, they are not connected in a scatter plot. 

The data in a scatter plot is considered to express a trend. With further analysis using tools like regression, we can mathematically calculate this relationship and use it to predict trends outside the dataset.

`DataFrame.plot.scatter(x, y, keywords)` Create a scatter plot with varying marker point size and color.
The coordinates of each point are defined by two dataframe columns and filled circles are used to represent each point. This kind of plot is useful to see complex correlations between two variables.
<u>Parameters</u>
- `x` : int or str
    - The column name or column position to be used as horizontal coordinates for each point.
- `y` : int or str
    - The column name or column position to be used as vertical coordinates for each point.
- `keywords`: color, marker, colormap, colorbar, label, etc


### Scatter Plot for one Pair of Data
**Example**
~~~
auto.plot.scatter(x='acceleration', y='mpg', c='b', marker='o')
plt.show()
~~~
 
### Scatter Plot for More Pairs of Data
To put the scatter plots of more pairs in one graph, in the second graph we need to let the `ax=ax1` where ax1 is the returning axes of the first graph.

**Example**
~~~
ax1 = auto.plot.scatter(x='weight', y='mpg', c='r', marker='s', label='mpg')
# name the graph object as ax1
auto.plot.scatter(x='weight', y='acceleration', c='b', marker='o',label='acceleration', ax=ax1)
# let ax=ax1 put the two scatter plots in one graph
plt.show()
~~~

### Scatter Plot with Color Map
Scatter plot with color map can provide more information about the data. Here for the parameter color (c) is not a fixed color. It is changing with another column of a data frame. The example below lets the c=‘cylinders’. The scatter plot with color map shows that the more weight, the less mpg; the less cylinder, the bigger mpg and the less weight.

**Example** 
~~~
auto.plot.scatter(x='weight', y='mpg', c='cylinders', alpha=0.4, cmap=plt.get_cmap("jet"), colorbar=True)
plt.show()
~~~

### Scatter Matrix
Using pandas we can create scatter matrices to easily visualise any trends in our data. `pandas.satter_matrix()` generates a matrix of scatter plot of any two numerical columns in a data frame. The scatter matrix below shows that displacement, acceleration, and weight are negatively correlated to mpg; weight and displacement are positively correlated.

**Example**
~~~
pd.plotting.scatter_matrix(auto, alpha=0.4, figsize=(15, 15))
plt.show()
plt.close('all')
~~~
[Back to Top](#In-this-Section)

## Box Plot
A box plot is a way of statistically representing the distribution of the data through five main dimensions:
- Minimun: Smallest number in the dataset.
- First quartile: Middle number between the minimum and the median.
- Second quartile (Median): Middle number of the (sorted) dataset.
- Third quartile: Middle number between median and maximum.
- Maximum: Highest number in the dataset.

### Graphing Box Plots in Pandas
In Pandas, graph box plot using `DataFrame.boxplot()`

**Example**
~~~
# Box Plot of one Column
auto.boxplot(column='mpg',grid=False)
plt.show()

# Box Plot of one Column by other column
auto.boxplot(by='origin', column='mpg',grid=False)
plt.show()

# Box Plot of selected Columns
auto.boxplot(column=['mpg','acceleration'],grid=False)
plt.show()

# Box Plot of selected Columns by othe column
auto.boxplot(by='origin', column=['mpg','acceleration'], figsize=(6,8), grid=False)
plt.show()
~~~

### Graphing Box Plots in Pandas: Numerical and Drop Columns
**Example**
~~~
# Box Plot of all numerical columns
auto.boxplot(grid=False)
plt.show()

# Drop columns 'weight' and 'displacement' - values too big compared with other columns
auto = auto.drop(['weight','displacement'], axis=1)
auto.boxplot(grid=False)
plt.show()
plt.close()
~~~

**<u>NOTE!</u>** use `plt.close()` to close the current figure, use `plt.close(all)` to close all figures. 

[Back to Top](#In-this-Section)
