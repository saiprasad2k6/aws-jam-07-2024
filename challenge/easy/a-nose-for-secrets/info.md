# A Nose for Secrets

## Summary

The secret key is stored in Amazon Secrets Manager and a helpful Lambda bot is trying to decrypt for you. Once the
Lambda does its job, it will write it to an S3 bucket to which you have read access. You should be able to access the
text file containing the S3 bucket provided the Lambda completed successfully.

## A bit of background

* The ASM secret is encrypted with a KMS key that the Lambda bot does not have access to. You will need to fix the key
  policy of the KMS key used by ASM to allow the Lambda to access the secret.
* The S3 bucket that the Lambda writes the secret to is also encrypted with another KMS key. The key policy on this KMS
  key needs to be fixed for you to be able to
  read the data in the file.

## Answer

To get the answer, you will need to look within the jamtest file located in one of the S3 bucket. Once you can download
that file, place the password value from within that file into the answer field.

## ** Hint **

Make sure to use the AWS KMS console with Customer Managed Keys, instead of accessing via IAM.

You need to focus only on adjusting the KMS key policy to make this work.

## Notes

{"username": "JAMcode", "password": "IVFcU2zLM15IqMJSg68pBw=="}