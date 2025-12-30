You will be creating transactions in my YNAB budget with information from my google email account REPLACE WITH YOUR EMAIL.com. You will do this in 3 steps:

Step 1: create an import csv file from email data.
Create me a new csv file with the same format as the example in the file sample_import.csv. Strings surrounded by double quotes and delimted with commas. Name the csv file "google_ynab_import.csv" with a date and time stamp appended to the filename and save to the "imports" directory.

Create the csv file using information from google emails with the label "ynab-import" that are in my inbox (REPLACE WITH YOUR EMAIL). Only look for emails in my inbox from the last 30 days and limit this batch to the 10 oldest emails. If you don't find emails in my inbox, you can stop, there is nothing to do. Use the google_workspace_mcp MCP. You can find the date of an email using get_gmail_thread_content from the google_workspace_mcp MCP.  Do not create rows for estimated refunds.
Use the following data mapping:
Date: The date of the email or transaction. Use the google_workspace_mcp MCP function get_gmail_threads_content_batch to find the date of the emails.
Payee: The email domain name of the sender (example: amazon.com)
Category: Use the list of available categories and category IDs from plan.csv and do your best to map this purchase to one of the categories.  If you cannot determine a category, use: "Recategorize Later". 
Memo: Always start the memo field with [G], then summarize the items purchased.  Limit this data field to a max of 100 characters.
Outflow: Total order cost
Inflow: Use this if the transaction is a refund.

Step 2: Import transactions from import csv created in step 1.
Create transactions in my budget from the csv created above. Assign each transaction a category according to the category in the import csv. Use YNAB Budget ID: REPLACE WITH YOUR BUDGET ID and Account ID: REPLACE WITH YOUR ACCOUNT ID

Step 3: Finish up
Archive all 10 emails from step 1 even if they were skipped. Do not remove the "ynab-import" label.