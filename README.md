# Koi API
A Scalable Backend API built to support an ecommerce website. 

## Authors
#### [Dennis Hsu](https://github.com/denniseh7)

## Tech Stack

### Development
![NodeJS](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)
![ExpressJS](https://img.shields.io/badge/Express.js-404D59?style=for-the-badge)
![JavaScript](https://img.shields.io/badge/JavaScript-323330?style=for-the-badge&logo=javascript&logoColor=F7DF1E)
![PostGresQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![AWS](https://img.shields.io/badge/Amazon_AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)

### Environment and Testing
![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Git](https://img.shields.io/badge/GIT-E44C30?style=for-the-badge&logo=git&logoColor=white)
![VSCode](https://img.shields.io/badge/Visual_Studio_Code-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white)
![ESLint](https://img.shields.io/badge/eslint-3A33D1?style=for-the-badge&logo=eslint&logoColor=white)
![Jest](https://img.shields.io/badge/Jest-323330?style=for-the-badge&logo=Jest&logoColor=white)

<!--- Dennis: Product Overview --->
## Summary
This is a backend API for an ecommerce website the supports legacy code from a frontend page. The service meets business requirements of 1000 requests per second, less than 50 ms query times, less than 2000ms response time, and under 0.1% error rate. The API supports the endpoints for ratings and reviews of retail products. The microservice scales to meet user traffic while maintaining requirements under load.


## Ratings and Reviews
This section shows information about the backend API for the ratings and reviews endpoint.

### API End Points

* GET Reviews- Returns a list of reviews based off of product ID; Each Review has the review info and associated images and rating
* GET Meta- Returns metadata of the product based on product ID; Includes Average rating, count, and characteristics data of the product
* POST Helpful- Marks a review as helpful and increased the helpfulness count of that review
* POST Report- Marks a review as reported, removing the review from future query lists

## Stress Testing

### PostgresQL Query Times
* Optimized Read Requests with Table Indexing due to read requests outnumbering write requests
* Bundled queries into one call to reduce query time to 3.71ms
* Stress tests using local K6 and New Relic

#### K6
![OptimizedReadQueryTest](https://user-images.githubusercontent.com/7811764/235556281-143329c0-18b2-4bbf-869d-b20753c272a8.png)

#### New Relic
![NewRelicTesting](https://user-images.githubusercontent.com/7811764/235556773-269e0f00-7548-48f5-9c8e-f66251466229.png)


### Deployed AWS Server Metrics
* Deployed 4 instances of Express Servers with a PostgresQL database server and a NGINX Load Balancer Server with 10Mb Caching
* Handles up to 1500 Requests per second with 0% error rate and 147ms response time
* Stress tests were run on servers located in U.S. West AWS and Loader.IO server in U.S. East Virginia for latency testing across the U.S.

![NginxCachingRandomID](https://user-images.githubusercontent.com/7811764/235556547-4dea4758-765e-40d1-a81e-6b2de829d311.png)


## Getting Started

### Requirements
* Node.js v16.19.0
* postgres ^3.3.4

### Installation
* Clone the repository
    ```
        https://github.com/AquariumSDC/KoiApi
    ```
* Install the dependencies
    ```
        npm install
    ```
* Create a .env file in the root folder with server port and Postgres database authentication
    ```
      
        PORT = DESIRED_SERVER_PORT_NUMBER

        DB_PORT = DB_PORT_NUMBER
        DB_HOST='database hostname'
        DB_NAME='database name'
        DB_USER='database user'
        DB_PASS='database user password'
    ```
* Ensure your Postgres Database service is running with correct authentication

* ETL Necessary Data for the Database from a CSV file if needed

* Run the one of the following commands to start
    ```
        npx run start
        npm run start
    ```

