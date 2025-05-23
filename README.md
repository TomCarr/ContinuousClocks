# ContinuousClocks

_(things here still being developed)_

Estimates of substitution rates (and therefore divergence times) from molecular sequence data are strongly influenced/entirely determined by assumptions. This is because the substitution rate for each branch is not identifiable i.e. the likelihood depends on a product of the substitution rate and time duration of each branch. Often the assumptions we use in this context are difficult to justify.  

Some continuous traits (e.g. longevity) are known to be associated with molecular substitution rates. Continuous traits are also useful because they retain a consistent phylogenetic signal regardless of the rate at which they evolve - i.e. they do not become saturated ([Parins-Fukuchi 2018](https://doi.org/10.1093/sysbio/syx072)). 

The method(s) outlined below is still being developed, but is designed to use these useful characteristics of continuous traits as a means of getting better estimates of molecular substitution rates (and therefore divergence times).

## Outline

- A fixed tree toplogy is used (although it could easily be extended to use a distribution of topologies). The expectation is that this topology is estimated from molecular sequence data - we assume that molecular sequence data is better than morphological data for estimating tree topologies (in cases where molecular data is available).
- Continuous traits are reconstructed on this topology. Importantly, continous traits are reconstructed using a BM process that accounts for any amount variation between branches in the rate that the continouous trait(s) evolve (i.e. among-branch-variation in _σ<sup>2</sup>_).
- This is achieved by reconstructing the continuous traits on disparity branch lengths - i.e. the expected trait variance between ancestral and descendant nodes is dependent on _σ<sup>2</sup>*t_ for each branch. This avoids having to explicitly estimate _σ<sup>2</sup>_, and thus the extent to which it varies among branches.
- This is conceptually similar to the difference between estimating molecular branch lengths (_rate * time_), compared to seperately estimating rate _and_ time on each branch in divergence time estimation. Molecular branch lengths are identifiable and will typically converge on the correct value (like estimates of continuous traits on disparity branch lengths). Sadly divergence time estimates are not ([Britton 2005](https://doi.org/10.1080/10635150590947311)).
- The correlation between the reconstructed continuous trait and molecular substitution rates is then estimated. This can be done simultaneously within the same analysis as the reconstructions and divergence time estimates. It can also be done prior to the divergence time analysis and specified when performing the analysis. The situations in which this final step is and is not feasable still needs to be detemrined.   
- This information enables you to estimate substitution rates for each branch, and therefore divergence times. 
- Broadly speaking, this method may be useful because it uses identifiable parameters (i.e. continuous trait reconstructions on disparity branch lengths) to inform molecular rate estimates. In certain situations this can provide a means of alleviating identifiability issues that undermine other methods. 

### [Example 1](https://github.com/TomCarr/ContinuousClocks/blob/main/ContinuousClocks1.Rev)
This does the above steps in a fairly simple manner. It works in simulations in terms of it estimates accurate divergence times regardless of variation in _σ<sup>2</sup>_.
In this model the correlation between each continuous trait and the molecular sequence data needs to be specified prior to running it - line 125 - you have one value for each continuous trait.

### [Example 2](https://github.com/TomCarr/ContinuousClocks/blob/main/ContinuousClocks2.Rev)
This one calculates the correlation based on root to tip distances in  the molecular branch length tree, and the trait values along those branches. There are other ways to do this too. Is then uses these calculations in the divergence time estimation. 


### [Example 3](https://github.com/TomCarr/ContinuousClocks/blob/main/ContinuousClocks3.Rev)
This one estimates the correlation as part of the model, rather than calculating it based on root to tip values prior to the analysis. 

The latter two examples can be extended to run over multiple loci. The most efficient way of doing this still needs to be worked out - it potentially involves a large increase in the number of parameters. This is likely to involve moving away from RevBayes for very large datasets. 

Ideally, estimates from the latter two examples are most strongly influenced by trait/loci combinations with the strongest correlation. The extent to which this is the case still needs to be determined - if it is not the case, more extensive filtering of datasets would be required.  





