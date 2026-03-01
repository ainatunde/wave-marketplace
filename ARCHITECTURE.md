# Architecture Documentation

## Overview
This document provides an overview of the system architecture for the Wave Marketplace, detailing the integration of Medusa and Next.js, the database schema, and the Nigerian payment flow.

---

## System Design
The Wave Marketplace is designed as a modern e-commerce platform leveraging a headless architecture. The application consists of the following key components:

- **Frontend**: Built with Next.js, providing a fast and responsive user interface.
- **Backend**: Powered by Medusa, an open-source headless commerce engine that provides the backend functionalities including product management, order processing, and customer management.
- **Database**: A relational database is used to store user, product, and transaction information.

---

## Medusa + Next.js Integration
The integration between Medusa and Next.js involves the following:
1. **API Communication**: The Next.js frontend communicates with the Medusa backend via RESTful APIs to fetch product data and manage user sessions.
2. **Server-side Rendering**: Next.js supports server-side rendering, which improves performance and SEO by rendering pages on the server before sending them to the client.
3. **Static Site Generation**: Certain product pages can be statically generated at build time for better performance.

---

## Database Schema
The database schema is designed to efficiently store and relationally manage the following entities:
- **Users**: Contains user profile information and authentication credentials.
- **Products**: Stores product details including name, description, price, and stock availability.
- **Orders**: Manages order data, including associated products and user details.
- **Payments**: Tracks payment information, including transaction IDs and statuses.

Example of the database schema:
```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE,
    password_hash VARCHAR(255) NOT NULL
);

CREATE TABLE products (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    price DECIMAL(10, 2) NOT NULL,
    stock INT NOT NULL
);

CREATE TABLE orders (
    id SERIAL PRIMARY KEY,
    user_id INT REFERENCES users(id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE payments (
    id SERIAL PRIMARY KEY,
    order_id INT REFERENCES orders(id),
    amount DECIMAL(10, 2) NOT NULL,
    status VARCHAR(50) NOT NULL
);
```

---

## Nigerian Payment Flow
The payment flow for users in Nigeria includes the following steps:
1. **Payment Method Selection**: Users can choose from various payment methods supported in Nigeria, including card payments, bank transfers, and mobile money.
2. **Payment Processing**: Upon payment submission, a request is sent to the payment gateway.
3. **Confirmation and Notifications**: The gateway processes the payment, and both the user and the platform receive notifications regarding the success or failure of the transaction.
4. **Order Fulfillment**: Once payment is confirmed, the order is processed, and users can track their order status in their account.

---

## Conclusion
This document serves as a foundational outline for understanding the architecture of the Wave Marketplace. For detailed implementation specifics, refer to the respective component documentation.