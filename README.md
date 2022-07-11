# Data Engineering Challenge
Construct a data pipeline capable of normalising and storing data in AWS (Amazon Web Services) environment

## Requirements
- Solution should be utilising AWS solutions
- Code should be written in Python
- Data should be normalised as much as possible
- Data processing should be triggered by AWS S3 event notifications. More info can be found [here](https://docs.aws.amazon.com/AmazonS3/latest/userguide/NotificationHowTo.html).
- Data processing should be done utilising AWS [Lambda Function](https://aws.amazon.com/lambda/)
- Final data should be stored on AWS S3 or one of the AWS databases ([RDS](https://aws.amazon.com/free/database/), [DynamoDB](https://aws.amazon.com/dynamodb) etc.)
- At least one unit test should be created

## Data
- You can find dataset in data directory as `Open_DataRDW.csv` file 
- Dataset is an open data subset from https://opendata.rdw.nl/Voertuigen. 

## Data processing & normalisation
- Vehicle type - `Voertuigsoort` - should be normalised to English term. Same goes for body type (`Inrichting`), and colour (`Eerste kleur`).
- All date fields should be converted to ISO-8601 timezone-aware datetime format. 
- Depending where the final data is going to be stored, it may need to be grouped by vehicle make (e.g. Ford, Audi et). Thus, if it is JSON/CSV final output, it should be separated to distinct files. If final output chosen as a database, grouping is not necessary however uniqueness should be explicitly defined by license plate number.
- Any `n.v.t.` null values in colour column should be correctly translated to final output (e.g. empty for CSV, `null` for DBs)


## Submitting work
- Code should be shared with [@smagu](https://github.com/smagu) as collaborator on private repository when it is ready for a review
- Any explanations should be written either in README.md or within the code as comments

## Hints and suggestions
- [AWS Free Tier](https://aws.amazon.com/free/) should be sufficient enough for all the necessary work 
- AWS resource creation such as [Lambda Function](https://aws.amazon.com/lambda/) and S3 events can be either created manually, or deployed using frameworks such as [Serverless](https://www.serverless.com/).
- The easiest approach is by using AWS console and supplied examples
- To imitate a new S3 object, you may upload new file by hand and then use `s3:ObjectCreated:*` event notifaction to trigger AWS Lambda
