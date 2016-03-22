# parallel-data-processing
Consists of projects for CS6240 - Parallel Data Processing

Dataset: Bureau of Transport Statistics' On-time Performance (OTP) dataset has information about flights in the USA. The full dataset covers 27 years of air travel and is over 60GB in plain text => 
- https://s3.amazonaws.com/cs6240sp16/all-v1.tar 
- s3://mrclassvitek

Data Description: http://www.transtats.bts.gov/Fields.asp?Table_ID=236

Technologies Used: Java, R, Spark, Scala, Amazon Web Services CLI, Elastic-MapReduce, S3, Shell scripts, makefile


### [Cluster Analysis](https://github.com/dixitk13/parallel-data-processing/blob/master/hw2-Cluster\ Analysis)

A Hadoop Map-reduce code that can run in pseudo-distributed mode as well as on EMR. Plots the graph of average ticket price for each month for each airline in R.


### [Comparisons](https://github.com/dixitk13/parallel-data-processing/blob/master/hw3-Comparisons)
A map-reduce code which finds mean, median, fast median for single threaded Java, multi-threaded Java, pseudo-distributed MR, and distributed MR. 

### [Linear Regression](https://github.com/dixitk13/parallel-data-processing/blob/master/hw4-Linear\ Regression)
Compute linear regressions for {distance traveled, flight time} using pipeline of jobs to run on EMR (map-reduce) and locally. 

### [Missed Connections (Map-Reduce)](https://github.com/dixitk13/parallel-data-processing/blob/master/hw5-Missed\ Connections\ (Map-Reduce))

Finding connections and missed connections in Map-reduce. 
Connection : is any pair of flight F and G of the same carrier such as F.Destination = G.Origin and the scheduled departure of G is <= 6 hours and >= 30 minutes after the scheduled arrival of F. 
Missed Connection : is when the actual arrival of F < 30 minutes before the actual departure of G.

### [Missed Connections (Spark)](https://github.com/dixitk13/parallel-data-processing/blob/master/hw6-Missed\ Connections\ (Spark))
Finding missed connections in Spark

### [Prediction & Routing](https://github.com/dixitk13/parallel-data-processing/blob/master/hw7-Prediction\ &\ Routing)

- Prediction: Build a model. Take a single test file. This represents all the future flights we want to predict. Output a file containing predictions in the format [FL_NUM]_[FL_DATE]_[CRS_DEP_TIME], logical. The first column uniquely identifies a flight and the second is TRUE if the flight will be late.

- Routing: Build a model. One single test file that contains all scheduled flights for the next year, to create itineraries, and one request file. For each request, your program should propose an itinerary, written flight_num, flight_num, duration


### Version
1.0

created using : [Dillinger](http://dillinger.io/)
