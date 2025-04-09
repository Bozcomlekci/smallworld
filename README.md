**One of the early key papers that launched network science is the one by Watts and Strogatz, titled [&#34;Collective dynamics of ’small-world’ networks&#34;](http://snap.stanford.edu/class/cs224w-readings/watts98smallworld.pdf) Nature, 1998. This article demonstrates that many biological, technological and social networks consist of a connection topology which is not either completely random or completely regular. In the intermediary region between randomness and regularness, peculiar types of networks are present and they are called small-world networks. Some of the examples to these networks are the power grid of the western United States, the neural network of the worm Caenorhabditis elegans and the collaboration graph of film actors. In this article, regular networks are reorganized via a rewiring procedure to obtain the described small-world networks.**

**Small-world networks have peculiar properties regarding propagation speed. To show that, an example of infectious diseases propagating through the network is covered in the article. According to this theory, infectious diseases spread more easily in small-world networks than in regular lattices.**

**Throughout this report, the theory behind small-world networks will be explained by defining appropriate parameters of a graph. Then utilizing computer-generated networks as described in the paper, the figures in the paper will be reproduced.**

### Theory

Initially, we need to start with the definition of the appropriate parameters of our ring-shaped graph. These are:

* *$N$*: Number of vertices in the graph
* *$k$*: Number of edges for each vertex (even to make initial regular connections symmetric)
* *$p$*: Probability to rewire the graph edges in the rewiring process.

Once the parameters are defined, construction of the graph is performed according to the following procedure:

1. Start with a circularly aligned N vertices.
2. Connect each vertex to its k nearest neighbor (even k). Do not allow duplicate edges.
3. Select a vertex and the edge to its ith nearest clockwise neighbour vertex (initially, first nearest neighbour). Rewire this edge to a random vertex with probability p. Do not allow duplicate edges.
4. Iterate over all of the vertices in clockwise direction to apply the rewiring procedure.
5. Once one lap is completed, proceed with the (i+1)th nearest neighbours. Apply the same procedure for the next lap.
6. The procedure should be applied for k/2 laps to complete the rewiring and thus, the construction of the intended graph.

The graph will be available for an analysis when these steps are completed.

The graph topology can be in 3 different ways:

* *Fully regular when p=0:* Basically, rewiring procedure is skipped.
* *Intermediary networks 0<p<1:* The graph becomes increasingly disordered p. For some values of p in this region, small-world phenomenon is observed.
* *Fully random when p=1:* Each edge is connected randomly yielding a random network.

To collect information on the topology of the graph, two informative metrics are defined:

* **Characteristic Path Length, L(p)**: Average of the shortest distance between any two vertices on the graph. This property provide information concerning the global topology of the graph.
* **Clustering Coefficient, C(p)**: Average of the proportions of connections among the neighbours of a graph to maximum number of connections among these neighbours ($\frac{k(k-1)}{2}$). This property provide information concerning the local cliqueness of the graph.

For example, in a friendship network, L is the average number of friendships in the shortest chain connecting two people and C measures the cliquishness of a friendship circle.

Given these measures, a fully regular (p=0) and a fully random (p=1) networks display the certain trends for these metrics.

* **For a fully regular (p=0) network,** $L \sim \frac{n}{2k}$ and $C \sim \frac{3}{4}$
* **For a fully random (p=1) network,** $L\_{random} \sim \frac{ln(n)}{ln(k)}$ and $C\_{random} \sim \frac{k}{n}$

In conclusion, small-world phenomenon in slightly randomly connected networks are confirmed. For some values of p, we are able to obtain high local connectivity (cliqueness) measured by $C(p)>C\_{random}$ and low characteristic path length $L(p)\sim L\_{random}$ simultaneously. These values imply the existence of a small-world phenomenon in the network.

#### References

[1] Watts, D., Strogatz, S. Collective dynamics of ‘small-world’ networks. Nature 393, 440–442 (1998). [https://doi.org/10.1038/30918](https://doi.org/10.1038/30918)

[2] B. Maier, Smallworld. GitHub, 2021. [Online]. Available: [https://github.com/benmaier/smallworld](https://github.com/benmaier/smallworld)
