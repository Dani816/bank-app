# Bank App

A simple banking app built to demonstrate basic knowledge of Spring Boot. The project consists of four main features.

## Features

1. **Import File During Startup**
    - On every startup, a new `.txt` file is generated with random transactions, ensuring that no sender's account balance becomes negative.
    - The file is split into batches and saved to the database using `Files.readAllLines()`, as the file size is capped at 100,000 records.

2. **REST API and Service**
   The app exposes the following REST endpoints:

   ### 2.1 Customer Endpoint:
    - **Endpoint**: `GET /customer/details/{id}`
    - **Example**: `http://localhost:8080/customer/details/5`

   ### 2.2 Transaction Endpoint:
    - **Endpoint**: `POST /transaction/save`
    - **Request Body (JSON)**:
      ```json
      {
        "senderAccountId": "1",
        "receiverAccountId": "2",
        "amount": "10.50",
        "message": "Test transaction"
      }
      ```
    - **Example**: `http://localhost:8080/transaction/save`

   ### 2.3 Transaction History Endpoint:
    - **Endpoint**: `GET /transaction/history/{accountId}`
    - **Endpoint**: `GET /transaction/history/{customerId}?{filter_name}={filter_value}​`
    - **Examples**:
        - `http://localhost:8080/transaction/history/7`
        - `http://localhost:8080/transaction/history/1?filter_name=amount&filter_value=10.50`

3. **Monthly Transaction Update Job**
    - **@Scheduled(cron = "* 1 * * * *")**: triggered every minute for testing purposes seconds
   
4. **Transaction confirmation**
    - **Trigger success email**: Follow step 2.2
    - **Trigger fail email**: Follow step 2.2 and replace "amount": "10.50", with "amount": "999999.0",
---

