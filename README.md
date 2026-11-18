### VVIDRA - *Vector-Valued Individualized Desirability and Reachability Advisor for Countermeasure Protocol Selection*

##### Proof of concept implementation of the **feasibility-desirability architecture** for personalized decision support in human digital twins

**Status:** Early development

##### Overview
'vvidra_1.0' is the computational core of VVIDRA, developed as part of PhD thesis "Systems Biology and Personalized Medicine for Optimizing Human Performance in Aging Athletes" (thesis title will most likely change). The motivating application is astronaut health monitoring, but the core is intentionally domain-agnostic: markers, objectives, and interventions are supplied as configuration, not hard-coded. 

The architecture couples two independently specified models:
- **Feasibility model:** a hierarchical, discrete-time stochasstic state-space model that projects the distribution of reachable marker states forward in time under a candidate intervention. It is represented as a weighted particle cloud and personalized through Bayesian posterior updating, starting from cohort-level priors. 
- **Desirability model:** a graded, vector-valued objective field with asymmetric deviation penalties (a modified Derringer-Suich formulation) anchored to a personalized reference point. Acceptability thresholds are annotations on the field, not hard constraints. 

The two models have **independent provenance**: neither is derived from the other. The **coupling** stage evaluates the desirability field over the feasibility cloud and returns, for each candidate intervention, a full distribution of desirability vectors (a *desirability cloud*) together with the probability mass at each threshold. This output is designed to feed a later ranking stage that serves human decision support rather than autonomous optimization. Ranking is outside the scope of this particular PoC.

See included documentation from C:\Users\kevin\proj\vvidra-poc\documentation for full rationale.