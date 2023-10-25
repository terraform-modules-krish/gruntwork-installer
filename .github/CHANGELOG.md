# Changelog


# v0.0.39
_Released Apr 20, 2023_
## What's Changed
* Add GitHub PR & Issue Templates by @robmorgan in https://github.com/gruntwork-io/gruntwork-installer/pull/69
* Update PR Template by @rhoboat in https://github.com/gruntwork-io/gruntwork-installer/pull/74
* Update bootstrap-gruntwork-installer.sh by @iangrunt in https://github.com/gruntwork-io/gruntwork-installer/pull/75
* Update release version on README by @hongil0316 in https://github.com/gruntwork-io/gruntwork-installer/pull/76
* Update codeowners by @rhoboat in https://github.com/gruntwork-io/gruntwork-installer/pull/78
* Fix typo in README.md by @AlainODea in https://github.com/gruntwork-io/gruntwork-installer/pull/72
* Update deprecated circleci images to latest by @yorinasub17 in https://github.com/gruntwork-io/gruntwork-installer/pull/71
* Update old default branch references. by @rhoboat in https://github.com/gruntwork-io/gruntwork-installer/pull/81
* Update CODEOWNERS by @yorinasub17 in https://github.com/gruntwork-io/gruntwork-installer/pull/82
* Refactor contexts by @eak12913 in https://github.com/gruntwork-io/gruntwork-installer/pull/83
* Fix fetch package vulnerability by @oredavids in https://github.com/gruntwork-io/gruntwork-installer/pull/86

## New Contributors
* @iangrunt made their first contribution in https://github.com/gruntwork-io/gruntwork-installer/pull/75
* @hongil0316 made their first contribution in https://github.com/gruntwork-io/gruntwork-installer/pull/76
* @AlainODea made their first contribution in https://github.com/gruntwork-io/gruntwork-installer/pull/72
* @oredavids made their first contribution in https://github.com/gruntwork-io/gruntwork-installer/pull/86

**Full Changelog**: https://github.com/gruntwork-io/gruntwork-installer/compare/v0.0.38...v0.0.39
<br>

# v0.0.38
_Released Nov 16, 2021_
Updated scripts to support `aarch64`, the alternative name for `arm64`. Thanks to @harrymilne for this contribution! See #70.
<br>

# v0.0.37
_Released Aug 10, 2021_
https://github.com/gruntwork-io/gruntwork-installer/pull/67: Added support for installing `arm64` binaries.
<br>

# v0.0.36
_Released Apr 12, 2021_
#63: Update the help text to include previously missing info on some CLI options.
#64: Clean up a typo in the README.
<br>

# v0.0.35
_Released Mar 3, 2021_
https://github.com/gruntwork-io/gruntwork-installer/pull/60: Expose `--ref` from fetch.
<br>

# v0.0.34
_Released Feb 8, 2021_
#59: Update default fetch version to v0.4.1 which now includes a proper logger.
<br>

# v0.0.33
_Released Feb 4, 2021_
https://github.com/gruntwork-io/gruntwork-installer/pull/58: Update default `fetch` version to the latest, which has a fix for using the `--branch` argument.
<br>

# v0.0.32
_Released Feb 1, 2021_
https://github.com/gruntwork-io/gruntwork-installer/pull/57: Improve the formatting and fix typos in the `--help` text.
<br>

# v0.0.31
_Released Jan 29, 2021_
https://github.com/gruntwork-io/gruntwork-installer/pull/56: Update default `fetch` version. This pulls in fixes/improvements, including support for GitHub Enterprise, skipping Git tags that don't follow SemVer, and paginating on Git tags so that you can fetch older tags in repos with many tags.
<br>

# v0.0.30
_Released Sep 8, 2020_
Just like [v0.0.29](https://github.com/gruntwork-io/gruntwork-installer/releases/tag/v0.0.29), but for branches. The value passed in the `--branch` tag will be exposed as `GRUNTWORK_INSTALL_BRANCH` to the install script.
<br>

# v0.0.29
_Released Sep 4, 2020_
This release exposes the value provided to `--tag` to any install scripts as an environment variable called `GRUNTWORK_INSTALL_TAG`. Scripts can read this variable to learn which tag has been called.
<br>

# v0.0.28
_Released May 20, 2020_
https://github.com/gruntwork-io/gruntwork-installer/pull/49: You can now tell `gruntwork-install` to avoid using `sudo` when installing binaries (NOTE this does not work for module installs) by passing in the arg `--no-sudo "true"`.
<br>

# v0.0.27
_Released May 8, 2020_
https://github.com/gruntwork-io/gruntwork-installer/pull/50 : Minor fixes to ensure scripts pass [shellcheck](https://www.shellcheck.net/).
<br>

# v0.0.26
_Released May 5, 2020_
https://github.com/gruntwork-io/gruntwork-installer/pull/44: Fix bugs in how `gruntwork-install` parses, passes around, and logs `--module-param` arguments to ensure whitespace is handled correctly.

Special thanks to @jeckhart for the PR!
<br>

# v0.0.25
_Released May 4, 2020_
https://github.com/gruntwork-io/gruntwork-installer/pull/46, https://github.com/gruntwork-io/gruntwork-installer/pull/47: Switch from `local readonly` to `local -r`, which is the proper way to declare local, read-only variables in Bash. 

Special thanks to @jeckhart for the fix!
<br>

# v0.0.24
_Released Jan 20, 2020_
#39 Update CodeOwners
#40 Fix broken links in readme
#41 Use a newer terragrunt version in test
<br>

# v0.0.23
_Released Aug 8, 2019_
https://github.com/gruntwork-io/gruntwork-installer/pull/34: Allow omitting github token environment variable when accessing public repo.
<br>

# v0.0.22
_Released Nov 20, 2018_
https://github.com/gruntwork-io/gruntwork-installer/pull/32: Update to fetch v0.3.2, which includes several improvements, including support for GitHub Enterprise.
<br>

# v0.0.21
_Released Mar 1, 2018_
- `gruntwork-install` now uses [v0.2.0 of fetch](https://github.com/gruntwork-io/fetch/releases/tag/v0.2.0), and supports two new parameters: ` --binary-sha256-checksum` and ` --binary-sha512-checksum`, which can be used to validate the binary asset being installed with `gruntwork-install`.
<br>

# v0.0.20
_Released Nov 16, 2017_
https://github.com/gruntwork-io/gruntwork-installer/pull/20: The bootstrap script now supports 32-bit, 686 architecture.
<br>

# v0.0.19
_Released Nov 14, 2017_
- #18: Fixed an issue where `--module-param` passed arguments surrounded by single quotes as a literal (e.g. `'value'` instead of `value`).
- #19: Add better log formatting.
<br>

# v0.0.18
_Released Nov 8, 2017_
- #16: Trivial update that nevertheless fixes a common error message.
<br>

# v0.0.17
_Released Aug 15, 2017_
https://github.com/gruntwork-io/gruntwork-installer/pull/14: Fix a bug in the Gruntwork Installer where `module-param` arguments were being wrapped in single-quotes incorrectly.
<br>

# v0.0.16
_Released Apr 10, 2017_
- UPDATE: `gruntwork-install` now accepts a parameter `--download-dir` which indicates a custom directory to which the Gruntwork Module will be downloaded and from which it will be installed. This is useful if the default download directory (`/tmp`) resides on a file system mounted with the `noexec` (no file execution allowed) option.
<br>

# v0.0.15
_Released Apr 2, 2017_
- Gruntwork-installer now installs [fetch](github.com/gruntwork-io/fetch) v0.1.1.
<br>

# v0.0.14
_Released Sep 1, 2016_
- Add Gruntwork Script Module `packer-file-copy` as a freely available module
- Improve the README explaining what `gruntwork-installer` is and why it exists.
- NOTE: Going forward, releases will now use a `v` in front of them such as `v0.0.14` to maintain consistency with our versioning scheme in other repos.

<br>

# 0.0.9
_Released Jun 4, 2016_
- Update fetch version to v0.0.4

<br>

# 0.0.8
_Released Jun 4, 2016_
- Allow installing modules from a custom repo using the `--repo` param

<br>

# 0.0.7
_Released May 18, 2016_
- Fix links to fetch constraint expressions in docs
- Add basic automated tests
- Fix handling of `--module-param` values that have spaces and equal signs in them

<br>

# 0.0.6
_Released May 9, 2016_
- Create an `/etc/user-data` folder during bootstrap as a storage place for User Data scripts

<br>

# 0.0.5
_Released May 9, 2016_
- Use `sudo` to get permissions to install in `/usr/local/bin`

<br>

# 0.0.4
_Released May 9, 2016_
- Install to `/usr/bin` instead of `/usr/local/bin`.

<br>

# 0.0.3
_Released May 9, 2016_
- Slightly more log output while downloading a module

<br>

# 0.0.2
_Released May 9, 2016_
- Fix bash command in all documentation to use `/dev/stdin`

<br>

# 0.0.13
_Released Jun 21, 2016_
- When installing binaries, `gruntwork-install` now uses `sudo` to copy them into `/usr/local/bin`

<br>

# 0.0.12
_Released Jun 20, 2016_
- Add support for installing binaries uploaded to GitHub releases with the `--binary-name` option.
- The `--repo` param is now required. It will no longer default to the script-modules repo.

<br>

# 0.0.11
_Released Jun 20, 2016_
- Update to fetch `v0.0.6`, which loads source paths in a backwards compatible way (unlike `v0.0.5`)

<br>

# 0.0.10
_Released Jun 20, 2016_
- Update to fetch `v0.0.5`, which supports installing binaries assets from releases of private GitHub repos

<br>

# 0.0.1
_Released May 9, 2016_
- Initial release

<br>

