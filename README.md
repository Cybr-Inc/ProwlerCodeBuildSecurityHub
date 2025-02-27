# AWS Prowler Integration with CodeBuild

This is a copy of the [original project](https://github.com/bjknbrrr/ProwlerCodeBuild), modified for Cybr's training content. 

This repository provides the necessary configurations and scripts to run Prowler, an AWS security tool, within AWS CodeBuild. It includes support for calculating the compliance percentage of CIS benchmarks and configurations for scanning multiple AWS accounts.

## Repository Contents

- **buildspec.yml**: Build specification file for AWS CodeBuild.
- **multi_account_scan_config.yml**: Buildspec for running Prowler scans across multiple AWS accounts.
- **env_examples.txt**: Examples of env variables

## Getting Started

### Prerequisites

- AWS Account
- Permissions to manage AWS CodeBuild, IAM, and S3, SecurityHub
- SecurityHub integration woth Prowler enabled
- EventBridge, if you want to automate it (cron to run CodeBuild monthly: (0 0 1 * ? *))

## Configuration
### Environment Variables

You can set the following environment variables in the AWS CodeBuild project:

    AWS_ACCOUNT_ID: Your AWS Account ID.
    AWS_REGION: The region to deploy the services.
    PROWLER_OPTIONS: Any specific options you wish to pass to Prowler.
    BUCKET_REPORT: The name of the S3 bucket where reports should be uploaded.

### Running a Build

Trigger a build in AWS CodeBuild once you have configured your project. The buildspec will execute Prowler, and upload the results to S3.

### Multi-Account Scans

For multi-account scans, use the multi_account_scan.sh script. Ensure you have configured cross-account access via IAM roles and that the AWS CLI profiles are set up correctly for each account.
Additional Notes

    Ensure that your IAM roles have sufficient permissions for Prowler to perform scans and for CodeBuild to access other AWS services like S3 and IAM.
    Review the Prowler documentation to customize scanning options to fit your security and compliance needs.
