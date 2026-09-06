# AML Transaction Alert
The table below provides information regarding a transaction that the model has identified as suspicious. The data features are those that appear in the top 12 most important features as reported by the model. All others are excluded.

|  Features           |Value                       |
|:--------------------|:---------------------------|
|Payment.Format       |ACH                         |
|source_ratio_out     |7.82                        |
|dest_ratio_in        |1                           |
|AmountPaid           |9147.26                     |
|source_fan_out       |11                          |
|dest_fan_in          |2                           |
|Amount.Received      |9147.26                     |
|source_deg_out       |86                          |
|fan_out_bins_2.3     |2                           |
|source_sum_col4_out  |7880205.46                  |
|source_skew_col4_out |3.42           |
|source_avg_col4_out  |91630.3       |
|BankName             |India Bank #47              |
|EntityName           |Sole Proprietorship #158506 |

# Varirable Importance from XGBoost ML model - Top 12 Predictors
The machine learning algorithm provided a set of the most "important" or influential varirables when the model was fit. The top 12 of these is provided below. This is give the investigator some context for the primary factors considered by the model when triggering an alert. Please review the **column definitions** below to understand what the feature names mean and how they can be interpreted.

| Feature | Permutation_Importance |
| :--- | :--- |
| Payment Format_ACH | 0.043290 |
| source_ratio_out | 0.004268 |
| dest_ratio_in | 0.003352 |
| AmountPaid | 0.002374 |
| source_fan_out | 0.002267 |
| dest_fan_in | 0.002196 |
| Amount Received | 0.002038 |
| source_deg_out | 0.001551 |
| fan_out_bins_2-3 | 0.001527 |
| source_sum_col4_out | 0.001509 |
| source_skew_col4_out | 0.001303 |
| source_avg_col4_out | 0.001138 |

# Column Definitions
### Payment & Transaction Values
* **Payment Format_ACH**: A binary flag indicating whether the transaction was processed as an Automated Clearing House (ACH) electronic transfer rather than a wire, check, credit card, or cash.  
* **AmountPaid**: The gross dollar amount sent by the originator for this specific transaction.  
* **Amount Received**: The net dollar amount received by the beneficiary account (accounting for any deductions, fees, or FX currency conversions). 

### Network & Flow Ratios (Graph Metrics)
* **source_ratio_out**: The proportion of the sender's total activity that consists of outbound money transfers (e.g., whether the account acts primarily as a source of outflows rather than holding balances).  
* **dest_ratio_in**: The proportion of the recipient's total activity that consists of inbound transfers (e.g., whether the recipient account acts predominantly as a collection point or funnel).  
* **source_fan_out**: The number of unique counterparties to which the sending account disperses funds. In AML, a high "fan-out" often indicates money laundering typologies like structuring or dispersing funds across multiple accounts.  
* **dest_fan_in**: The number of unique sending accounts transferring money into this single recipient. A high "fan-in" typically characterizes funnel accounts or aggregation points.  
* **source_deg_out**: The total count of outgoing connection paths/transactions initiated by the source account across the entire transaction network.  
* **fan_out_bins_2-3**: A categorized flag indicating whether the sender's fan-out count falls specifically into a low-to-moderate range of 2 to 3 distinct recipients. 

### Historical & Statistical Account Aggregations
* **source_sum_col4_out**: The total cumulative dollar sum of all outbound transactions previously sent by the originating account.  
* **source_avg_col4_out**: The historical average (mean) transaction amount sent by the source account.  
* **source_skew_col4_out**: The statistical skewness (asymmetry) of the sender's outbound transaction amounts. A high skewness indicates an account that normally sends small amounts but occasionally exhibits an unusually massive spike in transfer size.



# Transaction History
This is the history of transactions for this particular Account. This is to provide an investigator with some potential context for the transactions.

|         |Timestamp           |Account   |ReceivingAccount |FromBank |ToBank |PaymentFormat | source_ratio_out| dest_ratio_in| AmountPaid| source_fan_out| dest_fan_in| AmountReceived| source_deg_out| fan_out_bins_2.3| source_sum_col4_out| source_skew_col4_out| source_avg_col4_out|
|:--------|:-------------------|:---------|:----------------|:--------|:------|:-------------|----------------:|-------------:|----------:|--------------:|-----------:|--------------:|--------------:|----------------:|-------------------:|--------------------:|-------------------:|
|2057571  |2022-09-01 06:03:00 |81655BDA0 |8173B69E0        |159692   |262084 |Credit Card   |               52|          15.8|   15539.40|              1|           5|       15539.40|             52|                0|            550412.7|                -0.79|            10584.86|
|2072780  |2022-09-01 06:09:00 |81655BDA0 |8173B69E0        |159692   |262084 |Cash          |               52|          15.8|   10607.54|              1|           5|       10607.54|             52|                0|            550412.7|                -0.79|            10584.86|
|2074846  |2022-09-01 06:10:00 |81655BDA0 |8173B69E0        |159692   |262084 |ACH           |               52|          15.8|    2071.37|              1|           5|        2071.37|             52|                0|            550412.7|                -0.79|            10584.86|
|2109426  |2022-09-01 06:26:00 |81655BDA0 |8173B69E0        |159692   |262084 |Cheque        |               52|          15.8|   14121.13|              1|           5|       14121.13|             52|                0|            550412.7|                -0.79|            10584.86|
|7389395  |2022-09-02 23:12:00 |81655BDA0 |8173B69E0        |159692   |262084 |ACH           |               52|          15.8|    2071.37|              1|           5|        2071.37|             52|                0|            550412.7|                -0.79|            10584.86|
|7404455  |2022-09-02 23:19:00 |81655BDA0 |8173B69E0        |159692   |262084 |Cash          |               52|          15.8|   10607.54|              1|           5|       10607.54|             52|                0|            550412.7|                -0.79|            10584.86|
|7409458  |2022-09-02 23:22:00 |81655BDA0 |8173B69E0        |159692   |262084 |Cheque        |               52|          15.8|   14121.13|              1|           5|       14121.13|             52|                0|            550412.7|                -0.79|            10584.86|
|7424929  |2022-09-02 23:29:00 |81655BDA0 |8173B69E0        |159692   |262084 |Credit Card   |               52|          15.8|   15539.40|              1|           5|       15539.40|             52|                0|            550412.7|                -0.79|            10584.86|
|9479004  |2022-09-05 03:30:00 |81655BDA0 |8173B69E0        |159692   |262084 |ACH           |               52|          15.8|    2071.37|              1|           5|        2071.37|             52|                0|            550412.7|                -0.79|            10584.86|
|9487300  |2022-09-05 03:37:00 |81655BDA0 |8173B69E0        |159692   |262084 |Cash          |               52|          15.8|   10607.54|              1|           5|       10607.54|             52|                0|            550412.7|                -0.79|            10584.86|
|9490113  |2022-09-05 03:39:00 |81655BDA0 |8173B69E0        |159692   |262084 |Cheque        |               52|          15.8|   14121.13|              1|           5|       14121.13|             52|                0|            550412.7|                -0.79|            10584.86|
|9500305  |2022-09-05 03:47:00 |81655BDA0 |8173B69E0        |159692   |262084 |Credit Card   |               52|          15.8|   15539.40|              1|           5|       15539.40|             52|                0|            550412.7|                -0.79|            10584.86|
|12617424 |2022-09-06 19:02:00 |81655BDA0 |8173B69E0        |159692   |262084 |Cash          |               52|          15.8|   10607.54|              1|           5|       10607.54|             52|                0|            550412.7|                -0.79|            10584.86|
|12631512 |2022-09-06 19:13:00 |81655BDA0 |8173B69E0        |159692   |262084 |Credit Card   |               52|          15.8|   15539.40|              1|           5|       15539.40|             52|                0|            550412.7|                -0.79|            10584.86|
|12647137 |2022-09-06 19:25:00 |81655BDA0 |8173B69E0        |159692   |262084 |Cheque        |               52|          15.8|   14121.13|              1|           5|       14121.13|             52|                0|            550412.7|                -0.79|            10584.86|
|12650143 |2022-09-06 19:27:00 |81655BDA0 |8173B69E0        |159692   |262084 |ACH           |               52|          15.8|    2071.37|              1|           5|        2071.37|             52|                0|            550412.7|                -0.79|            10584.86|
|14240012 |2022-09-07 15:05:00 |81655BDA0 |8173B69E0        |159692   |262084 |Credit Card   |               52|          15.8|   15539.40|              1|           5|       15539.40|             52|                0|            550412.7|                -0.79|            10584.86|
|14245977 |2022-09-07 15:09:00 |81655BDA0 |8173B69E0        |159692   |262084 |ACH           |               52|          15.8|    2071.37|              1|           5|        2071.37|             52|                0|            550412.7|                -0.79|            10584.86|
|14263438 |2022-09-07 15:23:00 |81655BDA0 |8173B69E0        |159692   |262084 |Cash          |               52|          15.8|   10607.54|              1|           5|       10607.54|             52|                0|            550412.7|                -0.79|            10584.86|
|14271101 |2022-09-07 15:29:00 |81655BDA0 |8173B69E0        |159692   |262084 |Cheque        |               52|          15.8|   14121.13|              1|           5|       14121.13|             52|                0|            550412.7|                -0.79|            10584.86|
|15428600 |2022-09-08 05:34:00 |81655BDA0 |8173B69E0        |159692   |262084 |Cheque        |               52|          15.8|   14121.13|              1|           5|       14121.13|             52|                0|            550412.7|                -0.79|            10584.86|
|15430856 |2022-09-08 05:36:00 |81655BDA0 |8173B69E0        |159692   |262084 |ACH           |               52|          15.8|    2071.37|              1|           5|        2071.37|             52|                0|            550412.7|                -0.79|            10584.86|
|15435626 |2022-09-08 05:40:00 |81655BDA0 |8173B69E0        |159692   |262084 |Cash          |               52|          15.8|   10607.54|              1|           5|       10607.54|             52|                0|            550412.7|                -0.79|            10584.86|
|15459280 |2022-09-08 05:58:00 |81655BDA0 |8173B69E0        |159692   |262084 |Credit Card   |               52|          15.8|   15539.40|              1|           5|       15539.40|             52|                0|            550412.7|                -0.79|            10584.86|
|18811438 |2022-09-09 17:40:00 |81655BDA0 |8173B69E0        |159692   |262084 |Credit Card   |               52|          15.8|   15539.40|              1|           5|       15539.40|             52|                0|            550412.7|                -0.79|            10584.86|
|18828490 |2022-09-09 17:49:00 |81655BDA0 |8173B69E0        |159692   |262084 |ACH           |               52|          15.8|    2071.37|              1|           5|        2071.37|             52|                0|            550412.7|                -0.79|            10584.86|
|18835152 |2022-09-09 17:53:00 |81655BDA0 |8173B69E0        |159692   |262084 |Cheque        |               52|          15.8|   14121.13|              1|           5|       14121.13|             52|                0|            550412.7|                -0.79|            10584.86|
|18839271 |2022-09-09 17:55:00 |81655BDA0 |8173B69E0        |159692   |262084 |Cash          |               52|          15.8|   10607.54|              1|           5|       10607.54|             52|                0|            550412.7|                -0.79|            10584.86|
|21992076 |2022-09-12 10:04:00 |81655BDA0 |8173B69E0        |159692   |262084 |Cheque        |               52|          15.8|   14121.13|              1|           5|       14121.13|             52|                0|            550412.7|                -0.79|            10584.86|
|21995991 |2022-09-12 10:08:00 |81655BDA0 |8173B69E0        |159692   |262084 |ACH           |               52|          15.8|    2071.37|              1|           5|        2071.37|             52|                0|            550412.7|                -0.79|            10584.86|
|22020879 |2022-09-12 10:26:00 |81655BDA0 |8173B69E0        |159692   |262084 |Cash          |               52|          15.8|   10607.54|              1|           5|       10607.54|             52|                0|            550412.7|                -0.79|            10584.86|
|22020887 |2022-09-12 10:26:00 |81655BDA0 |8173B69E0        |159692   |262084 |Credit Card   |               52|          15.8|   15539.40|              1|           5|       15539.40|             52|                0|            550412.7|                -0.79|            10584.86|