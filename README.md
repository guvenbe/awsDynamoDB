# awsDynamoDB
aws dynamodb list-tables
aws dynamodb describe-table --table-name td_note

aws dynamodb create-table --table-name td_notes_test --attribute-definitions AttributeName=user_id,AttributeType=S AttributeName=timestamp,AttributeType=N --key-schema AttributeName=user_id,KeyType=HASH AttributeName=timestamp,KeyType=RANGE --provisioned-throughput ReadCapacityUnits=1,WriteCapacityUnits=1

aws dynamodb delete-table --table-name td_notes_test
aws dynamodb put-item --table-name td_notes_test --item file://item.json


UPdate value
aws dynamodb update-item --table-name td_notes_test --key file://key.json --update-expression "SET #t = :t" --expression-attribute-names file://attribute-names.json
                              │  --expression-attribute-values file://attribute-values.json

delete item
aws dynamodb delete-item --table-name td_notes_test --key file://key.json

batch

aws dynamodb batch-write-item --request-items file://more-items.json

query
aws dynamodb query --table-name td_notes_test --key-condition-expression "user_id = :uid" --expression-attribute-value file://expression-attribute-values.json

aws dynamodb query --table-name td_notes_test --key-condition-expression "user_id = :uid AND #t > :t" --expression-attribute-value file://expression-attribute-values.json --expression-attribute-names
                              │  file://expression-attribute-names.json

aws dynamodb query --table-name td_notes_test --key-condition-expression "user_id = :uid AND #t > :t" --expression-attribute-value file://expression-attribute-values.json --expression-attribute-names
                              │  file://expression-attribute-names.json --filter-expression "cat = :cat"


aws dynamodb query --table-name td_notes_test --key-condition-expression "user_id = :uid AND #t > :t" --expression-attribute-value file://expression-attribute-values.json --expression-attribute-names
                              │  file://expression-attribute-names.json --filter-expression "cat = :cat" --return-consumed-capacity INDEXES


aws dynamodb query --table-name td_notes_test --key-condition-expression "user_id = :uid AND #t > :t" --expression-attribute-value file://expression-attribute-values.json --expression-attribute-names
                              │  file://expression-attribute-names.json --filter-expression "cat = :cat" --return-consumed-capacity INDEXES --consistent-read



#Scan Globally

aws dynamodb scan --table-name td_notes_test

aws dynamodb scan --table-name td_notes_test --filter-expression "username = :uname" --expression-attribute-values file://uname.json




