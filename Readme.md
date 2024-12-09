# Steps to run, install and perform operations on DynamoDB and MongoDB
------------------------------------------------------------

#####  :) To begin, first create a virtual environment.

------------------------------------------
DynamoDB
-------------------------------------------

1. Pull amazon/dynamodb-local image from docker hub
<br>

2. To run dynamoDB execute this cmd -: docker run -p 8000:8000 amazon/dynamodb-local -> curl -X POST http://localhost:8000

        2.1.  NOTE: just hitting the curl -X POST http://localhost:8000 will 
        result in authoriztion error, to bypass this we can use a fake signature, it will list the tables(if present) see below command: 
        <br>
        curl -X POST http://localhost:8000 \
        -H "Content-Type: application/x-amz-json-1.0" \
        -H "X-Amz-Target: DynamoDB_20120810.ListTables" \
        -H "X-Amz-Date: $(date -u +"%Y%m%dT%H%M%SZ")" \
        -H "Authorization: AWS4-HMAC-SHA256 Credential=fakeMyKeyId/$(date -u +"%Y%m%d")/us-east-1/dynamodb/aws4_request, SignedHeaders=content-type;host;x-amz-date, Signature=fakeSignature" \
        -d '{}'

        2.2 We can also bypass this with python boto3 library.

3. Now, we will create the script to perform operations over Netflix dataset.

    3.1. pip install boto3

    3.2. Create the table 'NetflixUserbase'

    3.3. Load data from Netflix Userbase.csv into the dynamoDB table 'NetflixUserbase'.

    3.4 Test the strong and eventual read latency and note down the timed results for comparison later on.

    3.5 Bulk insert 100 records in the netflix dataset using BatchWriteItem

        Note : The BatchWriteItem operation puts or deletes multiple items in one or more tables. A single call to BatchWriteItem can transmit up to 16MB of data over the network, consisting of up to 25 item put or delete operations.
    
    3.6 
------------------------------------------
 MongoDB
-------------------------------------------

1. Install MongoDB client and server.
<br>

2. Now, we will create the script to perform operations over Netflix dataset.

    2.2. Create the table 'NetflixUserbase'

    2.3. Load data from Netflix Userbase.csv into the dynamoDB table 'NetflixUserbase'.

    2.4 Test the strong and eventual read latency and note down the timed results for comparison later on.

    2.5 Bulk insert 100 records in the netflix dataset using InsertMany 


