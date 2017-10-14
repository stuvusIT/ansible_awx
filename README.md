# awx

This role sets up a local AWX installation using the Docker installation.
Non-containerized installation is not supported by AWX as of writing.

The data can be found in `/var/lib/awx`.

## Requirements

Ubuntu

## Role Variables

| Name                 | Default/Required | Description                                                                                     |
|----------------------|:----------------:|-------------------------------------------------------------------------------------------------|
| `awx_arch`           | `amd64`          | Architecture of the target CPU                                                                  |
| `awx_tunables`       |                  | Dict of all installer [tunables](https://github.com/ansible/awx/blob/devel/installer/inventory) |
| `awx_docker_storage` |                  | Storage backend to use for Docker. Uses the default when omitted.                               |
| `awx_web_mounts`     |                  | Allows mounting host files/directories into the web container. See next section                 |

### Mounts

Each mount consists of:

| Name   | Default/Required   | Description                                           |
|--------|:------------------:|-------------------------------------------------------|
| `from` | :heavy_check_mark: | Location on the host                                  |
| `to`   | `[from]`           | Location on the guest, defaults to the previous value |
| `rw`   | `false`            | Also mount writable

## Example Playbook

```yml
- hosts: awx
  roles:
  - awx
     awx_tunables:
       awx_secret_key: secretsecretkey
       host_port: 127.0.0.1:8080 # Bind to localhost
       awx_official: true # Use official AWX branding
     awx_web_mounts:
       - from: /etc/ldap/ldap.conf
         to: /etc/openldap/ldap.conf
```

## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).

## Author Information

- [Janne Heß](https://github.com/dasJ)
