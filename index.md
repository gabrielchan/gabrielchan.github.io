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