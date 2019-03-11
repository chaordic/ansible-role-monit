# ansible-role-monit


# ansible-role-monit
Installs and configure [monit](https://www.systutorials.com/docs/linux/man/1-monit/) on Linux.

## Role Variables

Please look at the [defaults/main.yml](defaults/main.yml) to see all default variables.

For a simple installation and configuration, there is no mandatory variable.

## Example Playbook

```yml
---
- hosts: all
  vars:
    monit_linux_arch: linux-x64
    monit_version: 5.25.2
    monit_httpd_enable: true
    monit_services:
      - name: web-service
        start_program: /etc/init.d/web-service start
        stop_program: /etc/init.d/web-service stop
        start_timeout: 2
        extra_config: |
          if failed host localhost port 8080
          protocol HTTP request "/healthcheck" then restart

  roles:
    - role: monit.chaordic
      tags: monit
```

## Author Information
Cloud Infrastructure Team, Linx Impulse
