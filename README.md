GitHub PKI
==========

github_pki is a command that can be used to retrieve and dump SSH keys from GitHub.


## Examples

### Dump all keys from team `devops` in organization `zeorg` to `/home/bob/.ssh/authorized_keys`

```shell
$ AUTHORIZED_KEYS=/home/bob/.ssh/authorized_keys \
  GITHUB_ORG="zeorg" \
  GITHUB_TEAM="devops" \
  GITHUB_TOKEN=398d6d326b546d70f9e1ef91abad1fc5ee0f1f39 \
    github_pki
```

### Dump all keys from specified users as X509 public keys

```shell
$ SSL_DIR=/etc/software/ssl \
  GITHUB_USERS="bob,alice" \
  GITHUB_TOKEN=398d6d326b546d70f9e1ef91abad1fc5ee0f1f39 \
    github_pki
```


## Environment variables

### GITHUB_TOKEN

The Github token to use to connect to the Github API. It must allow two actions:

- read:org
- read:public_key

### GITHUB_ORG

An organization from which to select users to authorize.

### GITHUB_TEAM

A team if the provided organization from which to select users to authorize.
If not specified, all users in `GITHUB_ORG` will be authorized.

### GITHUB_USERS

A list of GitHub users to authorize.

### AUTHORIZED_KEYS

The location of the `authorized_keys` file to create.

### SSL_DIR

The location of the SSL directory where X509 public keys should be dumped.
