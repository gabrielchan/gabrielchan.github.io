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