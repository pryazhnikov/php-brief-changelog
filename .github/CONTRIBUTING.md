# Contruibuting

## Log item template

See https://keepachangelog.com/en/1.0.0/

#### Added
 for new features.

#### Changed
 for changes in existing functionality.

#### Deprecated
 for soon-to-be removed features.

#### Removed
 for now removed features.

#### Fixed
 for any bug fixes.

#### Security
 in case of vulnerabilities.

## How to update calendar

You can extract all events from README file using this shell command:

```shell
grep -e '^### 2' README.md | sed -e 's/###/\*/'
```