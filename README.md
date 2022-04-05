# LOL_Analysis_Project

Use a data set of League of Legends matches to find the most important variables that affect the gold collection of the blue team.

*** 

## Contributors
Qianli Wu, Yun Lin, Proud Jiao


### Process of Removing Predictors
* Removing useless variables
    1. Since destroyedTopBaseTurret, destroyedMidBaseTurret, lostTopBaseTurret, and lostMidBaseTurret for all observations are 0, thus we can remove those variables.

* Removing incorrect observations
    1. a Turret cannot be destroied twice, thus we remove observations which destroyedBotBaseTurret and lostBotBaseTurret greater than 1. 
    2. Since no Top and Mid base Turret is destroied or lost, there's no Top and Mid inhibitors can be destroied or lost. Therefore, we remove observations with destroyedTopInhibitor, lostTopInhibitor, destroyedMidInhibitor, lostMidInhibitor other than zero. 

* Removing predictors with severse collinearity problem
    1. expDiff and champLevelDiff are highly correlated, thus we remove expDiff since Champions can have same level but different exp which doesnt impact the game/the gold gain
    2. we can calculate **KDA** by $$ KDA = \frac{kills + assists} {deaths}$$ Then we remove **kills**, **deaths**, **assists**.

* Removing predictors by best-submodel selection and Bayesian Information Criterion value
    1. For submodels with number of predictors from 1 to full model, we select one best submodel by highest r-square. 
    2. We select the submodel with lowest Bayesian Information Criterion, which considers both complexity and accuracy. 
    3. Therefore, we only have 34 significant predictors left.  
