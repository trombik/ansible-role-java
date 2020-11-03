# ansible-role-java

Installs and configures Java (JDK or JRE).

## Notes for Ubuntu 14.04

At this time of writing, JDK 1.8 is not in the official apt repository. The
role adds a ppa repository and installs `oracle-java8-installer`, i.e. no JRE
support.

# Requirements

None

# Role Variables

Note that the digits in the sub-section names below does not represent versions
the role supports.

| Variable | Description | Default |
|----------|-------------|---------|
| `java_packages` | list of Java package name to install | `{{ __java_packages }}` |

## Debian-8

| Variable | Default |
|----------|---------|
| `__java_packages` | `["openjdk-8-jdk"]` |


## FreeBSD

| Variable | Default |
|----------|---------|
| `__java_packages` | `["java/openjdk13"]` |

## OpenBSD

| Variable | Default |
|----------|---------|
| `__java_packages` | `["jdk--%11"]` |

## RedHat

| Variable | Default |
|----------|---------|
| `__java_packages` | `["java-1.8.0-openjdk", "java-1.8.0-openjdk-devel"]` |

## Ubuntu-14

| Variable | Default |
|----------|---------|
| `__java_packages` | `["oracle-java8-installer"]` |

## Ubuntu-16

| Variable | Default |
|----------|---------|
| `__java_packages` | `["openjdk-8-jdk"]` |

## Ubuntu-18

| Variable | Default |
|----------|---------|
| `__java_packages` | `["openjdk-8-jdk"]` |

## Ubuntu-20

| Variable | Default |
|----------|---------|
| `__java_packages` | `["openjdk-11-jdk"]` |

# Dependencies

None

# Example Playbook

```yaml
---
- hosts: localhost
  roles:
    - role: trombik.apt_repo
      when: ansible_os_family == 'Debian'
    - role: ansible-role-java
  vars:
    os_java_packages:
      FreeBSD:
        - java/openjdk13
      RedHat:
        - java-1.8.0-openjdk
        - java-1.8.0-openjdk-devel
      OpenBSD:
        - jdk--%11
      Debian:
        - openjdk-8-jdk
    java_packages: "{{ os_java_packages[ansible_os_family] }}"
```

# License

```
Copyright (c) 2016 Tomoyuki Sakurai <y@trombik.org>

Permission to use, copy, modify, and distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
```

# Author Information

Tomoyuki Sakurai <y@trombik.org>

This README was created by [qansible](https://github.com/trombik/qansible)
