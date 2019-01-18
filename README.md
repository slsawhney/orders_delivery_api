# RESTful APIs

## About

- [Docker](https://www.docker.com/) as the container service to isolate the environment.
- [Php](https://php.net/) to develop backend support.
- [MySQL](https://mysql.com/) as the database layer
- [NGINX](https://docs.nginx.com/nginx/admin-guide/content-cache/content-caching/) as a proxy / content-caching layer

## How to Install & Run

1.  Clone the repo
2.  Set Google Distance API key in /include/.env file
3.  Run `start.sh` file to compose Docker. Use $ `bash start.sh` or `./start.sh` command to run it. 
4.  After starting container, testcases will run automatically

## Manually Starting the docker and test Cases

1. You can run `docker-compose up` from terminal
2. Server is accessible at `http://localhost:8080`
3. Run manual testcase suite by:

   **Unit test:** `docker exec delivery_php php ./vendor/phpunit/phpunit/phpunit /var/www/html/tests/Unit/OrderUnitTest.php`
   
   **Integration tests:** `docker exec delivery_php php ./vendor/phpunit/phpunit/phpunit /var/www/html/tests/Feature/OrderControllerTest.php`

## How to Run Tests (From CLI)

 Test Cases can be executed by: 
 
   **Unit test:** `docker exec delivery_php php ./vendor/phpunit/phpunit/phpunit /var/www/html/tests/Unit/OrderUnitTest.php`
   
   **Integration tests:** `docker exec delivery_php php ./vendor/phpunit/phpunit/phpunit /var/www/html/tests/Feature/OrderControllerTest.php`

## Application Structure

**/code/tests**

- this folder contains testcases.

  ***Unit Test case***
    -/code/tests/Unit

  ***Integration Test case***
    -/code/Feature/Unit

**/code**

- contains all the server configuration files, classes and models
- `/code/index.php` contains all the api's methods :
    1. localhost:8080/orders - GET url to fetch orders with page and limit
    2. localhost:8080/order - POST method to insert new order with origin and destination
    3. localhost:8080/order - PUT method to update status for taken.(Handled simultaneous update request from multiple users at the same time with response status 409)

**code/configuration/environments/environment.env**
- add google apk key in corresponding to GOOGLE_API_KEY

**code/configuration/settings.php**

- contains all configuration related to database connection
