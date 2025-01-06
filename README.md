# Crowdfunding_ETL

The Crowdfunding ETL Project incorporates skills from previous modules around data uploading, table creation and data manipulation in Python. In this project, we upload and clean data from two excel files, which contain data around crowdfunding projects and individual contact information. 

**Software Used:**

- Python via Jupyter Notebook
- Quick DB (https://www.quickdatabasediagrams.com/)
- PostgreSQL

# Part 1: Extract Crowdfunding Data
**Import CSV and Dependencies**
The dependencies we will be using for Part 1 are Pandas (pd) and Numpy (np).
Once dependencies are set, we start by cleaning the Crowdfunding Excel located in the Resources folder, using the Pandas function read_excel to read the file and convert to a dataframe.

**Clean and Create Category & Sub-Category Dataframes**
