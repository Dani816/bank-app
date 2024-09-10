# bank-app

Simple banking app made to show basic knowledge of spring boot app.
Task contains three subtasks with solutions

1. Import file during startup 
    On every startup, new .txt file is generated with random transactions which can't lead sender account to be negative balance
    Same txt is split in batches and saved to database with Files.readAllLines( since we knew that file is max 100k records.

2. Provide a REST API and a service. Example shared for every API.
   base_url: http://localhost:8080
   
   2.1. Customer Endpoint:
      {{base_url}}/customer/details/5

   2.2. Transaction endpoint:
      {{base_url}}/transaction/save
      JSON: 
      {
       "senderAccountId": "1",
       "receiverAccountId": "2",
       "amount": "10.50",
       "message": "Test transaction"
       }

   2.3. Transaction history endpoint:
      {{base_url}}/transaction/history/7
      {{base_url}}/transaction/history/1?filter_name=amount&filter_value=10.50

3. Monthly transaction update job 
    //TODO