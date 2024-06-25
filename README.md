# Summary of the Solution

## Several task that need to be done is through :

### 1. Table Format Initialization
#### Since each json file has different keys, it is important to create base table that can contain all keys each json file has. accounts_frm, cards_frm, and savings_accounts_frm are created to collect JSON data that has been converted into Dataframe.

### 2. JSON Conversion to Dataframe
#### Conversion process from JSON to Dataframe starts by iterating each keys & values on each JSON files. These keys will be checked to the table that has been initialized in step 1 and transfer its values when matched, whereas if the keys do not match, it will transfer blank ('') value to the table in step 1. Timestamp data in "ts" key will be converted into proper timestamp format ('YYYY-MM-DD HH:MM:SS').

### 3. Dataframe Join
#### JSON file that has been converted into Dataframe are joined into one Dataframe. Accounts is the main Dataframe to be joined, since it contained card_id & savings_account_id. By ingesting id and eliminating rows without certain values on certain columns for each Dataframe, accounts Dataframe left joined to cards & savings_accounts Dataframe. Column with duplicate name needs to be renamed, hence on this new Dataframe, the "ts" column from cards & savings_account are renamed to credit_used_timestamp & balanced_timestamp respectively.

### 4. Result
#### From 
