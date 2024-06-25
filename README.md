# Summary of the Solution

## Several step that performed in this task are :

### 1. Table Format Initialization
#### Since each json file has different keys, it is important to create base table that can contain all keys each json file has. accounts_frm, cards_frm, and savings_accounts_frm are created to collect JSON data that has been converted into Dataframe.

### 2. JSON Conversion to Dataframe
#### Conversion process from JSON to Dataframe starts by iterating each keys & values on each JSON files. These keys will be checked to the table that has been initialized in step 1 and transfer its values when matched, whereas if the keys do not match, it will transfer blank ('') value to the table in step 1. Timestamp data in "ts" key will be converted into proper timestamp format ('YYYY-MM-DD HH:MM:SS').

### 3. Dataframe Join
#### JSON file that has been converted into Dataframe are joined into one Dataframe. Accounts is the main Dataframe to be joined, since it contained card_id & savings_account_id. By ingesting id and eliminating rows without certain values on certain columns for each Dataframe, accounts Dataframe left joined to cards & savings_accounts Dataframe. Column with duplicate name needs to be renamed, hence on this new Dataframe, the "ts" column from cards & savings_account are renamed to credit_used_timestamp & balanced_timestamp respectively.

### 4. Result
#### From the joined Dataframe, we can conclude that :
##### 1. account_id a1 has 1 savings_account_id & 2 card_id (c1 has already closed on 2020-01-10 and new card, c2, start active on 2020-01-18)
##### 2. There are total of 8 transactions happening in account_id a1. The details are :
######  a. 4 from sa1, occured in January 2 (increased by 15000), 10 (increased by 25000, decreased by 19000) , and 20 (increased by 12000)
######  b. 3 from c1, occured in January 6 (increased by 12000), 8 (increased by 7000), and 10 (decreased by 19000)
######  c. 1 from c2, occured in January 18 (increased by 37000)


#### Due to technical issue and error, the Docker file is not ready at the time, hence there is no Docker file pushed at this repository.
#### The result can still be seen from .ipynb file and can be run using google colab. (When using google colab, please do make sure to also upload JSON file in "data" folder)
