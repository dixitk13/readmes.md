# parallel-data-processing-in-class
Consists of in-class assignments for CS6240 - Parallel Data Processing

Various class homeworks have various different smaller datasets 

Technologies Used: Java, sqlite3, R, Spark, Scala, Amazon Web Services CLI, Elastic-MapReduce, S3, Shell scripts, makefile


### [Factors]()

A "Factorize.java" program which uses threads to find factors.


### [sqlite3]()
Finds the following queries using sqlite3:
- In 2009, which player hit the most homeruns per dollar of salary?
- What did they get paid per home run?
- In 2008, which team paid the highest average price per homerun?
- What did they pay per home run?

Dataset: http://www.ccs.neu.edu/home/ntuck/courses/2016/01/cs6240/data/lahman-baseball-2014.tar.gz

### [R]()
Generate a plot of player salary (in Salaries.csv) vs. homeruns (HR in Batting.csv).
Save the image as a PNG.

Dataset: http://www.ccs.neu.edu/home/ntuck/courses/2016/01/cs6240/data/lahman-baseball-2014.tar.gz


### [complex-reducer]()

A custom partitioner that splits the keys among three reducers:
-   Words starting with a capital letter.
-   Words starting with a lowercase letter.
-   Words starting with a non-letter.
The Map-reduce program outputs the total number of words in their category to stdout,
E.g. (System.out.println ("There are " + count + " words starting with letters like [" + sampleLetter + "]");)

### [joins-in-map-reduce]()
A map-reduce job which will calculate, for each (player, year), how much the player was paid per home run.

### [starting-spark]()
A Spark program that finds 
- the (player, year) that hit the most home runs per dollar of salary.
- the (name, year) of the pitcher (appears in Pitching.csv) with the best batting average (Hits / At Bats).

### [fast-queries]()
A spark based inverted index with Two Spark programs:
- Build index.
- Query list of teams for a player ordered by year.

### [Sockets]()
A prime checker tool that works as follows:

- You start up N server processes with a script called as "./start N".
- Each server process is started with a single integer X as a parameter.
- When a server starts up, it listens on port 10000 + X for connections.
- When a server gets a connection, it listens for a number Y and checks if Y is divisible by X. If so, it sends back X. Otherwise, it connects to port 10000 + X + 1, sends on Y, waits for a response, and then sends back that response.
- The client takes a number as an argument, sends that number as a query to port 10002, and prints the response (e.g. the first integer >1 that divides the number) as well as "prime" if the number is prime or "not prime" if not.

### [Shortest Path]()

Implements a shortest path algorithm to find the shortest path from the "Apple" article to the "Ivory" article in the included Wikipedia graph. Here the graph is the inlinks graph of the wikipedia crawl.

### Version
1.0

created using : [Dillinger](http://dillinger.io/)
