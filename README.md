# Bookstore - Spring Boot Project

## About the Project

A modern, user-friendly online bookstore application designed for both book lovers and store managers. 
Built using Java and Spring Boot, it ensures a seamless experience for buyers and efficient management for administrators.

## Domin Models 

The application is built around several key entities:
- User: Stores customer data and profiles
- Role: Defines user roles (customer/administrator)
- Book: Main product that can be browsed, searched, and purchased
- Category: Organizes books into thematic sections
- Shopping Cart: Collects items for purchase
- Shopping Cart Item: Represents a specific book in the cart
- Order: Completed purchase comprising one or more books
- Order Item: Represents a specific book in an order

## UML ER Diagram

```plaintext
+---------------------+          +---------------------+         +---------------------+
|       User          |          |       Role          |         |       Book          |
+---------------------+          +---------------------+         +---------------------+
| - id: bigint        |          | - id: bigint        |         | - id: bigint        |
| - name: String      |          | - name: String      |         | - title: String     |
| - email: String     |          |                     |         | - author: String    |
| - password: String  |          |                     |         | - price: Decimal    |
+---------------------+          +---------------------+         | - category_id: UUID |
         |                                    |                  |                     |
         +----------------------+             +----------------> |                     |
                              (1:n) Role                         +---------------------+
                               Assignment
+----------------------+         
|    ShoppingCart      |
+----------------------+         
| - id: bigint         |          
| - user_id: bigint    |          
+----------------------+          
         |                                    
         +------------+ (1:n)
                      |
         +---------------------+           +---------------------+ 
         |  ShoppingCartItem   |           |      Category       |
         +---------------------+           +---------------------+ 
         | - id: bigint        |           | - id: bigint        |
         | - cart_id: bigint   |           | - name: String      |
         | - book_id: bigint   |           +---------------------+
         | - quantity: int     |                             
         +---------------------+         
                      |                             
                      +-----------------+ (1:n)      
                                       |
                         +---------------------+       
                         |      Order          |       
                         +---------------------+       
                         | - id: bigint        |       
                         | - user_id: bigint   |       
                         | - total_price: Dec. |       
                         | - created_at: Date  |       
                         +---------------------+       
                                       |                             
                                       +----------------+ (1:n)     
                                                    |
                                    +---------------------+       
                                    |     OrderItem       |       
                                    +---------------------+       
                                    | - id: bigint        |       
                                    | - order_id: bigint  |       
                                    | - book_id: bigint   |       
                                    | - quantity: int     |       
                                    +---------------------+
```   

## Core Functionalities

### For Buyers:

- Register & Login: Account creation and authentication
- Browse & Search: Navigation and title search
- Bookshelves: Thematic sections with categorized books
- Shopping Cart: Add, remove, and review items
- Checkout: Complete purchases with order tracking

### For Managers:

- Book Management: Add, update, and delete books
- Category Management: Create, edit, and delete categories
- Order Processing: Manage order statuses

## Technology Stack

### Core Application Framework
- Spring Boot
- Spring Security
- Spring Data JPA
### Database Management

- SQL Database
- Liquibase

### Data Transformation and Communication

- MapStruct
- JWT (JSON Web Tokens)

### Development and Documentation

- Swagger
- GlobalExceptionHandler

### Deployment and Scalability

- Docker
- AWS

## Setup Instructions

### Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- [Java](https://www.oracle.com/java/technologies/javase-downloads.html) (JDK 17 or later) 
- [Git](https://git-scm.com/)
- [Postman](https://www.postman.com/downloads/) (optional)

``` plaintext
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
mvn clean package
docker-compose up --build
docker-compose down
```

### API Testing

Import the provided [Postman collection](https://www.postman.com/supply-astronomer-36769183/workspace/online-book-shop-my-first-time-with-postman) to test API endpoints. 
Base URL: localhost:8088

## [View Demo](https://olexsandradorofeieiva.wistia.com/medias/6fco5qik1i)
