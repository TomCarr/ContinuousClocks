# ContinuousClocks

**(things here still being actively developed)**

Estimates of substitution rates from molecular sequence data are strongly influenced by assumptions. This is because the substitution rate along each branch is not identifiable i.e. the likelihood depends on a product of the rate and time along each branch. Often the assumptions we use in relaxed clock models are difficult to justify.  

Some continuous traits (for example longevity) are known to be associated with molecular substitution rates. Continuous traits are also useful because they retain a consistent phylogenetic signal regardless of the rate at which they evolve - i.e. they do not become saturated ([Parins-Fukuchi 2018](https://doi.org/10.1093/sysbio/syx072)). 

These models outlined below are designed to use these useful characteristics of continuous traits as a means to estimate molecular substitution rates and divergence times.

## Outline

- All the models below use a fixed tree topology (although could easily be extended to use a distribution of topologies), presumably estimated from molecular sequence data.
- Continuous traits are reconstructed on this topology. Importantly, continous traits are reconstructed using a BM process that accounts for any amount of variation in rate (σ<sup>2</sup>). This is because the continuous traits are reconstructed on disparity branch lengths - i.e. the expected variance between ancestral and descendant branches is dependent on σ<sup>2</sup>*t for each branch. This avoids having to explicitly estimate σ<sup>2. This is similar to the difference between estimating molecular branch lengths (rate * time) compared to seperately estimating rate _and_ time on each branch in divergence time estimation. The molecular branch lengths are identifiable and will often converge on the correct value. Sadly the divergence time estimates are not ([Britton 2005](https://doi.org/10.1080/10635150590947311)).
- The correlation between the reconstructed continuous trait and molecular substitution rates is then estimated. This can be don simultaneously within the same analysis as the reconstructions and divergence time estimates. Or can br done prior to the divergence time analysis and specified when performing the analysis. We are still exploring the situations in which this step is and is not feasible.  
- This enables you to estimate substitution rates, and subsequently divergence times on each branch. 

### Model 1










