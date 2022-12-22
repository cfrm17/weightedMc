# Weighted Monte Carlo Simulation

A regular Monte Carlo (MC) simulation algorithm assigns each simulation scenario, or path, an identical probability weight. A weighted Monte Carlo (WMC), however,  allows a different probability to be assigned to each simulation path.  For example, we can choose the probabilities of each path in a manner such that the simulation is guaranteed to reproduce the prices of “benchmark” securities, whose prices are known from market data.  A simulation thus calibrated to benchmarks will then price off-market securities in a realistic manner.

The technique of assigning probability weights has, at least theoretically, the additional benefits of accelerating the convergence of the simulation, as well as allowing the sensitivities of the simulated price with respect to the benchmark securities to be computed without performing additional simulations. 

Sometimes WMC fails to predict a “correct” value for an outstanding trade. According to the theory of WMC, we could not expect the difference between the regular MC simulation and WMC to be so large.  The reason leading to such difference is shown in Figures 1 and 2.

Figures 1 and 2 show the Value of Protection for the first tranche when we change the number of scenarios of the simulation with and without WMC, respectively. It can be seen in Figure 2 the regular MC’s behaviour meets our expectation of a MC simulation. As the number of scenario increases, the value of protection tends to converge. However, the results with WMC, as shown in Figure 1, show two effects. First, like a regular MC, it tends to converge as the number of scenario increases. Secondly, it is obvious that there are two solutions to which the WMC tends to converge. One is the same as the regular MC and the other is totally something else, which is obviously “wrong”. 

If we take the number of scenarios be 5000, WMC will converge to the “wrong” solution and the first 15 largest weights are shown in Figure 3.  Although the solution is a stable one, it is certainly wrong because the maximum weight for a single scenario could be as large as 0.22, which deviates from 1/N (N=number of scenarios) dramatically. 


Figure 1. Value of Protection for the 1st Tranche with WMC (Random Seed=4357)
 


Figure 2. Value of Protection for the 1st Tranche without WMC (Random Seed=4357)
 

Through our tests, we have shown that WMC could converge to two stable solutions, one being consistent with regular MC and the other obviously wrong. The reason why WMC converges to two stable solutions is unknown yet. 

The chance of getting the “wrong” solution tends to decrease when the number of scenarios increases.   For most of trades, the number of scenarios is taken as 200,000, 500,000 and 1,000,000. Hence the chance of getting a wrong result is very small. However, we won’t be able to tell how many scenarios are enough to get rid of the wrong result.

References:
https://finpricing.com/lib/IrInflationCurve.html



