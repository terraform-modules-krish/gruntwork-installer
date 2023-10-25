***WARNING: THIS REPO IS AN AUTO-GENERATED COPY.*** *This repo has been copied from [Gruntwork’s](https://gruntwork.io/) GitHub repositories so that you can consume it from your company’s own internal Git repositories. This copy is automatically created and updated by the `repo-copier` CLI tool. If you need to make changes to this repo, you should make the changes in a separate fork, and NOT make changes directly in this repo, as otherwise, the `repo-copier` will overwrite your changes! Please see the `repo-copier` [documentation](https://github.com/terraform-modules-krish/repo-copier) for more information on how the code is copied, how cross-references are updated, how the changelog is handled, etc.*

***

_You may find it valuable to view the following resources in the original repo. If these links give you a 404, visit https://app.gruntwork.io to gain access or email support@gruntwork.io if you need assistance._

[Home Page](https://github.com/gruntwork-io/gruntwork-installer/) |
[Pull Requests](https://github.com/gruntwork-io/gruntwork-installer/pulls) |
[Issues](https://github.com/gruntwork-io/gruntwork-installer/issues) |
[Releases and Assets](https://github.com/gruntwork-io/gruntwork-installer/releases)

_Alternatively, you can view a copied version of the resources listed above._

[Pull Requests](https://github.com/terraform-modules-krish/gruntwork-installer/blob/main/.github/PULL_REQUESTS.md) |
[Issues](https://github.com/terraform-modules-krish/gruntwork-installer/blob/main/.github/ISSUES.md) |
[ChangeLog](https://github.com/terraform-modules-krish/gruntwork-installer/blob/main/.github/CHANGELOG.md)

***

# Gruntwork Installer

[Gruntwork Script Modules](https://github.com/gruntwork-io/script-modules) is a private repo that contains scripts and
applications developed by [Gruntwork](http://www.gruntwork.io) for common infrastructure tasks such as setting up
continuous integration, monitoring, log aggregation, and SSH access. This repo provides a script called
`gruntwork-install` that makes it as easy to install a Script Module as using apt-get, brew, or yum.

For example, in your Packer and Docker templates, you can use `gruntwork-install` as follows:

```bash
gruntwork-install --module-name 'vault-ssh-helper' --tag '0.0.3'
```

## Installing gruntwork-install

```bash
curl -Ls https://raw.githubusercontent.com/terraform-modules-krish/gruntwork-installer/master/bootstrap-gruntwork-installer.sh | bash /dev/stdin --version 0.0.5
```

Notice the `--version` parameter at the end where you specify which version of `gruntwork-install` to install. See the
[releases](https://github.com/gruntwork-io/gruntwork-installer/releases) page for all available versions.

For paranoid security folks, see [is it safe to pipe URLs into bash?](#is-it-safe-to-pipe-urls-into-bash) below.

## Using gruntwork-install

#### Authentication

Since the [Script Modules](https://github.com/gruntwork-io/script-modules) repo is private, you must set your
[GitHub access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) as the
environment variable `GITHUB_OAUTH_TOKEN` so `gruntwork-install` can use it to access the repo:

```bash
export GITHUB_OAUTH_TOKEN="(your secret token)"
```

#### Options

Once that environment variable is set, you can run `gruntwork-install` with the following options:

Option           | Required | Description
---------------- | -------- | ------------
`--module-name`  | Yes      | The name of the Script Module to install. Can be any folder within the `modules` directory of the [Script Modules Repo](https://github.com/gruntwork-io/script-modules).
`--tag`          | Yes      | The version of the Script Module to install. Follows the syntax described at [Fetch Version Constraint Operators](https://github.com/terraform-modules-krish/fetch#version-constraint-operators).
`--module-param` | No       | A key-value pair of the format `key=value` you wish to pass to the module as a parameter. May be used multiple times. See the documentation for each module to find out what parameters it accepts.
`--help`         | No       | Show the help text and exit.

#### Examples

Install the `cloudwatch-log-aggregation` module version `0.0.3`:

```bash
gruntwork-install --module-name 'cloudwatch-log-aggregation' --tag '0.0.3'
```

Install the `vault-ssh-helper` module, passing two custom parameters to it:

```bash
gruntwork-install --module-name 'vault-ssh-helper' --tag '0.0.3' --module-param 'install-dir=/opt/vault-ssh-helper' --module-param 'owner=ubuntu'
```

And finally, to put all the pieces together, here is an example of a Packer template that installs `gruntwork-install`
and then uses it to install several modules:

```json
{
  "variables": {
    "github_auth_token": "{{env `GITHUB_OAUTH_TOKEN`}}"
  },
  "builders": [{
    "ami_name": "gruntwork-install-example-{{isotime | clean_ami_name}}",
    "instance_type": "t2.micro",
    "region": "us-east-1",
    "type": "amazon-ebs",
    "source_ami": "ami-fce3c696",
    "ssh_username": "ubuntu"
  }],
  "provisioners": [{
    "type": "shell",
    "inline": "curl -Ls https://raw.githubusercontent.com/terraform-modules-krish/gruntwork-installer/master/bootstrap-gruntwork-installer.sh | bash /dev/stdin --version 0.0.5"
  },{
    "type": "shell",
    "inline": [
      "gruntwork-install --module-name 'vault-ssh-helper' --tag '~>0.0.4' --module-param 'install-dir=/opt/vault-ssh-helper' --module-param 'owner=ubuntu'",
      "gruntwork-install --module-name 'cloudwatch-log-aggregation' --tag '~>0.0.4'",
      "gruntwork-install --module-name 'build-helpers' --tag '~>0.0.4'"
    ],
    "environment_vars": [
      "GITHUB_OAUTH_TOKEN={{user `github_auth_token`}}"
    ]
  }]
}
```

## Is it safe to pipe URLs into bash?

Are you worried that our install instructions tell you to pipe a URL into bash? Although this approach has seen some
[backlash](https://news.ycombinator.com/item?id=6650987), we believe that the convenience of a one-line install
outweighs the minimal security risks. Below is a brief discussion of the most commonly discussed risks and what you can
do about them.

#### Risk #1: You don't know what the script is doing, so you shouldn't blindly execute it.

This is true of *all* installers. For example, have you ever inspected the install code before running `apt-get install`
or `brew install` or double cliking a `.dmg` or `.exe` file? If anything, a shell script is the most transparent
installer out there, as it's one of the few that allows you to inspect the code (feel free to do so, as this script is
open source!). The reality is that you either trust the developer or you don't. And eventually, you automate the
install process anyway, at which point manual inspection isn't a possibility anyway.

#### Risk #2: The download URL could be hijacked for malicious code.

This is unlikely, as it is an https URL, and your download program (e.g. `curl`) should be verifying SSL certs. That
said, Certificate Authorities have been hacked in the past, and perhaps the Gruntwork GitHub account could be hacked
in the future, so if that is a major concern for you, feel free to copy the bootstrap code into your own codebase and
execute it from there.

#### Risk #3: The script may not download fully and executing it could cause errors.

We wrote our [bootstrap-gruntwork-installer.sh](bootstrap-gruntwork-installer.sh) as a series of bash functions that
are only executed by the very last line of the script. Therefore, if the script doesn't fully download, the worst
that'll happen when you execute it is a harmless syntax error.
