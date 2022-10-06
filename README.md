# Ridge Regression

Linear regression refers to a model that assumes a linear relationship between input variables and the target variable.

With a single input variable, this relationship is a line, and with higher dimensions, this relationship can be thought of as a hyperplane that connects the input variables to the target variable. The coefficients of the model are found via an optimization process that seeks to minimize the sum squared error between the predictions (yhat) and the expected target values (y).

`loss = sum i=0 to n (y_i – yhat_i)^2`

A problem with linear regression is that estimated coefficients of the model can become large, making the model sensitive to inputs and possibly unstable. This is particularly true for problems with few observations (samples) or less samples (n) than input predictors (p) or variables (so-called p >> n problems).

One approach to address the stability of regression models is to change the loss function to include additional costs for a model that has large coefficients. Linear regression models that use these modified loss functions during training are referred to collectively as penalized linear regression.

One popular penalty is to penalize a model based on the sum of the squared coefficient values (beta). This is called an L2 penalty.

`l2_penalty = sum j=0 to p beta_j^2`

An L2 penalty minimizes the size of all coefficients, although it prevents any coefficients from being removed from the model by allowing their value to become zero.

The effect of this penalty is that the parameter estimates are only allowed to become large if there is a proportional reduction in SSE. In effect, this method shrinks the estimates towards 0 as the lambda penalty becomes large (these techniques are sometimes called “shrinkage methods”).<br>
                                                                                                            — Page 123, Applied Predictive Modeling, 2013.

This penalty can be added to the cost function for linear regression and is referred to as Tikhonov regularization (after the author), or Ridge Regression more generally.

A hyperparameter is used called “lambda” that controls the weighting of the penalty to the loss function. A default value of 1.0 will fully weight the penalty; a value of 0 excludes the penalty. Very small values of lambda, such as 1e-3 or smaller are common.

`ridge_loss = loss + (lambda * l2_penalty)`
