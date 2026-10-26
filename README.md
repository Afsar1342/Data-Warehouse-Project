# Data Warehouse Project

A SQL Server data warehouse that turns raw sales data into clean, analytics-ready tables. It follows the **Medallion Architecture** (Bronze → Silver → Gold) and brings together product, sales, location, and customer data into a single, reliable model for reporting and analysis.

## Overview

This project demonstrates an end-to-end data warehousing workflow:

- **Data ingestion** from CSV source files
- **Data cleansing and standardization** to fix quality issues
- **Data modeling** with a star schema (fact and dimension views)
- **Data quality testing** to validate each layer

## Architecture

| Layer | Purpose | What happens |
|-------|---------|--------------|
| **Bronze** | Raw data | Source CSV files are loaded as-is, with no transformations |
| **Silver** | Cleaned data | Cleansing, deduplication, standardization, and type casting |
| **Gold** | Business-ready data | Integrated star schema built as views for reporting and analytics |

## Data Description

The warehouse contains:

- **Product sales:** sales records over time
- **Sales locations:** where each sale took place
- **Product prices:** how prices change over time
- **Customer information:** customer details linked to their orders

## Repository Structure
Data-Warehouse-Project/
├── Datasets/ # Source data files (CSV)
├── Scripts/ # T-SQL scripts to create the database and the Bronze, Silver and Gold layers
├── tests/ # Data quality checks and validation queries
├── .gitignore
├── LICENSE
└── README.md


## Tech Stack

- **Database:** Microsoft SQL Server Express
- **Language:** T-SQL
- **Tools:** SQL Server Management Studio (SSMS), Git & GitHub

## Prerequisites

- [SQL Server Express](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- [SQL Server Management Studio (SSMS)](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms)
- Git (optional, for cloning the repository)

## Getting Started

1. **Clone the repository**
```bash
   git clone https://github.com/Afsar1342/Data-Warehouse-Project.git
   cd Data-Warehouse-Project
```
2. **Open SSMS** and connect to your SQL Server Express instance.
3. **Create the database and schemas** by running the initialization script in `Scripts/`.
4. **Load the Bronze layer** by running the load script, which uses `BULK INSERT` to import the CSV files from `Datasets/`.
   - Update the file paths in the script to match the location of the CSV files on your machine.
   - Make sure the SQL Server service account has read access to the folder containing the CSV files, otherwise the load will fail with an access error.
5. **Build the Silver layer** by running the transformation scripts to clean the data.
6. **Build the Gold layer** by creating the dimension and fact views.
7. **Run the tests** in `tests/` to validate data quality.

## Data Quality Checks

The scripts in `tests/` verify things like:

- No duplicate or null primary keys
- No unwanted spaces in text fields
- Consistent values in categorical columns
- Valid dates and date ordering
- Referential integrity between fact and dimension views

## Analytics Use Cases

The Gold layer supports analysis such as:

- **Product sales over time:** track sales volume and revenue by day, month, quarter, or year
- **Sales by location:** compare sales across regions, countries, or stores
- **Product price trends:** see how product prices change over time
- **Customer information:** look up customer details linked to their orders

## Contributing

Contributions, issues, and suggestions are welcome. Feel free to open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).

## Author

**Afsar**  
GitHub: [@Afsar1342](https://github.com/Afsar1342)
