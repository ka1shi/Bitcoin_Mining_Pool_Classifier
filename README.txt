Bitcoin mining pool classifier to predict if an address belongs to a miner or not.
 
Data Collection: Data is collected from Google Bigquery (https://console.cloud.google.com) with sql queries written in file sql_query_mining_pool_true.txt and sql_query_mining_pool_false.txt
Data is collected with two sql queries with is_miner = ‘true’ and with is_miner = ‘false’. Data is combined, shuffled and further analysed. 
 
Data folder : data files collected.
mining_data_final: final data after combining both collected datasets.

Data Dictionary: The columns of data and their definitions are as follows: 
is_miner : if node is miner or not  
address : address of node 
output_month_min : Minimum of block_timestamp_month(month of block which contains transaction) when this address (output) receives the transaction 
output_month_max : Maximum of block_timestamp_month(month of block which contains transaction) when this address (output) receives the transaction 
input_month_min : Minimum of block_timestamp_month(month of block which contains transaction) when this address (input) initiates the transaction 
input_month_max : Maximum block_timestamp_month(month of block which contains transaction) when this address (input) initiates the transaction 
output_active_time : Total time when address is active as receiver 
input_active_time : Total time when address is active as sender 
io_max_lag : input/output maximum time lag 
io_min_lag : input/output minimum time lag 
output_active_months : Count of months when address is active as receiver 
total_tx_output_count : Count of transaction as receiver 
total_tx_output_value :  Total value of amount received 
mean_tx_output_value : Average of value of amount received 
stddev_tx_output_value : Standard deviation of total value of amount received 
total_output_tx : Total number of transactions when address received amount with distinct hash 
mean_monthly_output_value : Average value of amount received per month 
mean_monthly_output_count : Average number of transaction blocks received per month 
input_active_months : Count of months when address is active as sender 
total_tx_input_count : Count of transaction as sender 
total_tx_input_value : Total value of amount sent 
mean_tx_input_value : Average of value of amount sent 
stddev_tx_input_value : Standard deviation of total value of amount sent 
total_input_tx : Total number of transactions when address sent amount with distinct hash 
mean_monthly_input_value : Average value of amount sent per month 
mean_monthly_input_count : Average number of transaction blocks sent per month 
mean_output_idle_time : Average time when address is not receiving any transaction 
stddev_output_idle_time : Standard deviation of time when address is not receiving any transaction 
mean_input_idle_time : Average time when address is not sending any transaction 
stddev_input_idle_time : Standard deviation of time when address is not sending any transaction

 
Models: 

Logistic Regression and 
Random Forest Classifier 
 
Conclusion: 
-Able to achieve an detect if an address belongs to a miner with AP of 95% with Random Forest Classifier. 
-Able to somewhat detect dark miners (data points where model predicts true, but are labelled as false). 