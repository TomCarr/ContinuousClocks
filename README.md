# ContinuousClocks

**(things here still being actively developed)**

Estimates of substitution rates from molecular sequence data are strongly influenced by assumptions. This is because the substitution rate along each branch is not identifiable i.e. the likelihood depends on a product of the rate and time along each branch. Often the assumptions we use in relaxed clock models are difficult to justify.  

Some continuous traits (for example longevity) are known to be associated with molecular substitution rates. Continuous traits are also useful because they retain a consistent phylogenetic signal regardless of the rate at which they evolve - i.e. they do not become saturated [Parins-Fukuchi 2018](https://doi.org/10.1093/sysbio/syx072). 

These models outlined below are designed to use these useful characteristics of continuous traits as a means to estimate molecular substitution rates and divergence times.

## Outline

- All the models below use a fixed tree topology (although could easily be extended to use a distribution of topologies), presumably estimated from molecular sequence data.
- Continuous traits are reconstructed on this topology. Importantly, continous traits are reconstructed using a BM process that accounts for any amount of variation in rate (σ<sup>2</sup>). This is because the continuous traits are reconstructed on disparity branch lengths - i.e. the expected variance between ancestral and descendant branches is dependent on σ<sup>2</sup>*t for each branch.
- 










