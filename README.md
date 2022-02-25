# Community detection in collaboration network

- Network: [Collaboration network](https://snap.stanford.edu/data/ca-AstroPh.html#:~:text=Dataset%20information-,Dataset%20information,edge%20from%20i%20to%20j.) between authors in Astro Physics category.
- Community detection with 2 different methods and comparison
- Communities represent authors that are working on similar topics 

## Methodology
**1. Louvain community detection (community library)**
 - Complexity:  O(n*log2n)
 - Optimization of modularity.
 - First small communities are found, then each small community is grouped into one node and the first step is repeated

**2. Clauset-Newman-Moore greedy modularity maximization (networkx library)**
 - Complexity: O(m*n*log(n)).
 - Modularity maximization method.
 - Begins with each node in its own community and joins the pair of communities that most increases modularity until no such pair exists.

## Experimental setup
Single nodes that are not connected to the network (separate components of size 1) are removed! For plotting custom interactive Dash application ([NetHi](https://github.com/egalijatov1/NetHi)) will be used that removes edges so that communities can be easily observed (plotting edges worsens visibility of communities)!

Evaluation: 
- Modularity 
- Coverage (ratio of the number of intra-community edges to the total number of edges in the graph)
- Average community size

**Network properties:**

![image](https://user-images.githubusercontent.com/88715320/155748062-f8b0fc60-ec0c-435b-bdc7-1fdfd173184c.png)

## Results
**1. Louvain community detection**
- Number of communities detected: 326
- Size of largest community: 1983
- Size of smallest community: 1
- Modularity of partition: 0.626461
- Coverage:  0.692
-Average community size: 177
- Communities that have more than average nodes: 22
![image](https://user-images.githubusercontent.com/88715320/155748299-62176014-110c-4342-a19b-dd9a38febbea.png)

**2. Clauset-Newman-Moore greedy modularity maximization**
- Number of communities detected: 440
- Size of largest community: 4910
- Size of smallest community: 1
- Modularity of partition: 0.49595
- Coverage: 0.782
- Average community size: 84
- Communities that have more than average nodes: 11
![image](https://user-images.githubusercontent.com/88715320/155748547-0d8995a9-aa3f-483e-b830-0e53fb1e1f4e.png)

## Discussion
- Greedy modularity maximization took a lot more time to compute communities (number of edges slows down the execution).
- Based on visualizations and average community size we can conclude that Louvain created more larger communities (average size 177), while greedy algorithm produced more communities in total (average size 84). 
- Louvain gave far better modularity (0.626 in comparison to 0.495), while greedy algorithm gave better coverage (0.782 in comparison to 0.692).

