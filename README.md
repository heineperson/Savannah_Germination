# Savannah_Germination

## 00 Building Phylogenetic Tree

We constructed the phylogenetic tree used for this analysis following the S.PhyloMaker R script described in (Qian & Jin, 2016). This program matched the genera and families in our species list to an angiosperm mega-phylogeny (PhytoPhylo), which is an expansion of the tree published in (Zanne et al., 2014). We selected “Scenario 3” in S.PhyloMaker to construct our tree using the same methodology as phylomatic (Webb & Donoghue, 2005) and assign branch lengths in accordance with BLADJ in phylocom (Webb, Ackerly, & Kembel, 2008).

The file "R Codes from S.Phylomaker" is from the following repo: https://github.com/jinyizju/S.PhyloMaker, which asks that you cite the following paper:
Qian, H. and Y. Jin. (2016) An updated megaphylogeny of plants, a tool for generating plant phylogenies and an analysis of phylogenetic community structure. Journal of Plant Ecology 9(2): 233–239.

## 01 Phylogenetic Signal

 We tested for the presence of phylogenetic signal in species mean GP, T50, log Seed Mass, and Moisture Content in our dataset by calculating Blomberg’s K (Blomberg, Garland, & Ives, 2003) in the picante package in R (Kembel et al., 2010), which determines the statistical significants of K versus random reshuffling on tips of tree. To assess the importance on species identity (taxonomic signal) on traits measured, we conducted an a one-way analysis of variance on the full dataset for each trait to determine if there is greater trait variance among versus within species.  

## 02 Bayesian Models

We used the MCMCglmm function (Hadfield & others, 2010) to determine the which replicate level (log seed mass, moisture content) and species level (habitat, dormancy, dispersal mode) traits predict variation in GP and T50. In these Bayesian mixed effect models, we specified each trait as a fixed effect and species as a random effect with an associated phylogenetic covariance matrix created with the function inverseA. For models predicting GP, we used a multinomial error distribution, which is equivalent to a binomial error distribution when the number of outcomes (k) is 2. For models predicting T50, we used a gassian error distribution. Priors for each model are specificed in table SX. We ran all MCMCglmm models for 5,000,000 iterations with a burn in of 100,000 iterations. Each MCMC chain was thinned every 500 iterations, resulting in an effective sample size of 9800.


