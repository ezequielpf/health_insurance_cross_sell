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
- Four machine learning models were trained in a training dataframe representing 70% of the available database. The remaining 30% were used for validation.
- The used models: Linear Regression, Random Forest, HGBoost and XGBoost.
- The target variable is unbalanced. Far fewer people are interested in purchasing vehicle insurance compared to those who are not. The proportion is about 12% to 88%. Under this circumstances, accuracy might give a misleadingly high result.
- Recall was selected as the evaluation metric because it is important to indentify as many customers as possible who are interested in car insurance, even if the model makes some mistakes.
- All features were used.
- A Bayesian search was used to perform the hyperparameter tuning of the models.
- The predictions of each model were sorted by the probability of a customer being likely to purchase insurance.
- The predictions from each model were ranked by the likelihood of a customer purchasing insurance.
- Some metrics were evaluated based on the ranked list.

## Results
The results of each model for a sample of 25000 customers are summarized in the following table. In order to make the calculations, it was assumed a US$ 1000.00 anual average cost of vehicle insurance and a US$ 1.00 cost per contact. 

|                     | Recall @ K | Number of interests | Contact per sale | Cost of contacts (US$) | Revenue (US$) | Profit (US$) | Gain (%) |
|---------------------|------------|---------------------|------------------|------------------------|---------------|--------------|----------|
| Random              | 0.218660   | 2980                | 8.39             | 2980.0                 | 2980000.0     | 2977020.0    | -        |
| Logistic Regression | 0.575109   | 8059                | 3.1              | 8059.0                 | 8059000.0     | 8050941.0    | 170.44  |
| Random Forest       | 0.541212   | 7583                | 3.3              | 7583.0                 | 7583000.0     | 7575417.0    | 154.46  |
| HGBoost             | 0.616927   | 8644                | 2.89             | 8644.0                 | 8644000.0     | 8635356.0    | 190.07  |
| XGBoost             | 0.506530   | 7098                | 3.52             | 7098.0                 | 7098000.0     | 7090902.0    | 138.19  |
---------------------------------------------------------------------------------------------------------------------------------------

- The Historic Gradiente Boosting (HGB) model achieved the lowest contact rate per sale (2.89), requiring fewer calls for each successfull sale.
- Using this model, the company achieves an aproximately 190% increase in profit compared to a random selection of customers.
- out of the 25000 contacted customers, the HGB was able to recall approximately 62% of interested, compared to only 22% achieved by a random selection.
