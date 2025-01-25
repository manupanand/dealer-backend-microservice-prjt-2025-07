
# Dealer and Product Microservices with Docker Compose

This project demonstrates two microservices, Dealer Details and Product List, running in separate containers orchestrated using Docker Compose.

    Dealer Details Service: A Node.js-based microservice providing dealer and pricing details.
    Product List Service: A Python Flask-based microservice listing available products and their dealers.

## Project Structure
```
.
├── dealer_details/
│   ├── Dockerfile          # Dockerfile for Dealer Details service
│   ├── server.js           # Main Node.js application file
│   ├── package.json        # Node.js dependencies and scripts
│   ├── utils/
│       └── dealers.json    # Dealer data file
├── product_list/
│   ├── Dockerfile          # Dockerfile for Product List service
│   ├── app.py              # Main Python Flask application file
│   ├── requirements.txt    # Python dependencies
│   ├── products.json       # Product data file
├── docker-compose.yml      # Docker Compose file for orchestration
├── Makefile                # Makefile to simplify Docker Compose commands
└── README.md               # Project documentation
```

## Prerequisites

    Docker installed on your system.
    Docker Compose installed on your system.

## Installation and Setup

### Clone the Repository:

```
git clone https://github.com/manupanand-freelance-developer/ci-cd-pipeline-project.git
cd ci-cd-pipeline-project 
```

### Build and Start Services: Run the following command:
```
    make image
    
```

### This will:
    - Build the Docker images for both microservices.
    - Start the containers for both services.

### Access the Services:
    - Dealer Details Service: Accessible at http://localhost:8080
    - Product List Service: Accessible at http://localhost:5000


## API Endpoints
### Dealer Details Service (http://localhost:8080)

### Get Product Price by Dealer:
        Endpoint: /price/:dealer/:product
        Method: GET
        Response:
```
    {
      "message": "ProductName costs Price at DealerName"
    }
```
### Get Prices of All Dealers for a Product:

    Endpoint: /allprice/:product
    Method: GET
    Response:
```
        {
          "prices": [
            {"key": "Dealer1", "value": "Price1"},
            {"key": "Dealer2", "value": "Price2"}
          ]
        }
```
### Product List Service (http://localhost:5000)

    Get All Products:
        Endpoint: /products
        Method: GET
        Response:
```
    {
      "products": ["Product1", "Product2", "Product3"]
    }
```
### Get Dealers for a Product:

    Endpoint: /getdealers/:product
    Method: GET
    Response:
```
        {
          "dealers": ["Dealer1", "Dealer2"]
        }
```
Notes

    Makefile: Use the provided Makefile for easy orchestration. Run:
```
    make image
```
    Persistent Data:
        The data for dealers and products is stored in utils/dealers.json and products.json respectively.
        Update these files to reflect your own data.

    Dependencies:
        Node.js microservice depends on express, cors, and nodemon.
        Flask microservice depends on Flask and flask-cors.

#### Contributions

Feel free to open issues or submit pull requests to improve this project.
License

This project is licensed under the MIT License.
