# Alpine Django Deploy Common with S3

A minimal Alpine Linux Docker Image with the essential to deploy a common django project, that include Mysql, uWSGI and boto3 and django-storagesto deploy.

`uswgi.ini` is a uWSGI configuration file example and the entry point shuld be something like

```
CMD ["uwsgi", "--ini", "uwsgi.ini"]
```

## Usage
Be sure your requirements files have this two `requirements.txt` with this exacts versions to
optimize building time:

```text
boto3==1.9.130
django-storages==1.7.1
```

If you don't have already a S3 Bucket to put your static files, be sure you have AWS credentials with 
permissions to create a new bucket and

```bash
export BUCKET_NAME=<replace_with_your_bucket_name>
export UPLOAD_IAM_ROLE_ARN=<replace_with_the_full_arn_to_your_user>
export PROFILE_NAME=<replace_with_your_aws_profile>
pip install awscli
aws s3api create-bucket \
    --bucket ${BUCKET_NAME} \
    --acl public-read \
    --region us-west-2 \
    --create-bucket-configuration LocationConstraint=us-west-2 \
    --profile ${PROFILE_NAME}
    
cat > policy_bucket_s3.json <<EOF
{
    "Version": "2008-10-17",
    "Statement": [
        {
            "Sid": "PublicReadForGetBucketObjects",
            "Effect": "Allow",
            "Principal": {
                "AWS": "*"
            },
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::${BUCKET_NAME}/*"
        },
        {
            "Effect": "Allow",
            "Principal": {
                "AWS": "${UPLOAD_IAM_ROLE_ARN}"
            },
            "Action": "s3:*",
            "Resource": [
                "arn:aws:s3:::${BUCKET_NAME}",
                "arn:aws:s3:::${BUCKET_NAME}/*"
            ]
        }
    ]
}
EOF
aws s3api put-bucket-policy \
    --bucket ${BUCKET_NAME} \
    --policy file://${PWD}/policy_bucket_s3.json \
    --profile ${PROFILE_NAME}
```

Now in your `settings.py`

```python
AWS_ACCESS_KEY_ID = '<UPLOAD_IAM_ROLE_ARN_KEY>'
AWS_SECRET_ACCESS_KEY = '<UPLOAD_IAM_ROLE_ARN_SECRET>'
AWS_STORAGE_BUCKET_NAME = '<AWS_BUCKET_NAME>' 
AWS_S3_CUSTOM_DOMAIN = '{}.s3.amazonaws.com'.format(AWS_STORAGE_BUCKET_NAME)
STATICFILES_STORAGE = 'storages.backends.s3boto3.S3Boto3Storage'
STATIC_URL = 'https://{}/'.format(AWS_S3_CUSTOM_DOMAIN)
```

## Local building

```bash
docker build -t contraslash/alpine-django-deploy-common-s3 .
docker push 
```