# R_SocialNetworkAnalysis

Social network analysis (SNA) is the process of investigating social structures and reslationship through the use of networks and graph theory. 
It identifies and demonstrates networked structures in terms of nodes (individual actors, people, or things within the network) and 
the ties, edges, or links (relationships or interactions) that connect them.

Trough network analysis, it helps us to understand, predict better the network among the group and features.

<img width="598" alt="Screenshot 2021-05-26 at 13 57 35" src="https://user-images.githubusercontent.com/61825187/119656122-9e611b00-be2a-11eb-8db7-26a42145bdf7.png">
reference: picture is from https://towardsdatascience.com/how-to-get-started-with-social-network-analysis-6d527685d374

Here, I will share the implementation for 2 practices of social network analysis in R and the result of UCINET.

# First of all, social network analysis in R

## Part A: Lazega’s Lawyers
For part A of this assessment, you will be using a network observed on lawyers at a lawfirm. You can read about this data set here. The network and attribute file called lazegacowork.txt and lazpractice.txt are available on Blackboard. The first file is the adjacency matrix for co-work (symmetrical, that is an undirected network) and the second one is a node attribute; the type of law that each lawyer practices (0 = litigation, 1 = corporate). Below you will find the R syntax for importing the network and attribute file:
Your tasks for Part A are the following:
a) Visualize and describe the co-work network in terms of number of nodes, number of edges and density. Interpret the results. (10%)
b) Assume we want to test for homophily based on the attribute "practice". We want to use the null model U|L, that is uniform graph distribution given number of edges. State the hypotheses and describe how you would perform this test. (15%)
c) You are interested in running an ERGM with the following statistics – nodecov("practice")
– match("practice")
– gwesp(decay = 0.693)
Describe what these statistics represent and why they might be of interest to include in an ERGM. Fit the mentioned ERGM and interpret the parameter estimates. What can you conclude? Briefly explain how you would assess the goodness of fit of this model. (50%)
 LazNet <- read.table('lazcowork.txt') LazAtt <- read.table('lazpractice.txt')


## Part B: SAOM
a) We obtained network data from a workplace of 34 employees. At two time points a few months apart, we measured who trusted whom (binary, directed trust network) and the sex of employees (binary sex covariate). To explain how the network evolved between the two observations, we fitted a Stochastic Actor-oriented Model (SAOM) to the data using RSiena. The results from the model are presented in the table below.
 Effect
par. (s.e.)
 Rate 1
outdegree (density)
reciprocity
transitive triplets
indegree - popularity
sex alter
sex ego
same sex
∗ p<0.05;∗∗ p<0.01;∗∗∗ p<0.001; convergence t ratios all < 0.03.
Overall maximum convergence ratio 0.1.
8.96 (1.61) –2.32∗∗∗ (0.40) 1.39∗∗∗ (0.29) 0.16∗ (0.08) –0.04 (0.07) 0.06 (0.31) 0.60 (0.40) 0.91∗∗ (0.28)
  Interpret the results. Assess the convergence of the model and discuss each effect in the table. (10%)
b) Let’s assume that we are modelling changes in a network of four actors (named A, B, C, D) using SAOMs. In one of the simulation chains, we consider a ‘ministep’ when actor A is prompted to make a change to the network. The state of the network at this moment is shown in the figure below.
The shape of nodes represents their sex (circle – female, square – male). Actor A is coloured differently to highlight that we are considering the choice to be made by this actor.
The following parameter values are used in the simulation: – outdegree: -2.5;
– reciprocity: +1.5;
 2

– transitive triplets: +0.5; – same sex: +1.0;
– all other parameters: 0.
What is the probability that A will create a tie to D in this ministep? Present the details of your calculation, including: the four options for the multinomial choice, the effect statistics in each option, the value of the objective function in each option, and the probability of the AD tie to be created. (10%)
c) We are interested in the goodness of fit of the SAOM presented in point a). We run the sienaGOF function and get the result shown in the figure below.
Discuss the goodness of fit of the model with regard to the indegree distribution. (5%)

# Setup the social network analysis in UCINET

The UCINET data SAMPSON contains numerous rankings of a novice group of monks collected by Sampson. Extract the data SAMPLK1, SAMPLK2 and SAMPLK3. The non-symmetric valued data is coded so that 3 represents the top or first choice, 2 the second choice and 1 the third or last choice.  They were only asked to give their top 3 choices but ties and no responses were allowed. Sampson identified four groups:

Winifred, John, Gregory, Hugh, Boniface, Mark and Albert (The Young Turks)
Bonaventure, Ambrose, Berthold, Peter and Louis (The Loyal Opposition)
Basil, Elias and Simplicius (The Outcasts)
Romuland, Victor and Amand (The Floaters).



Produce a visualization of SAMPLK3 which identifies both the groups described above and the most central actors. How would you describe the roles of the most central actors in each group?.
What is the community structure of SAMPLK3?
Examine SAMPLK1 and SAMPLK2 together with SAMPLK3, how have things changed over time? Produce a visualization that captures the changes.
By examining the network do you think Sampson was correct in his group identification and description of the groups?  Use the Qudratic Assignment Procedure to test Sampson’s description at both time 1 and time 3. Discuss your results.

