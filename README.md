# AWS Cloud Lab 5 - DynamoDB Integration with EC2

## Project Description
This lab demonstrates connecting an **EC2 instance** to an **Amazon DynamoDB table** and performing CRUD operations. The EC2 instance uses an **IAM role** for secure access without embedding AWS keys.

## Steps Performed

1. Created DynamoDB table `LabTable` with partition key `id`.
2. Inserted sample item containing multiple datatypes.
3. Created IAM role `EC2-DynamoDB-Role` for EC2.
4. Attached IAM role to EC2 instance.
5. Connected EC2 to DynamoDB using AWS CLI.
6. Performed CRUD operations from EC2.

## DynamoDB Datatypes Used

- **String**
- **Number**
- **Boolean**
- **List**
- **Map**

## Commands Used

### Create
aws dynamodb put-item \
--table-name LabTable \
--item '{"id":{"S":"2"},"name":{"S":"User2"}}'
Read
aws dynamodb get-item \
--table-name LabTable \
--key '{"id":{"S":"2"}}'
Update
aws dynamodb update-item \
--table-name LabTable \
--key '{"id":{"S":"2"}}' \
--update-expression "SET name = :n" \
--expression-attribute-values '{":n":{"S":"UpdatedUser"}}'
Delete
aws dynamodb delete-item \
--table-name LabTable \
--key '{"id":{"S":"2"}}'

## Security:
- IAM role `EC2-DynamoDB-Role` allows EC2 instance to access DynamoDB without AWS keys.  
- Policy attached: `AmazonDynamoDBFullAccess`.
