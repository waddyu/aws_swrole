# aws_swrole

[![Build Status][travis-badge]][travis-link]
[![Slack Room][slack-badge]][slack-link]

Switch AWS IAM Roles and start new session.

## Requirements

This plugin use these command line tools.

* [aws/aws\-cli: Universal Command Line Interface for Amazon Web Services](https://github.com/aws/aws-cli)
* [stedolan/jq: Command\-line JSON processor](https://github.com/stedolan/jq)

## Install

With [fisherman]

```
fisher waddyu/aws_swrole
```

## Usage

```fish
aws_swrole [-o] <aws profile>
```

* Print AWS_XXX environments commands with -o option.
* Without -o option, start new fish shell with AWS_XXX environments set.
* AWS Session will be expired in a hour.

## Example

```fish
$ aws_swrole
Usage: swrole [-o] <aws profile>

Defined profiles:
  development
  test
  staging
  production
```

```fish
$ aws_swrole development   
Enter MFA code > 123456

$ aws dynamodb list-tables --region ap-northeast-1
{
   "TableNames": [
       "Movies"
   ]
}
```

```fish
$ aws_swrole -o test
Enter MFA code > 123456
set -x AWS_ACCESS_KEY_ID XXXXXXXXXXXXXXXXXX
set -x AWS_SECRET_ACCESS_KEY YYYYYYYYYYYYYYYYYYYYYYYY
set -x AWS_SESSION_TOKEN ZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ
```

[travis-link]: https://travis-ci.org/waddyu/aws_swrole
[travis-badge]: https://img.shields.io/travis/waddyu/aws_swrole.svg
[slack-link]: https://fisherman-wharf.herokuapp.com
[slack-badge]: https://fisherman-wharf.herokuapp.com/badge.svg
[fisherman]: https://github.com/fisherman/fisherman
