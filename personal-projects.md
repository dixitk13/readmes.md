#personal-projects


# Enron Data Mining

This personal project caters to the mining of data present in the enron-data-set available at [CMU](http://www.cs.cmu.edu/~enron/).

Data Cleaning and features: 
  - Unique Mails: The dataset consists of duplicate mails. The technique I have used here to eliminate emails duplicate is make an MD5 byte of the following elements : to, from, cc, bcc, subject and first 250 words of the email string. The body of the E-mail is discarded after an MD5 is made except for those who are in the 150 folders - to observe for content analysis. This filtering technique helps eliminate multiple E-mails which need not be processed again. 
  - Duplicate E-mail addresses: There's multiple email addresses belonging to a single person. These E-mail addresses have been unified using a utility written by me which makes use of duplicates.properties - again created manually by me. A part of data cleaning which needed to be done manually. The E-mail addresses are most commonly not following consistent patterns.
  - Distribution Lists: numerous distribution lists/groups were noted on the first run instance. These lists or E-mail addresses have been added to blacklist.properties manually by me to help remove them from the analysis in Enron. These form part of communication which maybe un-interesting or broadcast messages.
  - Multi-threaded Environment: The dataset contains 5,17,401 emails and 150 people's mail-box in raw format. The emails/body/subject need to be extracted from every mail and hence mutli-threading improves the performance of the same. I created a single thread for each person's internal folder (out of the 150 people). This creates about 3,350 threads which process together and converge one-by-one to make a single Set of E-mails present in the dataset. A thread-pool executor is used for this purpose. I do not process mails from distribution lists or people outside the enron. After applying these filtering and cleaning methods we come to 89,515 mails between 16,135 people or Nodes.
  - Content Analysis: For the 150 people we look at the unigram of the mails sent by them so I cna do a content analysis of what these guys talk about. I implement a Postings List from Information Retrieval to do the same and maintain the postings for 150 people only. The output can be seen in peoplecontent.txt and the 150 people are read from viewpeople.properties.
  - Adjacency List and Matrix: To show versatility in implementation of graph algorithm's I implement a Network which can spit out an Adjancey list of a Matrix and have implemented algorithms - some using list some using matrix. The matrix is huge to commit and isn't on github but the list can be found at NetworkMatrix_AdjList.
  - D3 JS graph: a d3 js graph shows the nodes present in the Network aka visualization.

The output of the whole run is present in output.txt. The js files read by the index.html form automatically in the folder called js viz. nodes_150.txt and nodes_all.txt. There's corresponding SVG(scalable vector graphics) files for the two visualization. The 150 people are read from : folder.people.properties.
  - [nodes_150](https://github.com/dixitk13/personal-projects/blob/master/EnronDataMining/js/edges_150.svg) : shows the interaction between the 150 nodes only.
  - [nodes_all](https://github.com/dixitk13/personal-projects/blob/master/EnronDataMining/js/edges_all.svg) : shows the interaction between all the nodes - 16k people.

Graph Algorithms implemented: 
  - Freeman's Degree Centrality
  - Closeness Centrality
  - Farness Centrality
  - Betweenness Centrality
  - EigenVector Centrality - using JBLAS library
  - Transitive Closure
  - FloydWarshall's Algorithm

### Freeman's Degree Centrality
[Degree Centrality](https://www.cl.cam.ac.uk/teaching/1314/L109/stna-lecture3.pdf) gives the centrality measure of a specific node in a network. Since a social network is a directed network we have two kinds of degree centrality - Indegree Centrality and OutDegree Centrality. The central most person is likely to hear information flowing thro' the network first!

### Closeness Centrality
[Closeness](http://faculty.ucr.edu/~hanneman/nettext/C10_Centrality.html#paths) is the measure of "how close a Node is to others in a network". A Node has higher closeness if it is situated closer to all other Nodes. It defines the amount of time it takes for the information to flow accross the network. The Closeness Centrality is normalized using the technique presented by [Tore Opsahl](http://toreopsahl.com/2010/03/20/closeness-centrality-in-networks-with-disconnected-components/).

### Farness Centrality
[Farness](http://faculty.ucr.edu/~hanneman/nettext/C10_Centrality.html#paths) is the exact inverse of closeness.

### Betweenness Centrality
[Betweenness](http://faculty.ucr.edu/~hanneman/nettext/C10_Centrality.html#freebet) is the defined as the the measure by which a Node is favored over the other Node's between a pair of Node's in the network. So if a Node A is not present in a path of pair of Node B and C in a network, the Node A loses some power.
I have implemented [A faster algorithm](http://algo.uni-konstanz.de/publications/b-fabc-01.pdf) stated here using a adjacency list to find betweenness centrality between all Nodes in the Network is implemented and it computes for all Nodes in the Network.

### EigenVector Centrality
[EigenVector Centrality](http://www.markhneedham.com/blog/2013/08/05/javajblas-calculating-eigenvector-centrality-of-an-adjacency-matrix/) finds the influence of a Node in the Network. Its recursive in nature, because the power iteration method to find the EigenVector of Node A relies on the Nodes connected to Node A and their EigenVector values. I've used JBLAS library for the same.

### Transitive Closure
Transitive closure is a boolean matrix defining the reachability relationship of a DAG. The output matrix is not committed on github due to its size.

### FloydWarshall's Algorithm
The [FloydWarshall](http://www.geeksforgeeks.org/dynamic-programming-set-16-floyd-warshall-algorithm/) matrix defines the shortest path from any Node to all other Nodes. It is also called as the "all-pairs-shortest-path" since it defines the shortest path from a single Node to all the Nodes in the matrix.

### Node Analysis: 
Let's jot the top 20 people found with the help of the following algorithms - (in-order)
#### Out Degree Centrality
```sh
| Node                        | Out-bound |
| david.forster@enron.com     | 963       |
| lee.wright@enron.com        | 823       |
| julie.clyatt@enron.com      | 823       |
| sally.beck@enron.com        | 779       |
| sonya.johnson@enron.com     | 709       |
| billy.lemmons@enron.com     | 691       |
| lynette.crawford@enron.com  | 683       |
| louis.allen@enron.com       | 662       |
| david.oxley@enron.com       | 642       |
| tammie.schoppe@enron.com    | 628       |
| constance.charles@enron.com | 616       |
```
#### In Degree Centrality
```sh
| Node                        | In-bound  |
| louise.kitchen@enron.com    | 424       |
| tana.jones@enron.com        | 391       |
| vince.kaminski@enron.com    | 386       |
| sara.shackleton@enron.com   | 369       |
| sally.beck@enron.com        | 352       |
| mark.taylor@enron.com       | 349       |
| ljohn.lavorato@enron.com    | 342       |
| kenneth.lay@enron.com       | 332       |
| jeff.dasovich@enron.com     | 299       |
| jeff.skilling@enron.com     | 291       |
| < 561:steven.kean@enron.com | 290       |
```
#### Closeness Centrality
```sh
| Node                   | Closeness          |
| sally.beck@enron.com   | 0.4024385060829423 |
| david.forster@enron.com| 0.39863597726181366|
| billy.lemmons@enron.com| 0.39516445601416905|
| julie.clyatt@enron.com | 0.39002992792500496| 
| lee.wright@enron.com   | 0.38793394015590627| 
| david.oxley@enron.com  | 0.3819269569733967 | 
| nicki.daw@enron.com    | 0.37958201254961826|
| jeff.dasovich@enron.com| 0.3777866321934469 |
| john.lavorato@enron.com| 0.37571646980345874|
| sonya.johnson@enron.com| 0.3749793396966656 |
```
#### Farness Centrality
```sh
| Node                        | Farness  |
| teresa.rascon@enron.com     | 118719.0 |
| philippe.giguere@enron.com  | 118718.0 |
| john.nemila@enron.com       | 118718.0 |
| mark.eilers@enron.com       | 118718.0 |
| jeri.fish@enron.com         | 118718.0 |
| joe.thorpe@enron.com        | 118718.0 |
| nagwa.elkachouty@enron.com  | 118718.0 |
| val.artman@enron.com        | 118718.0 |
| alaadin.suliman@enron.com   | 118718.0 |
| sunitha.kongara@enron.com   | 118718.0 |
```
#### Betweenness Centrality
```sh
| Node                        | Betweenness      |
| sally.beck@enron.com        | 6620982.311084982|
| vince.kaminski@enron.com    | 4964929.726568458|
| jeff.skilling@enron.com     | 4694979.866902691|
| jeff.dasovich@enron.com     | 3646856.865575315|
| tana.jones@enron.com        | 3352800.345229301|
| kenneth.lay@enron.com       | 3259899.78586894 |
| john.lavorato@enron.com     | 3093945.137707474|
| louise.kitchen@enron.com    | 2950334.655030438|
| shelley.corman@enron.com    | 2469561.474426528|
| sara.shackleton@enron.com   | 2405295.787497394|
| mark.taylor@enron.com       | 2356094.159953910|
```
## Most influential and suspected people out of the analysis:
When we study the output of this cleaned data of which we mine information we come to the conclusion of the following people who lead Enron into its fate of Bankruptcy.
```sh
| Node            | Position                            |
| david forester  | Chairman                            |     
| kenneth lay     | CEO and chairman                    |
| vince.kaminski  | Managing Director                   |
| jeff.skilling   | CEO                                 |
| jeff.dasovich   | Director of State Govt. affairs     |
| louise.kitchen  | Trader(spearheading Europe markets) |  
| john.lavorato   | Chief Executive                     | 
| mark.taylor     | Vice President                      | 
```
### Version
1.0

created using : [Dillinger](http://dillinger.io/)
