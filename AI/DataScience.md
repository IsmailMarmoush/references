### Lesson 1 Introduction

**Substantive Expertise**

* Knows which Questions to ask
* Can interpret data well
* Understands the structure of the data

* Collaborating filtering algorithm (netflix)
* recommending connection (social networking)
* bioinformatics
* urban planning
* astrophysics
* Public health
* sports

### Lesson 2 Data Wrangling

**Data Sanity Checking**
Pandas.describe: count, mean, std, min, 25%, 50%, 75%, max

For each column using the previous attributes you can now do analysis for example checking the count would imply the
missing values, the min and max values are logical or not, also the mean.

* If data are missing randomly it could be ok, but if systematically it will not give good data analysis results.

**Solutions**

* Partial Deletion
    * Listwise (one of two columns missing, then will not use all of it in both analysis)
    * pairwise (will only not use the columns needed)
* Imputation
    * Easy Imputation: put the mean instead of missing values
        * lessens the correlation between imputed variables and any other variable.
    * Linear Regression: predict the value
        * over emphasizes trends (relations between columns would become stronger)

### Lesson 3 Data Analaysis

* Statistical significance test
    * Using Normal Distribution (Gaussian Distribution, Bell Curve)

**Normal Distribution**

* Mean (meu)
* Standard Deviation (Sigma)
* Variance (sigma^2)
* Welch test
* Non parametric test
    * mann whiteny u test
* non normal data

Data Scientist has many tools (statistical tests).

**Stats vs Machine Learning**
Philosophical difference:

* Statistics is focused on analyzing existing data and drawing valid conclusions
* Machine Learning is focused on making predictions.
* Clustering, hierarchical clustering
* PCA principal Component Analysis
* using k means clustering and pca to reduce dimentiality

**Coefficient of Determination**
The closer R^2 to one the better our model

**Kurt Advice on machine learning**

* use k means and pca to understand data more
* look closely to see which attributes really affect predictions

### Lesson 4 Data Visualization

* Visual Encoding
    * Hue and saturation colors
    * 1985 AT&T research graphical perceptions and methods and their effectiveness order
* Numeric Data
* Categorical Data
* Time series data
* Data scales
* Visualizing Time series data
    * Scatter plots
    * Line charts
    * LOESS curve
* Multivariate Data

## References

* http://statsguys.wordpress.com/
* http://en.wikipedia.org/wiki/Principal_component_analysis
* http://georgemdallas.wordpress.com/2013/10/30/principal-component-analysis-4-dummies-eigenvectors-eigenvalues-and-dimension-reduction/
* http://blog.revolutionanalytics.com/2013/05/statistics-vs-data-science-vs-bi.html
* http://www.dataversity.net/distinguishing-analytics-business-intelligence-data-science/
* http://www.sas.com/en_us/industry/defense-security.html
* http://rapidminer.com/download-rapidminer/
* http://www.talend.com/download
* http://www.spagoworld.org/xwiki/bin/view/SpagoWorld/Download
* http://en.wikipedia.org/wiki/Weka_(machine_learning)

## Reading DataScience

http://www.fast.ai/2018/01/26/v2-launch/
https://docs.google.com/presentation/d/1kSuQyW5DTnkVaZEjGYCkfOxvzCqGEFzWBy4e9Uedd9k/edit#slide=id.g22aaaf9c33_0_23

### Data Sources

* http://www.andresmh.com/nyctaxitrips/
* https://archive.org/download/nycTaxiTripData2013/

### Deep learning

* https://developer.nvidia.com/deep-learning-getting-started

### Datascience Books

* http://www.manning.com/marz/
* Machine Learning for hackers https://github.com/johnmyleswhite/ML_for_Hackers
* The complete idiots guide to statistics
* http://www.f6s.com/voxdel

### Recurrent Neural Networks

* http://karpathy.github.io/2015/05/21/rnn-effectiveness/

### Online

* https://en.wikipedia.org/wiki/Lambda_architecture
* http://karpathy.github.io/2015/05/21/rnn-effectiveness/
* https://www.edx.org/course/scalable-machine-learning-uc-berkeleyx-cs190-1x?utm_source=edX+Course+Announcements+Mailing+List&utm_campaign=d39b3ebee9-Student_Newsletter_February_23_CS&utm_medium=email&utm_term=0_237694b56d-d39b3ebee9-51804889#.VO7CkHWGm00

## Mario, NEAT

MarI/O is a program made of neural networks and genetic algorithms that kicks butt at Super Mario World. Source
Code: http://pastebin.com/ZZmSNaHX
"NEAT" Paper: http://nn.cs.utexas.edu/downloads/pap... Some relevant Wikipedia links:
https://en.wikipedia.org/wiki/Neuroev...
https://en.wikipedia.org/wiki/Evoluti...
https://en.wikipedia.org/wiki/Artific... BizHawk Emulator: http://tasvideos.org/BizHawk.html

SethBling Twitter: http://twitter.com/sethbling
SethBling Twitch: http://twitch.tv/sethbling
SethBling Facebook: http://facebook.com/sethbling
SethBling Website: http://sethbling.com
SethBling Shirts: http://sethbling.spreadshirt.com
Suggest Ideas: http://reddit.com/r/SethBlingSuggestions

Another one made it https://www.youtube.com/watch?v=xOCurBYI_gY&feature=youtu.be

### Types of Data

- Biostatistics for medical data
- Data Science for data from web analytics
- Machine learning for data in computer science/computer vision
- Natural language processing for data from texts
- Signal processing for data from electrical signals
- Business analytics for data on customers
- Econometrics for economic data
- Statistical process control for data about industrial processes

### Tools

* https://github.com/PredictionIO
* Spark
* Mahout
* Giraph (graphs)
* Cassandra
* Hadoop
    * Hive
    * Pig
* https://github.com/vkostyukov/la4j

### Types of Data science Questions

* Descriptive
    * Census
* Exploratory
    * Correlation doesn't imply causation
* Inferential
* Predictive
* Causal
* Mechanistic

### Confounding

Pay attention to other variables that might be causing the relationship, because correlation is not causation.

* Shoe size -> literacy
* Age -> shoe size , Age -> literacy

### Pioneers

* Nate Silver
* Drew conway  https://github.com/drewconway, http://drewconway.com/
    * Machine Learning for hackers https://github.com/johnmyleswhite/ML_for_Hackers
* Kurt smith https://twitter.com/kurtosis0
* Don dini principle data scientist T&T http://dmdini.com/
* http://ramnathv.github.io/

### Resources

* http://stats.stackexchange.com/
* https://www.udacity.com/courses#!/data-science
* http://www.datasciencecentral.com/profiles/blogs/great-list-of-resources-nosql-big-data-ml-and-much-more-posted-on
* graphical perceptions and methods AT&T
