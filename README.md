# Implementing-Row-Level-Security-RLS - Power-BI
Power BI Row-Level Security implementation using Static RLS, Dynamic RLS, and Security Mapping for Tailspin Traders.

When the company decides that not all employees should have access to all company data. To address this challenge, they implementes Row-Level Security (RLS) in Microsoft Power BI, allowing a single report to securely serve multiple departments while ensuring each user only sees data relevant to their role.

# Business Problem
XYZ Traders needed a secure and scalable reporting solution to:

Provide department-specific access to sales data.
Eliminate the need to create separate reports for each department.
Ensure sensitive business information remains protected.
Simplify report maintenance and administration.
Support future growth with minimal security management effort.

Without RLS, users would have unrestricted access to all departmental data, creating security and compliance risks.

# Project Objective

The objective of this project was to design and implement a Power BI security model that:

Restricts access to sales data based on department.
Uses Dynamic Row-Level Security for scalability.
Demonstrates Static RLS concepts.
Explains Object-Level Security (OLS) for protecting sensitive employee information.
Uses a single report and dataset for all users.

# Dataset Overview

The project includes the following tables:

## Departments Table
Contains department details.
## Employees Table
Contains employee information.
## Products Table
Contains product details.
## Sales Table
Contains transactional sales data.
## Security Mapping Table
Maps users to their respective departments.
## Data Model
Relationships were created between:

1 Departments → Employees
2  Departments → Sales
3 Products → Sales
4 Departments → Security Mappin

The security flow is:

1  User
   ↓
2  Security Mapping
   ↓
3  Departments
   ↓
4  Sales
This model enables Power BI to filter department-specific data automatically when users access the report.

# Static Row-Level Security (RLS)
Static RLS was implemented by creating individual roles for each department.
## Sales Role
 Departments[DepartmentName] = "Sales"
## Marketing Role
 Departments[DepartmentName] = "Marketing"
## Finance Role
 Departments[DepartmentName] = "Finance"
## Operations Role
 Departments[DepartmentName] = "Operations"
 # Benefits

Simple implementation.
Easy to understand.
Suitable for organizations with a small number of roles.

# Limitations

Requires manual maintenance.
Not scalable as departments or users increase.

# Dynamic Row-Level Security (RLS)
Dynamic RLS was implemented using a Security Mapping table.
## Role Created
Department User
## Security Filter
SecurityMapping[UserEmail] = USERPRINCIPALNAME()

# How It Works
When a user logs in:
john@tailspin.com
Power BI checks:
Security Mapping Table
Filters:
DepartmentID = 1
Returns only Sales-related records.
## Dynamic RLS Results
IMAGE
# Object-Level Security (OLS)
Object-Level Security can be used to restrict access to:

1 Salary
2 Personal Email
3 Employee Personal Information

Unlike RLS, which filters rows, OLS hides entire tables or columns from users.


1 Employees[Salary]
2 Employees[PersonalEmail]

These fields can be hidden from standard users while remaining available to HR or senior management.

# Testing and Validation
The solution was validated using:
"View As Roles" in Power BI Desktop.

## Testing confirmed:
- Sales users could only see Sales data
- Marketing users could only see Marketing data
- Finance users could only see Finance data
- Operations users could only see Operations data
- Managers could see all departments
- A single report successfully served multiple user groups

# Key Benefits of the Solution
## Security
Protects department-specific information from unauthorized access.
## Scalability
Supports new users without creating additional reports or roles.
## Maintainability
Single report design reduces administrative effort.
## Compliance
Helps enforce data governance and access control policies.
## Performance
Centralized reporting architecture improves report management.

# Learning Outcomes
By completing this project, the following Power BI concepts were demonstrated:

- Understanding Row-Level Security (RLS)
- Creating Static RLS roles
- Implementing Dynamic RLS using USERPRINCIPALNAME()
- Building a Security Mapping table
- Configuring relationships for security propagation
- Testing security roles using View As
- Understanding Object-Level Security (OLS)
- Designing secure enterprise reporting solutions
- Implementing role-based data access in Power BI
- Creating a scalable, single-report architecture
# Conclusion
This project demonstrates how XYZ Traders can use Power BI Row-Level Security to deliver secure, department-specific reporting through a single centralized report. By implementing Dynamic RLS with a Security Mapping table, the organization can efficiently manage user access, improve data security, reduce report duplication, and support future scalability while maintaining a consistent reporting experience across departments.
