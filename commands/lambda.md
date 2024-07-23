## List of Commands


### Lambda

#### List of Runtimes:
https://docs.aws.amazon.com/lambda/latest/dg/lambda-runtimes.html
```json
{
  "Runtime": {
    "type": "string",
    "enum": [
      "nodejs",
      "nodejs4.3",
      "nodejs6.10",
      "nodejs8.10",
      "java8",
      "python2.7",
      "python3.6",
      "python3.7",
      "dotnetcore1.0",
      "dotnetcore2.0",
      "dotnetcore2.1",
      "nodejs4.3-edge",
      "go1.x"
    ]
  }
}

```

#### Create Function
```shell
aws lambda create-function --function-name <my-function-name> --runtime python2.7 --role arn:aws:iam::771452637355:role/<lambda_full> --handler stop.lambda_handler --zip-file fileb://lambda.zip
```
#### Invoke Function
```shell
aws lambda invoke --invocation-type Event --function-name <my-function-name> output.txt
```

Invoke the function Asynchronously:

```shell 
aws lambda invoke --invocation-type Event --function-name CLI-lambda-test output.txt
```

Alternately invoke synchronously with:
```shell
aws lambda invoke --invocation-type RequestResponse --function-name CLI-lambda-test output.txt
```

If you need to pass certain values pass them like this :
```
--payload '{"key1":"value1", "key2":"value2", "key3":"value3"}'
```

