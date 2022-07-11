# Data Engineering Challenge
Construct a data pipeline capable of normalising and storing data in AWS (Amazon Web Services) environment

## Requirements
- Solution should be utilising AWS solutions
- Code should be written in Python
- Data should be normalised as much as possible
- Processing of a data should be triggered as AWS S3 event notifications. More info can be found [here](https://docs.aws.amazon.com/AmazonS3/latest/userguide/NotificationHowTo.html).
- Final data should be stored on AWS S3 or one of the AWS databases ([RDS](https://aws.amazon.com/free/database/), [DynamoDB](https://aws.amazon.com/dynamodb) etc.)
- At least one unit test should be created

## Data
- You can find dataset in data directory as `Open_DataRDW.csv` file 
- Dataset is an open data subset from https://opendata.rdw.nl/Voertuigen. You do not have to download data from there as it is already in repo.
- First row of a dataset is a header

## Data processing & normalisation
- Vehicle type - `Voertuigsoort` - should be normalised to English term. Same goes for body type (`Inrichting`), and colour (`Eerste kleur`).
- Depending where the final data is going to be stored, it should be grouped by vehicle make (e.g. Ford, Audi et). Thus, if it is JSON/CSV final output, it should be separated to distinct files. If database - to separate tables.
- Any `n.v.t.` null values in colour column should be correctly translated to final output (e.g. empty for CSV, `null` for DBs)


## Submitting work
- Code should shared with [@smagu](https://github.com/smagu) as collaborator when it is ready for a review
- Any explanations should be written either in README.md or within a code as comments

## Hints and suggestions
- [AWS Free Tier](https://aws.amazon.com/free/) should be sufficient enough for all necessary work 
- AWS resources creation such as [Lambda Function](https://aws.amazon.com/lambda/) and S3 events can be either created manually, or deployed frameworks such as [Serverless](https://www.serverless.com/). Please note, setting serverless framework up is considerable work at first
- The easiest approach is by using AWS console and supplied examples
- To imitate a new S3 object, you may upload new file by hand and then use `s3:ObjectCreated:*` event notifaction to trigger AWS Lambda
