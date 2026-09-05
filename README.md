# 🛒 Market Basket Analysis using Apriori

A Machine Learning project that uses the **Apriori algorithm** to discover relationships between items purchased together in transactions.

The project performs **Market Basket Analysis** using Python, Pandas, and the `mlxtend` library.

---

## 📌 Project Overview

Market Basket Analysis is a technique used to identify patterns in customer purchases.

For example, if customers frequently purchase **Milk and Bread together**, an association rule can identify this relationship.

This project:

* Creates a sample transaction dataset.
* Converts transactions into a basket format.
* Finds frequent itemsets using the **Apriori algorithm**.
* Generates association rules.
* Uses **confidence** to filter useful rules.

---

## 🧠 How It Works

```text
Transaction Data
       ↓
Create Pandas DataFrame
       ↓
Convert to Basket Format
       ↓
Apriori Algorithm
       ↓
Frequent Itemsets
       ↓
Association Rules
       ↓
Analyze Item Relationships
```

---

## 🛠️ Technologies Used

* Python
* Pandas
* mlxtend
* Apriori Algorithm
* Association Rule Mining

---

## 📦 Installation

Install the required libraries:

```bash
pip install pandas mlxtend
```

---

## 📊 Dataset

The project uses a small sample transaction dataset containing items such as:

* 🥛 Milk
* 🍞 Bread
* 🥚 Eggs
* 🧷 Diaper
* 🍺 Beer

Example:

```python
data = {
    'Transaction': [1, 1, 1, 1, 2, 2, 3, 3, 4, 4, 4, 5, 5, 5, 5],
    'Item': [
        'Milk', 'Bread', 'Eggs', 'Bread',
        'Diaper', 'Beer', 'Milk', 'Diaper',
        'Beer', 'Bread', 'Milk',
        'Diaper', 'Bread', 'Milk', 'Eggs'
    ]
}
```

---

## 🧺 Creating the Basket

The transaction data is converted into a basket representation:

```python
basket = df.groupby(
    ['Transaction', 'Item']
)['Item'].count().unstack().fillna(0)
```

This allows the Apriori algorithm to determine which items occur together across transactions.

---

## 🔍 Apriori Algorithm

The Apriori algorithm is used to identify frequently occurring item combinations.

```python
freq_Itemsets = apriori(
    basket,
    min_support=0.3,
    use_colnames=True
)
```

### Minimum Support

The `min_support=0.3` parameter means an itemset must appear in at least **30% of transactions** to be considered frequent.

---

## 🔗 Association Rules

Association rules are generated from the frequent itemsets:

```python
rules = association_rules(
    freq_Itemsets,
    metric='confidence',
    min_threshold=0.49
)
```

The project uses **confidence** as the main metric.

A confidence threshold of `0.49` means that only rules with at least **49% confidence** are included.

---

## 📈 Important Concepts

### Support

Measures how frequently an itemset appears in the dataset.

### Confidence

Measures how often the consequent appears when the antecedent occurs.

### Association Rule

A rule generally has the form:

```text
Item A → Item B
```

Meaning that customers who purchase **Item A** may also be likely to purchase **Item B**.

---

## 🖥️ Output

The generated rules are displayed using:

```python
print("Association-Rules:")
print(rules)
```

The output contains information such as:

* Antecedents
* Consequents
* Support
* Confidence
* Lift

---

## 📁 Project Structure

```text
📦 Market-Basket-Analysis
│
├── main.py
├── README.md
└── requirements.txt
```

---

## 🎯 Learning Outcomes

This project demonstrates:

* Data manipulation using Pandas
* Transaction data preprocessing
* Market Basket Analysis
* Apriori algorithm
* Frequent itemset mining
* Association rule generation
* Support and confidence
* Basic recommendation pattern discovery

---

## 🚀 Future Improvements

The project can be extended by:

* Using a larger real-world transaction dataset.
* Adding **lift** as a rule-filtering metric.
* Visualizing frequent itemsets.
* Creating a recommendation system.
* Building an interactive dashboard.
* Comparing different support and confidence thresholds.

---

## 👨‍💻 Author

**Yash**

⭐ If you found this project useful, consider giving the repository a star.
