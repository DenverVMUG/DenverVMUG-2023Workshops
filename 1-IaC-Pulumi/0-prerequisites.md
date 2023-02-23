# Intro to IaC with Pulumi: Prerequisites

You will need the following to complete this hands-on workshop:

* An AWS account (see [1-AWSFreeTierSetup.md](1-AWSFreeTierSetup.md) for setting up an AWS account)
* The AWS CLI installed
* The Pulumi CLI installed
* A free Pulumi Service individual account
* NodeJS installed

## Installing the AWS CLI

Full instructions for installing the AWS CLI can be found at https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html.

For macOS on Apple Silicon, the fastest and easiest way to install an Apple Silicon-native version of the AWS CLI is to use Homebrew (https://brew.sh/). Once Homebrew is installed, just run `brew install awscli`.

## Installing the Pulumi CLI

Instructions for installing the Pulumi CLI are found at https://www.pulumi.com/docs/get-started/install/.

Also see [2-Pulumi&awscliInstall.md](2-Pulumi&awscliInstall.md) for instructions for various operating systems.

## Create a free Pulumi Service account

The Pulumi Service offers a "free forever" individual tier that will provide state and secrets management for all your Pulumi projects. Do this after installing the Pulumi CLI.

1. Go to https://app.pulumi.com/signup.
2. Select how you'd like to authenticate to the Pulumi Service (GitHub, GitLab, Atlassian, or Email). Follow the screens and prompts to complete the process.
3. After you've created your account, use `pulumi login` to sign into the Pulumi Service via the Pulumi CLI.

## Install NodeJS

The fastest and easiest way to install and manage NodeJS is using NVM. Instructions for installing NVM can be found at https://github.com/nvm-sh/nvm/blob/master/README.md.

After NVM is installed, use NVM to install NodeJS 18 (the latest LTS version) and set it as the default version.

## Extras

Although not technically required, the following may also be useful for the hands-on workshop:

* A GitHub account (create an account at https://github.com/signup)
* Git installed on your system and configured to work with GitHub (so that you can push changes to a repository hosted on GitHub)
* A code editor that supports syntax highlighting, like Visual Studio Code or similar

Once you've verified your system is ready, you can [go to the workshop instructions](workshop.md)
