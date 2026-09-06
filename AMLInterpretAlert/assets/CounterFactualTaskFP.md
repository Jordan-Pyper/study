# AML Transaction Alert
The table below provides information regarding a transaction that the model has identified as suspicious. The data features are those that are more frequently used to generate counterfactual examples. All others are excluded. Please review the **column definitions** below to understand what the feature names mean and how they can be interpreted.



# Variable Definitions

### The Current Transaction
These variables describe the specific details of the money transfer currently taking place:
* **AmountPaid**: The total amount of money being sent in the current transaction.  
* **AmountReceived**: The total amount of money actually received in the current transaction.
* **PaymentFormat_ACH**: Indicates whether the current transaction was processed specifically as an ACH (Automated Clearing House) transfer, which is one of the available payment formats. Transaction that are ACH will be represented by '1' and non-ACH transaction as '0'.
 
### The Receiver's History ("dest" variables)
These variables summarize the historical network activity of the "destination" (the account receiving the money):  
* **dest_deg_in**: The total number of incoming transactions this account has received in the past.  
* **dest_ratio_in**: The proportion of this account's historical network activity that consists of incoming transactions.  
* **dest_ratio_out**: The proportion of this account's historical network activity that consists of outgoing transactions.  
* **dest_max_col4_in**: The single largest payment amount this account has ever received.  
* **dest_sum_col4_in**: The combined total sum of all payment amounts this account has ever received.  
* **dest_avg_col4_in**: The average payment amount this account typically receives.  

### The Sender's History ("source" variables)
These variables summarize the historical network activity of the "source" (the account sending the money):  
* **source_deg_in**: The total number of incoming transactions this sending account has received from others in the past.  
* **source_ratio_out**: The proportion of this sending account's historical network activity that consists of outgoing transactions.  
* **source_avg_col4_out**: The average payment amount this account typically sends out to others.

# What Is A Counterfactual Explanation?

A counterfactual explanation explains a machine learning prediction by showing the smallest change to the input data needed to flip the model's decision to a different outcome. It answers the fundamental question: "What would have had to be different for the model to decide otherwise?"

Rather than describing the internal math or weights of the model, a counterfactual provides an intuitive, hypothetical "what-if" scenario.

# Counter Factual Differences
This tables provides the difference between counterfactual cases and the AML transaction alert. This way it is easy to see what changed in the counterfactual case, compared to the transaction alert that would make the model no longer think the transaction is suspicious. Positive numbers represents an increase compared to the alert transaction and negative values represents a decrease compared to the alert transaction.

| dest_ratio_in| dest_max_col4_in| dest_sum_col4_in| AmountReceived| PaymentFormat_ACH| AmountPaid| dest_avg_col4_in| dest_deg_in| source_avg_col4_out| dest_ratio_out| source_ratio_out| source_deg_in| numChanged| mathDist|
|-------------:|----------------:|----------------:|--------------:|-----------------:|----------:|----------------:|-----------:|-------------------:|--------------:|----------------:|-------------:|----------:|--------:|
|          0.00|                0|                0|              0|                -1|          0|             0.00|           0|                 0.0|            -33|             0.00|             0|          2|     0.01|
|          0.00|                0|                0|              0|                -1|          0|             0.00|           0|                 0.0|              0|             0.00|             0|          1|     0.01|
|          0.00|                0|                0|              0|                -1|          0|         -6740.88|           0|                 0.0|            -33|             0.00|             0|          3|     0.01|
|          0.00|                0|                0|              0|                -1|          0|             0.00|           0|           -119138.8|              0|             0.00|             0|          2|     0.01|
|         22.85|                0|                0|              0|                 0|          0|             0.00|           0|                 0.0|              0|            15.86|             0|          2|     0.00|

# Treansaction History
This is the history of transactions for this particular Account. This is to provide an investigator with some potential context for the transactions.