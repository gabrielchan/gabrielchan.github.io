# Gabriel's Library

This is a list of documentation, books, articles, blog posts and other forms of content that I found interesting, helpful, and/or educational. 

## Organization System

The content will be tagged as follows: "(Domain-Type) Link"
- Context: Why I was drawn to this content
- Helped: How it helped me

Domains:
- GEN: General
- COMM: Communications
- SDLC: Key things for working as a developer in a company
- DE: Data engineer and big data topics
- ML: Machine learning, AI and data science topics
- FE: Front-end development topic
- BE: Back-end development topic

Types:
- EDU: Educational or teaching materials
- INT: Something interesting
- REF: Technical reference
- THT: Good thought piece

# References
## April 2021
- (ML-EDU) [Randomized Search Cross Validation with Scikit-Learn](https://jamesrledoux.com/code/randomized_parameter_search)
  - **Context**: Lead data scientist used randomized search as a method to tune a model's hyperparameter. This is a process intensive option so the ask was to see of the library `joblibspark` could let this function leverage a spark clustered back-end instead. Important to understand how Scikit-Learn's `RandomizedSearchCV()` function works first.
  - **Helped**: Provided a detailed tutorial of how a basic Randomized Search works on a test data set (Iris data) and an overview of what hyperparamters are, what hyperparameter tuning is and why it's important
- (SDLC-REF) [Git Switch for Pulling a Remote Branch](https://stackoverflow.com/questions/9537392/git-fetch-remote-branch)
  - **Context**: Needed to pull a remote branch that wasn't in my local and did not remember the steps (e.g., something like fetch then pull?)
  - **Helped**: `git switch <remote_branch_name>` is a new git feature that would let you pull a remote branch, if it's not in your local it just creates its. Very handy for a quick pull. You also don't need to write "origin". [Official reference](https://git-scm.com/docs/git-switch)
- (COMM-INT) [Setting KPIs for Internal Platform(s)/Product(s) by Willemdoesproduct](https://hackernoon.com/setting-kpis-for-platform-products-511m3zdg)
  - **Context**: Provided by lead when coming up with success factors for a project
  - **Helped**: Key takeaway is to focus on the time to conduct a standard BAU operation on the product
- (ML-REF) [Class Labels in the Context of Supervised Learning / Classification by blazs](https://stackoverflow.com/questions/36362541/in-data-mining-what-is-a-class-label-please-give-an-example)
  - **Context**: Mathematical reference of a decision tree model referenced "class labels" when speaking to the probability of a given boolean when building the decision tree
  - **Helped**: Clarfied that a class label is essentially a discrete or categorical variable related to a given set of data (e.g., yes/no, true/false)
- (ML-EDU) [Decision Tree Classifer by Google Developers](https://www.youtube.com/watch?v=LDRbO9a6XPU)
  - **Context**: Existing model built uses a decision tree learning algorithmn
  - **Helped**: Provided a great overview of the CART (Classification and Regression Trees) algorithm with sample code and examples. In short it recursively builds a tree by identifying the "best boolean question to ask" at a node on the tree to split the data set in two until all the data is identical (that is, *unmixed*). A leaf is then created saying what the % chance a given set of data equates to a label. It uses *Gini Impuirity* (if we were to randomly attempt to match between data and labels, what is our probability of guessing wrong) and *Information Gain* (`IG = gini_impurity(parent) - cumulative_avg(gini_impurity(true_child), gini_impurity(false_child))`. How much does a boolean question reduce the impurity)
- (GEN-EDU) [Python's Sequence Unpacking by Sadrach Pierre](https://towardsdatascience.com/sequence-unpacking-in-python-14d995f9a619)
  - **Context**: Lead DS I'm working with used this but I didn't understand the syntax
  - **Helped**: Gave a detailed overview of how sequence unpacking works, and some tricks such as unpacking a object within an object ("()"), ignoring something ("_"), and taking an arbitrary amount of stuff ("*")
- (ML-EDU): [One-Hot Encoding by DeepLizard](https://www.youtube.com/watch?v=v_4KWmkwmsU)
  - **Context**: A pipeline I am working with uses one-hot encoding
  - **Helped**: Provided a high-level explaination of what one-hot encoding is. In short, it is representing categorical data that a ML model would often not understand into binary numbers that the model would understand. It converts it into a vector of length number of categories, where each value is either 0 or 1 depending on what the category is for a particular item
- (DE-EDU): [Spark Executor Cores and Memory by Spoddutur](https://spoddutur.github.io/spark-notes/distribution_of_executors_cores_and_memory_for_spark_application.html)
  - **Context**: Understanding how Spark executor configuration works
  - **Helped**: Provided a detailed outline of how to set this configuration, the "behind the scenes" services that need compute assigned for it to run well (e.g., hadoop, yarn, etc.)
- (DE-EDU): [AWS Elastic Netowrk Interfaces Blog by Amazon](https://aws.amazon.com/blogs/aws/new-elastic-network-interfaces-in-the-virtual-private-cloud/)
  - **Context**: For the AWS Solutions Architect Certification
  - **Helped**: Provided additional explaination on what an ENI is. In short, like other aspects of AWS, its the ability to highly configure and move around a particular component - specifically IPs

## March 2021
- (GEN-EDU): [Binary Heaps in Python by NoobCoder](https://www.youtube.com/watch?v=hkyzcLkmoBY)
  - **Context**: Needed a data structure that would allow me to track a max item of a list without needing to spend O(nlog(n)) just to sort and maintain a max/min each time. A priority queue / max-heap suits this scenario
  - **Helped**: Very educational walkthrough (and refresher from Academia) of the data structure
- (GEN-REF): [Python3 Floor Division vs Regular Division](https://stackoverflow.com/questions/49282799/python-3-int-division-operator-is-returning-a-float)
  - **Context**: Py3 `int/int` division returned a float
  - **Helped**: Provided tech reference of why `/` will return a float. If you want to maintain the type you should use **Floor Division `a//b == floor(a/b)`** instead. This will also maintain typing
- (DE-EDU) [Options to Process a Pandas DataFrame](https://stackoverflow.com/questions/16476924/how-to-iterate-over-rows-in-a-dataframe-in-pandas)
  - **Context**: Needed to understand how to iterate through rows in a Pandas DF
  - **Helped**: Provided context of why iterating through a dataframe isn't reccomended, and why transformations are prefered from an optimization standpoint. In short - DataFrames can be very large and iterating through each row is an anti-pattern towards the efficiency that a DataFrame is suppose to bring

## Feburary 2021
- (DE-EDU) [What makes a subnet Public vs Private?](https://stackoverflow.com/questions/48830793/aws-vpc-identify-private-and-public-subnet)
  - **Context**: See below
  - **Helped**: In short, if the subnet has a route that leads to an internet gateway, it's public
- (DE-EDU) [AWS EC2 Instance Public IP](https://stackoverflow.com/questions/26706683/ec2-t2-micro-instance-has-no-public-dns)
  - **Context**: EC2 instance spun up by Terraform isn't being assigned a Public IP even though it's being explictly told too
  - **Helped**: Indicated that a VPC on a Private Subnet can never have a public IP
- (DE-EDU) [What is a Data Pipeline](https://www.xplenty.com/blog/what-is-a-data-pipeline/)
  - **Context**: Needed a formal understanding of a data pipeline, key operations, and terminonlogy
  - **Helped**: This article gave a high-level overview of how a data pipeline is structured, data lake vs data warehouse, and key attributes

## January 2021
- (DE-EDU) [Spark - Introduciton to Partitioning](https://www.talend.com/blog/2018/03/05/intro-apache-spark-partitioning-need-know/)
  - **Context**: Wanted to understand the default partitioning behaviour and why Spark isn't automatically optimal
  - **Helped**: According to the above documentation, if left alone, Spark may distribute the data in a skewed way across its executors, causing an overloaded executor to become a bottle neck. This leads to an inefficient program
- (GEN-EDU) [Why Use Docker? By ActiveLAMP](https://www.youtube.com/watch?v=SYozbyvsP8A)
  - **Context**: Need to understand what Docker is, what it's difference is with kubernetes, and why it's important?
  - **Helped**: Explains why Docker is useful in a world where scalability is important. Docker gives you the ability to containerize your services and provide easy deployment and management of them. Multiple containers can be run on a single kernel
- (GEN-EDU) [What is Kubernetes? By Google](https://www.youtube.com/watch?v=cC46cg5FFAM)
  - **Context**: Needed to understand how Kubernetes interacts with a general cloud architecture
  - **Helped**: Provided the key overview of Kubernetes being the "container orchestrator", similar to a conductor in a orchestra. Kubernetes gives you the ability to automate and manage your countainers across a cluster of nodes on the cloud (e.g container provisoning, networking, etc.)
- (DE-REF) [Cheapest Spark RDD Action Operation (hint: it's `first()` but it might not always be what you need)](https://stackoverflow.com/questions/42272800/what-is-best-or-most-lightweight-efficient-cheapest-rdd-action-to-perform-on-hug#:~:text=1%20Answer&text=answer%20was%20accepted%E2%80%A6-,rdd.,materialize%20all%20partitions%20is%20rdd.)
  - **Context**: Needed to conduct an action to increment a accumulator, but wanted to not use something as expensive as `collect()` or `count()`
  - **Helped**: Showed me `first()` but also warned of why its not always a one-size-fit all cheap operation
- (DE-EDU) [High-Level Overview of RDD Transformations vs. Action Operations](https://medium.com/@aristo_alex/how-apache-sparks-transformations-and-action-works-ceb0d03b00d0)
  - **Context**: Refresher on how RDD operations work
  - **Helped**: Overview on how Transformations are when we 'change an RDD' into a new one within each individual executor, Actions have executors compute a result and return it to the driver. It also reviews that Transformations are lazy. Transformations will not be done until an action is called, thus all transformations before it will be done such that the action can be performed
- (GEN-EDU) [List Comprehension in Python](=https://medium.com/better-programming/list-comprehension-in-python-8895a785550b)
  - **Context**: Needed to understand why, given some list_1 that contains `''`, `list_2 = [x for x in list_1 if x]` removes the `''`
  - **Helped**: Gave a good overview of how to breakdown the list comprehension syntax into a standard for loop. This syntax essentially looks for if x contains any value, then it returns true. Thus it "adds" the value from list_1 to list_2
- (DE-REF) [Why PyCharm Warning for SparkSQL Column Parameter Can Be Ignored](https://stackoverflow.com/questions/33375535/expected-type-unionstr-bytearray-got-int-instead-warning-in-write-metho)
  - **Context**: When trying to do something like `df1.select("id").join(df2, df1.id == df2.id)`, PyCharm returns a error along the lines of `Expected Type Union[...], got 'bool' instead`
  - **Helped**: This post indicated that PyCharm attempts to guess (based on the limited information its provided in the IDE) to guess if the provided inputs are of correct type. Because directly calling the column like `df1.id` is some "intelligent magic" that PySpark does at run-time, PyCharm doesn't know that `df1.id == df2.id` is a valid input for PySpark to interpret. Therefore it spits a warning
- (DE-REF) [Spark .repartition() vs .coalesce()](https://stackoverflow.com/questions/31610971/spark-repartition-vs-coalesce)
  - **Context**: Previous Data Engineer specifically used `.repartition(15)` right after a DataFrame was created. Was curious of why that action was chosen. Consulting the lead developer later, it was because they wanted to use the max number of cores available
  - **Helped**: This documentation helped me understand why these functions are used and why it can be expensive if used improperly (due to a expensive shuffle of data across the cluster). Repartition will distribute the data evenly across n nodes. It seems that generally, if I'm reducing the number of nodes - coalesce is better because the nodes that have data being moved to it does not get shuffled. This document also enlighted me to `partitions.size`
- (DE-THT) [How to Become a Data Engineer in 2021](https://khashtamov.com/en/how-to-become-a-data-engineer/)
  - **Context**: Found this on /r/dataengineering
  - **Helped**: Although this isn't a bible of what is needed to be a DE, I think its a good reference of tools, languages and skillsets that are generally required paired with reccomended teaching tools
- (ML-EDU) [Neural Networks from Scratch in Python by Kie Codes](https://www.youtube.com/watch?v=51EoNgwoaTo)
  - **Context**:
  - **Helped**:
- (COMM-EDU) Never Split the Difference by Chris Voss
  - **Context**: Interesting book that was reccomended by a dear friend in regards to job negotiation
  - **Helped**: This book not only goes over how to negotiate and get what you want, but also how to properly listen and communicate to find a mutually agreeable middle ground. As a developer I will be negotiating for my job, ticket sizes, and technical decisions, I want to be equipped to do this effectively
- (SDLC-THT) [6 Things I Wish I Knew At my First Software Engineering Job by Udara W](https://levelup.gitconnected.com/6-things-i-wish-i-knew-at-my-first-software-engineering-job-f2cdd4e41ca2)
  - **Context**: As I am starting my first data engineering role, I wanted to make sure I don't make beginner mistakes
  - **Helped**: Content reminded me to focus on more than just the code, but also to bring 'big picture' and communication aspects from my consulting days