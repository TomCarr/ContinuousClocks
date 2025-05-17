# ContinuousClocks

**(things here still being actively developed)**

Estimates of substitution rates (and thus divergence times) from molecular sequence data are strongly influenced/entirely determined by assumptions. This is because the substitution rate for each branch is not identifiable i.e. the likelihood depends on a product of the substitution rate and time duration of each branch. Often the assumptions we use in this context are difficult to justify.  

Some continuous traits (e.g. longevity) are known to be associated with molecular substitution rates. Continuous traits are also useful because they retain a consistent phylogenetic signal regardless of the rate at which they evolve - i.e. they do not become saturated ([Parins-Fukuchi 2018](https://doi.org/10.1093/sysbio/syx072)). 

The models outlined below are still being developed, but are designed to use these useful characteristics of continuous traits as a means of getting better estimates of molecular substitution rates (and therefore divergence times).

## Outline

- All the models below use a fixed tree topology (although could easily be extended to use a distribution of topologies). The expectation is that this topology is estimated from molecular sequence data - i.e. we assume that molecular sequence data is better than morphological data for estimating tree topologies (in cases where molecular data is available).
- Continuous traits are reconstructed on this topology. Importantly, continous traits are reconstructed using a BM process that accounts for any amount of among-branch-rate-variation (among-branch-variation in _σ<sup>2</sup>_).
- This is achieved by reconstructing the continuous traits on disparity branch lengths - i.e. the expected variance between ancestral and descendant nodes is dependent on _σ<sup>2</sup>*t_ for each branch. This avoids having to explicitly estimate _σ<sup>2</sup>_, and thus the extent to which it varies among branches.
- This is conceptually similar to the difference between estimating molecular branch lengths (_rate * time_) compared to seperately estimating rate _and_ time on each branch in divergence time estimation. Molecular branch lengths are identifiable and will typically converge on the correct value (like estimates of continuous traits on disparity branch lengths). Sadly divergence time estimates are not ([Britton 2005](https://doi.org/10.1080/10635150590947311)).
- The correlation between the reconstructed continuous trait and molecular substitution rates is then estimated. This can be done simultaneously within the same analysis as the reconstructions and divergence time estimates. It can also be done prior to the divergence time analysis and specified when performing the analysis. We are still exploring the situations in which this final step is and is not feasible.  
- This information enables you to estimate substitution rates, and subsequently divergence times on each branch. 
- Broadly speaking, this method may be useful because it uses identifiable parameters (i.e. continuous trait reconstructions on disparity branch lengths) to inform rate estimates. In certain situations this can provide a means of alleviating identifiability issues that critically undermine other methods. 

### [Model 1](https://github.com/TomCarr/ContinuousClocks/blob/main/ContinuousClocks1.Rev)
This does the above steps in a fairly simple manner. It works in simulations in terms of it estimates accurate divergence times regardless of variation in _σ<sup>2</sup>_.
In this model the correlation between each continuous trait and the molecular sequence data needs to be specified prior to running it - line 125 - you have one value for each continuous trait










