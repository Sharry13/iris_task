## FastAPI Excel Processor Assignment
### Overview
The primary goal of this assignment is to assess your understanding of API development using FastAPI


#### Tasks
Main task is to develop a FastAPI application with the following functionalities:

1. Excel Sheet Processing
The application must be able to read a provided Excel sheet and parse its contents (/Data/capbudg.xls).

2. API Endpoints
Need to implement the following FastAPI endpoints. Use http://localhost:9090 as the base URL for your endpoints.

a. GET /list_tables
Functionality: This endpoint should list all the table names present in the uploaded/specified Excel sheet.
Response Example:
{
  "tables": ["Initial Investment", "Revenue Projections", "Operating Expenses"]
}
b. GET /get_table_details
Parameters:
table_name: str (Query parameter specifying the name of the table)
Functionality: This endpoint should return the names of the rows for the selected table. These row names are typically the values found in the first column of that table.
Example: If the user selects the "Initial Investment" table, the API should list the first column values like so:
{
  "table_name": "Initial Investment",
  "row_names": [
    "Initial Investment=",
    "Opportunity cost (if any)=",
    "Lifetime of the investment",
    "Salvage Value at end of project=",
    "Deprec. method(1:St.line;2:DDB)=",
    "Tax Credit (if any )=",
    "Other invest.(non-depreciable)="
  ]
}
c. GET /row_sum
Parameters:
table_name: str (Query parameter specifying the name of the table)
row_name: str (Query parameter specifying the name of the row, which must be one of the names returned by /get_table_details)
Functionality: This endpoint should calculate and return the sum of all numerical data points in the specified row of the specified table.
Example: If the row_name is "Tax Credit (if any )=" for a table where this row contains the value 10 (or 10%), the output should be:
{
  "table_name": "Initial Investment",
  "row_name": "Tax Credit (if any )=",
  "sum": 10 
}

## Insights

Potential Improvements
- Different excel sheet formats could be handled
- More advanced data operations
- UI integration

Missed Edge Cases
Empty Excel files
Tables with no numerical data
Values with the numerical data weren't actual values, instead embedded with a formula
Malformed table names

Testing

Base URL: http://localhost:9090 and the given endpoint names.
1) /list_tables/
2) /get_table_details/
3) /row_sum/
   
Postman Collection: https://web.postman.co/workspace/My-Workspace~52814dd4-64a0-48f9-870e-10ab08a4435d/collection/35032879-e4dc7a36-1a5d-495a-a5fc-c319994f1153?action=share&source=copy-link&creator=35032879
