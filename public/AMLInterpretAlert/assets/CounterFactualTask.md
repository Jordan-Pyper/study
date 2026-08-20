# Variable Definitions
### The Current Transaction
These variables describe the specific details of the money transfer currently taking place:
* **AmountPaid**: The total amount of money being sent in the current transaction.  
* **AmountReceived**: The total amount of money actually received in the current transaction.
* **PaymentFormat_ACH**: Indicates whether the current transaction was processed specifically as an ACH (Automated Clearing House) transfer, which is one of the available payment formats.  
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



