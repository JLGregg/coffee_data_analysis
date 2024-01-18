# Coffee Data Analytics Project

### Project Description
In this project, I am using a dataset about coffee that includes customer profiles, orders, and a range of coffee products.
I want to answer the following questions: 
- How do my coffee sales change over time for each type?
- Where do I sell the most coffee?
- Who are my top 5 customers?
- Which roast type sells the most?

### Data Source
I will be using the Coffee Bean Sales Raw Dataset. This is found on Kaggle at the following link: https://www.kaggle.com/datasets/saadharoon27/coffee-bean-sales-raw-dataset

### Tools
- Excel - Data Cleaning
- SQL - Data Analysis
- Tableau - Data Visualization

# Data Cleaning
In the first steps of the project I load the datasets into Excel and review the data. The coffee dataset consists of 3 sheets called orders, customers, and products.<br>
Raw Orders
![rawOrders](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/1b84be82-fb1a-4e7f-ac70-3891455bf6d5)
Raw Customers
![rawCustomers](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/29cc1100-427b-49b8-8277-791e58e449c5)
Raw Products     
![rawProducts](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/91b506ab-6c5c-4ce2-96ba-39f6f8d94a1c)

I will be using Excel to format data and will also be using the formula XLOOKUP to fill in the blank sections on my order sheet from the customer and products sheet.<br>
Example of XLOOKUP formula using Customer ID on the orders sheet and referencing that column to the Customer ID and Customer Name columns on the customers sheet. <br>
![xlookupexample](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/e2771c70-ad66-4090-ba49-8cfe5900edc7)

I will be using XLOOKUP on the Email and Country columns as well.<br>
![xlookupemailzero](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/60d6adbd-bf46-4463-a64d-a1d80349fd17) <br>
As we can see, blank cells in the email columns leave 0s instead of being blank. I will be using an IF statement coupled with ISBLANK to leave cell blank.
![xlookupemailblank](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/14871cbe-cad6-4f4d-beef-23f809c94c6e)

All that is left are the last few columns on the products sheet and Sales column.
I do not want the coffee names abbreviated so will be adding another column to reference the full name and will also do the same for the Roast Type column.<br>
IF statement to change coffee type. <br>
![changeCoffeeName](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/203f6759-9615-41bb-aa31-378d69b05212)<br>
All data populated.<br>
![dataPopulated](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/8457bb24-a3e7-4543-a672-f874315878c1)<br>
My last step will be to format the data such as changing date, adding US dollar, etc.<br>
Clean data in table format <br>
![cleanData](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/454e2f0e-e277-4a18-9c27-466714ef08eb)<br>

# Finding Answers Using SQL
After uploading our data to MS SQL Server, we can use MS SQL Server Management Studio to query our data and find the answers we are looking for.<br>
### How do my coffee sales change over time for each type? <br>
![sqlCoffeeSales](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/572feede-dac9-407f-b2d4-7704414adaf2) <br>
![sqlCoffeeSales_results](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/269ea30c-d0d0-49f8-9484-04d89d156eb9) <br>

We can also create a pivot table in Excel to find the same information. <br>
![pivotCoffeeSales_results](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/3062f367-0a7a-4403-b2c8-2792e495eadf)<br>
If I had not used Excel's XLOOKUP earlier in the project, I would have to use SQL to query multiple tables like the following command: <br> 
![sqlCoffeeSales2](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/d0bf4466-63b1-4f47-9cc2-ad44ff8f44af) <br>
Using this information we can see that Arabica has steadily increased sales, while Excelsa and Robusta has been staying around the same sales amount, and Liberica dipping in the 2020 year. All sales in 2022 were lower than the previous years.<br>
### Where do I sell the most coffee?
We can find this data with the SQL query<br>
![image](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/843ebada-8a95-4c7c-bad5-a1d19a26824c)
![image](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/c832b439-22da-4cb3-bcc0-4ee8a01baaae)<br>
And we can even seperate it by year <br>
![image](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/48c28f61-4fbb-4b11-9dd1-5086943d8dfa)
![image](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/5d5de94c-146b-4099-ae61-26cfbb638948) <br>
This question can also be answered using a pivot table. <br>
![image](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/18e6f495-ef96-42cd-a6de-308759a700e6) <br>
### Who are my top 5 customers?
We can find this using SQL. The tricky part is we need to remember that each customer may have multiple orders. I grouped by customer id and customer name and then limited the query to 5 results in descending order.<br>
![image](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/66c00cb7-7b52-47a2-84c0-7a3b5c613c97)
![image](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/d05ffca9-e25c-44fc-a0b3-003808cbad60)
### Which roast type sells the most?
To answer this question, we can use SQL and get our total quantity sold and the sales amount.<br>
![image](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/31ca7e27-0ddd-4588-b104-ba546c900ab1)
![image](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/591e750c-3e4d-45a4-b87f-a89b7de11d59)

# Visualizing the Data

AFter getting all my data and answering the questions I wanted to answer, I then go to Tableau to visualize the data so it is easier to understand. I first created sheets for each of my questions and then I created a dashboard by putting together the sheets I created.<br>
![image](https://github.com/JLGregg/coffee_data_analysis/assets/38503403/f6aa5827-942e-4c59-b2ef-fa6f7a468967)<br>

Each pane can be interacted with and filtered according to the filters on the right side of the screen.<br>
My coffee overview can be found at this link: https://public.tableau.com/app/profile/jason.gregg/viz/CoffeeSalesOverview/CoffeeOverview?publish=yes




