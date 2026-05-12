import pandas as pd
from mlxtend.frequent_patterns import apriori
from mlxtend.frequent_patterns import association_rules
data = {
'Transaction': [1, 1, 1, 2, 2, 2, 3, 3, 3, 4, 4, 4, 5, 5, 5], 'Item': ['Milk', 'Bread', 'Eggs', 'Bread', 'Diaper', 'Beer', 'Milk', 'Diaper', 'Beer', 'Bread', 'Milk', 'Diaper', 'Bread', 'Milk', 'Eggs']
}
df = pd.DataFrame(data)
basket = df.groupby(['Transaction', 'Item'])['Item'].count().unstack().fillna(0)
freq_Itemsets = apriori(basket, min_support = 0.4, use_colnames = True)
rules = association_rules(freq_Itemsets, metric = 'confidence', min_threshold = 0.6)
print("Association Rules:")
print(rules)
