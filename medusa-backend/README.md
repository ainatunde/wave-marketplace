# Medusa Backend Setup and API Documentation

## Introduction
This document provides a setup guide for the Medusa backend and details on the available APIs.

## Setting Up Medusa Backend

1. **Prerequisites**
   - Node.js (>= 14.x)
   - Yarn (>= 1.22.x)
   - A PostgreSQL database

2. **Installation**
   ```bash
   git clone https://github.com/medusajs/medusa.git
   cd medusa
   yarn install
   ```

3. **Configuration**
   - Create a `.env` file in the root directory and set the following variables:
     ```plaintext
     DATABASE_URL=postgres://username:password@localhost:5432/my_database
     MEDUSA_SECRET=your_secret_key
     ```

4. **Running the Server**
   ```bash
   yarn develop
   ```
   Your backend should now be running on `http://localhost:9000`

## API Documentation

### Authentication
- **POST /store/auth**  
  Authenticate a user and get a token.

### Products
- **GET /store/products**  
  Retrieve all products.
- **GET /store/products/:id**  
  Retrieve a single product by ID.

### Orders
- **POST /store/orders**  
  Create a new order.
- **GET /store/orders/:id**  
  Retrieve order details by ID.

For detailed API usage and other available endpoints, please refer to the [Medusa API documentation](https://medusajs.com/docs).

## Conclusion
This README should help you get started with the Medusa backend. For further assistance, refer to the official [Medusa documentation](https://medusajs.com/docs).