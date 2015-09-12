# Information-Retrieval
Consists of projects for CS6200 - Information Retrieval



### [Focussed Crawler](http://www.ccs.neu.edu/course/cs6200f14/hw1.html)

The crawler starts with the seed as http://en.wikipedia.org/wiki/Gerard_Salton and crawls to a depth of level 3 from the seed URL. It requests documents over HTTP and ends when the third level of documents are crawled.
The following filters where applied for the links to be selected : 
 - Crawls only wikipedia pages aka pages with prefix "http://en.wikipedia.org/wiki/"
 - Crawls pages without ":" in their URL
 - Can crawl pages based on an optional "keyphrase" to perform focussed crawling. Depending on the presence of a keyphrase the link can be choosen to crawl/not crawl.

Based on the following filters and the seed - number of documents retrieved for unfocussed crawling is about 4,000 documents.

### [Pagerank Algorithm](http://www.ccs.neu.edu/course/cs6200f14/hw2.html)
The classic pagerank algorithm is implemented here for a collection of 183,811 web documents - [the famous WT2g collection](http://ir.dcs.gla.ac.uk/test_collections/access_to_data.html). 
It is iterative in nature and in the end retrieves the top-pages ranked according to the algorithm. The algorithm uses a perplexity based entropy calculation to find out the convergence. If the perplexity of the pagerank distribution remains constant for about 4 times, we consider that its "converged".

The detailed explaination and analysis for Pagerank of documents and their ID is given in the document [PageRank algorithm Analysis.docx](https://github.com/dixitk13/Information-Retrieval/blob/master/Pagerank%20Algorithm/PageRank%20algorithm%20Analysis.docx) inside the project folder. It gives details of pagerank by in-link count and pagerank values as well as why the document is ranked higher. The verification is done by the [Lemur interface](http://fiji4.ccs.neu.edu/~zerg/lemurcgi_IRclass/lemur.cgi) provided here.

### [Zips law](http://www.ccs.neu.edu/course/cs6200f14/hw3.html)
This program explore's Zipf's law. It does calculations such as probability of the word, its rank and more details. The [perl script](http://www.ccs.neu.edu/course/cs6200f14/parse.pl) is used to strip off the punctuations from the text file.

The zipf's law is closely related to the number of postings that a inverted index would have and what amount of that could be dropped from the index. The program verifies zipf's law in the text for the document [Alice in Wonderland](http://www.gutenberg.org/ebooks/11) from the [Project Gutenberg website](http://www.gutenberg.org/). The output is an HTML file which shows the details in a tabular format.

The detailed graph and [report](https://github.com/dixitk13/Information-Retrieval/blob/master/Zips%20law/hw3.docx) is present in the project folder. There is also a design document for a plagiarized detection system which encompasses a  large collection of documents.

### [SmallSearchEngine](http://www.ccs.neu.edu/course/cs6200f14/hw4.html)
Implemenets the BM25 retrieval model. The search engine works in two parts:
 
 - [Indexer](https://github.com/dixitk13/Information-Retrieval/blob/master/SmallSearchEngine/indexer.py) : The indexer does the work of creating an inverted index from the provided input [tccorpus](http://www.ccs.neu.edu/course/cs6200f14/tccorpus.zip). It reads the documents from the file provided in raw format defining the document ID and its contents.

 - [Retriever](https://github.com/dixitk13/Information-Retrieval/blob/master/SmallSearchEngine/bm25.py) : The retriever reads the queries based on the input queries provided in the file queries.txt and produces the most relevant pages for that specific query.

 The details of [implemenetation](https://github.com/dixitk13/Information-Retrieval/blob/master/SmallSearchEngine/Q2_SmallSearchEngine_describe_implementation.docx) and report are present in the project folder again.

### [WeightedPageRank](http://people.cis.ksu.edu/~halmohri/files/weightedPageRank.pdf)
Small use of how a weighted pagerank works. It is part of power iteration method which takes into account the weights of the links which are present. More used in Eigen Vector calculation which finds the dominant Eigen Vector in the collection - used more in Network Analysis.
