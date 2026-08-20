# AML Transaction Alert
|Features             |Value               |
|:--------------------|:-------------------|
|Payment.Format       |ACH                 |
|source_ratio_out     |3.18   |
|dest_ratio_in        |1                   |
|AmountPaid           |37777.52            |
|source_fan_out       |11                  |
|dest_fan_in          |2                   |
|Amount Received      |37777.52            |
|source_deg_out       |35                  |
|fan_out_bins_2.3     |0                   |
|source_sum_col4_out  |222049202.79        |
|source_skew_col4_out |3.72                |
|source_avg_col4_out  |6344262.94          |
|Bank Name            |China Bank #9       |
|Entity Name          |Corporation #199303 |

# Columns Definitions
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

# Varirable Importance from XGBoost ML model - Top 12 Predictors
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

# Transaction History

|         |Timestamp           |Account   |Receiving Account |From Bank |To Bank |Payment Format | source_ratio_out| dest_ratio_in|  Amount Paid| source_fan_out| dest_fan_in| Amount Received| source_deg_out| fan_out_bins_2.3| source_sum_col4_out| source_skew_col4_out| source_avg_col4_out|
|:--------|:-------------------|:---------|:----------------|:--------|:------|:-------------|----------------:|-------------:|-----------:|--------------:|-----------:|--------------:|--------------:|----------------:|-------------------:|--------------------:|-------------------:|
|16707374 |2022-09-08 21:57:00 |80DD650C0 |80DD650C0        |135161   |135161 |ACH           |         3.555556|      2.066667|    88611.61|              9|          15|       11290.78|             32|                4|           221864081|             3.523958|             6933253|
|16707378 |2022-09-08 21:57:00 |80DD650C0 |80E37DA70        |135161   |33065  |ACH           |         3.555556|      2.000000|    11290.78|              9|           3|       11290.78|             32|                4|           221864081|             3.523958|             6933253|
|18102750 |2022-09-09 11:01:00 |80DD650C0 |802DE8830        |135161   |867    |ACH           |         3.555556|      2.000000|     7037.48|              9|           4|        7037.48|             32|                4|           221864081|             3.523958|             6933253|
|18102751 |2022-09-09 11:01:00 |80DD650C0 |80DD650C0        |135161   |135161 |ACH           |         3.555556|      2.066667|    47134.24|              9|          15|        7037.48|             32|                4|           221864081|             3.523958|             6933253|
|18958337 |2022-09-09 19:02:00 |80DD650C0 |80C220110        |135161   |118247 |ACH           |         3.555556|     19.250000|   109760.05|              9|           4|      109760.05|             32|                0|           221864081|             3.523958|             6933253|
|19078661 |2022-09-09 20:10:00 |80DD650C0 |8164AA6E0        |135161   |6      |ACH           |         3.555556|      2.000000|   665779.39|              9|           2|      665779.39|             32|                4|           221864081|             3.523958|             6933253|
|19078738 |2022-09-09 20:10:00 |80DD650C0 |80DD650C0        |135161   |135161 |ACH           |         3.555556|      2.066667|    60714.61|              9|          15|      665779.39|             32|                4|           221864081|             3.523958|             6933253|
|21358401 |2022-09-12 01:56:00 |80DD650C0 |80DD650C0        |135161   |135161 |ACH           |         3.555556|      2.066667|   111774.05|              9|          15|       14242.11|             32|                4|           221864081|             3.523958|             6933253|
|21358413 |2022-09-12 01:56:00 |80DD650C0 |80105ADC0        |135161   |11315  |ACH           |         3.555556|      5.000000|    14242.11|              9|           3|       14242.11|             32|                4|           221864081|             3.523958|             6933253|
|22283207 |2022-09-12 13:48:00 |80DD650C0 |8168DF1D0        |135161   |23187  |ACH           |         3.555556|      3.333333|    11849.54|              9|           3|       11849.54|             32|                4|           221864081|             3.523958|             6933253|
|22283208 |2022-09-12 13:48:00 |80DD650C0 |80DD650C0        |135161   |135161 |ACH           |         3.555556|      2.066667|    79363.45|              9|          15|       11849.54|             32|                4|           221864081|             3.523958|             6933253|
|22474350 |2022-09-12 16:15:00 |80DD650C0 |80ABD9CD0        |135161   |15767  |ACH           |         3.555556|     16.000000|    13691.97|              9|           3|       13691.97|             32|                4|           221864081|             3.523958|             6933253|
|22474389 |2022-09-12 16:15:00 |80DD650C0 |80DD650C0        |135161   |135161 |ACH           |         3.555556|      2.066667|   107456.47|              9|          15|       13691.97|             32|                4|           221864081|             3.523958|             6933253|
|22614579 |2022-09-12 18:03:00 |80DD650C0 |8009283F0        |135161   |1148   |ACH           |         3.555556|      2.666667|    43996.07|              9|           3|       43996.07|             32|                6|           221864081|             3.523958|             6933253|
|22614580 |2022-09-12 18:03:00 |80DD650C0 |80DD650C0        |135161   |135161 |ACH           |         3.555556|      2.066667| 97216169.14|              9|          15|    12387165.36|             32|                6|           221864081|             3.523958|             6933253|
|22614606 |2022-09-12 18:03:00 |80DD650C0 |8009283F0        |135161   |1148   |ACH           |         3.555556|      2.666667| 12343169.30|              9|           3|    12343169.30|             32|                6|           221864081|             3.523958|             6933253|
|23939041 |2022-09-13 10:18:00 |80DD650C0 |810222950        |135161   |243541 |ACH           |         3.181818|      1.000000|    37777.52|             11|           2|       37777.52|             35|                0|           222049203|             3.721236|             6344263|
|26572491 |2022-09-14 19:17:00 |80DD650C0 |80226DE70        |135161   |11315  |ACH           |         3.181818|     12.250000|    16652.63|             11|           4|       16652.63|             35|                2|           222049203|             3.721236|             6344263|
|26572494 |2022-09-14 19:17:00 |80DD650C0 |80DD650C0        |135161   |135161 |ACH           |         3.181818|      2.133333|   130692.12|             11|          15|       16652.63|             35|                2|           222049203|             3.721236|             6344263|