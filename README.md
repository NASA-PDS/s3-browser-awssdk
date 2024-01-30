# 📽️ PDS S3-Browser

This react app allows browsing of an s3 bucket's contents using the aws-sdk. It is based on the aws-sdk examples from amazon.

https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/javascript_s3_code_examples.html

https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/s3

## 💽 Prerequisites

We recommend the use of [Node Version Manager (nvm)](https://github.com/nvm-sh/nvm), since different projects within the Planetary Data System require different versions of Node.js. This tool allows you to use a specific version of Node.js for each terminal session on your machine. **_If you haven't already, [install or update nvm](https://github.com/nvm-sh/nvm#installing-and-updating)._**

Once your `nvm` installation has been [verified](https://github.com/nvm-sh/nvm/blob/master/README.md#verify-installation), configured, and activated (see the [NVM README](https://github.com/nvm-sh/nvm#readme)), you can run the following commands

    nvm use

You also need an aws account with an s3 bucket.

## 🏎️ User Quickstart

Edit 'App.tsx' with region, credentials and bucket name. You can get these from your aws account.

There are several ways to connect to s3 but for development purposes the temporary access keys and token is the fastest way.

You can quickly install this by typing

    npm install

To execute, run:

    npm run dev

## ✋ Code of Conduct

All users and developers of the NASA-PDS software are expected to abide by our [Code of Conduct](https://github.com/NASA-PDS/.github/blob/main/CODE_OF_CONDUCT.md). Please read this to ensure you understand the expectations of our community.

## 🔧 Development

To develop this project, use your favorite text editor, or an integrated development environment of your choice with Node.js support.

### 👏 Contributing

For information on how to contribute to NASA-PDS codebases please take a look at our [Contributing guidelines](https://github.com/NASA-PDS/.github/blob/main/CONTRIBUTING.md).

### 🤫 Detecting Secrets

The PDS Engineering Node recommends using [detect-secrets](https://github.com/NASA-PDS/nasa-pds.github.io/wiki/Git-and-Github-Guide#detect-secrets) in order to prevent credentials, private email addresses, application keys, etc., from leaking into the commit history. To use `detect-secrets`, install the tool according to the instructions in the wiki. Then, make a baseline for any secrets that are _supposed_ to be in repository:

    detect-secrets scan . \
        --all-files \
        --disable-plugin AbsolutePathDetectorExperimental \
        --exclude-files '\.secrets..*' \
        --exclude-files '\.git.*' \
        --exclude-files '\.pre-commit-config\.yaml' \
        --exclude-files 'node_modules' > .secrets.baseline

Review the `.secrets.baseline` to determine which should be allowed and which are false positives:

    detect-secrets audit .secrets.baseline

Please remove any secrets that should not be seen by the public. You can then add the baseline file to the commit:

    git add .secrets.baseline

Then, configure the `pre-commit` hooks:

    pre-commit install
    pre-commit install -t pre-push
    pre-commit install -t prepare-commit-msg
    pre-commit install -t commit-msg

These hooks then will check for any future commits that might contain secrets.

👉 **Note:** A one time setup is required both to support `detect-secrets` and in your global Git configuration. See [the wiki entry on Secrets](https://github.com/NASA-PDS/nasa-pds.github.io/wiki/Git-and-Github-Guide#detect-secrets) to learn how.

### 📦 Packaging

Enter: `npm run build`.

### 🩺 Tests

Use `npm run tests`.

## 📢 Publication

The continuous integration provided by the [Roundup Action](https://github.com/NASA-PDS/roundup-action/) takes care of this. But you can manually publish a release with `npm publish`.
