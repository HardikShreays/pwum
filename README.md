pwum
=============

pwum is a set of python scripts for working with web log files and extracting frequent patterns and clustering sessions. 

Two main functions:

Finding frequent patterns. Extract frequently co-accessed pages in web sessions. Uses traditional frequent pattern mining algorithm Apriori. For more information on the implementation, please see [here](http://xc.ee/wp-content/uploads/2011/03/report-pattern-mining-web-logs.pdf)

Finding similar sessions based on behavior,i.e, visited pages by clustering. Available methods are based on building Markov chain like transition matrix out of session and clustering these or representing sessions as simple feature vectors. Clustering is currently done by the k-means algorithm.
More detailed description [here](http://xc.ee/wp-content/uploads/2011/03/poster-clustering-web-users.pdf)




Installing
-----------
Tested with Python 2.6
No installation is needed, but there are dependencies:

* numpy
* Pycluster
* matplotlib (optional)


Using pwum
-----------

    python pwum.py [logfile|directory containing only logs]

or see options

    python pwum.py -h

outputs two HTML files to the `example` folder, one containing information about frequent patterns and other lists clusters information.




## Some notes
Due to the complex nature of the task, the current scripts are not meant for distributed as python packages. Currently, there are many implemented methods in the code, but there is no convenient configuration available to select from.

Only apache log files in common log format are supported (see data for examples).
logparser.py and logreader.py are responsible for construction sessions from files. If you have logs with different structure, modify the implementation. logparser currently composes sessions using the timeout window.

Some configuration options are available through config.py editing.

Note this code is meant for prototyping and is not scalable to large amounts of data, as it keeps all data in memory.



