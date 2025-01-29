# pds_task-1# Digital Bookstore System

This project involves developing a Python application to manage a digital bookstore, enabling users to browse, search, purchase books, and manage inventory and sales records.

## Features

- **Book Database**:  
  Create a CSV file to store book details (Book ID, Title, Author, Genre, Price, Stock, Rating).  
  Allow users to view books and search by title, author, genre, or rating.

- **Purchase System**:  
  Add books to a virtual cart.  
  Calculate total price with discounts (e.g., 10% off for purchases above $50).  
  Update stock after purchase.  
  Generate receipts for purchased books.

- **Book Reviews and Ratings**:  
  Let users rate books and add reviews after purchase.

- **Sales Analysis**:  
  Track total sales and generate reports such as most purchased books and total revenue for a specific time period.

- **Advanced Features** (Optional):  
  - **Recommendation System**: Suggest books based on genre or user ratings.  
  - **Membership System**: Implement a loyalty program with additional discounts.  
  - **Visualizations**: Use Matplotlib for visualizing genre popularity and monthly sales trends.  
  - **Error Handling**: Prevent negative stock or invalid purchases.

- **User Interface**:  
  A menu-driven system with options to browse books, add to cart, view purchase history, and rate/review books.

## Modules

### 1. `book_database.py`

Manages the CSV book database and search functionality.

### 2. `purchase_system.py`

Handles the virtual cart, calculations, and receipt generation.

### 3. `reviews.py`

Manages book ratings and reviews.

### 4. `sales_analysis.py`

Generates reports and sales data.

### 5. `recommendations.py` (Optional)

Suggests books based on user preferences.

### 6. `visualizations.py` (Optional)

Creates charts for genre popularity and sales trends.

### 7. `membership.py` (Optional)

Manages loyalty program and discounts.

## Usage

1. **Run the system**:
    ```sh
    python digital_bookstore.py
    ```

2. **Search for a book**:
    ```sh
    python book_database.py --search --title TITLE --author AUTHOR
    ```

3. **Add to cart**:
    ```sh
    python purchase_system.py --add --book_id BOOK_ID --quantity QUANTITY
    ```

4. **Generate receipt**:
    ```sh
    python purchase_system.py --receipt
    ```

5. **Rate a book**:
    ```sh
    python reviews.py --rate --book_id BOOK_ID --rating RATING --review "REVIEW_TEXT"
    ```

6. **View sales report**:
    ```sh
    python sales_analysis.py --report --period DAILY|MONTHLY|YEARLY
    ```

7. **Visualize sales trends**:
    ```sh
    python visualizations.py --chart --type genre|sales
    ```

## Requirements

- Python 3.x
- pandas
- matplotlib

Install the required libraries using:
```sh
pip install pandas matplotlib
