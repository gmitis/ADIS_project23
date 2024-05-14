### Back log:
- create kubernetes cluster
- create a home server and run Kubernetes cluster there
- search for online free VMs

#### Project:
- follow templates: https://www.ieee.org/conferences/publishing/templates.html
- 

Description:
PrestoDB, Trino - > distributed SQL query engines (heterogenous data sources)
Task-> performance queries, data location, storage technologies 
Cassandra, Postgre, Redis-> data sources 

Steps:

0. Prep  
1. Installation/Setup (PrestoDB, Trino, SQL, PostGre, Redis)
2. Data generation 
3. Query generation 
4. Measurement of performance 

Tasks:
0. 
  - search (sources/documentation)
  - read (similar projects {docker images, report structure, methodology}, documentation, exercises, TPC-DS benchmark, LaTex) 
  
1.
  - create docker script for installation of db's (search/run/debug)  
2.
  - find data generator 
  - create dataset (billions records/not able to fit ram) 
  - load dataset (different of distributing tables (different stores etc), devise strategy) 
  - test db's with dataset 
3.
  - get wrecked with documentation and understand all of the theory 
  - select set of queries (simple, complex, cover dataset) 
4.
  [ identify variables that affect query quality and try to find a very good solution with different data sources and execution ] 
  - measure performance (query latency, optimizer plan) 
  - execute over (different number of workers, different distribution plan) 

Thoughts:
- Try a lot of different experiments and try to find a pattern, see where and when the performance indicators converge optimally (brute force, educated guess, algorithm) 
- create a log of actions 

Problems/Solutions:
- I don't have okeanos resources 
-> Write scripts on docker/kubernetes and be flexible about where to execute them 
-> ask someone to give you their resources 
-> find free/cheap online vms 

- I don't know jack shit about these db's and have a lot of gaps in db's 
-> study a lot u dumbass

Sources:
- online free VMs: https://www.reddit.com/r/cloudcomputing/comments/uxs3lu/is_there_a_free_cloud_based_virtual_machine/
- TPC-DS benchmark: https://www.tpc.org/tpcds/