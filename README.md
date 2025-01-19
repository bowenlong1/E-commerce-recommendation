Expense Matching for TTSE
Background
For TurboTax Self-Employed (TTSE) customers, we’d like to personalize their experiences to help them identify relevant SE-expenses in order to maximize tax benefits.

The current expense match model presents a static table when an industry category is determined by the industry match model.
Documented materials
TTSE UPS Sync deck
TTSE UPS Study doc
Features for Expense Match
Feature Exploration Slides
Offline evaluation
Objective
Our primary goal is to build a personalized recommender presenting the expense categories that are most relevant to the customer based on what expense categories similar customers have used.

A stretch goal is to further personalize the expense examples shown under each category.
Customized ML Design
The personalized recommender is designed to have two components.
Given input features, calculate the likelihood of the categories being selected (propensity score)
This component can be designed as a supervised ML model
Features (X)
user features (e.g., gender, marital status, income source, etc.)
expense category features (e.g., description of the categories)
interactions features
Label (y)
Interaction data (whether the category viewed by the customer is selected)
Given the scores, design a recommendation strategy without or with randomness
Without randomness (“ Pure Exploitation”)
Recommend expense categories with the highest propensity scores
With randomness (“Exploration”)
Recommend expense categories with uncertain rankings for the purpose of gathering more information.
Example of exploration strategy
Bandit algorithms
Epsilon-greedy: choosing between exploration and exploitation randomly 
Upper confidence bound (UCB)
Thompson sampling: This is a Bayesian method. To align with it, the supervised model needs to be updated.

Initial Data Exploration
Definition of data 
User data
User features potentially useful for expense match
Item data
The item is defined as the expense category shown to the user.
The item data include the expense categories and/or descriptions/expense examples of the expense categories.
Interaction data
The viewed expense data, and selected expense data.

Steps for data exploration
Explore features relevant to the expense match
Investigate the data availability
Look at the distribution of relevant features
Build a sample dataset to do correlation analysis
Analyze the correlation between user features and selected expense categories

Quick links for data exploration
Spreadsheet of features selected for initial exploration.
Item data
Descriptions
Interaction data
Data source: kkause_test_ws.ttse_qbse_taxfiler_expense_count_agg
Notebook (SQL embedded)
User data
Data source: cgdata_taxml_dwh.taxml
catalog, SQL, Notebook
Data source: ued_c360_dwh.entities_v4
catalog, SQL, Notebook
User data filtered by the interaction data
Data source: cgdata_taxml_dwh.taxml, ued_c360_dwh.entities_v4, kkause_test_ws.ttse_qbse_taxfiler_expense_count_agg
SQL, Notebook (build dataset), Notebook (exploration & correlation)

