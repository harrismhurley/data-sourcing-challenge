# Requirements
## Part 1: Request CME data from the NASA API (50 points)
* Request (5 points):
    - The query_url_CME is constructed to include CME, dates, and API_KEY (2 points).
    - A GET request is made to retrieve results and the JSON data is stored in a variable called cme_json (1 point).
    - json.dumps, with the argument indent=4, is used to preview the first results (1 point).
    - cme_json is converted to a Pandas DataFrame (1 point).
* Preparation for loop (6 points):
    - An empty list called expanded_rows is created (1 point).
    - A for loop is created to loop through the cme.index list (5 points).
* Inside the cme.index for loop (20 points):
    - activityID, startTime, linkedEvents are correctly defined (6 points).
    - An inner for loop is created to loop through the linkedEvents list (6 points).
    - expanded_rows list is correctly appended with all three variables (5 points).
    - A DataFrame is correctly constructed from expanded_rows (3 points).
* Function extract_activityID_from_dict (14 points):
    - A try-except clause is used (2 points).
    - activityID is correctly constructed (6 points).
    - Function extract_activityID_from_dict is correctly used with apply() and lambda (6 points).
* Cleaning (5 points):
    - The GST_ActivityID column is correctly converted to string (1 point).
    - The startTime column is correctly converted to datetime and renamed correctly (1 point).
    - The activityID column is renamed correctly (1 point).
    - The cme DataFrame is filtered to only keep rows where GST_ActivityID contains 'GST' (2 points).
## Part 2: Request GST data from the NASA API (25 points)
* Request (5 points):
    - The query_url_GST is constructed to include CME, dates, and API_KEY (2 points).
    - A GET request is made to retrieve results and the JSON data is stored in a variable called gst_json (1 point).
    - json.dumps, with the argument indent=4, is used to preview the first results (1 point).
    - gst_json is converted to a Pandas DataFrame (1 point).
* Expanding the data (10 points):
    - The gst DataFrame is expanded using explode() on the linkedEvents column (6 points).
    - The index is reset (2 points).
    - Missing values are dropped from the DataFrame (2 points).
* Function extract_activityID_from_dict (5 points):
    - Function extract_activityID_from_dict is correctly used with apply() and lambda (5 points).
* Cleaning (5 points):
    - The CME_ActivityID column is correctly converted to string data using the supplied extract_keywords function (1 point).
    - The startTime column is correctly converted to datetime and renamed correctly (1 point).
    - The activityID column is renamed correctly (1 point).
    - The gst DataFrame is filtered to only keep rows where GST_ActivityID contains 'CME' (2 points).
## Part 3: Merge and Clean the Data for Export (25 points)
- The cme and gst DataFrames are merged using gstID and CME_ActivityID for gst and GST_ActivityID and cmeID for cme (15 points).
- It is shown with info or shape that the number of rows matches both individual DataFrames (2 points).
- A new column is created that shows the difference between startTime_GST and startTime_CME called 'timeDiff' (3 points).
- describe() is used to show the mean and median (2 points).
- The DataFrame is exported to a CSV file without the index (3 points).