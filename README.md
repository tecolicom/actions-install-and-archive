# actions-install-and-archive

![actions-install-and-archive](https://github.com/tecoli-com/actions-install-and-archive/actions/workflows/test.yml/badge.svg)

This GitHub action execute given `command` for `target`, and archive
installed files.  Before installation, an epoch file is made, and any
files those have newer timestamp than this epoch file are archived.

This is a backend action for other series of actions and not supposed
to be used from normal workflow.

## Usage

```yaml
# inputs:
#   command:   { required: true,  type: string }
#   target:    { required: true,  type: string }
#   archive:   { required: false, type: string }
#   directory: { required: false, type: string }
#   list:      { required: false, type: string, default: "/tmp/updated-list" }
#   sudo:      { required: false, type: boolean }
#   verbose:   { required: false, type: boolean, default: false }

- uses: tecoli-com/actions-install-and-cache@v0
  with:

    # install command
    command: ''

    # install target
    target: ''

    # archive file
    # if empty, do not archive
    archive: ''

    # install directory
    # multiple directories can be specified
    # must start with /
    directory: ''

    # sudo: sudo or not
    sudo: false

    # verbose: show verbose output
    verbose: false
```

## Example

```yaml
- uses: tecoli-com/actions-install-and-cache@v0
  with:
    target: mecab mecab-ipadic-utf8
    command: apt-get install -qq
    archive: /tmp/apt-archive.tz
    sudo: true
    directory: >-
      /etc
      /usr/bin
      /usr/sbin
      /usr/lib
      /usr/share
      /var/lib
```

## See Also

### [tecoli-com/actions](https://github.com/tecoli-com/actions)

### [tecoli-com/actions-install-and-cache](https://github.com/tecoli-com/actions-install-and-cache)
