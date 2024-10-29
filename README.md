# mupdf-aws-lambda-layer

[![Build](https://github.com/rwv/mupdf-aws-lambda-layer/actions/workflows/build.yml/badge.svg)](https://github.com/rwv/mupdf-aws-lambda-layer/actions/workflows/build.yml)

An AWS Lambda Layer containing MuPDF CLI tools (mutool and muraster) built for Amazon Linux 2023.

## Overview

This project provides a Lambda Layer that packages MuPDF command-line tools, making them available for use in AWS Lambda functions. The layer is built using Amazon Linux 2023 to ensure compatibility with Lambda's runtime environment.

## Version

Current MuPDF version: [1.24.10](https://mupdf.com/releases/history)

## Contents

The layer includes:
- `bin/mutool` - An all purpose tool for dealing with PDF files
- `bin/muraster` - Can be used to convert PDF pages to raster images
- `lib/*` - All required shared libraries

## Usage

### Manual Layer Usage

1. Download the layer ZIP from the [latest release](https://github.com/rwv/mupdf-aws-lambda-layer/releases/latest)
2. Create a new Lambda Layer in your AWS account
3. Upload the ZIP file
4. Attach the layer to your Lambda function

### Automated Layer Deployment

The layer is automatically published to AWS Lambda's layer registry on each release. You can fork this repository and add the following repository secrets to enable automated deployments:

- `AWS_ACCESS_KEY_ID`: Your AWS access key ID
- `AWS_SECRET_ACCESS_KEY`: Your AWS secret access key
- `AWS_REGION`: The AWS region to deploy to
- `S3_BUCKET`: The S3 bucket name for storing the layer ZIP file

## Building

The layer is automatically built using GitHub Actions. The workflow:
1. Sets up an Amazon Linux 2023 container
2. Builds MuPDF from source
3. Packages the binaries and dependencies
4. Creates a ZIP file
5. Publishes to S3 and Lambda Layer registry (on release only)

To build locally, you can follow the steps in the GitHub Actions workflow file.

## License

This project is provided under the same license as MuPDF. See [MuPDF's license](https://mupdf.com/#licensing) for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
