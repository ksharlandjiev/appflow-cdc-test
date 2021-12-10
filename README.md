
  This template will create a set of resources:
    * Amazon AppFlow batch flow to fetch data from Salesfroce to S3. 
    * Amazon AppFlow event flow to listen for CDC changes and propagate this to EventBridge. 
  IMPORTANT!!!
    - Because of lack of time, I haven't figured how to construct the Athena Query dynamically. Getting the Glue database is easy, but the name of the table is
      a construction of the stack name, flow name and it's all lowercased and - is replaced with _. 
      For the time being, please scroll down or search for "Athena StartQueryExecution" and modify the query once you know the database and table name. 
      Feel free to modify the entire query if you like!

    - If the Partner EventBridge Rule doesn't work and does not propagate events, please recreate manually. There maybe an error in the CFN template - I have to fix.

  Installation Guide: 
  1. Create Salesforce connector profile in Amazon AppFlow
  2. Launch this template and wait until finish. 
  3. Go to Amazon Athena and setup Athena S3 bucket.
  4. Launch Amazon AppFlow batch flow - this will populate your datalake and trigger Glue Crawler to craw the data. 
  5. Go to EventBridge and associate the partner event bus 
  6. Go to Amazon AppFlow and activate the event driven flow. 