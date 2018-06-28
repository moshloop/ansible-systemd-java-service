##  moshloop.java-systemd-service
 [![Build Status](https://travis-ci.org/moshloop/ansible-java-systemd-service.svg?branch=master)](https://travis-ci.org/moshloop/ansible-java-systemd-service)

A ansible role that installs a fat jar (commonly produced by tools like dropwizard / spring boot) as a systemd service.

### Arguments

| Argument       | Default              | Description |
| -------------- | -------------------- | ----------- |
| **jar**        | [Required]           | URL to jar  |
| install_dir    | /opt                 |             |
| filename       |                      |             |
| install_path   |                      |             |
| validate_certs | Yes                  |             |
| service        |                      |             |
| args           |                      |             |
| heap           | 50% of available RAM | Heap size   |
| jvm_opts       |                      |             |

### Example

```yaml
---
- hosts: localhost
  roles:
    - moshloop.systemd
  tasks:
    - include_role: name=moshloop.java
      vars:
        validate_certs: no
    - include_role: name=moshloop.java-systemd-service
      vars:
        jar: https://search.maven.org/remotecontent?filepath=net/sourceforge/winstone/winstone/0.9.10/winstone-0.9.10.jar
        args: --webroot /tmp
        validate_certs: no
```

