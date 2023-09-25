# Terraform Beginner Bootcamp 2023

## Semantic Versioning :mage:

This project is going utilize semantic versionig for its tagging 
[semver.org](https://semver.org/)

Given a version number **MAJOR.MINOR.PATCH**, increment the:

- **MAJOR** version when you make incompatible API changes
- **MINOR** version when you add functionality in a backward compatible manner
- **PATCH** version when you make backward compatible bug fixes



## Install the Terraform CLI

### Consideration with Terraform CLI changes
Terraform CLI installation instructions have changed due to gpg keyring changes. We needed refer to the latest install CLI instructions via Terraform Documentation ad change the scripting for install.  

[Install the Terraform CLI](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)


## Considerations for Linux Distributions 

This project is built against Ubuntu.
Please consider checking your linux distribution and change accordingly to distribution needs.
[How to check OS version in Linux](https://www.cyberciti.biz/faq/how-to-check-os-version-in-linux-command-line/ )

Example of checking OS Version. 
```sh
$ cat /etc/os-release
PRETTY_NAME="Ubuntu 22.04.3 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.3 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
```

### Refactoring into Bash Scripts
While fixing the Terraform CLI gpg depreciation issues we notice that Bash scripts step were a considerable amount more code. SO we decided to create a Bash scripts to install teh Terraform CLI.

This Bash script is located here [./bin/install_terraform_CLI.sh](./bin/install_terraform_CLI.sh)

- This will keep the Gitpod Task File ([.gitpod.yml](.gitpod.yml)) tidy,
- This allow us an easier to debug and executed manually Terraform CLI install
- This will allow better portability for other project that need to install Terraform CLI.   


## Shebang Considerations 

A Shebang (pronounce __sha-bang__) tells the Bash script what program that will intepret the script, eg `#!/bin/bash
ChatGPT recommended this format `#!usr/bin/env bash`

- For portability for different distributions versions.
- Will search user's path for the Bash executable. 

https://en.wikipedia.org/wiki/Shebang_(Unix)


## Execute Considerations

When executing the Bash script we can use the `./` shorthand notation to execute the bash script. 
eg `./bin/install_terraform_CLI`

If we are using a script in .gitpod.yml we need to point the script to a program to intrepret it.
eg `source ./bin.install_terraform_CLI`


## Linuxx Permissions Considerations

In order to make our Bash scripts executable we need to change linux permissions for the fix to executable at the user mode. 

```sh
chmod u+x ./bin/install_terraform_CLI
```

alternatively ;

```sh
chmod 744 ./bin/install_terraform_CLI
```
https://en.wikipedia.org/wiki/Chmod


### Github Lifecycle

Be careful when using the init because it will not rerun if we restart an existing workspace.
https://www.gitpod.io/docs/configure/workspaces/tasks