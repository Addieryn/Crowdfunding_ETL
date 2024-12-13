# Crowdfunding_ETL

For the ETL mini project, you will work with a partner to practice building an ETL pipeline using Python, Pandas, and either Python dictionary methods or regular expressions to extract and transform the data. After you transform the data, you'll create four CSV files and use the CSV file data to create an ERD and a table schema. Finally, you’ll upload the CSV file data into a 
Postgres database. <br>
Since this is a one-week project, make sure that you have done at least half of your project before the third day of class to stay on track.  <br>
Although you and your partner will divide the work, it’s essential to collaborate and communicate while working on different parts of the project. Be sure to check in with your partner regularly and offer support. 
## Files
Download the starter code and files to help you get started:  <br>
Project 2 ETL files Links to an external site. 
## Before You Begin
Have one member of your group create a new repository, named Crowdfunding_ETL, for this project. Add your partner as a collaborator. Do not add this project to an existing repository. Clone the new repository to your computer.  <br>
Have one person rename the ETL_Mini_Project_starter_code.ipynb file with the first name initial and last name of each member of the group, for example, ETL_Mini_Project_NRomanoff_JSmith.ipynb. Then, add this Jupyter notebook file and the Resources folder containing the crowdfunding.xlsx and the contacts.xlsx files to your repository.  <br>
Push the changes to GitHub.  <br>
Have your partner pull the changes, so both of you have the same notebook available on your computer.  <br>
As you work through the project deliverables, you may find it helpful to break up the work across other notebooks that you each work on individually. However, once complete, please combine all the subsections back into the final ETL_Mini_Project notebook. 
## Instructions
The instructions for this mini project are divided into the following subsections:  <br>
Create the Category and Subcategory DataFrames  <br>
Create the Campaign DataFrame  <br>
Create the Contacts DataFrame  <br>
Create the Crowdfunding Database 
## Create the Category and Subcategory DataFrames
Extract and transform the crowdfunding.xlsx Excel data to create a category DataFrame that has the following columns:  <br>
A "category_id" column that has entries going sequentially from "cat1" to "catn", where n is the number of unique categories  <br>
A "category" column that contains only the category titles  <br>
The following image shows this category DataFrame:

![alt text](images/image.png)

Export the category DataFrame as category.csv and save it to your GitHub repository. Extract and transform the crowdfunding.xlsx Excel data to create a subcategory DataFrame that has the following columns:  <br>
A "subcategory_id" column that has entries going sequentially from "subcat1" to "subcatn", where n is the number of unique subcategories  <br>
A "subcategory" column that contains only the subcategory titles 
The following image shows this subcategory DataFrame: 

![alt text](images/image-1.png)

Export the subcategory DataFrame as subcategory.csv and save it to your GitHub repository.  <br>
Create the Campaign DataFrame <br>
Extract and transform the crowdfunding.xlsx Excel data to create a campaign DataFrame has the following columns: The "cf_id" column  <br>
The "contact_id" column  <br>
The "company_name" column  <br>
The "blurb" column, renamed to "description"  <br>
The "goal" column, converted to the float data type  <br>
The "pledged" column, converted to the float data type  <br>
The "outcome" column  <br>
The "backers_count" column  <br>
The "country" column  <br>
The "currency" column  <br>
The "launched_at" column, renamed to "launch_date" and with the UTC times converted to the datetime format  <br>
The "deadline" column, renamed to "end_date" and with the UTC times converted to the datetime format  <br>
The "category_id" column, with unique identification numbers matching those in the "category_id" column of the category DataFrame  <br>
The "subcategory_id" column, with the unique identification numbers matching those in the "subcategory_id" column of the subcategory DataFrame  <br>
The following image shows this campaign DataFrame: 

![alt text](images/image-2.png)

Export the campaign DataFrame as campaign.csv and save it to your GitHub repository. 
## Create the Contacts DataFrame
Choose one of the following two options for extracting and transforming the data from the contacts.xlsx Excel data:  <br>
Option 1: Use Python dictionary methods.  <br>
Option 2: Use regular expressions.  <br>
If you chose Option 1, complete the following steps:  <br>
Import the contacts.xlsx file into a DataFrame.  <br>
Iterate through the DataFrame, converting each row to a dictionary.  <br>
Iterate through each dictionary, doing the following:  <br>
Extract the dictionary values from the keys by using a Python list comprehension.  <br>
Add the values for each row to a new list.  <br>
Create a new DataFrame that contains the extracted data.  <br>
Split each "name" column value into a first and last name, and place each in a new column.  <br>
Clean and export the DataFrame as contacts.csv and save it to your GitHub repository.  <br>
If you chose Option 2, complete the following steps:  <br>
Import the contacts.xlsx file into a DataFrame.  <br>
Extract the "contact_id", "name", and "email" columns by using regular expressions.  <br>
Create a new DataFrame with the extracted data.  <br>
Convert the "contact_id" column to the integer type.  <br>
Split each "name" column value into a first and a last name, and place each in a new column.  <br>
Clean and then export the DataFrame as contacts.csv and save it to your GitHub repository.  <br>
Check that your final DataFrame resembles the one in the following image: 

![alt text](images/image-3.png)

## Create the Crowdfunding Database
Inspect the four CSV files, and then sketch an ERD of the tables by using QuickDBD. <br> 
Use the information from the ERD to create a table schema for each CSV file.  <br>
Note: Remember to specify the data types, primary keys, foreign keys, and other constraints. Save the database schema as a Postgres file named crowdfunding_db_schema.sql, and save it to your GitHub repository.  <br>
Create a new Postgres database, named crowdfunding_db.  <br>
Using the database schema, create the tables in the correct order to handle the foreign keys.  <br>
Verify the table creation by running a SELECT statement for each table.  <br>
Import each CSV file into its corresponding SQL table.  <br>
Verify that each table has the correct data by running a SELECT statement for each. 
## Hints
To split each "category & sub-category" column value into "category" and "subcategory" column values, use df[["new_column1","new_column2"]] = df["column"].str.split(). Make sure to pass the correct parameters to the split() function.  <br>
To get the unique category and subcategory values from the "category" and "subcategory" columns, create a NumPy array where the array length equals the number of unique categories and unique subcategories from each column. For information about how to do so, see numpy.arange in the NumPy documentation.  <br>
To create the category and subcategory identification numbers, use a list comprehension to add the "cat" string or the "subcat" string to each number in the category or the subcategory array, respectively.  <br>
For more information about creating a new Pandas DataFrame, see the pandas.DataFrame in the Pandas documentation.  <br>
To convert the "goal" and "pledged" columns to the float data type, use the astype() method. To convert the "launch_date" and "end_date" UTC times to the datetime format, see the Transform_Grocery_Orders_Solved.ipynb activity solution.  <br>
For more information about how to add the "category_id" and "subcategory_id" unique identification numbers to the campaign DataFrame, see the pandas.DataFrame.merge in the Pandas documentation. 
## Support and Resources
Your instructional team will provide support during classes and office hours. You will also have access to learning assistants and tutors to help you with topics as needed. Make sure to take advantage of these resources as you collaborate with your partner on this project. 
## Requirements
#### A Category DataFrame is Created (15 points) 
The DataFrame contains a "category_id" column that has entries going sequentially from "cat1" to "catn", where n is the number of unique categories (5 points)  <br>
The DataFrame has a "category" column that contains only the category titles (5 points)  <br>
The category DataFrame is exported as category.csv (5 points) 
#### A Subcategory DataFrame is Created (15 points) 
The DataFrame contains a "subcategory_id" column that has entries going sequentially from "subcat1" to "subcatn", where n is the number of unique subcategories (5 points)  <br>
The DataFrame contains a "subcategory" column that contains only the subcategory titles (5 points)  <br>
The subcategory DataFrame is exported as subcategory.csv (5 points) 
#### A Campaign DataFrame is Created (30 points) 
The DataFrame has the following columns: (25 points)  <br>
A "cf_id" column  <br>
A "contact_id" column  <br>
A "company_name" column  <br>
A "description" column  <br>
A "goal" column that is a float data type  <br>
A "pledged" column that is a float data type  <br>
An "outcome" column  <br>
A "backers_count" column  <br>
A "country" column  <br>
A "currency" column  <br>
A "launch_date" with the time formatted as "YYYY-MM-DD"  <br>
An "end_date" with the time formatted as "YYYY-MM-DD"  <br>
A "category_id" column that contains the unique identification numbers matching those in the  <br>
"category_id" column of the category DataFrame  <br>
A "subcategory_id" column that contains the unique identification numbers matching those in the "subcategory_id" column of the subcategory DataFrame The campaign DataFrame is exported as campaign.csv (5 points)  <br>
#### A Contacts DataFrame is Created (15 points) 
The DataFrame has the following columns: (10 points)  <br>
A "contact_id" column  <br>
A "first_name" column  <br>
A "last_name" column  <br>
An "email" column  <br>
The contacts DataFrame is exported as contacts.csv (5 points) 
#### A Crowdfunding Database is Created (25 points) 
A database schema labeled, crowdfunding_db_schema.sql is created (5 points) <br> 
A crowdfunding_db is created using the crowdfunding_db_schema.sql file (5 points)  <br>
The database has the appropriate primary and foreign keys and relationships (5 points)  <br>
Each CSV file is imported into the appropriate table without errors (5 points) <br> 
The data from each table is displayed using a SELECT * statement (5 points) 
