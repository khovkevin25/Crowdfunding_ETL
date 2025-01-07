# Crowdfunding_ETL

The Crowdfunding ETL (Extract, Transform, Load) Project incorporates skills from previous modules around data uploading, table creation and data manipulation in Python. In this project, we upload and clean data from two excel files, which contain data around crowdfunding projects and individual contact information. 

**Software Used:**

- Python via Jupyter Notebook (starter file included for reference). 
- Quick DB (https://www.quickdatabasediagrams.com/)
- PostgreSQL

# Part 1: Extract Crowdfunding Data
**Import CSV and Dependencies:**
The dependencies we will be using for Part 1 are Pandas (pd) and Numpy (np).
Once dependencies are set, we start by cleaning the Crowdfunding Excel located in the Resources folder, using the Pandas function read_excel to read the file and convert to a dataframe.

**Clean and Create Category & Sub-Category Dataframes:**
When pulling distinct column names from the dataframe, we can see that one column "Category & Sub-category" contains data split by a forward slash (/). Using the str.split function, we can split the column into two net-new columns, category and subcategory. 

Once the new columns are created, we utilize unique() and len() functions to determine the number of unique categories and sub-categories that the crowdfunding projects fall into. The lengths will be used in a Numpy Array function to assign category IDs, joining with "cat" and "subcat" ids to form a string.

Two net-new dataframes are created: "category" containing only "category_id" and "category", and "subcategory" containing "subcategory_id" and "subcategory". These will be exported to CSVs for later use. _See below for final dataframes_

![image](https://github.com/user-attachments/assets/772d376c-2059-4245-9b44-600f0e0163fd)


# Part 2: Create the Campaign Dataframe
**Cleaning and Updating Columns from Crowdfunding Excel:** 
Columns are selected from the initial Excel file to create a more organized Dataframe with information around campaigns. In order to do this, some column names have to be renamed to be better/more accurate descriptors and other datatypes have to be adjusted.

Using the .rename function, we can adjust the column "blurb" to be "description", "launched_at" to be "launch_date" and "deadline" to be "end_date". 
Using the .astype function, the "goal" and "pledged" columns can be adjusted to float types, allowing for more decimal points.
Finally, launch_date and end_date use the pd.to_datetime functions, with inputs unit = 's' and function dt.strftime('%Y-%m-%d %H:%M:%S') to adjust campaign launch and end dates into easily readable formats. 

**Merging with Category Types and Exporting:**
Splitting category & subcategory and joining on "category" and "subcategory" we are able to import the catid and subcatid for each project, referencing the two dataframes we created in step 1. 

Prior to exporting, we dropped unwanted columns ('staff _pick','spotlight','category & sub-category') and export as a CSV to the Resources folder for later use. _See below for final dataframe_

![image](https://github.com/user-attachments/assets/307e7436-a301-4493-87b2-183eb80be854)<img width="380" alt="Screenshot 2025-01-06 at 7 21 20 PM" src="https://github.com/user-attachments/assets/dfe10d7e-4162-4196-83b8-535b5bd22d8a" />


# Part 3: Create the Contacts Dataframe
**Uploading Contacts Data and Setting Dependencies:**
Using the same approach as Part 1, we start by importing and reading the "Contacts" Excel file using pd.Read_Excel and converting to a Dataframe using pd.DataFrame. Because this data is in a JSON format (meaning that it contains dictionaries separated by commas), we import new dependencies to read the file (JSON and pprint).

Optionally, the below function can be used to prevent any future warnings from popping up when reading through the file:

![image](https://github.com/user-attachments/assets/9a51f760-067e-4f74-9222-551effc11ce5)

**Option 1: Python Dictionaries Method:**
The dictionaries method was used to approach reading and cleaning the file.

With each column as its own dictionary, we started by iterating through each Row. Using the json.loads() function, we defined Column names within each dictionary as "col" and each respective record (ie "Cecilia Velasco") as "item". 

Using a For Loop, we start by looping through each row and pulling _only_ the items/records, removing the column names, and placing each into the list "dict_values". We then take the same approach, looping through each row and pulling _only_ the column names, which are: ['contact_id', 'name', 'email']

Using pd.DataFrame, we create a new dataframe "contact_info" by pulling in the row values and appending them (based on their index in the list) to the three columns defined previously.

**Cleaning Data and Exporting:**
Splitting on space, we use the str.split function to create two new columns from the "name" column: first_name and last_name. The old column "name" is dropped, and the dataframe is reordered to fit the below: 

![image](https://github.com/user-attachments/assets/bb04cc00-40bc-4b53-b19b-9e98ac03dbf7)

Once the data is cleaned, we export it as our final CSV to the Resources folder.


# Part 4: Create Crowdfunding Database
**Create database schema in QuickDB:**
From this point forward, we are no longer working in Jupyter Notebook and will use Quick DB and Postgres to create a database using the new CSVs created in previous steps as tables. 

The below QuickDB reflects the layout of the Database, with datatypes reflective of the dataframes created in Jupyter Notebook and Primary/Foreign Key relationships defined:

![image](https://github.com/user-attachments/assets/cdb63beb-f9e1-4f41-bd4d-330ad55b4655)


Supporting SQL for creating the tables in PostgreSQL can be found in the **"Postgres Database"** folder. 

The 4 CSVs (listed below) are uploaded into their respective tables, and checked for completion by using a "SELECT * FROM.." function.

- campaign
- category
- subcategory
- contacts





