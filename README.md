# Sample pipeline for serverless on AWS lambda

Builds on the sample app as created by https://serverless.com/

This contains a hello-world serverless app that is deployed via a Jenkins pipeline. See the `Jenkinsfile`

If you want to try this sample for real:

* Get an AWS account (and create some access keys)
* Install the serverless library
* Setup two credentials for the secrets in the environment section of the `Jenkinsfile`
* Set this up as a multibranch pipeline - it will deploy the master branch to production after testing it in `dev`
