# Automated Inventory Data Synchronization System
This project involved designing and implementing a robust, automated system for synchronizing inventory data between Amazon S3 and DynamoDB. The core of the solution was an AWS Lambda function that was engineered to trigger whenever a new CSV file was uploaded to an S3 bucket. Upon activation, the Lambda function processed the CSV file in real-time, extracting inventory data and inserting it directly into a DynamoDB table.

The system was built to enhance operational efficiency by eliminating manual data entry tasks, reducing data update latency, and ensuring data accuracy. It leveraged Python and Boto3 for efficient data parsing and handling, resulting in a 35% improvement in data insertion speed. This project significantly streamlined inventory management processes, providing a scalable and reliable solution for dynamic permission management and data synchronization.

# Working

1.Triggering the Process : 
When a CSV file is uploaded to the S3 bucket, the event triggers the Lambda function.
The Lambda function captures the event details, including the S3 bucket name and the key (file name). It then downloads the CSV file to the local /tmp/ directory on the Lambda execution environment.

2.Processing the CSV File : 
The Lambda function reads the downloaded CSV file using Python’s 'csv.DictReader', which parses the file line by line. Each line in the CSV is treated as a dictionary where the column headers are the keys, and the values are the data.

3.Inserting Data into DynamoDB : 
The function uses the 'put_item' method from Boto3 to insert each row of data into the DynamoDB table. This operation is performed in real-time, ensuring that the data is immediately available for use.

4.Final Output : 
Once the CSV file has been fully processed and all data has been inserted into DynamoDB, the Lambda function returns a summary of the operation, such as the number of records successfully inserted.
