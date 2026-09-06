# AML Transaction Alert
The table below provides information regarding a transaction that the model has identified as suspicious. The data features are those that are used by the decision tree. All others are excluded. Please review the **Feature Definitions** below to understand what the feature names mean and how they can be interpreted.

|Features         |Value            |
|:----------------|:----------------------|
|Payment.Format   |ACH                    |
|dest_fan_in      |7                      |
|source_ratio_out |2                      |
|dest_ratio_in    |12.4285714285714       |
|dest_max_col4_in |490428.96              |
|BankName         |National Bank of Butte |
|EntityType       |SoleProprietorship     |

# Model Decision Algorithm - Decision Tree
A decision tree is a predictive model that makes decisions by following a flowchart-like series of simple "if-then" or "yes/no" questions based on data features.
- **The Structure**: It starts at a single top rule (the root) and splits into branches based on each answer. Following the path through subsequent questions leads to an end point (a leaf), which provides the final prediction or classification.
- **Why It Matters**: Unlike "black-box" machine learning models, decision trees are inherently transparent because you can directly trace the exact visual path and logic that produced an outcome.

![DecisionTree](GOSDTdiagram.png)

# Feature Definitions
1. <span style="color: red;">dest_fan_in</span>
- *The Investigator Translation*: "The Gathering Pool" or "Number of Unique Depositors."
- *The Mechanics*: This metric looks at the account receiving the money (the destination). It simply counts the number of distinct source accounts that have sent money to this single destination account over a specific timeframe.
- *The Fraud Typology*: A high fan-in (like the > 27.5 threshold in the tree) is a classic topological signature of a "funnel account." In many scams, or in distributed money laundering (smurfing), criminals use a network of compromised victim accounts or money mules to pool illicit funds into a central hub. Legitimate retail accounts rarely receive transfers from dozens of different, unrelated accounts simultaneously.
2. <span style="color: red;">source_ratio_out</span>
- *The Investigator Translation*: "The Outbound Imbalance" or "Burn Rate."
- *The Mechanics*: This focuses on the account sending the money. It measures the ratio of the account's outbound transaction volume (or count) compared to its inbound volume or historical baseline.
- *The Fraud Typology*: A high outbound ratio indicates an account is flushing money out much faster than it is taking legitimate funds in. This is the exact behavior of an intermediary mule account or a newly compromised account, where the immediate goal is to wire stolen funds away to a secondary destination before the bank can initiate a clawback or freeze the assets.
3. <span style="color: red;">dest_ratio_in</span>
- *The Investigator Translation*: "The Inbound Imbalance" or "Sudden Influx."
- *The Mechanics*: The mirror image of the metric above, looking at the receiving account. It measures how heavily the account's recent activity is dominated by incoming funds compared to its outgoing funds or baseline history.
- *The Fraud Typology*: If an account that typically has a balanced ratio of deposits to daily spending suddenly experiences a massive spike where the ratio is heavily skewed toward incoming transfers, it is highly suspicious. This pattern flags "sleeper accounts" or older, seemingly legitimate accounts that have suddenly been activated strictly to receive large fraudulent disbursements.
4. <span style="color: red;">dest_max_col4_in</span>
- *The Investigator Translation*: "The Single Largest Deposit."
- *The Mechanics*: Assuming col4 represents the transaction amount (given the specific $66,796.01 threshold in the model), this feature isolates the absolute largest single incoming transaction to the destination account during the tracking window.
- *The Fraud Typology*: Even if an account doesn't trigger the "Gathering Pool" alert (low fan-in), receiving a massive, outlier payday is a major red flag. This node is designed to catch high-value, low-frequency events like a targeted wire fraud payment, a business email compromise (BEC) settlement, or a ransomware payout, where the illicit transfer occurs in a single, massive lump sum rather than a distributed pool. 

# Transaction History
This is the history of transactions for this particular Account. This is to provide an investigator with some potential context for the transactions.

|         |Timestamp           |Account   |ReceivingAccount |FromBank |ToBank |PaymentFormat | dest_fan_in| source_ratio_out| dest_ratio_in| dest_max_col4_in|
|:--------|:-------------------|:---------|:----------------|:--------|:------|:-------------|-----------:|----------------:|-------------:|----------------:|
|1491250  |2022-09-01 01:49:00 |8019FFFD0 |8019FFFD0        |23128    |23128  |Reinvestment  |           2|                1|          2.50|          4084.29|
|23924508 |2022-09-13 10:07:00 |8019FFFD0 |8019FFFD0        |23128    |23128  |ACH           |           2|                2|          3.00|          4942.15|
|23924523 |2022-09-13 10:07:00 |8019FFFD0 |8010FA8E0        |23128    |1137   |ACH           |           7|                2|         12.43|        490428.96|
|23924562 |2022-09-13 10:07:00 |8019FFFD0 |8010FA8E0        |23128    |1137   |ACH           |           7|                2|         12.43|        490428.96|