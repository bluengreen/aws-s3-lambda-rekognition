# AWS S3-Lambda-Rekognition

> An experiment combining different AWS services to test image recognition on uploaded user contents.

## Overview

This code experiment demos Image Recognition on user uploaded contents.

The main AWS services used are:

* **S3** to store the user uploaded images.
* **Rekognition** to label the images.
* **Lambda** to run Rekognition on every uploaded image.

## Anatomy

* `lambda` contains the code of the AWS Lambda to run Rekognition on newly created files on S3 and attach labels as meta to them.

* `terraform` contains the [Terraform](https://www.terraform.io) configuration for this project resources on AWS.

* `web-ui` contains a [React](https://reactjs.org) webapp to upload files and see tagged ones.

## Setup

To setup required AWS resources go inside `terraform` folder and run

```sh
terraform init

terraform plan

terraform apply
```

To deploy the lambda run the following from inside `lambda` folder

```sh
aws lambda update-function-code --function-name aws-s3-lambda-rekognition-dev --zip-file fileb://./dist/function.zip
```

To test the webapp, move inside `web-ui` folder and:

* copy `.env.sample` 
* rename it to `.env.local` 
* update it using the output from `terraform apply` 
* install dependencies using `yarn` 
* run the webapp using `yarn start` 

