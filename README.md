# Car Insurance Sell

## Problem

### Context
Our client is an Insurance company that has provided Health Insurance to its customers. Now the company needs help to build a model capable of predict if a policyholder (customers) from past year will also be interested in **Vehicle Insurance**, also provided by the company.
A prediction model will help the company being more effective in its communication strategy to reach out those customers most likely to purchase a vehicle insurance.

### Proposal for solution
Supposing that the company does not have enough resources to contact every client in the data base, a good strategy would be creating a list of clients ordered by their propensity of being interested in Vehicle Insurance. Such strategy would allow the company to maximize the effort of reaching the potential clients in comparison to a randomized choice in a list.
Let's say the company has a marketing budget to contact **25000** person.
The purpose is to employ a Machine Learning model to order a list of clients, from the most interested in to the less one. Next, with that list it is possible to plot a Cumulative Gains Curve to evaluate the effectiveness of the model in comparison to a randomized choice.

## Solution
- Four machine learning models were trained in a training dataframe representing 70% of the available database. The remaining 30% were used for validation
- The used models: Linear Regression, Random Forest, HGBoost and XGBoost
- The targer variable is unbalanced. There are far fewer people interested in purchasing a vehicle insurance compared to thoso who are not. The proportion is about 12% to 88%.
