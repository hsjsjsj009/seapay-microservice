 # Description

 ## Seapay
 
Seapay is a fintech app consists of 4 different services
  - API gateway
    - API gateway service routes all requests to other services
  - User account
    - User account service takes care of user management: user creation, get user data, etc
  - Wallet
    - Wallet service handles all wallet functionalities: update balance, get balance, create wallet, etc
  - Transaction
    - Transaction service manage all transaction data

The project itself has 4 modules
 - seapay-api
   - a module that abstracts interface for all services
 - seapay-common
   - a module that groups all common functionalities used by all services
 - seapay-domain
   - the bussiness logic for all services goes here
 - seapay-monolith
   - an entry point of our monolithic app, including all handlers
  
 # How to use

 ### Dependencies
 In Linux:
 - Java 8
 - Postgresql
 - Postman
 
 ### Potgresql Linux SetUp (Before that install Postgresql)
  
  To access PSQL:
  ```
  sudo -u postgres psql
  ```

  - Create User According to Your Linux Username
    - Open PSQL
    - Type this code:
    ```
    CREATE USER <username> superuser;
    ```
  - Provide User Login
    - Open PSQL
    - Type this code:
    ```
    ALTER ROLE "<username>" with LOGIN;
    ```
  - Grant user access (No Password Required)
    -  Open ``` pg_hba.conf ```, type this code :
    ```
    cd /etc/postgresql/<your version>/main
    sudo nano pg_hba.conf
    ```
    - Change this:
    ```
    local       all         postgres            peer

    to

    local       all         postgres            trust
    ```
    
    ```
    host  all   all         127.0.0.1/32        md5

    to

    host  all   all         127.0.0.1/32        trust
    ```

  - Restart service
  ```
  sudo service postgresql restart
  ```

 ### How to build
 In Ubuntu

 ```
 make all
 ```

 ### How to run
 In Ubuntu
 
 Services:
 - transaction
 - gateway
 - user
 - wallet
 - monolith

 ```
 make run-<services>
 ```

 ### Port
 - Gateway = 8080
 - Monolith = 8080
 - Transaction = 8081
 - User = 8082
 - Wallet = 8083
  



