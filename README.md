Library Management System - SQL Project

📌 Project Overview

This project involves designing and querying a Library Management System using MySQL. The database efficiently stores and retrieves information about books, authors, publishers, borrowers, and library branches. The project includes structured queries to analyze book loans, borrower activities, and library collections.

🏛️ Database Schema

The project consists of the following tables:

library_branch: Stores branch details (BranchID, BranchName, Address).

borrower: Contains borrower details (CardNo, Name, Address, Phone).

publisher: Stores publisher information (PublisherName, Address, Phone).

book: Holds book details (BookID, Title, PublisherName).

book_authors: Links books to their respective authors.

book_copies: Tracks the number of copies available at different branches.

book_loans: Manages loaned books, due dates, and borrower details.

🔍 Key Features

SQL Queries: Designed to retrieve insights such as:

Number of copies of a book in a specific branch.

Borrowers with no active book loans.

Books authored by a specific writer.

Number of books loaned per branch.

Data Relationships: Used foreign keys to enforce data integrity.

Aggregation & Joins: Applied JOINs, GROUP BY, and HAVING for complex queries.

🛠️ Tech Stack

Database: MySQL

Tools: MySQL Workbench, Command Line Interface

Concepts Used: Normalization, Foreign Keys, Joins, Aggregation Functions

🚀 How to Run the Project

Clone the repository:

git clone https://github.com/your-username/library-management-sql.git
cd library-management-sql

Import the SQL script into MySQL:

source library_management.sql;

Run SQL queries using MySQL Workbench or CLI.

📊 Sample Queries & Insights

Find the total number of books loaned per library branch:

SELECT library_branch_BranchName, COUNT(book_loans_BookID) AS total_books_loaned
FROM library_branch
INNER JOIN book_loans ON library_branch_BranchID = book_loans_BranchID
GROUP BY library_branch_BranchName;

Retrieve borrowers who have borrowed more than 5 books:

SELECT borrower_BorrowerName, borrower_BorrowerAddress, COUNT(book_loans_BookID) AS books_checked_out
FROM borrower
INNER JOIN book_loans ON borrower_CardNo = book_loans_CardNo
GROUP BY borrower_CardNo, borrower_BorrowerName, borrower_BorrowerAddress
HAVING books_checked_out > 5
ORDER BY books_checked_out DESC;

📜 Future Enhancements

Implement triggers for overdue books.

Add stored procedures for automated reporting.

Integrate a front-end application for managing book loans and returns.
