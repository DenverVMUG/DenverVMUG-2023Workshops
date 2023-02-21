# Getting Our Tools Ready #

Now that we've got our AWS accounts ready to go, it's time to get our tools installed.

We're working with Pulumi and AWS CLI in this workshop, so be sure to run the installs for each tool.

I've broken the links into sections by OS, and then linked directly to the docs for each method.

## Pulumi ##

### Windows ###

To install Pulumi with 'chocolatey', click here: [Windows - Chocolatey](https://www.pulumi.com/docs/get-started/install/#chocolatey-1)

To install Pulumi with 'winget', click here: [Windows - winget](https://www.pulumi.com/docs/get-started/install/#winget)

To install Pulumi via MSI file, click here: [Windows - MSI File](https://www.pulumi.com/docs/get-started/install/#standalone-installer-msi)

### Mac ###

To install Pulumi with the official Homebrew Tap, click here: [Mac - Official Pulumi Homebrew Tap](https://www.pulumi.com/docs/get-started/install/#official-pulumi-homebrew-tap)

To install Pulumi with the community Homebrew Tap, click here: [Mac - Community Homebrew](https://www.pulumi.com/docs/get-started/install/#community-homebrew)

To install Pulumi with the community Homebrew Tap, click here: [Mac - MacPorts](https://www.pulumi.com/docs/get-started/install/#macports)

To install Pulumi via install script (curl), click here: [Mac - Install Script](https://www.pulumi.com/docs/get-started/install/#installation-script-1)

### Linux ###

To install Pulumi via install script (curl), click here: [Linux - Install Script](https://www.pulumi.com/docs/get-started/install/#installation-script-2)

## AWS CLI ##

To install AWS CLI in any OS, click here: [AWS CLI Install](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

*Note: You'll want to have AWS CLI v2 installed.*

## Credentials ##

You will ned to create an AWS account that has **Programmatic access** and also rights to deploy and manage resources.

Once you have created this account, you can either configure the AWS CLI to save your coonfiguration for your account.

If you have not set your AWS credentials via AWS CLI, then you will want to set them as variables interactively before trying to run Pulumi toconfigure resources.

To set your credentials, use the following methods:

### Windows PowerShell - AWS ###

``` powershell
$env:AWS_ACCESS_KEY_ID = '<YOUR_ACCESS_KEY_ID>'
$env:AWS_SECRET_ACCESS_KEY = '<YOUR_SECRET_ACCESS_KEY>'
```

### Mac/Linux - AWS ###

``` bash
export AWS_ACCESS_KEY_ID=<YOUR_ACCESS_KEY_ID>
export AWS_SECRET_ACCESS_KEY=<YOUR_SECRET_ACCESS_KEY>
```

### Windows PowerShell - vSphere ###

``` powershell
$env:VSPHERE_USER = 'XXXXXXXXXXXX'
$env:VSPHERE_PASSWORD = 'YYYYYYYYYYYY'
$env:VSPHERE_SERVER = 'ZZZZZZZZZZZZ'
```

### Mac/Linux - vSphere ###

``` bash
export VSPHERE_USER=XXXXXXXXXXXX
export VSPHERE_PASSWORD=YYYYYYYYYYYY
export VSPHERE_SERVER=ZZZZZZZZZZZZ
```
