# Recommender-Engines
In this project related to a complex recommender engine, a content-based algorithm will be built using Word2Vec and NLP.

## Project aims/goals

This project deals with a transnational retail store's transactions occurring between 1 December 2010 and 9 December 2011. The retail store is UK-based and is registered as a non-store online retail. The datasets was downloaded from the [UC Irvine Machine Learning Repository](https://archive.ics.uci.edu/dataset/352/online+retail). The aim of this project is to build a recommender engine that will recommend top 5 similar products to customers based on their first purchase.

## Data cleaning

After loading the dataset into a pandas dataframe, it contained a total of 541909 rows. The dataset has eight features which are `[InvoiceNo]`, `[StockCode]`, `[Description]`, `[Quantity]`, `[InvoiceDate]`, `[UnitPrice]`, `[CustomerID]`, and `[Country]`. The features are a combination of categorical, numerical and date datatypes. Some columns contained rows that were either zero or had negative values. These values were removed from the `[Quantity]` and `[UnitPrice]` columns as they would have a negative effect on the recommender engine. The `[CustomerID]` column contained over 130000 missing values, which were all removed. They were removed because the recommender engine is based on recommending products for the customers based on their first purchase. And this will be done by grouping the `[CustomerID]` and concatenating all the products they bought as a list (`[StockCode]`). Initially, I didn't remove the missing values and found the anomaly that a particular customer bought over 130000 products. This was not a real customer but rather all the missing value's `[StockCode]` grouped together. There was no point in dealing with duplicates in the dataset, as duplicates in this dataset is logically reasonable.

After removing null values and outliers, the dataset to be used for analysis and modeling reduced to 397884. The next step was to group the dataset by the `[CustomerID]` column. The dataset further reduced to 4338. One customer bought a total of 7847 products. The conclusion reached was that this customer must be a small business owner that buys in bulk and resells. The data description I later got to read agreed with that [data-driven insight](https://archive.ics.uci.edu/dataset/352/online+retail).

## Word2Vec and recommender function

The prepared dataset was split into training and testing set, where 90% was for training and 10% for testing. The count vectorizer was fitted on the training data and used to transform both the train and test set. The cosine similarity vectors for both sets were then calculated and the recommender function was defined.

## Results
- The recommendations from the recommender engine seems to agree with the purchases of the selected customers.

### Key takeaways
There was no way to validate the recommender engine except manually comparing and trying to find similarities between the entire previous purchase of a particular customer and compare it with the top 5 recommended products from the recommender engine. 

## Challenges 
 - Due to the train test split, I found it really difficult to write the proper function that will recommend the top five products to customers based on their first purchase.

## Future Goals
- Use this model to analyse different clusters of customers and determine segments of customer spending behaviours.

### Repo structure

```
├── README.md                  <-- Markdown file explaining the project's 
|                              approach, methodology, and findings
│
├── Online Retail.xlsx         <-- Dataset used in building the engine.
│
├── recommender_engines.ipynb   <-- Files with user defined functions 
|                                        and classes
```

### Tech stack

* `Pandas` libraries for data analysis
* `Scikit-Learn` library for model evaluation and performance review
* `Matplotlib`, `Seaborn` libraries for visualizations


> Please reach out to me if you have further ideas or suggestions to improve this project. Questions and discussions are also welcomed. I am also very much open to collaborating. **I am available through e-mail** drsamuelsurulere@gmail.com
