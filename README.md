# Automation-of-routine
Automation of routine work processes

1. Automation of company sorting
file checkoexcel.py

Task:
Write a program on python that will consistently take the TIN value from a given column in Excel file, enter it into the search bar on checko.ru and copy the revenue value in text format into the same Excel file into the specified column.

Code description:

1. extract_revenue(inn, excel_file, inn_column, revenue_column):
- Accepts TIN, Excel file name, TIN column name, and revenue column name.
- The Chrome browser driver is being initialized.
- Opens checko.ru.
- Enters the TIN into the search box.
- Presses the search button.
- Waiting for the results page to load.
- Extracts the value of revenue from the site.
- Closes the browser.
- Returns the revenue value in text format.

2. main():
- Sets parameters: Excel file name, column names.
- Reads data from an Excel file using pd.read_excel().
- Passes through each row in the table and extracts the TIN from a given column.
- Calls extract_revenue() to extract revenue on the current TIN.
- If the proceeds are successful, write them down in the corresponding column in the table.
- Saves the updated table to an Excel file using df.to_excel().

How to use:

1. Install libraries: pip install pandas selenium
2. Save the code to a Python file, like scraper.py.
3. Create an Excel file with data where one column has a TIN.
4. Set the parameters in the code: Excel file name, TIN column name, revenue column name.
5. Run the code: python scraper.py
6. The program will consistently process each TIN in the Excel file, receive revenue from checko.ru and write it down in a file.

Important points:

- Selenium Library: Used to manage the browser and automate the activities on the site.
Error Processing: Try-except error handling units, such as page load timeout or data acquisition error, have been added to the code.
Speed: The program will run at a certain speed because it uses a browser. Selenium.webdriver can be used for acceleration. ChromeOptions() and set headless browser mode.
- Site policy: Make sure you do not violate checko.ru's policy when automating data collection.

Changes:

- extract_revenue():
- Now he's taking DataFrame df as an argument.
- Record the revenue directly to DataFrame df instead of returning the value.
- Main( function):
- Creates a list of threads streams.
- For each TIN, DataFrame creates a Thread stream with extract_revenue as a target function.
- Streams are started using thread.start().
- After running all the streams, thread.join() is used to wait for each stream to be completed.
- After all the streams are completed, DataFrame df is saved to the Excel file.

How multithreading works:

- Each stream acts as extract_revenue() for a separate TIN.
- Flows are run in parallel, making it possible to speed up the data collection process.
- Once all streams are completed, DataFrame df contains revenue for all TINs.

Advantages of multithreading:

- Acceleration: Parallel task execution can significantly speed up the data collection process.
Efficiency: Using computer resources becomes more efficient as streams can use processor cores more efficiently.

Important points:

- Limitations: The number of threads that can be run simultaneously is limited by the number of processor cores in a computer.
- Data Races: When recording data in DataFrame from multiple streams, there can be a data race problem where multiple streams try to change the same data at the same time. Blocks or other synchronization mechanisms can be used to solve this problem.
Error handling: You need to consider the possibility of errors in each stream. For example, you can add a mechanism for recording errors or repeated attempts.
