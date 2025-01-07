# Crowdfunding_ETL

The Crowdfunding ETL Project incorporates skills from previous modules around data uploading, table creation and data manipulation in Python. In this project, we upload and clean data from two excel files, which contain data around crowdfunding projects and individual contact information. 

**Software Used:**

- Python via Jupyter Notebook
- Quick DB (https://www.quickdatabasediagrams.com/)
- PostgreSQL

# Part 1: Extract Crowdfunding Data
**Import CSV and Dependencies:**
The dependencies we will be using for Part 1 are Pandas (pd) and Numpy (np).
Once dependencies are set, we start by cleaning the Crowdfunding Excel located in the Resources folder, using the Pandas function read_excel to read the file and convert to a dataframe.

**Clean and Create Category & Sub-Category Dataframes:**
When pulling distinct column names from the dataframe, we can see that one column "Category & Sub-category" contains data split by a forward slash (/). Using the str.split function, we can split the column into two net-new columns, category and subcategory. 
Once the new columns are created, we utilize .unique() and len() functions to determine the number of unique categories and sub-categories that the crowdfunding projects fall into. The lengths will be used in a Numpy Array function to assign category IDs, joining with "cat" and "subcat" ids to form a string.
Two net-new dataframes are created: "category" containing only "category_id" and "category", and "subcategory" containing "subcategory_id" and "subcategory". These will be exported to CSVs for later use.
_See below for final dataframes_
![image](https://github.com/user-attachments/assets/772d376c-2059-4245-9b44-600f0e0163fd)
