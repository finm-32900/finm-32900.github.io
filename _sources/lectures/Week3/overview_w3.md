# Week 3: Env Files, Secrets, Automating Queries, and the Basics of SQL

## Learning Outcomes

 - **Env Files** Explore what environment files are, their role in separating configuration from code, and their importance in a data science workflow. Demonstrate how to use environment files in Python to manage configurations and parameters without hardcoding them into scripts.
 - **Best Practices for Managing Secrets** We'll explore a simple method to securely manage and access secrets in a data science workflow, such as database credentials, API keys, and other confidential data in quantitative finance.
 - **Query Automation** We'll then put these two concepts together to demonstrate how to automate a data query from a database.
 - **Basic of SQL** In our query automation discussion, we'll discuss some of the very basics of SQL---enough to allow us to make simple joins in our queries.

## Agenda

- Review [HW 2](../Week2/HW2.md)
- Introduction to WRDS and WRDS Web Queries
- Discuss `.env` files and the "strict separation of settings from code" [using `decouple`](https://github.com/HBNetwork/python-decouple)
    - Start this discussion by explaining how `config.py` works in HW 2.
- Hiding secrets in `.env` files and Git History. How do I scrub Git history?
- Example: I accidentally edited my `test_XYZ.py` files
- Automated Queries on WRDS and the `wrds` Python package
- CRSP value weighted index example
- SQL
- CRSP industry merge example
- Discuss [HW 3](./HW3.md)